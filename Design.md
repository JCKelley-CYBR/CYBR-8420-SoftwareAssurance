# Design

## Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## 1. Introduction
To mitigate all of the highest impact threats, all generated threats from TMT of highest priority were divided amongst the team and assessed for mitigations that already exist in the KeePassXC implementation. Each invidual threat review is listed as follows: (1) identification of the threat, (2) mitigation justification is given, (3) existing & implemented mitigations are listed, and (4) any gaps in identified threats and existing mitigations are highlighted.

## 2. Data Flow Diagram and Threat Modeling
  1. [KeePassXC Data Flow Diagram](Design/README.md)
  2. [Threat Modeling Report](https://htmlpreview.github.io/?https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/Design/Report.htm) This needs to be changed to the real threat modelling report when it is done

## 3. Individual Threat Review
- *Threat ID: 1*
  - Threat Name: Risks from Logging
  - Category: Tampering
  - Description: Log readers can come under attack via log files. Consider ways to canonicalize data in all logs. Implement a single reader for the logs, if possible, in order to reduce attack surface area. Be sure to understand and document log file elements which come from untrusted sources.
  - Existing Mitigations: KeePassXC does not use any form of logs that could be tampered with.
  - Notable Gap: None
- *Threat ID: 2*
  - Threat Name: Spoofing of Source Data Store File System
  - Category: Spoofing
  - Description: File System may be spoofed by an attacker and this may lead to incorrect data delivered to KeePassXC Desktop Application. Consider using a standard authentication mechanism to identify the source data store.
  - Existing Mitigations: No mitigations
  - Notable Gap: **KeePassXC does not conduct file integrity checks, and this sort of spoofing results in application crashing**
- *Threat ID: 3*
  - Threat Name: Spoofing the KeePassXC Desktop Application Process
  - Category: Spoofing
  - Description: KeePassXC Desktop Application may be spoofed by an attacker and this may lead to information disclosure by File System. Consider using a standard authentication mechanism to identify the destination process.
  - Existing Mitigations: No sensitive information stored in the file system
  - Notable Gap: None
- *Threat ID: 4*
  - Threat Name: Elevation by Changing the Execution Flow in KeePassXC Desktop Application
  - Category: Elevation Of Privilege
  - Description: An attacker may pass data into KeePassXC Desktop Application in order to change the flow of program execution within KeePassXC Desktop Application to the attacker's choosing.
  - Existing Mitigations: No mitigations
  - Notable Gap: **Application will crash with any changes to the base file system**
- *Threat ID: 5*
  - Threat Name: KeePassXC Desktop Application May be Subject to Elevation of Privilege Using Remote Code Execution
  - Category: Elevation Of Privilege
  - Description: File System may be able to remotely execute code for KeePassXC Desktop Application.
  - Existing Mitigations: KeePassXC trusts all file system operations
  - Notable Gap: **KeePassXC does not perform any form of file integrity checking subjecting the application to potential malicious input from the file system.**
- *Threat ID: 6*
  - Threat Name: Data Store Inaccessible
  - Category: Denial of Service
  - Description: An external agent prevents access to a data store on the other side of the trust boundary.
  - Existing Mitigations: None, in the event the application fails to communicate with the file system the application has a hard interrupt and crashes.
  - Notable Gap: **KeePassXC requires the file system to be 100% functional to perform any operation.**
- *Threat ID: 7*
  - Threat Name: Data Flow Application Data Is Potentially Interrupted
  - Category: Denial of Service
  - Description: KeePassXC Desktop Application crashes, halts, stops or runs slowly; in all cases violating an availability metric.
  - Existing Mitigations: None, in the event the application fails to communicate with the file system the application has a hard interrupt and crashes.
  - Notable Gap: **KeePassXC requires the file system to be 100% functional to perform any operation.**
  
- *Threat ID: 29*
    - Threat Name: Data Flow Sniffing
    - Category:	Information Disclosure
    - Description: Data flowing across User Input may be sniffed by an attacker. Depending on what type of data an attacker can read, it may be used to attack other parts of the system or simply be a disclosure of information leading to compliance violations. Consider encrypting the data flow.
    - Existing Mitigations: None
    - Notable Gap: **KeePassXC does not encrypt the datastream between the user and the application.**

- *Threat ID: 30*
    - Threat Name: Potential Data Repudiation by KeePassXC Desktop Application
    - Category:	Repudiation
    - Description: KeePassXC Desktop Application claims that it did not receive data from a source outside the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
    - Existing Mitigations: None
    - Notable Gap: **KeePassXC does not save any logs about the user, their activities, or the data they sent and received.**

- *Threat ID: 31*
    - Threat Name: Potential Lack of Input Validation for KeePassXC Desktop Application
    - Category:	Tampering
    - Description: Data flowing across User Input may be tampered with by an attacker. This may lead to a denial of service attack against KeePassXC Desktop Application or an elevation of privilege attack against KeePassXC Desktop Application or an information disclosure by KeePassXC Desktop Application. Failure to verify that input is as expected is a root cause of a very large number of exploitable issues. Consider all paths and the way they handle data. Verify that all input is verified for correctness using an approved list input validation approach.
    - Existing Mitigations: KeePassXC does not validate user input. However, they never perform any checking against user input either. All input that is taken from the user gets hashed and compared to another hashed value. Hashed input can be considered as safe or sanitized input, since they only contain hex characters.
    - Notable Gap: None

- *Threat ID: 32*
    - Threat Name: Spoofing the KeePassXC Desktop Application Process
    - Category:	Spoofing
    - Description: KeePassXC Desktop Application may be spoofed by an attacker and this may lead to information disclosure by User. Consider using a standard authentication mechanism to identify the destination process.
    - Existing Mitigations: None
    - Notable Gap: **KeePassXC does not perform any process verification. An attacker could spoof the process and disclose sensitive information.**

- *Threat ID: 33*
    - Threat Name: Data Flow User Interface Data Is Potentially Interrupted
    - Category:	Denial Of Service
    - Description: An external agent interrupts data flowing across a trust boundary in either direction.
    - Existing Mitigations: None
    - Notable Gap: **KeePassXC does not make any attempts to detect or deflect any Denial of Service Attacks. For this attack to be successful, the attacker would need access to the system running KeePassXC, in which case they could just steal the vault and passwords.**

- *Threat ID: 34*
    - Threat Name: External Entity User Potentially Denies Receiving Data
    - Category:	Repudiation
    - Description: User claims that it did not receive data from a process on the other side of the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
    - Existing Mitigations: None
    - Notable Gap: **KeePassXC does not save any logs about the user, their activities, or the data they sent and received.**
## 4. Design Observations Summary
This here
### 4.1 Findings:

### 4.2 Gaps:

## 5. Team Reflection

> ### This is a __jovial__ team environment.

## Teamwork

Project Board: [Assurance Case](https://github.com/users/JCKelley-CYBR/projects/3/views/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)
