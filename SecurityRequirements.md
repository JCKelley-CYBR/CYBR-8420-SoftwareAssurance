# Security Requirements Report
Project [Wiki](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/wiki)

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## Essential Interactions, Diagrams, and Alignment Analysis
- Use Case 1: [Autotype](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/Autotype.md)
- Use Case 2: [Export Database Entries](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/Export_Vault/readme.md)
- Use Case 3: [HaveIBeenPwned](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/HaveIBeenPwned.md)
- Use Case 4: [KeeShare](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/KeeShare.md)
- Use Case 5: [Unlocking Database](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/UseCase/Unlocking_DB.md)

## Findings Summary
### 1 - Introduction

### 2 - Commonalities

### 3 - Use Case Summaries
The findings related to each use case identified above are shown in order below.

#### 3.1 - 

#### 3.2 - 

#### 3.3 - 

#### 3.4 - 

#### 3.5 - 
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
