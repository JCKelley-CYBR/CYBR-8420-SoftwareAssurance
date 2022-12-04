

# Code Review Report

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

[Back to Project](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance)

## Code Review

### 1. Introduction

### 2. Code Review Strategy

### 3. Automated Scan Strategy
Hit Go
NOICE

### 4. Selected Common Weakness Enumerations (CWEs)

* [CWE-532: Insertion of Sensitive Information into Log File](https://cwe.mitre.org/data/definitions/532.html)

CWE-532: Insertion of Sensitive Information into Log File is a type of Improper Authorization weakness that occurs when an application or system writes sensitive information, such as passwords or other sensitive data, to a log file. This can allow attackers who have access to the log file to easily obtain sensitive information, potentially allowing them to gain unauthorized access to sensitive data or systems.

In the context of KeePassXC, a password manager, CWE-532: Insertion of Sensitive Information into Log File could have a significant impact. If KeePassXC writes sensitive information, such as user passwords, to a log file, and an attacker is able to gain access to that log file, they could potentially obtain sensitive information and use it to gain unauthorized access to a user's password database. This could allow the attacker to gain access to sensitive information such as passwords, potentially allowing them to perform unauthorized actions or gain access to other sensitive data. To prevent this weakness, KeePassXC ensures that it does not write sensitive information, such as user passwords, to log files, and should properly secure any log files that are created to prevent unauthorized access.


### 5. Summary of Findings

### 6. OSS Contributions

### Reflection
Fuck this shit im out

> ### This is a __jovial__ team environment.

## Teamwork

Project Board: [Code Review](https://github.com/users/JCKelley-CYBR/projects/5/views/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)
