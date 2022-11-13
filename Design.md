# Design

## Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## 1. Introduction

## 2. Data Flow Diagram and Threat Modeling
  1. [KeePassXC Data Flow Diagram](Design/README.md)
  2. [Threat Modeling Report](https://htmlpreview.github.io/?https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/Design/Report.htm) This needs to be changed to the real threat modelling report when it is done
## 3. Individual Threat Review
- Threat ID: 8
  - Threat Name: Potential Process Crash or Stop for KeePassXC Desktop Application 
  - Description:	KeePassXC Desktop Application crashes, halts, stops or runs slowly; in all cases violating an availability metric. 
  - Category:	Denial Of Service
  - Existing mitigation: None known of, but we have not been able to get the program to crash
  - Notable Gap: None
- Threat ID: 9
  - Threat Name: Weak Access Control for a Resource  
  - Description:	Improper data protection of File System can allow an attacker to read information not intended for disclosure. Review authorization settings.
  - Category:	Information Disclosure
  - Existing mitigation: Runs as a user process which gives it the same file permissions that the user who runs it has
  - Notable Gap: This is an unnecessary level of permissions, as KeePassXC doesn't need access to all the user's files
- Threat ID: 10
  - Threat Name: Potential Data Repudiation by KeePassXC Desktop Application  
  - Description:	KeePassXC Desktop Application claims that it did not receive data from a source outside the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
  - Category:	Repudiation
  - Existing mitigation: KeePassXC will error with detail if a file has been tampered with or is not existent
  - Notable Gap: None
- Threat ID: 11
  - Threat Name: Data Store Inaccessible  
  - Description:	An external agent prevents access to a data store on the other side of the trust boundary.
  - Category:	Denial Of Service
  - Existing mitigation: Application errors if filesystem not intact
  - Notable Gap: KeePassXC needs the filesystem and takes no actions to automatically fix tampering
- Threat ID: 12
  - Threat Name: Data Flow User Data Is Potentially Interrupted  
  - Description:	An external agent interrupts data flowing across a trust boundary in either direction.
  - Category:	Denial Of Service
  - Existing mitigation: Application errors if the filesystem is no intact 
  - Notable Gap: KeePassXC needs the filesystem and will take no actions to fix it if found missing or corrupt
- Threat ID: 13
  - Threat Name: Potential Excessive Resource Consumption for KeePassXC Desktop Application or File System  
  - Description:	Does KeePassXC Desktop Application or File System take explicit steps to control resource consumption? Resource consumption attacks can be hard to deal with, and there are times that it makes sense to let the OS do the job. Be careful that your resource requests don't deadlock, and that they do timeout.
  - Category:	Denial Of Service
  - Existing mitigation: None
  - Notable Gap: KeePassXC does nothing to prevent excessive resource consumption
- Threat ID: 14
  - Threat Name: Data Flow Sniffing  
  - Description:	Data flowing across User Data may be sniffed by an attacker. Depending on what type of data an attacker can read, it may be used to attack other parts of the system or simply be a disclosure of information leading to compliance violations. Consider encrypting the data flow.
  - Category:	Information Disclosure
  - Existing mitigation: All data in motion is encrypted and with proper up to date versions of best practices
  - Notable Gap: None
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
