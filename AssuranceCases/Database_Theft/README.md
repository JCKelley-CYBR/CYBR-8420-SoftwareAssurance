## Assurance Claim 5: The system Mitigates the effects of Database Theft
[Back to Assurance Cases](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/AssuranceCases.md)

### Description:
KeePassXC stores credentials in a database that may be subject to theft by a third party. Measures must be taken to mitigate a third party's potential to harm the stolen database. The impetus of the system is to guarantee the security of the database even when in third-party hands. The system achieves these goals primarily through encryption of the database and avoiding single points of failure.

### Alignment Assessment
KeePassXC provides the following evidence per the Assurance Cases identified (E1-E3) in the diagram below:

- **E1**: **Database Encryption** - The system encrypts the database in a sufficiently secure manner such that stolen database files reasonably cannot be accessed by a third party. See Assurance Case: [Credential Confidentiality](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/Credential_Confidentiality).

- **E2**: **Source Code Review of MFA Implementation** - The system implements drivers for YubiKey as a manner of "2-factor authentication" for database encryption [here](https://github.com/keepassxreboot/keepassxc/tree/develop/src/keys/drivers).

- **E3**: **System separation of credentials for database instances** - The system uses separate credentials for authentication with different instances of the database. See Assurance Case: [Credential Confidentiality](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/Credential_Confidentiality).

### Diagram
<img src="Assurance Case.drawio.png">
