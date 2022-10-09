# Claim 3 - The system ensures shared credentials confidentiality

[Back to Assurance Cases](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/Adding-Claims-Remaining/AssuranceCases.md)

### Description
KeepassXC's primary responsibility is to take in user credentials and store them securely, protected by only a single password. KeePassXC allows our technicians to use far more complex password schemes without memorizing every password and reduce the risk of insecure storage, such as on a .txt document or even a sticky note. The security of this database, and subsequent database shares, are critical to maintaining the confidentiality of client login credentials and the associated systems. In order to identify a reasonable level of assurance and alleviate doubts concerning KeePassXC's ability to maintain the confidentiality of both shared and root database records, these doubts must be addressed and mitigated.

## Alignment Analysis
KeePassXC provides the following evidence per the Assurance Cases identified (E1-E4) in the diagram below:
* **E1: *AES CBC Mode*** - The cypto services offered by KeepassXC are stored in [Cypto](https://github.com/keepassxreboot/keepassxc/tree/develop/src/crypto) folder containing the different libraries and methods for encrypting, decrypting, and key creation. Keepass allows the use of AES-128 CBC, AES-256 CBC, ChaCha20, and Twofish CBC. As seen in [Crypto.cpp Line 65](https://github.com/keepassxreboot/keepassxc/blob/f56fcdd79b3e064c31fadd6be9acc5749f9aed1e/src/crypto/Crypto.cpp#L65) and [SymmetricCipher.cpp Line 152-162](https://github.com/keepassxreboot/keepassxc/blob/f56fcdd79b3e064c31fadd6be9acc5749f9aed1e/src/crypto/SymmetricCipher.cpp#L152). 
* **E2: *Hardware Randomness Library*** - KeePassXC uses the [Botan C++ library](https://botan.randombit.net/) to ensure the proper amount of entropy and generate ciphertext with a proper degree of randomness. KeePassXC random.cpp [Line 36-83](https://github.com/keepassxreboot/keepassxc/blob/f56fcdd79b3e064c31fadd6be9acc5749f9aed1e/src/crypto/Random.cpp#L36).
* **E3: *Assurance Case: User Authentication*** - KeePassXC ensures proper user authentication as shown in the accompaning [Assurance Case: The system ensures proper user authentication](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/edit/Adding-Claims-Remaining/AssuranceCases/User_Auth).
* **E4: *RFC 8018*** - KeePassXC does not use RFC-8018, but instead uses [AES KDF](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/kdf/AesKdf.cpp) or [Argon2 KDF](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/kdf/Argon2Kdf.cpp) for key deriviation. 

## Diagram
![](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/Adding-Claims-Remaining/AssuranceCases/Credential_Confidentiality/CredentialConfidentiality.png) 
