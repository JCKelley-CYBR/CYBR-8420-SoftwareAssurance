

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
* [DeepScan.io](https://deepscan.io/)
    * [Results]()
* [FlawFinder](https://dwheeler.com/flawfinder/)
    * [Results]()
* [SonarQube](https://www.sonarqube.org/)
    * [Results]()
* [Github Scanner](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning)
    * [Results]()
* [Embold](https://app.embold.io)
    * [Results]()

### 4. Selected Common Weakness Enumerations (CWEs)
* [CWE-127 Buffer Under-Read](https://cwe.mitre.org/data/definitions/127.html)
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-261: Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html)
* [CWE-326: Inadequate Encryption Strength (Code and Documentation](https://cwe.mitre.org/data/definitions/326.html)
* [CWE-362 Concurrent Execution using Shared Resource with Improper Synchronization ('Race Condition')](https://cwe.mitre.org/data/definitions/362.html)
* [CWE-532: Insertion of Sensitive Information into Log File](https://cwe.mitre.org/data/definitions/532.html)
* [CWE-786 Access of Memory Location Before Start of Buffer](https://cwe.mitre.org/data/definitions/786.html)
### 5. Summary of Findings
KeePassXC is a shit app
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