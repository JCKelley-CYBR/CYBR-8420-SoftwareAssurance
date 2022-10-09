# Claim 2 - The system ensures reasonable protections from malicious user input

[Back to Assurance Cases](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/Adding-Claims-Remaining/AssuranceCases.md)

### Description
KeePassXC takes user input in multiple places. If this input is not handled correctly, it could lead to command injection, leakage of the database, or more. Due to the critical nature of this security requirement, we need assurance that malicious input has been mitigated.

## Alignment Analysis
KeePassXC provides the following evidence per the Assurance Cases identified (E1-E4) in the diagram below:
* **E1: *XSS Prevention*** - KeePassXC does not have an web interface, so XSS is not possible.
* **E2: *User Input Execution Prevention*** - KeePassXC does not execute any commands based on user inputted text. The KDBX database is accessed like an array, and only uses indexes to gather and store information, not inputted user strings. 
* **E3: *Character Testing Report*** - KeePassXC does not prohibit any characters in logins, or stored credentials. Instead, KeePassXC interprets all inputted characters as a safe representaiton of that character, and relies on the non-execution of the code to prevent execution. 
* **E4: *Executable Signing*** - KeePassXC does not sign the executable published on their Github [releases](https://github.com/keepassxreboot/keepassxc/releases/tag/2.7.1). However, they do release a signature file which can be installed, along with a SHA digest of the application. Since the signature must be installed seperately, this poses as a misalignment. 

## Diagram
![](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/Adding-Claims-Remaining/AssuranceCases/MaliciousUserInput/MaliciousUserInputV2.drawio.png) 
