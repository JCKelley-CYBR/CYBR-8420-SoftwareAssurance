# Security Requirements Report
Project [Wiki](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/wiki)

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## Essential Interactions, Diagrams, and Alignment Analysis
- Use Case 1: [Use Credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/Credentials)
- Use Case 2: [Sharing Credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/SharingCredentials)
- Use Case 3: [Password Generation](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Password_Generation)
- Use Case 4: [Authenticate to Application](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Auth_To_App)
- Use Case 5: [Export Credential Vault](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Export_Vault)

## Findings Summary
### 1 - Introduction
In order to increase the security of user systems, client systems, and application credentials, KeePassXC must provide a certain level of security that can be defined through careful analysis of the essential interactions carried out with KeePassXC. Through careful analysis and understanding, these requirements can be objectified, and through an improper understanding of these interactions, small security flaws can significantly impact the business. To best analyze the KeePass XC, we have identified the five most essential interactions between our technicians and the application. The following five essential interactions were identified for the development of security requirements:
  1. Using Credentials
  2. Sharing Credentials
  3. Generating Credentials
  4. Authenticating to the Vault/Application
  5. Exporting Credential Vaults
### 2 - Commonalities
Through careful analysis of the above essential interactions, we were able to identify several commonalities between the essential interactions that are important security requirements within KeePassXC. 
* These commonalities include: unlocking database, sharing database, displaying password to user, password strength. 
* The mitigation techniques and prevention methods for these commonalities include: using strong encrypion, using computationally difficult hashing, using the password generator, and ensuring passwords are salted.

### 3 - Use Case Summaries
The findings related to each use case identified above are shown below.

#### 3.1 - [Use Credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/Credentials)
The required security components associated with actively using credentials in KeePassXC include:
  1. Clearing Clipboard contents after use
  2. Requiring user interaction before auto-filling form fields
  3. Using keystroke encryption to prevent keyloggers from stealing plaintext input from AutoType
* Utilizing robust encryption algorithms to *mitigate* the risk of exploitation of keystroke encryption. 

KeePassXC currently provides the following features that directly reference the above security components: (1) Clearing the clipboard after 10 seconds and (2) requiring the user to interact with browser forms to autofill credentials.

Through careful evaluation, we have determined that KeePassXC adequately satisfied the requirements for (1) clearing the clipboard after using credentials and (2) requiring user interaction before auto-filling browser forms.

The only major weakness we could identify in KeePassXC's use of credentials lies within the autotype feature. If a malicious actor, such as a corporate competitor or black hat hacker, manages to install a keylogger onto our system, the autotype feature exposes the plaintext password. This weakness can expose our systems and client systems to further exploitation.

#### 3.2 - [Sharing Credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/SharingCredentials)
The required security components associated with organizational sharing of credentials with KeePassXC include:
  1. KeePassXC should not allow unauthorized access to shared credentials by members of the organization.
  2. KeePassXC should not allow unauthorized or accidental modification of shared credentials by members of the organization.
  3. KeePassXC should not allow unauthorized or accidental deletion of shared credentials by members of the organization.

KeePassXC currently provides features that directly reference the above security components: (1) KeeShares can be created for only specified groups. (2) KeeShares can be created as an export-only copy of the original vault. (3) KeeShare files are automatically updated whenever a change is made to the originating vault. (4) KeeShare files are automatically recreated should they not exist in the specified directory.

After evaluating the existing features against our security requirements, we have determined that KeePassXC adequately satisfied the requirements for (1) Delineating and protecting access to a set of credentials. (2) Preventing malicious or accidental modification or deletion of the original credentials. (3) Easily restoring a KeeShare should a modification or deletion take place.

The primary weakness of implementing the credential sharing feature is the lack of verification of the shared credentials with the originals upon initially accessing the KeeShare. Additionally, setting up the KeeShare is a manual process that may allow incorrect configuration.

#### 3.3 - [Password Generation](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/PasswordGeneration)
The required security components associated with password generation in KeePassXC include: 
1. Starring out the Visible Password
2. Strong Encryption Algorithm (SHA-256)
3. Password Complexity Options (numbers, letters, special characters, variable length)
4. Strong Random Password Generation (under review)

KeePassXC currently provides the following features that directly reference the above security components: (1) Starring out the generated password, (2) using a robust encryption algorithm, and (3) providing password complexity options like the use of numbers, letters, special characters, and variable length.

The only security component which requires further review is the randomization the KeePassXC application uses to generate passwords. This process was not documented anywhere in KeePassXC's documentation and will require further review of the source code to determine the alignment with our security requirements.

#### 3.4 - [Authenticate to Application](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Auth_To_App)
The required security components associated with Authenticating to Application in KeePassXC include:
1. Input Validation and Sanitation
2. Encryption such as Argon2
3. Password Hashing such that they are computationally difficult
4. Password Salting

KeePassXC currently provides some of these security components. It provides 1. Input Validation and Sanitation, 2. Encryption, 3. Password Hashing, and 4. Password Salting.

After through evaluation, we have determined that 1. Input Validation and Sanitation, 2. Encryption, 3. Password Hashing, and 4. Password Salting meet our security requirements.

Although below in 3.5, there is an issue with authentication to application via Windows Hello. In addition, all the above labelled security components are satisfactory.


#### 3.5 - [Export Credential Vault](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Export_Vault)
The required security components associated with exporting the vault in KeePassXC include: 
1. Using credential hashing such as *SHA-256*
2. Use strong cryptographic standards such *as AES-256*
3. Use a physical token such as YubiKey
4. Use Windows Hello for additional authentication 
5. Encrypt the exported vault using at least *AES-256*

KeePassXC currently provides 1. Use of credential hashing 2. Use of strong cryptographic standards 3. Use of physical tokens, and 4. Use of Windows Hello

After additional evaluation, we have determined that the 1. Use of credential hashing 2. Use of strong cryptographic standards, and 3. The use of physical tokens all satisfies our requirements.

We have discovered that 4. Use Windows Hello for additional authentication but currently has a bypass in the application that would allow an attacker to circumnavigate the additional authentication simply by canceling it. Additionally, the application does not have an option to encrypt the vault on export. However, given the nature of the application, keeping the exported vault stored locally allows an additional password requirement. The additional password can be applied to the file, but that exits the scope of the application. 


## OSS Project Documentation Review
KeePassXC does not maintain a particular security policy. Security is somewhat dependent on the user, however issue presented to the KeePassXC developers will be dealt with in the KeePassXC Github [Issues](https://github.com/keepassxreboot/keepassxc/issues), or via e-mail.

KeePassXC documentation per the Github Repo reveal a number of security related issues. Below are a few of the most notable ones and are related to our security requirements:
* Master Password shown as clear text [#7724](https://github.com/keepassxreboot/keepassxc/issues/7724)
* Database data not cleared from RAM after lock [#7335](https://github.com/keepassxreboot/keepassxc/issues/7335)
* Keyboard clipboard is not cleared after timeout [#4126](https://github.com/keepassxreboot/keepassxc/issues/4126)
* Password generator skips special characters [#3064](https://github.com/keepassxreboot/keepassxc/issues/3064)

## Reflection
Josh led the team again this week and ensured all tasks were completed on time and with high quality. The team worked well together, and all assigned tasks were completed to the team's high standards. Josh analyzed the "credential usage" use case. Mitchell identifies the use/misuse cases for "export credential vault". Aaron worked on the "password generation" use case. Daniel worked on the "password sharing" use case. Neil worked on the "application authentication" use case. 

Josh is greatly leading our team. The team is light on their feet-willing to change to whatever is required of the project. The team is always up to providing constructive criticism while maintaining a clear path forward. No issues arose this week. The team meshed well together and accomplished the task at hand. 

> ### This is a __jovial__ team environment.

## Project Board
To view our project board, visit the Security Requirements Project board [here](https://github.com/users/JCKelley-CYBR/projects/2).

