## Assurance Claim 3: The system minimizes information disclosure during communication
[Back to Assurance Cases](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/AssuranceCases/README.md)

### Description:
As a password manager, KeePassXC must ensure the security of the passwords it is storing. This includes during use of the passwords themselves. During use of passwords, being copying or autotype, the systems will minimize disclosure of data. 

### Alignment Assessment



- **E1**: KeePassXC does store the contents of the password to the clipboard if copied which can be insecure if someone gains access to the machine and the password is still remembered. However, the system does clear the clipboard after 10 seconds so that the user gets enough time to paste the password but it does not continue to exist afterwards.

- **E2**: A review of the source shows that no connections are made when copying a password or when using autotype to fill the password. 



### Diagram
<img src="AssuranceCase4V1.jpg">
