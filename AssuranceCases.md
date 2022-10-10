# Assurance Case Report

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## Claims, Arguments, and Detailed Alignment Assessments
* Claim 1 - [The system ensures proper user authentication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/User_Auth)
* Claim 2 - [The system ensures reasonable protections from malicious user input](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/MaliciousUserInput)
* Claim 3 - [The system ensures shared credentials confidentiality](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/Credential_Confidentiality)
* Claim 4 - [The system minimizes information disclosure during communication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/Comms_Disclosure)
* Claim 5 - [The system mitigates the impacts of database theft](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/Database_Theft)

## Alignment Assessment Summary
* Assurance Claim 1 - [The system ensures proper user authentication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/User_Auth)
  
  *Overview:* KeepassXC uses various methods to ensure that the security of the password vault is not compromised and that information is not at risk of disclosure. Using AES-256 for master password encryption, randomly generated adjustable salts, a backoff period for the password entry, and key derivation using Argon2. There are a couple of adjustable security features, an extended length of which is recommended. Those are some of the gaps that can be seen on the user end. There are considerations to database security, which are covered in [Assurance Claim 5](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/Database_Theft).
  
  *Conclusion:* Per assurance claim 1, the KeePassXC application exhibits high alignment with the assurance cases developed in this study. There are some gaps in terms of evidence. For example, there is no obvious way to determine the minimum length of a salt. A complete guarantee cannot be placed on this claim.

* Assurance Claim 2 - [The system ensures reasonable protections from malicious user input](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/MaliciousUserInput)
  *Overview:* KeePassXC takes a few steps to protect from malicious user input. KeePassXC does not have a web interface, dramatically reducing the attack surface for malicious user input and eliminating attack vectors such as cross-site scripting (XSS). To ensure the application is secure from attacks like command injection, KeePAssXC ensures that no user input is ever used in a command or record lookup. Nevertheless, all user input is escaped to a safe version of the string to prevent widespread misuse of user input. However, KeePassXC does not sign the executable published on their GitHub releases. They release a signature file that can be installed and an SHA digest of the application, but this does not satisfy our Assurance Case.

  *Conclusion:* Per assurance claim 2, the KeePassXC application provides a reasonably high level of protection from malicious user input, mostly aligned without assurance cases developed during this analysis. There are ways for KeePAssXC to improve in this area and extra steps we can take to assist, but as it is, our confidence is relatively high that the application has sufficient protection. It is excellent to see that KeePassXC uses no user-defined strings in any queries or commands and sanitizes all user input just in case. However, the lack of a code signature is somewhat concerning. More analysis will be required to dispel all doubts raised in the assurance cases.
* Assurance Claim 3 - [The system ensures shared credentials confidentiality](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/Credential_Confidentiality)

  *Overview:* KeepassXC takes many steps to protect the confidentiality of the information stored in the root databases and subsequent database shares. AES-128 CBC, AES-256 CBC, ChaCha20, and Twofish CBC encryption are used to encrypt the database. The default encryption method is AES-256 CBC in conjunction with using the KBX4 database type. In order for the system to ensure true randomness for generated ciphertext, KeePassXC utilizes the Botan C++ library. The details, including the effectiveness, remain unknown as there is little relevant documentation available from KeePassXC. The use of proper authentication mechanisms is critical to the security of the root database and the security of subsequent database shares of either individual or groups of credentials. Finally, AES or Argon2 is used for the essential derivation function (KDF), which generates a key from the users' input password and stretches that key per secret key generation best practices. Further analysis of the source code could reveal a gap in the KDF via not adequately stretching the generated secret key.

  *Conclusion:* Per assurance claim 3, the KeePassXC application provides reasonably high-level confidentiality in alignment with the assurance cases developed during this analysis. More analysis is required to adequately dispel all doubts raised in the assurance cases that could identify significant gaps in the application. E2 with the Botan C++ Library and E4 with KeePassXC's method of KDF are two potential gaps.

* Assurance Claim 4 - [The system minimizes information disclosure during communication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/Comms_Disclosure)

  *Overview*: KeePassXC takes some steps to minimize information disclosure during communication. The first method is to keep the communication solely local. There is never a time when the communication traffic is sent outside the local network, which can be seen by inspecting the source of the software. The second significant way the software does this is by clearing the clipboard after 10 seconds by default if any credentials are copied to it. This technique only works if credentials are copied by the software and not an outside source, such as the Windows copy function. This behavior can be analyzed in a live system test or source code. Other areas exist where KeePassXC could improve the assurance claim, including autotype and copying. In autotype, the software could encrypt its keystrokes to ensure no malicious software present can read typed credentials. The software could also block any copy function other than that of KeePassXC itself to always clear the clipboard.

  *Conclusion*: The software does an excellent job proving assurance claim 4. There are ways to improve the software, but as it is, KeePassXC does a reasonable job of minimizing information disclosure during communication. The remaining gaps are the lack of autotype protection and allowing circumnavigation of clipboard protections.   

* Assurance Claim 5 - [The system mitigates the impacts of database theft](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/AssuranceCases/Database_Theft)
- 

## Reflection
  Josh continued to lead the team this week and ensured all tasks were completed on time and of high quality. The team worked well together, and all assigned tasks were to the team's high standards. Josh analyzed the "The system ensures shared credentials confidentiality" assurance case. Mitchell analyzed the "The system minimizes information disclosure during communication" assurance case. Aaron worked on the "The system ensures reasonable protections from malicious user input" assurance case. Daniel worked on the "The system mitigates the impacts of database theft" assurance case. Neil worked on the "The system ensures proper user authentication" assurance case. 

  Josh's leadership continues to satisfy the team's needs. The team is still working great with one another to complete the task's goals. Constructive criticism is exchanged, which helps our groups meet the quality standards set. No issues arose this week. The team continues to work well as a unit and accomplish our weekly goals. 

> ### This is a __jovial__ team environment.

## Teamwork

Project Board: [Assurance Case](https://github.com/users/JCKelley-CYBR/projects/3/views/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)
