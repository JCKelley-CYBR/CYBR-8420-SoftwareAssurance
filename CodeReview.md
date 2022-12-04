

# Code Review Report

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

[Back to Project](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance)

## Code Review

### 1. Introduction

### 2. Code Review Strategy
The manual code review strategy for KeePassXC is as follows:
1. Selection of Common Weaknesses and Enumerations (CWEs) based on relevance to identified weaknesses/flaws within KeePassXC.
2. CWEs will be divided between group members during the manual review process.
3. Automated tools will then be employed against the KeePassXC respoitory (develope branch).
4. Selected CWEs will dictate the areas of concern from the automated test results.
5. Results will be investigated related to the selected CWEs and the automated scan results.
### 3. Automated Scan Strategy
The automated scan strategy adopted by the team for this project was as follows:
1. Each member uses an unique automated scanning tool on the KeePassXC repository.
2. Results of these scans are to be stored in their individual respositories in the [CodeReview](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/CodeReview) folder.
3. After conducting all five automated scans, each group member will evaluate all automated scans for correlation to the selected CWEs. Any issues, or new discoverys, will be evaluated in our findings.

#### 3.1 Selected Automated Scan Tools
* [CPPCheck](http://cppcheck.net/)
    * [Results](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview/CPPCheck/README.md)
* [FlawFinder](https://dwheeler.com/flawfinder/)
    * [Results]()
* [SonarQube](https://www.sonarqube.org/)
    * [Results]()
* [Github Scanner](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning)
    * [Results]()
* [Embold](https://app.embold.io)
    * [Results]()

### 4. Selected Common Weakness Enumerations (CWEs)
* CWE-127: Buffer Under-Read
* CWE-200: Exposure of Sensitive Information to an Unauthorized Actor
* CWE-261: Weak Encoding for Password
* CWE-326: Inadequate Encryption Strength (Code and Documentation
* CWE-362: Concurrent Execution using Shared Resource with Improper Synchronization ('Race Condition')
* CWE-532: Insertion of Sensitive Information into Log File
* CWE-786: Access of Memory Location Before Start of Buffer
### 5. Summary of Findings
* [CWE-261: Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html)
    * **Files Analyzed:**
        * [Crypto.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/Crypto.cpp)
        * [CryptoHash.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/CryptoHash.cpp)
        * [SymmetricCipher.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/SymmetricCipher.cpp)
        * [Argon2Kdf.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/kdf/Argon2Kdf.cpp)
    * **Automated Scan Issues:** There were no relevant issues found in the automated scans. 
    * **Code Review Summary:** We have concluded that KeePassXC properly encodes their passwords. They use the AES256 or TwoFish cipher with a configurable key transformation for the  master password to ensure proper security for the passwords. This process is detailed [here](https://keepassxc.org/docs/#faq-security-why-pm) and is implemented correctly when looking at their code. Additionally, for hashing they implement both SHA256 and SHA512 for the user to decide upon.
* [CWE-326: Inadequate Encryption Strength](https://cwe.mitre.org/data/definitions/326.html)
     * **Files Analyzed:**
        * [Crypto.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/Crypto.cpp)
        * [CryptoHash.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/CryptoHash.cpp)
        * [SymmetricCipher.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/SymmetricCipher.cpp)
        * [Argon2Kdf.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/kdf/Argon2Kdf.cpp)
        * [Random.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/Random.cpp)
    * **Automated Scan Issues:** There were no relevant issues found in the automated scans.
    * **Code Review Summary:** The encryption standards used for KeePassXC are up to current standards at minimum and have no found vulnerabilities in the code after manual review. The application uses AES256 as a default encryption method. Further, they allow configuration to use the TwoFish block cipher. Both of these are implemented properly in the code. Lastly, for encryption of the vault, they use a configurable key transformation in order to provide extra security for the user to fit to their needs. This function is also properly implemented.
### 6. OSS Contributions

### Reflection
Working with Josh, Aaron, Mitchell, Neil, and Danee has been a pleasure. Each member of the team has brought their own unique skills and perspectives to the table, resulting in a dynamic and productive work environment.

Josh is a strong leader who is able to clearly articulate our team's goals and objectives, and he is adept at delegating tasks and responsibilities to ensure that we are all working towards the same end. His attention to detail and commitment to excellence are impressive, and he has been a valuable asset to our team.

Aaron is a creative and innovative thinker, who is always coming up with new and exciting ideas. He is not afraid to take risks and try out new approaches, and this has helped to keep our team's work fresh and interesting.

Mitchell is a skilled problem-solver, who is always willing to roll up his sleeves and tackle tough challenges. He is a calm and level-headed presence in the face of adversity, and his ability to stay focused and positive has been a valuable asset to our team.

Neil is a highly organized and efficient member of the team, who is always on top of his work. He is skilled at managing his own time and tasks, and his ability to stay on track has helped to keep the rest of us on track as well.

Danee is a team player who is always willing to lend a helping hand to his team members. He is a strong communicator and an empathetic listener, and his ability to build strong relationships with his teammates has been a valuable asset to our team.

Overall, it has been a pleasure to work with this team and we believe that our collective skills and talents have helped to make our team a success.

> ### This is a __jovial__ team environment.

## Teamwork

Project Board: [Code Review](https://github.com/users/JCKelley-CYBR/projects/5/views/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)