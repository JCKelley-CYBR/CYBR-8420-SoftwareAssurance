## Use Case: Export Vault

### Description:
Each application user will need to create and maintain a password vault. This vault will need to be able to be exported for uses of transferring the vault or for backup and storage.  

### Alignment Analysis:
I. Security requirements deemed necessary through the use/misuse case diagramming process are as follows:
* *Credential Hashing* - The credentials needed to decrypt the database should be hashed and never stored in plain text in order to ensure no possible leak of credentials occurs.
* *Strong Cryptographic Standards* - Strong cryptographic standards should be used in order to prevent the breaking of the hashed credentials as well as the breaking of the database in general.
* *Use MFA Physical Token* - The second form of physical challenge to decrypt the database would help ensure security even against social engineering attacks.   
* *Blanks Password* - Blank the password so that a primary shoulder surfing attempt could be thwarted.
* *Use Windows Hello Authentication* - Windows hello authentication would increase security in this instance since the database is stored locally.
* *Encrypt Vault* - An encrypted vault would be the most secure way to store it after exporting.

II. Security features included within KeePassXC in regards to prior requirements:
* *Blanks Password* - The application does blank the password.
* *[Yubikey or Key File](https://keepassxc.org/project/)* - The application allows users of a Yubikey or Key File that provides an additional challenge before decryption.
* *[Strong Cryptographic Standards](https://keepassxc.org/docs/KeePassXC_UserGuide.html#_database_settings)* - The application uses 256-bit AES encryption with the option of using ChaCha20 or Twofish.
* *[Windows Hello](https://keepassxc.org/docs/KeePassXC_GettingStarted.html#_quick_unlock)* - The application uses Windows Hello authentication as a way to unlock the database as an additional challenge or can be configured for a quick unlock.

III. Observations:

KeePassXC does an excellent job of performing security on the database export function. The encryption is of quality standard. Using an "MFA" key thwarts many attack vectors, and Windows Hello provides an additional layer of security before the database can be exported. However, an excellent option for the export would be to export it encrypted. This is not a significant issue as the database remains local. This would be a requirement if it were to travel through the internet. Since it remains local, the scope starts to fall into the environment as to whether it should be a requirement or not. 

Additionally, when performing tests on the application, we discovered a bypass to the Windows Hello authentication, which means that it is present but needs to be fixed before it is effective. 

### Diagram: 
<img src="Export Vault Use CaseV6.jpg">
