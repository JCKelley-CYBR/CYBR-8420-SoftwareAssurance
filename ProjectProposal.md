# CYBR 8420 - Project Proposal

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## Open-Source Project: KeePassXC 

## Hypothetical Operation Environment
KeePassXC provides a highly flexible password management solution for individuals and organizations. KeePassXC allows local, network, and cloud storage of encrypted password databases and database shares. The software is expected in any environment to provide adequate encryption to maintain the confidentiality of the database contents, proper password maintenance ensuring password integrity, and ease of access for authorized individuals to ensure high availability.

Our hypothetical situation focuses on a Regional Managed Service Provider (MSP) whose job is to routinely log in remotely to hundreds of different environments and servers to conduct normal IT operations for their clientele. Due to the number of different credentials shared between technicians, the department wants to implement a local, open-source password management solution called KeePassXC. This software will be critical to daily operations, allowing authorized technicians to access client systems' usernames, passwords, URLs, IP addresses, and Notes. KeePassXC enables the MSP to save these credentials into an encrypted, locally stored database to protect its contents and offer high availability to authorized technicians. Implementing KeepassXC into our corporate environment would increase the speed at which technicians can find proper credentials, use these credentials to carry out normal business operations on client systems, and improve our overall security posture by reducing the potential mishandling of client system credentials. The implementation would allow technicians to use a password, key file, or hardware key to unlock the database. The organization will create a root database and database shares only, including the necessary client credentials to complete their job responsibilities following the principle of least privilege.

## System Engineering Diagram
<img src="system_engineering_diagram.png">

## Perceived Threats
In our selected environment of a Regional Managed Service Provider in which hundreds of environments' credentials are stored in a password manager such as KeePassXC, there are many potential threats to the clientele's systems and their clients if the credentials are not correctly stored. In order to properly perform our assessment of this software for the hypothetical environment, these threats must be considered and acknowledged. Below is a list of perceived threats to the environment. Our team will assume all have malicious intent or purpose:
* Black Hat Hacker: A bad actor would try and gain access to the password database to obtain system credentials. Their motivation would be reputation or financial, depending on their end goals and actions. Their targets would likely be easily accessible.
* Insider Threat (Employee): A bad actor could try and exfiltrate passwords to sell to hackers or other potential threat actors. Their motivation would be financial or revenge. Their target would be their employer.
* Malicious Contributor: A bad actor may contribute to the open source project that would allow them access to the database of our environment. Their motivation would be reputation or financial, depending on their end goal. This actor could also leverage greater threats. This is a particularly emphasized problem due to there being no security policy on GitHub. Their target would be the source of the software.

## Security Features
* Separate storage for TOTP secrets as passwords
* Option to compile without networking
* Hundreds of contributors on an open source platform with thousands of contribution
* Yubikey integration for MFA
* AES 256 encryption standard with TwoFish and ChaCha20 as additional choices
* Database health reports (Password strength, Have I been Pwnd checks, statistics)
* Secure password generation

## Team Motivation
The interconnectivity of the mobile device provided fertile grounds for the Service-as-a-Product business model to grow unchecked. In the last five years, Software-as-a-Service, e.g., Adobe Cloud, Office 365, etc., have also increased in popularity. For the individual, we now have more accounts over a more extensive variety of applications and services than ever before, a trend that is unlikely to slow down. Consequentially, password managers have seen a similar growth in popularity. This growth is not only in the enterprise environment but also in personal use. These password managers provide convenience in exchange for a single potential point of failure. 

We identified the importance of security within password management software during our initial perusal of open-source software. We shortlisted several open-source projects that intersected with various proprietary password managers. After our initial discussion with Dr.Gandhi, we settled on KeePassXC, a reasonably popular and well-maintained open-source password manager with a healthy community of contributors.

## Open-Source Project Description

[KeePassXC](https://keepassxc.org/) is a cross-platform password manager for anyone. The application is built and tested on Windows, macOS, and Linux. KeePassXC contains numerous features beyond simply storing passwords, including secure password generation, auto-typing into desktop applications, and auto-fill on websites. KeePassXC uses 256-bit AES to store information and is kept entirely offline on your device, with no internet connection needed. It then falls on the user to back up the offline database locally or with a trusted cloud storage provider. KeePassXC also includes many security features like YubiKey support, entry history, database reports, etc. 

To adequately scope our team's software audit, we limited our project to only the desktop application for KeePassXC. KeePassXC has other mobile applications and extensions for major browsers, which our team will not be auditing. The software we will be looking at is comprised of 96.6% C++, 1.2% CMake, 0.8% Shell, 0.7% C, 0.3% Objective-C++, and 0.3% Powershell code. 

The [open-source project](https://github.com/keepassxreboot/keepassxc), hosted on Github, has 314 active [contributors](https://github.com/keepassxreboot/keepassxc/graphs/contributors). The project is sponsored by two individuals, Johnathan White and Janek Bevendorff, and two companies, OpenCollective and Liberapay. The project remains highly active, with the [latest push](https://github.com/keepassxreboot/keepassxc/commit/dd15db721a3d8d9e276e6363ae5d51e35c33e4c7) happening just 7 hours before the time of writing. The repository has over 4,300 [commits](https://github.com/keepassxreboot/keepassxc/commits/develop), and 12 branches for developing different features. There are 535 open [issues](https://github.com/keepassxreboot/keepassxc/issues) at the time of writing, none of which appear to be security related. The [latest release](https://github.com/keepassxreboot/keepassxc/releases/tag/2.7.1) of KeePass XC is version 2.7.1 on April 5th, 2022, which appears to be mostly bug fixes. 

The KeePassXC repository contains extensive documentation on the application, which can be viewed as a web page [here](https://keepassxc.org/docs/KeePassXC_UserGuide.html). This set of documentation is aimed at the KeePassXC end-user. In addition, the [Github Wiki](https://github.com/keepassxreboot/keepassxc/wiki) page contains extensive documentation for KeePassXC developers and contributors. This documentation will likely be more relevant for our team's security audit. 

## Licensing Information
KeepassXC is licensed under [GNU General Public License Version 2](https://github.com/keepassxreboot/keepassxc/blob/develop/LICENSE.GPL-2), [GNU General Public License Version 3](https://github.com/keepassxreboot/keepassxc/blob/develop/LICENSE.GPL-3), [GNU Lesser General Public License Version 2.1](https://github.com/keepassxreboot/keepassxc/blob/develop/LICENSE.LGPL-2.1), and [GNU Lesser General Public License Version 3](https://github.com/keepassxreboot/keepassxc/blob/develop/LICENSE.LGPL-3). KeepassXC's primary license is the GNU GLP v2. This license allows for copying, distributing, and modifying the software it is licensing. Under this license, the authors do not offer any warranty. If someone wants to take this source code and offer it for free or a charge, they must share the source code with the recipient and give the recipient all the rights they (the seller/distributor) have. The third-party files' licensing in the repository are detailed [here](https://github.com/keepassxreboot/keepassxc/blob/develop/COPYING).

## Contributing
The KeePassXC team maintains a friendly community for project discussions on both [matrix](https://matrix.to/#/!zUxwGnFkUyycpxeHeM:matrix.org?via=matrix.org) and [Libera chat](https://web.libera.chat/). Still, they ask that new feature requests and bug reports be filed through the issue tracker on their GitHub repository. KeePassXC also welcomes direct contributions, be it code, documentation, or artistic work. KeePassXC's [Open Source Contribution Policy](https://github.com/keepassxreboot/keepassxc/blob/develop/.github/CONTRIBUTING.md) provides a guideline for content and a [styleguide](https://github.com/keepassxreboot/keepassxc/blob/develop/.github/CONTRIBUTING.md#styleguides) that they ask all pull requests to comply with before submission. There is no official Contribution Agreement, and their Contribution Policy is to "accept good code that they can use from anyone." The team will accept it if they judge the contribution as suitable, functional, efficient, and not restricted by licensing issues. Translations for KeepPassXC are managed via [Transifex](https://explore.transifex.com/keepassxc/keepassxc/). The KeePassXC team asks that contributors join an existing language team or request a new translation if there is not an existing one. 

## Security-Related History

There have not been any publically-disclosed CVEs for KeePassXC. KeePassXC is a fork of the now-deprecated KeePassX, which has been around for a while and is well regarded. Our team was able to locate one previous security-related issue on the KeePassXC issues page. This vulnerability was discovered and patched by the lead KeePassXC developer, who wrote:

> Given this bug, nobody ever tested the KeePassXC code with address sanitizer. I'd consider that fundamental quality assurance should be done by default, especially for security-related projects.

The previous versions of KeePass have been relatively free of vulnerabilities as well. The most major vulnerability our team could find was on KeePass (not X or XC), titled [CVE-2022-0725](https://www.cvedetails.com/cve/CVE-2022-0725), which allowed an attacker to log a KeePass password in plain text. This vulnerability was rated as a 5.0/10 severity. A PoC can be found [here](https://github.com/ByteHackr/keepass_poc).

## Repo Link
https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance

## Team Reflection
