# Design

## Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## 1. Introduction

## 2. Data Flow Diagram and Threat Modeling
  1. [KeePassXC Data Flow Diagram](Design/README.md)
  2. [Threat Modeling Report](https://htmlpreview.github.io/?https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/Design/Report.htm) This needs to be changed to the real threat modelling report when it is done
## 3. Individual Threat Review
- Threat ID: 
- *Threat ID: 22*
    - Threat Name: Risks from Logging
    - Category:	Tampering
    - Description: Log readers can come under attack via log files. Consider ways to canonicalize data in all logs. Implement a single reader for the logs, if possible, in order to reduce attack surface area. Be sure to understand and document log file elements which come from untrusted sources.
    - Existing Mitigations: The KeePassXC Desktop Application does not generate logs.
    - Notable Gap: **The KeePassXC Desktop Application does not generate logs, not even for debugging purposes.**

- *Threat ID: 23*
    - Threat Name: Spoofing of Destination Data Store File System
    - Category:	Spoofing
    - Description: File System may be spoofed by an attacker and this may lead to data being written to the attacker's target instead of File System. Consider using a standard authentication mechanism to identify the destination data store.
    - Existing Mitigations: The KeePassXC Desktop Application encrypts data before writing it out to the file system.
    - Notable Gap: None

- *Threat ID: 24*
    - Threat Name: Elevation by Changing the Execution Flow in KeePassXC Desktop Application
    - Category:	Elevation Of Privilege
    - Description: An attacker may pass data into KeePassXC Desktop Application in order to change the flow of program execution within KeePassXC Desktop Application to the attacker's choosing.
    - Existing Mitigations: No mitigations
    - Notable Gap: The KeePassXC Desktop Application will error out when execution flows is interrupted.

- *Threat ID: 25*
    - Threat Name: KeePassXC Desktop Application May be Subject to Elevation of Privilege Using Remote Code Execution
    - Category:	Elevation Of Privilege
    - Description: User may be able to remotely execute code for KeePassXC Desktop Application.
    - Existing Mitigations: The KeePassXC Desktop Application cannot be accessed remotely.
    - Notable Gap: None

- *Threat ID: 26*
    - Threat Name: Elevation Using Impersonation
    - Category:	Elevation Of Privilege
    - Description: The KeePassXC Desktop Application may be able to impersonate the context of User in order to gain additional privilege.
    - Existing Mitigations: KeePassXC Desktop Application runs at the system defined user trust level.
    - Notable Gap: None.

- *Threat ID: 27*
    - Threat Name: Data Flow User Input Is Potentially Interrupted
    - Category:	Denial Of Service
    - Description: An external agent interrupts data flowing across a trust boundary in either direction.
    - Existing Mitigations: The KeePassXC Desktop Application retains internal data until writing to file system.
    - Notable Gap: **The KeePassXC Desktop Application requires access to the file system to function fully.** 

- *Threat ID: 28*
    - Threat Name: Potential Process Crash or Stop for KeePassXC Desktop Application
    - Category:	Denial Of Service
    - Description: KeePassXC Desktop Application crashes, halts, stops or runs slowly; in all cases violating an availability metric.
    - Existing Mitigations: Crashes throw an error message.
    - Notable Gap: **The KeePassXC Desktop Application does not crash gracefully**


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
