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
  
  *Overview:* KeepassXC uses a variety of methods to ensure that the security of the password vault is not compromised and information is not disclosed. Using AES-256 for master password encryption, randomly generated adjustable salts, a backoff period for the password entry, key derivation using Argon2. As well as other methods of security. There are a couple of adjustable security features a long length of all of them are reccomended. Those are some of the gaps that can be seen on the user end. There are considerations to databse security which is covered in assurance claim 5.
  
  *Conclusion:* Per assurance claim 1, the KeePassXC application exhibits high alignment with the assurance cases with the assurance cases developed in this study.

* Assurance Claim 2 - [The system secures storage of credentials](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Credential_Storage/README.md)
- 
* Assurance Claim 3 - [The system ensures shared credentials confidentiality](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Credential_Confidentiality)

  *Overview:* KeepassXC takes many steps to protect the confidentiality of the information stored in the root databases and subsequent database shares. AES-128 CBC, AES-256 CBC, ChaCha20, and Twofish CBC encryption are used to encrypt the database. The default encryption method is AES-256 CBC in conjunction with using the KBX4 database type. In order for the system to ensure true randomness for generated ciphertext, KeePassXC utilizes the Botan C++ library. The details, including the effectiveness, remain unknown as there is little relevant documentation available from KeePassXC. The use of proper authentication mechanisms is critical to the security of the root database and the security of subsequent database shares of either individual or groups of credentials. Finally, AES or Argon2 is used for the essential derivation function (KDF), which generates a key from the users' input password and stretches that key per secret key generation best practices. Further analysis of the source code could reveal a gap in the KDF via not adequately stretching the generated secret key.

  *Conclusion:* Per assurance claim 3, the KeePassXC application provides a reasonably high level confidentiality in alignment with the assurance cases developed during this analysis. There is still more analysis required to adequately dispell all doubts raised in the assurance cases that could identify significant gaps in the application. E2 with the Botan C++ Library and E4 with KeePassXC's method of KDF are two potential gaps.

* Assurance Claim 4 - [The system minimizes information disclosure during communication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Communication_Disclosure)

  *Overview*: KeePassXC takes some steps to minimize information disclosure during communication. The first of the major ways this is done is by  keeping the communication solely local. There is never a time where the communication traffic is sent outside of the local network, which can be seen by inspecting the source of the software. The second major way the software does this is by clearing the clipboard after 10 seconds by default if any credentials are copied to it. This however only works if the credentials are copied by the software and not an outside source such as the Windows copy function. This can be seen by a live system test or in the source code. A few other areas exist where KeePassXC could improve the assurance claim, including autotype, and copying. In autotype the software could encrypt its keystrokes to ensure no malicious software present can read typed credentials. For copying, the software could also block any copy function other than that of KeePassXC itself so that it can always clear the clipboard.

  *Conclusion*: Overall, the software does a good job to prove assurance claim 4. There is some ways to improve the software, but as it is, KeePassXC does a good job of minimizing information disclosure during communication. The gaps that remain are the lack of protection of autotype, and the software allows circumnavigation of copy protections.  

* Assurance Claim 5 - [The system mitigates the impacts of database theft](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Database_Theft)
- 

## Reflection

## Teamwork

Project Board: [Assurance Case](https://github.com/users/JCKelley-CYBR/projects/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)
