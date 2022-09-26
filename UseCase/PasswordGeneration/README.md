# Use Case: Password Generation

[Back to Security Requirements](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/SecurityRequirements.md)

## Description:
The application should generate strong, unpredictable, non-brute forceable passwords for usage across sites and applications. 

## Alignment Analysis:
I. Security requirements deemed necessary through the use/misuse case diagramming process are as follows:
* *Star Password* - Start or blank the password to prevent shoulder surfing.
* *Strong Encryption Algorithm* - Strong cryptographic standards should be used in order to prevent the breaking of the encrypted credentials.
* *Strong Random Number Generation* - The use of a strong random number generator prevents and attacker from predicting a generated password.
* *Generated Password Complexity* - The user should be able to generate passwords with letters, numbers, and special characters to mitigate the possibility of brute forcing the password.


II. Security features included within KeePassXC in regards to prior requirements:
* *Blanks Password* - The application blanks out the password.
* *[Strong Cryptographic Standards](https://keepassxc.org/docs/KeePassXC_UserGuide.html#_database_settings)* - The application uses 256-bit AES encryption with the option of using ChaCha20 or Twofish.
* *Generated Password Complexity* - KeePassXC allows the user to specify the use of all three options when generating a password.

III. Observations:

Overall, KeePassXC meets most of the security requirements deemed necessary through the use/misuse case diagramming process. However, the KeePassXC documentation does not specify the process of generating a random password. This will need to be further investigated through source code analysis to determine the alignment with the security requirements. 

## Diagram:
<img src="Generate-PasswordV2.jpg" alt="Password Generation Diagram" />
