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
  
- *Threat ID: 15*
  - Threat Name: Authorization Bypass
  - Category: Information Disclosure
  - Description: Can you access File System and bypass the permissions for the object? For example by editing the files directly with a hex editor, or reaching it via filesharing? Ensure that your program is the only one that can access the data, and that all other subjects have to use your interface.
  - Existing Mitigations: KeePassXC does not unlock the Database if it has been tampered with.
  - Notable Gap:  **In the case of using Windows Hello, there is a possible bypass via closing the Windows Hello window.**

- *Threat ID: 16*
  - Threat Name: Data Store Denies File System Potentially Writing Data
  - Category: Repudiation
  - Description: File System claims that it did not write data received from an entity on the other side of the trust boundary. Consider using logging or auditing to record the source, time, and summary of the received data.
  - Existing Mitigations: KeePassXC trusts all file system operations.
  - Notable Gap: **KeePassXC could allow data that the file system did not write to the other side of the trust boundary. Logging is not present.**

- *Threat ID: 17*
  - Threat Name:  Potential Weak Protections for Audit Data
  - Category: Repudiation
  - Description: Consider what happens when the audit mechanism comes under attack, including attempts to destroy the logs, or attack log analysis programs. Ensure access to the log is through a reference monitor, which controls read and write separately. Document what filters, if any, readers can rely on, or writers should expect
  - Existing Mitigations: None.
  - Notable Gap: **KeePassXC does not have logging capability.**

- *Threat ID: 18*
  - Threat Name: Insufficient Auditing
  - Category: Repudiation
  - Description: Does the log capture enough data to understand what happened in the past? Do your logs capture enough data to understand an incident after the fact? Is such capture lightweight enough to be left on all the time? Do you have enough data to deal with repudiation claims? Make sure you log sufficient and appropriate data to handle a repudiation claims. You might want to talk to an audit expert as well as a privacy expert about your choice of data.
  - Existing Mitigations: None.
  - Notable Gap: **KeePassXC does not have logging cabability.**

- *Threat ID: 19*
  - Threat Name: Data Logs from an Unknown Source
  - Category: Repudiation
  - Description: Do you accept logs from unknown or weakly authenticated users or systems? Identify and authenticate the source of the logs before accepting them.
  - Existing Mitigations: None.
  - Notable Gap: **KeePassXC does not have logging cabability.**

- *Threat ID: 20*
  - Threat Name: Lower Trusted Subject Updates Logs
  - Category: Repudiation
  - Description: If you have trust levels, is anyone other outside of the highest trust level allowed to log? Letting everyone write to your logs can lead to repudiation problems. Only allow trusted code to log.
  - Existing Mitigations: None.
  - Notable Gap: **KeePassXC does not have logging cabability.**

- *Threat ID: 21*
  - Threat Name: The File System Data Store Could Be Corrupted
  - Category: Tampering
  - Description: Data flowing across User Data may be tampered with by an attacker. This may lead to corruption of File System. Ensure the integrity of the data flow to the data store.
  - Existing Mitigations: KeePass will not operate without functioning file system.
  - Notable Gap: **None.**

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
    - Existing Mitigations: KeePassXC Desktop Application runs at the system defined user trust level.
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

The KeePassXC application is not a security oriented application, as has many notable gaps in the security features. 

By outlining the overall data flow of KeePassXC and identifying potential trust boundaries, automatic threat generation revealed a number of potential security threats. In general, KeePassXC facilitates the transfer of data between one External Interactor (EI) and one Data Store (DS). Information is relayed to and from the application by the user. A single, local DS is located on the file system of the local computer.

With these entities in mind, trust boundaries were established between the User and KeePassXC, and between KeePassXC and the local filesystem. From these trust boundaries, the Microsoft Threat Modeling tool recognized a large number of automatically generated threats. From these threats, 25 were evaluated by the team as High Priority.

From these 25 established high priority threats, mitigations were formulated and justified. From these justifications, KeePassXC was canvassed for comparative flaws. While KeePassXC generally ensures authentication and encryption security, there are a number of gaps that became evident throughout the analysis.

### 4.1 Notable Gaps:

1. KeePassXC does not perform file integrity checking.
  - The KeePassXC filesystem must be 100% intact -- otherwise, the application performs a hard crash.
  - KeePassXC does not perform any types of remediation actions on the filesystem.
2. KeePassXC does not perform any logging or auditing.
3. KeePassXC runs as a user process, and therefore has access to the user file system and retains that users permissions.
4. KeePassXC does nothing to prevent excessive resource consumption.
5. In the case of using Windows Hello, a MFA authentication bypass exists within KeePassXC.
6. KeePassXC does not encrypt the datastream between the user and the application. 
7. KeePassXC does not perform any process verification.

## 5. Team Reflection

Josh's leadership continues to steer this team forward to ensure that all tasks are complete to a high standard in a timely manner. The team worked well together during all meetings thoughout the week, contributing together to the creation of the Data Flow Diagram and the subsequent Threat Modeling Report. Mitchell did an exceptional job managing the Microsoft Threat Modeling Tool and the individual threats generated were divided among the team members for indepth examination. Aaron lead the writing effort, together with the team, to evaulation the Software Security Engineering findings and gaps.

Our team continues to work together in a smooth and flexible fashion with excellent communication among members, addressing any changes to the project that needed to be made as necessary. There were no issues with our teamwork this week and our members have continued to accomplish all tasks to satisfaction.

> ### This is a __jovial__ team environment.

## Teamwork

Project Board: [Assurance Case](https://github.com/users/JCKelley-CYBR/projects/3/views/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)
