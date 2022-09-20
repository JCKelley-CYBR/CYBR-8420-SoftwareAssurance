## Use Case: Export KeePass Database


### Description:
Each user of the KeePassXC application will create and maintain their own KDBX style database in which the user's usernames, passwords, associated URLs, and associated notes will be stored. In order to export this database, KeePassXC has built in functionality to do so in teh CSV or HTML formats. The security functionality of this of this operation will be determined by analyzing the  security requirements needed to maintain a secure environment. 
### Alignment Analysis:
I. Security requirements deemed necessary through the use/misuse case diagramming process are as follows:
* *Credential Hashing* - The credentials needed to decrypt the database should be hashed and never stored in plain text in order to ensure no possible leak of credentials occurs.
* *Strong Cryptographic Standards* - Strong cryptographic standards should be used in order to prevent breaking of the hashed credentials as well as breaking of the database in general.
* *Use Yubikey or Key File "MFA"* - The password to the database does not technically constitute authentication, therefore a Yubikey or Key File would not be a "second authentication factor", however, a second form of challenge to decrypt the database would help ensure security.   
* *Blank Password* - Blank the password so that a basic shoulder surfing attempt could be thwarted.
* *Use Windows Hello Authentication* - Windows hello authentication would increase security in this instance since the database is stored locally.

II. Security features included within KeePassXC in regards to prior requirements:
* *Feat* - blah

III. Observations:

The

### Diagram: 
![](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/ExportDB-Shmuel90/UseCase/Export_Database_entries/Export%20Vault%20Use%20Case.jpg)