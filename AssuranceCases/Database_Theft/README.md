## Assurance Claim 5: The system Mitigates the effects of Database Theft
[Back to Assurance Cases](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/AssuranceCases/README.md)

### Description:
KeePassXC stores credentials in a database that may be subject to theft by a third party. Measures must be take to mitigate a third party's potential to do harm with the stolen database. The impetus of the system is to guarantee the security of the database even when in third party hands, the system achieves these goals primarily through encryption of the database and avoiding single points of failures.

### Alignment Assessment
KeePassXC provides the following evidence per the Assurance Cases identified (E1-E2) in the diagram below:

- **E1**: The system encrypts the database in a sufficiently secure manner such that stolen database files reasonably cannot be accessed by a third party. See Assurance Case: [Credential Confidentiality]().

- **E2**: **Multifactor authentication** The system implements YubiKey/OnlyKey as manners of 2 factor authentication for database encryption.

- **E3**: The system uses separate credentials for authentication with difference instances of the database. See Assurance Case: [Credential Confidentiality]().

### Diagram
<img src="AssuranceCases\Database_Theft\Assurance Case.drawio.png">
