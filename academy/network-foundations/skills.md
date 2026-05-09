# Skills Assessment

```
$ sudo nmap -sV -p 21,80 10.129.4.137

Starting Nmap 7.99 ( https://nmap.org ) at 2026-05-09 19:06 +0200
Nmap scan report for 10.129.4.137
Host is up (0.063s latency).

PORT   STATE SERVICE VERSION
21/tcp open  ftp     Microsoft ftpd
80/tcp open  http    Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.61 seconds
```

We can open an anonymous connection channel with the FTP server:

```
$ nc 10.129.4.137 21

220 Microsoft FTP Service
USER anonymous^M
331 Anonymous access allowed, send identity (e-mail name) as password.
PASS abc^M
230 User logged in.
```

We enter passive mode:

```
PASV^M
227 Entering Passive Mode (10,129,4,137,194,11).
```

Then, noting these numbers, we can submit our instruction:

```
LIST^M
```

To calculate the port number for the data channel where we will receive the return data from this instruction: `194 * 256 + 11 = 49675`. We have to be really fast about opening the data channel _just_ after sending the `LIST` instruction.

```
$ nc -v 10.129.4.137 49675

10.129.4.137: inverse host lookup failed: Unknown host
(UNKNOWN) [10.129.4.137] 49675 (?) open

02-08-25  09:37PM                  438 Note-From-IT.txt
```

We can note a `Note-From-IT.txt` is present on the FTP server. Let's retrieve it (we have to re-enter passive mode and we will get a new data channel port number):

```
PASV^M
227 Entering Passive Mode (10,129,4,137,194,12).
RETR Note-From-IT.txt
```

Then we connect to the data channel:

```
$ nc -v 10.129.4.137 49676

10.129.4.137: inverse host lookup failed: Unknown host
(UNKNOWN) [10.129.4.137] 49676 (?) open

Bertolis,

The website is still under construction. To stop users from poking their nose where it doesn't belong, I've configured IIS to only allow requests containing a specific user-agent header. If you'd like to test it out, please provide the following header to your HTTP request.

User-Agent: Server Administrator

The site should be finished within the next couple of weeks. I'll keep you posted.

Cheers,
jarednexgent

```

According to `Note-From-IT.txt`, the web server on port 80 is employing **packet filtering**, accepting only requests with the `User-Agent: Server Administrator` HTTP header set.

We can use `nc` again to connect to the HTTP format and send a crafted request:

```
$ nc 10.129.4.137 80

GET / HTTP/1.1
Host: 10.129.4.137
User-Agent: Server Administrator

// ...

HTTP/1.1 200 OK
Content-Type: text/html
Last-Modified: Fri, 07 Feb 2025 20:46:15 GMT
Accept-Ranges: bytes
ETag: "5acd7854a179db1:0"
Server: Microsoft-IIS/10.0
Date: Sat, 09 May 2026 17:22:04 GMT
Content-Length: 746

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>IIS Windows Server</title>
<style type="text/css">
<!--
body {
        color:#000000;
        background-color:#0072C6;
        margin:0;
}

#container {
        margin-left:auto;
        margin-right:auto;
        text-align:center;
        }

a img {
        border:none;
}

-->
</style>
</head>
<body>
<div id="container">
<a href="http://go.microsoft.com/fwlink/?linkid=66138&amp;clcid=0x409"><img src="iisstart.png" alt="IIS" width="960" height="600" /></a>
</div>
</body>
</html>
<!-- HTB{S00n_2_B_N3tw0rk1ng_GURU!} -->
```

All the way at the bottom we find our flag!
