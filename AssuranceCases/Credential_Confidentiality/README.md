# Claim 3 - The system ensures shared credentials confidentiality

[Back to Assurance Cases](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/Adding-Claims-Remaining/AssuranceCases.md)

### Description
KeepassXC's primary responsibility is to take in user credentials and store them securely, protected by only a single password. KeePassXC allows our technicians to use far more complex password schemes without memorizing every password and reduce the risk of insecure storage, such as on a .txt document or even a sticky note. The security of this database, and subsequent database shares, are critical to maintaining the confidentiality of client login credentials and the associated systems. In order to identify a reasonable level of assurance and alleviate doubts concerning KeePassXC's ability to maintain the confidentiality of both shared and root database records, these doubts must be addressed and mitigated.

## Alignment Analysis
KeePassXC provides the following evidence per the Assurance Cases identified (E1-E4) in the diagram below:
* **E1:** *AES CBC Mode* - 
* **E2:** *Hardware Randomness Library* - 
* **E3:** *Assurance Case: User Authentication* - 
* **E4:** *RFC 8018* - 

## Diagram
![](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/Adding-Claims-Remaining/AssuranceCases/Credential_Confidentiality/CredentialConfidentialityv2.png) 
