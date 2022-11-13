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
    - Justification: Logs do not contain sensitive information
    - Existing Mitigations: 
    - Notable Gap: 

- *Threat ID: 23*
    - Threat Name: Spoofing of Destination Data Store File System
    - Category:	Spoofing
    - Description: File System may be spoofed by an attacker and this may lead to data being written to the attacker's target instead of File System. Consider using a standard authentication mechanism to identify the destination data store.
    - Justification: Nothing sensitive is written to the file system. File system requires user level authentication on the system.
    - Existing Mitigations: The logs written contain only a minimal amount of information. It's composed of mostly unique IDs, timestamps, and IPs. The file system requires the system defined user trust level.
    - Notable Gap:

- *Threat ID: 24*
    - Threat Name: Elevation by Changing the Execution Flow in KeePassXC Desktop Application
    - Category:	Elevation Of Privilege
    - Description: An attacker may pass data into KeePassXC Desktop Application in order to change the flow of program execution within KeePassXC Desktop Application to the attacker's choosing.
    - Justification: 
    - Existing Mitigations: 
    - Notable Gap: 

- *Threat ID: 25*
    - Threat Name: KeePassXC Desktop Application May be Subject to Elevation of Privilege Using Remote Code Execution
    - Category:	Elevation Of Privilege
    - Description: User may be able to remotely execute code for KeePassXC Desktop Application.
    - Justification: 
    - Existing Mitigations: 
    - Notable Gap: 

- *Threat ID: 26*
    - Threat Name: Elevation Using Impersonation
    - Category:	Elevation Of Privilege
    - Description: KeePassXC Desktop Application may be able to impersonate the context of User in order to gain additional privilege.
    - Justification: 
    - Existing Mitigations: 
    - Notable Gap: 

- *Threat ID: 27*
    - Threat Name: Data Flow User Input Is Potentially Interrupted
    - Category:	Denial Of Service
    - Description: An external agent interrupts data flowing across a trust boundary in either direction.
    - Justification: An operating System error event is created. Application can function without the file system.
    - Existing Mitigations: Application recreates files that are missing
    - Notable Gap: **KeePassXC needs the file system to function correctly.** 

- *Threat ID: 28*
    - Threat Name: Potential Process Crash or Stop for KeePassXC Desktop Application
    - Category:	Denial Of Service
    - Description: KeePassXC Desktop Application crashes, halts, stops or runs slowly; in all cases violating an availability metric.
    - Justification: Coding best practices utilized.
    - Existing Mitigations: crashes throwing an error message.
    - Notable Gap: **does not crash gracefully**


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
