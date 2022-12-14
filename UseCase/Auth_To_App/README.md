# Authenticate To Application

[Back to Security Requirements](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/SecurityRequirements.md)

## Description
KeePassXC is based around an encrypted database file with a master password selected by the user. To access the database file, the user must log in using KeePassXC. As such, the software must ensure that security is enforced through use.

## Alignment Analysis
1. The use/misuse case diagram determined the below security requirements.
* Input Validation and Sanitation: Any input from users should be validated and sanitized. Ensuring the login function can be exploited to skip authentication or execute malicious code.
* Encryption: Strong encryption is needed to ensure that the database cannot be exploited when locked/logging in or that sessions cannot be hijacked while using the ssh-agent.
* Password Hashing: Hashes of passwords must be computationally complex to ensure the password database is secure.
* Password Salting: Ensures the security of the database and mitigates threats from rainbow tables.
2. Below are the security features implement
* Argon2 Key derivation for password hashing
* HMAC-SHA-256 for header data [authentication](https://keepassxc.org/docs/KeePassXC_UserGuide.html#_database_operations)
* Hardware call-response [challenge](https://keepassxc.org/docs/KeePassXC_UserGuide.html#_database_operations)

<img src="Authenticate_To_Application_Misuse_Case_diagramV2.jpg">
