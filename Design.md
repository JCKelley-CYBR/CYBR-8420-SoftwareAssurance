# Design

## Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## 1. Introduction

## 2. Data Flow Diagram and Threat Modeling
  1. [KeePassXC Data Flow Diagram](Design/README.md)
  2. [Threat Modeling Report](https://htmlpreview.github.io/?https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/Design/Report.htm) This needs to be changed to the real threat modelling report when it is done
## 3. Individual Threat Review
- Threat ID: 1
  - Threat Name: Risks from Logging
  - Category: Tampering
  - Description: Log readers can come under attack via log files. Consider ways to canonicalize data in all logs. Implement a single reader for the logs, if possible, in order to reduce attack surface area. Be sure to understand and document log file elements which come from untrusted sources.
  - Existing Mitigations: KeePassXC does not use any form of logs that could be tampered with.
  - Notable Gap: None
- Threat ID: 2
  - Threat Name: Spoofing of Source Data Store File System
  - Category: Spoofing
  - Description: File System may be spoofed by an attacker and this may lead to incorrect data delivered to KeePassXC Desktop Application. Consider using a standard authentication mechanism to identify the source data store.
  - Existing Mitigations: No mitigations
  - Notable Gap: **KeePassXC does not conduct file integrity checks, and this sort of spoofing results in application crashing**
- Threat ID: 3
  - Threat Name: Spoofing the KeePassXC Desktop Application Process
  - Category: Spoofing
  - Description: KeePassXC Desktop Application may be spoofed by an attacker and this may lead to information disclosure by File System. Consider using a standard authentication mechanism to identify the destination process.
  - Existing Mitigations: No sensitive information stored in the file system
  - Notable Gap: None
- Threat ID: 4
  - Threat Name: Elevation by Changing the Execution Flow in KeePassXC Desktop Application
  - Category: Elevation Of Privilege
  - Description: An attacker may pass data into KeePassXC Desktop Application in order to change the flow of program execution within KeePassXC Desktop Application to the attacker's choosing.
  - Existing Mitigations: No mitigations
  - Notable Gap: **Application will crash with any changes to the base file system**
- Threat ID: 5
  - Threat Name: KeePassXC Desktop Application May be Subject to Elevation of Privilege Using Remote Code Execution
  - Category: Elevation Of Privilege
  - Description: File System may be able to remotely execute code for KeePassXC Desktop Application.
  - Existing Mitigations: KeePassXC trusts all file system operations
  - Notable Gap: **KeePassXC does not perform any form of file integrity checking subjecting the application to potential malicious input from the file system.**
- Threat ID: 6
  - Threat Name: Data Store Inaccessible
  - Category: Denial of Service
  - Description: An external agent prevents access to a data store on the other side of the trust boundary.
  - Existing Mitigations: None, in the event the application fails to communicate with the file system the application has a hard interrupt and crashes.
  - Notable Gap: **KeePassXC requires the file system to be 100% functional to perform any operation.**
- Threat ID: 7
  - Threat Name: Data Flow Application Data Is Potentially Interrupted
  - Category: Denial of Service
  - Description: KeePassXC Desktop Application crashes, halts, stops or runs slowly; in all cases violating an availability metric.
  - Existing Mitigations: None, in the event the application fails to communicate with the file system the application has a hard interrupt and crashes.
  - Notable Gap: **KeePassXC requires the file system to be 100% functional to perform any operation.**
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
