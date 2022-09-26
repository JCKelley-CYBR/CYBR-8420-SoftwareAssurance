# Security Requirements Report
Project [Wiki](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/wiki)

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## Essential Interactions, Diagrams, and Alignment Analysis
- Use Case 1: [Use Credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/Credentials)
- Use Case 2: [Sharing Credentials](UPDATE ME)
- Use Case 3: [Generate Credentials](UPDATE ME)
- Use Case 4: [Authenticate to Application](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Auth_To_App)
- Use Case 5: [Export Credential Vault](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Export_Vault)

## Findings Summary
### 1 - Introduction
In order to increase the security of user systems, client systems, and application credentials, KeePassXC must provide a certain level of security that can be defined through careful analysis of the essential interactions carried out with KeePassXC. Through careful analysis and understanding these requirements can be objectified, and through improper understanding of these interactions small security flaws can result in significant impacts to the business. To best analyze the KeePass XC we have identified the five most essential interactions between our technicians and the application. The following five essential interactions were identified for the development of security requirements:
  1. Using Credentials
  2. Sharing Credentials
  3. Generating Credentials
  4. Authenticating to the Vault/Application
  5. Exporting Credential Vaults
### 2 - Commonalities
Through careful analysis of the above essential interactions, we were able to identify several commonalities between the essential interactions that are important security requirements within KeePassXC. These commonalities include: The mitigation techniques and prevention methods for these commonalities include:
### 3 - Use Case Summaries
The findings related to each use case identified above are shown in order below.

#### 3.1 - [Use Credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/Credentials)
The required security components associated with actively using credentials in KeePassXC include:
  1. Clearing Clipboard contents after use
  2. Requiring user interaction before auto-filling form fields
  3. Using keystroke encryption to prevent keyloggers from stealing plaintext input from AutoType
* Utilizing robust encryption algorithms to *mitigate* the risk of exploitation of keystroke encryption. 

KeePassXC currently provides the following features that directly reference the above security components: (1) Clearing the clipboard after 10 seconds and (2) requiring the user to interact with browser forms to autofill credentials.

Through careful evaluation, we have determined that KeePassXC adequately satisfied the requirements for (1) clearing the clipboard after using credentials and (2) requiring user interaction before auto-filling browser forms.

The only major weakness we could identify in KeePassXC's use of credentials lies within the autotype feature. If a malicious actor, such as a corporate competitor or black hat hacker, manages to install a keylogger onto our system, the autotype feature exposes the plaintext password. This weakness can expose our systems and client systems to further exploitation.

#### 3.2 - [Sharing Credentials](UPDATE ME)

#### 3.3 - [Generate Credentials](UPDATE ME)

#### 3.4 - [Authenticate to Application](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Auth_To_App)
The required security components associated with Authenticating to Application in KeePassXC include:
1. Input Validation and Sanitation
2. Encryption such as Argon2
3. Password Hashing such that they are computationally difficult
4. Password Salting


#### 3.5 - [Export Credential Vault](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/UseCase/Export_Vault)
The required security components associated with exporting the vault in KeePassXC include: 
1. Using credential hashing 
2. Use strong cryptographic standards
3. Use a physical token
4. Use Windows Hello for additional authentication 
5. Encrypt the exported vault

KeePassXC currently provides 1. Use of credential hashing 2. Use of strong cryptographic standards 3. Use of physical tokens and 4. Use of Windows Hello

After additional evaluation, we have determined that the 1. Use of credential hashing 2. Use of strong cryptographic standards and 3. Use of physical tokens all satisfy our requirements.

We have discovered that 4. Use Windows Hello for additional authentication is present, but currently has a bypass in the application that would allow an attacker to circumnavigate the additional authentication simply by cancelling it. Additionally, the application does not have an option to encrypt the vault on export. However, given the nature of the application keeping the exported vault always local, an additional introduction of a password can be applied to the file, but that exits the scope of the application. 


## OSS Project Documentation Review

## Reflection

## Teamwork
To view our project board, visit the Security Requirements Project board [here](https://github.com/users/JCKelley-CYBR/projects/2).
