

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
    * [Results](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview/FlawFinder/README.md)
* [Github Scanner](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning)
    * [Results](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/CodeReview/GitHubScanner)
* [Embold](https://app.embold.io)
    * [Results](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview/Embold/README.md)

### 4. Selected Common Weakness Enumerations (CWEs)
* [**CWE-127 Buffer Under-Read**](https://cwe.mitre.org/data/definitions/127.html) & [**CWE-786 Access of Memory Location Before Start of Buffer**](https://cwe.mitre.org/data/definitions/786.html)
    * **Descriptions:**
        * CWE-127: Buffer Under-Read: is a weakness that occurs when a KeePassXC attempts to read data from a buffer that has been under-allocated, meaning that there is not enough memory allocated to the buffer to store the data that is being read.
        
        * CWE-786: Access of Memory Location Before Start of Buffer: is a weakness that occurs when a KeePassXC attempts to access a memory location before the start of a buffer. This can happen when the KeePassXC attempts to read or write data to a memory location that is outside the bounds of the allocated memory buffer.
    * **Files Analyzed**
        * [Base32.h](https://github.com/keepassxreboot/keepassxc/blob/12be175d583fbfac5a7b6b250a3bb5f792925285/src/core/Base32.h#L35)
        * [Base32.cpp](https://github.com/keepassxreboot/keepassxc/blob/12be175d583fbfac5a7b6b250a3bb5f792925285/src/core/Base32.cpp#L211)
    * **Automated Scan Issues:** Embold reported Base32.cpp as vulnerable to CWE-127 & CWE-786 as a **Critical Vulnerability**. 
        * **Code Snippet:**
            ```C++
            while (n >= 0) {
                int index = (quantum & mask) >> n;
                Q_ASSERT(0 <= index && index <= 31);
                encodedData[o++] = alphabet[index];
                mask >>= 5;
                n -= 5;
            }
            ```
        * **Scan Description:** Either the condition '0<=index' is redundant or the array 'alphabet[33]' is accessed at index -1, which is out of bounds. Array index -1 is out of bounds.
    * **Code Review Summary:** The automated scans identified large vulnerability in the handling of indexs. In this case the amount of memory allocated to the buffer, and allowing access to memory locations before the start of the buffer. If this threat were to be realized by an attacker it could open up KeePassXC to potential data leakage, or crashing. The function this code was found in is used for encoding QByteArray& data. Fortunately, this function is not utilized anywhere in the repository for any sort of encoding. This vulnerability is not a threat to KeePassXC, however, we do recommend if it is not in use to remove it from the repository.
    
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
   * **Description** 
      * CWE-200: Exposure of Sensitive Information to an Unauthorized Actor, is a weakness that occurs when an application or system exposes sensitive information to unauthorized users or systems. This can happen when an application or system fails to properly protect sensitive information, such as by not encrypting data or by storing it in an insecure location. If KeePassXC, a password manager, were to suffer from this weakness, it could potentially expose sensitive information such as passwords or other sensitive data to unauthorized users or systems. This could allow attackers to gain access to a user's password database, potentially compromising the security of their online accounts. It is important for KeePassXC to properly protect sensitive information and ensure that it is not exposed to unauthorized actors. This can be achieved through the use of strong encryption and secure storage of sensitive data.
   * **Files Analyzed**
      * [Crypto.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/Crypto.cpp)
   * **Automated Scan Issues:** No automated scan issues found for `Crypto.cpp`.
   * **Code Review Summary:** KeePassXC minimizes the exposure of sensitive information to an unauthorized actor. 
      * Since there is no logging, there is no way that sensitive information is presented to unauthorized actors
      * KeePassXC has strong encryption, using 256-bit AES.
      * There is a possiblity, since SHA-1 is imported into the main.go file, there is leakage of senstive information. This is related to another CWE, CWE-327.

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
* [CWE-327: Use of a Broken or Risky Cryptographic Algorithm](https://cwe.mitre.org/data/definitions/327.html)
   * **Description**
      * CWE-327: A type of weakness or vulnerability in a system's encryption. It occurs when a system uses a cryptographic algorithm that is known to be insecure or has been broken by attackers. This can happen if the system uses an outdated or weak encryption algorithm, or if it has not been implemented properly. Using a broken or risky cryptographic algorithm can put the system and its users at risk of having their sensitive information, such as passwords, stolen by attackers. It is important for systems to use strong, secure encryption algorithms to protect against this type of vulnerability.
      
   * **Files Analyzed**
      * [main.go](https://github.com/keepassxreboot/keepassxc/blob/develop/utils/keepassxc-cr-recovery/main.go)
      * **Automated Scan Issues** Issue found with importing crypto/sha1 into `main.go` **Critical Vulnerability**
      * **Code Snippet:**
         ```go
         "crypto/hmac"
         "crypto/sha1"
         "fmt"
         ```
   * **Code Review Summary:** Appears to be use of SHA-1 (a weak hashing algorithm).
      * If there is SHA-1 used, this could be a secuirty issue
      * The context around the code snippet reveals that this SHA-1 hash is just used in the process of recovering a database after a hardware key is lost, it is not used to guarantee integrity or uniqueness

* [CWE-362 Concurrent Execution using Shared Resource with Improper Synchronization ('Race Condition')](https://cwe.mitre.org/data/definitions/362.html)

* [CWE-532: Insertion of Sensitive Information into Log File](https://cwe.mitre.org/data/definitions/532.html)
    * **Description:** CWE-532: A type of weakness that occurs when an application or system logs sensitive information, such as passwords or other authentication credentials. This can happen when an application or system fails to properly protect sensitive information, such as by not encrypting data or by storing it in an insecure location. 
        
    * **Code Review Summary:** If KeePassXC, a password manager, were to suffer from this weakness, it could potentially expose sensitive information such as passwords or other sensitive data to unauthorized users or systems. This could allow attackers to gain access to a user's password database, potentially compromising the security of their online accounts. It is important for KeePassXC to properly protect sensitive information and ensure that it is not exposed to unauthorized actors. This can be achieved through the use of strong encryption and secure storage of sensitive data.

### 5. Summary of Findings
During the initial code review activities, many tools were selected to carry out automated code analysis. It was found that some of these tools do not work well or not suited for KeePassXC. However, the team was able to find some CWEs of note, involving encryption, buffer issues, input, and shared resource access. Of all of the CWEs generated from automated and manual scans, seven were selected and split up amongst the team, these are listed in section four.

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
