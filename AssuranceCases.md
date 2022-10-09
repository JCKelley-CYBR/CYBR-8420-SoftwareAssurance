# Assurance Case Report

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec



## Claims, Arguments, and Detailed Alignment Assessments
* Claim 1 - [The system ensures proper user authentication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/User_Auth)
* Claim 2 - [The system secures storage of credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Credential_Storage)
* Claim 3 - [The system ensures shared credentials confidentiality](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Credential_Confidentiality)
* Claim 4 - [The system minimizes information disclosure during communication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Communication_Disclosure)
* Claim 5 - [The system mitigates the impacts of database theft](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Database_Theft)

## Alignment Assessment Summary
* Assurance Claim 1 - [The system ensures proper user authentication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/User_Auth)
- 
* Assurance Claim 2 - [The system secures storage of credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Credential_Storage/README.md)
- 
* Assurance Claim 3 - [The system ensures shared credentials confidentiality](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Credential_Confidentiality)
*Overview:* KeepassXC takes many steps to protect the confidentiality of the information stored in the root databases and subsequent database shares. AES-128 CBC, AES-256 CBC, ChaCha20, and Twofish CBC encryption are used to encrypt the database. The default encryption method is AES-256 CBC in conjunction with using the KBX4 database type. In order for the system to ensure true randomness for generated ciphertext, KeePassXC utilizes the Botan C++ library. The details, including the effectiveness, remain unknown as there is little relevant documentation available from KeePassXC. The use of proper authentication mechanisms is critical to the security of the root database and the security of subsequent database shares of either individual or groups of credentials. Finally, AES or Argon2 is used for the essential derivation function (KDF), which generates a key from the users' input password and stretches that key per secret key generation best practices. Further analysis of the source code could reveal a gap in the KDF via not adequately stretching the generated secret key.
*Conclusion:* Per assurance claim 3, the KeePassXC application provides a reasonably high level confidentiality in alignment with the assurance cases developed during this analysis. There is still more analysis required to adequately dispell all doubts raised in the assurance cases that could identify significant gaps in the application. E2 with the Botan C++ Library and E4 with KeePassXC's method of KDF are two potential gaps.
* Assurance Claim 4 - [The system minimizes information disclosure during communication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Communication_Disclosure)
- 
* Assurance Claim 5 - [The system mitigates the impacts of database theft](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Database_Theft)
- 
## Reflection

## Teamwork

Project Board: [Assurance Case](https://github.com/users/JCKelley-CYBR/projects/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)
