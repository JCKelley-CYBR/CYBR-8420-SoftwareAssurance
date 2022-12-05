# Code Review Report

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

[Back to Project](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance)

## Code Review

### 1. Introduction

### 2. Code Review Strategy
The manual code review strategy for KeePassXC is as follows:
1. Selection of Common Weaknesses and Enumerations (CWEs) based on relevance to identified weaknesses/flaws within KeePassXC.
2. CWEs will be divided between group members during the manual review process.
3. Automated tools will be employed against the KeePassXC repository (development branch).
4. Selected CWEs will dictate the areas of concern from the automated test results.
5. Results will be investigated related to the selected CWEs and the automated scan results.

### 3. Automated Scan Strategy
The automated scan strategy adopted by the team for this project was as follows:
1. Each member uses a unique automated scanning tool on the KeePassXC repository.
2. Results of these scans are to be stored in their repositories in the [CodeReview](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/CodeReview) folder.
3. After conducting all five automated scans, each group member will evaluate all automated scans for correlation to the selected CWEs. Any issues, or discoveries, will be evaluated in our findings.

#### 3.1 Selected Automated Scan Tools
* [CPPCheck](http://cppcheck.net/)
    * [Results](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview/CPPCheck/README.md)
* [FlawFinder](https://dwheeler.com/flawfinder/)
    * [Results](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview/FlawFinder/FlawfinderResults.csv)
* [Github Scanner](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning)
    * [Results](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/tree/main/CodeReview/GitHubScanner)
* [Embold](https://app.embold.io)
    * [Results](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview/Embold/README.md)

### 4. Selected Common Weakness Enumerations (CWEs)
* [**CWE-127 Buffer Under-Read**](https://cwe.mitre.org/data/definitions/127.html) & [**CWE-786 Access of Memory Location Before Start of Buffer**](https://cwe.mitre.org/data/definitions/786.html)
    * **Descriptions:**
        * CWE-127: Buffer Under-Read: a weakness occurs when a KeePassXC attempts to read data from a buffer that has been under-allocated, meaning that there is not enough memory allocated to the buffer to store the data that is being read.
        
        * CWE-786: Access of Memory Location Before Start of Buffer: This weakness occurs when a KeePassXC attempts to access a memory location before the start of a buffer. This can happen when the KeePassXC attempts to read or write data to a memory location that is outside the bounds of the allocated memory buffer.
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
    * **Code Review Summary:** The automated scans identified a significant vulnerability in handling indexes. The amount of memory allocated to the buffer and allowing access to memory locations before the start of the buffer. If this threat were to be realized by an attacker, it could open up KeePassXC to potential data leakage or crashing. The function this code was found in is used for encoding QByteArray& data. Fortunately, this function is not utilized anywhere in the repository for any encoding. This vulnerability is not a threat to KeePassXC. However, we recommend removing it from the repository if it is not in use.
    
* [**CWE-200: Exposure of Sensitive Information to an Unauthorized Actor**](https://cwe.mitre.org/data/definitions/200.html)
   * **Description** 
      * CWE-200: Exposure of Sensitive Information to an Unauthorized Actor is a weakness when an application or system exposes sensitive information to unauthorized users or systems. This can happen when an application or system fails to adequately protect sensitive information, such as by not encrypting data or storing it in an insecure location. If KeePassXC, a password manager, suffered from this weakness, it could expose sensitive information such as passwords or other sensitive data to unauthorized users or systems. This could allow attackers to gain access to a user's password database, potentially compromising the security of their online accounts. It is essential for KeePassXC to adequately protect sensitive information and ensure that it is not exposed to unauthorized actors. This can be achieved through strong encryption and secure storage of sensitive data.
   * **Files Analyzed**
      * [Crypto.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/Crypto.cpp)
   * **Automated Scan Issues:** No automated scan issues found for `Crypto.cpp`.
   * **Code Review Summary:** KeePassXC minimizes the exposure of sensitive information to an unauthorized actor. 
      * Since there is no logging, there is no way that sensitive information is presented to unauthorized actors
      * KeePassXC has strong encryption, using 256-bit AES.
      * There is a possibility since SHA-1 is imported into the main.go file. There is a leakage of sensitive information. This is related to another CWE, CWE-327.

* [**CWE-261: Weak Encoding for Password**](https://cwe.mitre.org/data/definitions/261.html)
    * **Files Analyzed:**
        * [Crypto.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/Crypto.cpp)
        * [CryptoHash.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/CryptoHash.cpp)
        * [SymmetricCipher.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/SymmetricCipher.cpp)
        * [Argon2Kdf.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/kdf/Argon2Kdf.cpp)
    * **Automated Scan Issues:** No relevant issues were found in the automated scans. 
    * **Code Review Summary:** We have concluded that KeePassXC properly encodes their passwords. They use the AES256 or TwoFish cipher with a configurable key transformation for the master password to ensure proper security for the passwords. This process is detailed [here](https://keepassxc.org/docs/#faq-security-why-pm) and is implemented correctly when looking at their code. Additionally, for hashing, they implement both SHA256 and SHA512 for the user to decide.

* [**CWE-326: Inadequate Encryption Strength**](https://cwe.mitre.org/data/definitions/326.html)
     * **Files Analyzed:**
        * [Crypto.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/Crypto.cpp)
        * [CryptoHash.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/CryptoHash.cpp)
        * [SymmetricCipher.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/SymmetricCipher.cpp)
        * [Argon2Kdf.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/kdf/Argon2Kdf.cpp)
        * [Random.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/crypto/Random.cpp)
    * **Automated Scan Issues:** There were no relevant issues found in the automated scans.
    * **Code Review Summary:** The encryption standards used for KeePassXC are up to current standards at a minimum and have no found vulnerabilities in the code after manual review. The application uses AES256 as a default encryption method. Further, they allow configuration to use the TwoFish block cipher. Both of these are appropriately implemented in the code. Lastly, for encryption of the vault, they use a configurable key transformation to provide extra security for the user to fit their needs. This function is also properly implemented.
* [**CWE-327: Use of a Broken or Risky Cryptographic Algorithm**](https://cwe.mitre.org/data/definitions/327.html)
   * **Description**
      * CWE-327: A weakness or vulnerability in a system's encryption. It occurs when a system uses a cryptographic algorithm known to be insecure or broken by attackers. This can happen if the system uses an outdated or weak encryption algorithm or if it is not been implemented properly. Using a broken or risky cryptographic algorithm can put the system and its users at risk of having their sensitive information, such as passwords, stolen by attackers. Systems need robust and secure encryption algorithms to protect against this vulnerability.
      
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
      * If there is SHA-1 used, this could be a security issue
      * The context around the code snippet reveals that this SHA-1 hash is just used in the process of recovering a database after a hardware key is lost. It is not used to guarantee integrity or uniqueness

* [CWE-362 Concurrent Execution using Shared Resource with Improper Synchronization ('Race Condition')](https://cwe.mitre.org/data/definitions/362.html)
   * **Description:**
      * CWE-362, or Concurrent Execution using Shared Resources with Improper Synchronization, is a weakness when an application allows multiple threads or processes to access or modify a shared resource without proper synchronization. This can lead to race conditions, where two or more threads or processes attempt to access or modify the same resource simultaneously, potentially leading to unpredictable or inconsistent behavior. In the case of KeePassXC, a password manager, this weakness could allow multiple threads or processes to access or modify a user's password database simultaneously, potentially leading to data corruption or other unpredictable behavior. This could result in a user being unable to access their password database or potentially losing access to their sensitive information. To prevent this, KeePassXC should adequately synchronize access to shared resources to ensure that only one thread or process can access or modify the password database at a time. This can help to prevent race conditions and ensure that the password database remains consistent and reliable.
   * **Files Analyzed:**
      * [DBusDispatch.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/fdosecrets/dbus/DBusDispatch.cpp)
      * [Config.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/core/Config.cpp)
      * [Database.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/core/Database.cpp)
      * [FileWatcher.cpp](https://github.com/keepassxreboot/keepassxc/blob/develop/src/core/FileWatcher.cpp)
   * **Automated Scan Issues:** Flawfinder reported many race conditions present with the inclusion of the Qt framework for their GUI.
   * **Code Review Summary:** The exploitation of CWE-362 may cause inconsistencies in the program's functioning. However, as the issues are only present with implementing the Qt framework, it only inconveniences the user. It does not present a security issue associated with accessing or modifying the Database.

* [**CWE-532: Insertion of Sensitive Information into Log File**](https://cwe.mitre.org/data/definitions/532.html)
    * **Description:** CWE-532: A type of weakness that occurs when an application or system logs sensitive information, such as passwords or other authentication credentials. This can happen when an application or system fails to adequately protect sensitive information, such as by not encrypting data or storing it in an insecure location. 
        
    * **Code Review Summary:** If KeePassXC, a password manager, suffered from this weakness, it could potentially expose sensitive information such as passwords or other sensitive data to unauthorized users or systems. This could allow attackers to gain access to a user's password database, potentially compromising the security of their online accounts. It is essential for KeePassXC to adequately protect sensitive information and ensure that it is not exposed to unauthorized actors. This can be achieved through strong encryption and secure storage of sensitive data.

### 5. Summary of Findings
Many tools were selected for automated code analysis during the initial code review activities. It was found that some of these tools do not work well or not suited for KeePassXC. However, the team found some CWEs involving encryption, buffer issues, input, and shared resource access. Seven of the CWEs generated from automated and manual scans were selected and split up amongst the team, which are listed in section four. The selected CWEs are as follows:
* [**CWE-127 Buffer Under-Read**](https://cwe.mitre.org/data/definitions/127.html)
* [**CWE-200: Exposure of Sensitive Information to an Unauthorized Actor**](https://cwe.mitre.org/data/definitions/200.html)
* [**CWE-261: Weak Encoding for Password**](https://cwe.mitre.org/data/definitions/261.html)
* [**CWE-326: Inadequate Encryption Strength**](https://cwe.mitre.org/data/definitions/326.html)
* [**CWE-327: Use of a Broken or Risky Cryptographic Algorithm**](https://cwe.mitre.org/data/definitions/327.html)
* [**CWE-362 Concurrent Execution using Shared Resource with Improper Synchronization ('Race Condition')**](https://cwe.mitre.org/data/definitions/362.html)
* [**CWE-532: Insertion of Sensitive Information into Log File**](https://cwe.mitre.org/data/definitions/532.html)
* [**CWE-786 Access of Memory Location Before Start of Buffer**](https://cwe.mitre.org/data/definitions/786.html)

From the Code Review carried out:
1. KeePassXC has a sufficient implementation of modern cryptographic standards. The application uses AES256 and TwoFish ciphers and has SHA256 and SHA512 hashing standards.
2. KeePassXC implements a robust and sufficiently random pseudo-random number generator with the Botan library. 
3. KeePassXC uses safe logging practices by never logging sensitive information. ;)
4. KeePassXC has a buffer under-read vulnerability. While it is not used in critical points of the application, it could cause unintended behavior.
5. KeePassXC uses shared resources; if the synchronization is not appropriately set, a race condition can present itself. This can cause unexpected behavior in the application or potential loss of availability.

As far as encryption is concerned, KeePassXC fulfills its job as a password manager, providing robust and proper encryption for users on the database. Regarding vulnerabilities found during the code review, they remained relatively minimal. The buffer under-read vulnerability found was never executed during critical security times, and the most likely behavior stemming from it would be a crash. Lastly, the shared resources issue was never used during critical security points, only ever in the GUI, therefore being a convenience issue over a security issue.

Overall, our findings for KeePassXC showed that it is a generally safe and stable codebase. From proper coding practices to the relatively small number of issues found, the application stands firm as a safe application for a password manager. While the few problems we found have little mitigation, they are not present in security functions, meaning the assurance is high. Risk is low for any entity implementing this application. 


### 6. OSS Contributions
The following open-source project contributions and interactions are noteworthy, given the continued work on KeePassXC as an open-source password management tool. 
* Reaffirmation and validation concerns regarding the hashing and encryption used by the application.
* The communication of findings discovered during the project that is relevant to KeePassXC. 
* The resolution of buffer under-reads could lead to crashes and vulnerabilities. 
* Elimination of race conditions in some parts of the code. 

### 7. Reflection
Working with Josh, Aaron, Mitchell, Neil, and Danee has been a pleasure. Each team member has brought their unique skills and perspectives to the table, resulting in a dynamic and productive work environment.

Josh is a strong leader who can clearly articulate our team's goals and objectives and is adept at delegating tasks and responsibilities to ensure that we are all working toward the same end. His attention to detail and commitment to excellence are impressive, and he has been a valuable asset to our team.

Aaron is a creative and innovative thinker who always comes up with new and exciting ideas. He is not afraid to take risks and try out new approaches, which has helped keep our team's work fresh and exciting.

Mitchell is a skilled problem-solver who is always willing to roll up his sleeves and tackle tough challenges. He is a calm and level-headed presence in the face of adversity, and his ability to stay focused and positive has been a valuable asset to our team.

Neil is a highly organized and efficient team member who is always on top of his work. He is skilled at managing his own time and tasks, and his ability to stay on track has helped keep the rest of us on track.

Danee is a team player who is always willing to lend a helping hand to his team members. He is a strong communicator and an empathetic listener, and his ability to build strong relationships with his teammates has been a valuable asset to our team.

Overall, working with this team has been a pleasure, and we believe that our collective skills and talents have helped to make our team a success.

> ### This is a __jovial__ team environment.

## Teamwork

Project Board: [Code Review](https://github.com/users/JCKelley-CYBR/projects/5/views/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)
