# Introduction To Information Security

| Principle       | Prevents                           |
| --------------- | ---------------------------------- |
| Confidentiality | Unauthorized access                |
| Integrity       | Unauthorized modification          |
| Availability    | Disruption of access               |
| Non-repudiation | Denial of authenticity             |
| Authentication  | Access with unknown identity       |
| Privacy         | Disclosure of personal information |

| Processes                           | Goal                                                 |
| ----------------------------------- | ---------------------------------------------------- |
| Risk assessment                     | Determine impact of security breach                  |
| Security planning                   | Develop strategies to address risks                  |
| Implementation of security controls | Deploy technical solutions that address risks        |
| Monitoring and detection            | Continuously watch for intrusion                     |
| Incident response                   | Contain and mitigate threats after security incident |
| Disaster recovery                   | Restore systems and data after major incident        |
| Continuous improvement              | Update measures based on learned experience          |

## Purposes

- Protecting sensitive data from unauthorized access
- Ensuring business continuity
- Maintaining regulatory compliance
- Preserving brand reputation
- Safeguarding intellectual property
- Enabling secure digital transformation

## Domains

### Network Security

| Element                                                  | Description                                                          |
| -------------------------------------------------------- | -------------------------------------------------------------------- |
| Firewalls                                                | Barrier between internal and external networks                       |
| Intrusion Detection and Prevention Systems (`IDS`/`IPS`) | Monitor network traffic (and take action to block malicious traffic) |
| Virtual Private Networks (VPNs)                          | Provide secure encrypted connection over public networks             |
| Access control mechanisms                                | Ensure only legitimate users can access network resources            |
| Encryption technologies                                  | Protect sensitive data both in transit and at rest                   |

### Application Security

1. Develop the app
2. Test for vulnerabilities
3. Ongoing security monitoring

Developing an app following **Security by Design**, security is considered right from the planning stage:

- Threat modeling (identify potential risks)
- Security-focused code reviews
- Server and database security
- Authentication and authorization

### Operational Security

| Step | Process                      | Description                                       |
| ---- | ---------------------------- | ------------------------------------------------- |
| 1    | Asset identification         | What is most important to protect?                |
| 2    | Threat identification        | Where could attacks come from                     |
| 3    | Vulnerability identification | How could attackers get to what's important       |
| 4    | Access control               | Implement security measures now the risk is known |
| 5    | Monitoring                   | Continuously watching for new threats and changes |

### Disaster Recovery and Business Continuity

- **Disaster recovery** involves restoring critical systems quickly after they failed
- **Business continuity** involves maintaining operations during and after a disruption

### Cloud Security

| Key Area                               | Description                                                                       |
| -------------------------------------- | --------------------------------------------------------------------------------- |
| Data protection                        | Encrypting data at rest and in transit                                            |
| Identity and access management (`IAM`) | Ensuring only authorized users can attain access                                  |
| Network security                       | Installing firewalls and VPNs to protect data in transit                          |
| Compliance and governance              | Ensure data handling and storage follow industry standards and legal requirements |

### Physical Security

- Unsecured access points
- Weak locks
- Inadequate perimeter security
- Poor key management
- Insufficient lighting
- Exposed IT infrastructure
- Lack of visitor management
- Unattended workstations

### Mobile Security

| Security Layer | Measures                                           |
| -------------- | -------------------------------------------------- |
| Device         | Passcodes, biometric authentication, remote wipe   |
| Data           | Encryption                                         |
| Network        | VPNs                                               |
| Application    | Vetting, permission management, secure development |

### Internet of Things Security

| Party                  | Responsibility                                                     |
| ---------------------- | ------------------------------------------------------------------ |
| Device manufacturers   | Build hardware with security in mind                               |
| Network administrators | Enable network segmentation and intrusion detection systems        |
| Application developers | Implement proper authentication methods and manage data encryption |
