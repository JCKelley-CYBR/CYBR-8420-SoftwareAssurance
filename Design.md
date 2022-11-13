# Design

## Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## 1. Introduction

## 2. Data Flow Diagram and Threat Modeling
  1. [KeePassXC Data Flow Diagram](Design/README.md)
  2. [Threat Modeling Report](https://htmlpreview.github.io/?https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/Design/Report.htm) This needs to be changed to the real threat modelling report when it is done

## 3. Individual Threat Review

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
