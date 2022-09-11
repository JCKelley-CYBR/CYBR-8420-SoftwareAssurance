# CYBR 8420 - Project Proposal

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## Open-Source Project: KeyPass 

## Hypothetical Operation Environment
KeepassXC provides a highly flexible password management solution for individuals and organizations. Allowing both local, network, and cloud storage of encrypted password databases and database shares. The software is expected in any environement to provide adequate encryption to maintain the confidentiality of the database contents, proper password maintanence ensuring password integrity, and ease of access for authorized individuals to ensure high availability.

Our hypothetical situation is based on a Regional Managed Service Provider (MSP) whose job is to routinely log in remotely to hundreds of different environments and servers to conduct normal IT operations for their clientele. Due to the number of different credentials shared between technicians, the department wants to implement a local, open-source password management solution called KeepassXC. This software will be critical to daily operations, allowing authorized technicians to access client systems' usernames, passwords, URLs, IP addresses, and Notes. KeepassXC enables the MSP to save these credentials into an encrypted, locally stored database to protect its contents and offer high availability to authorized technicians. Implementing KeepassXC into our corporate environment would increase the speed at which technicians can find proper credentials, use these credentials to carry out normal business operations on client systems, and improve our overall security posture by reducing the potential mishandling of client system credentials. The implementation would allow technicians to use a password, key file, or hardware key to unlock the database. The organization will create a root database and database shares only, including the necessary client credentials to complete their job responsibilities following the principle of least privilege.
## System Engineering Diagram
<img src="system_engineering_diagram.png">

## Perceived Threats
In our selected environment of a Regional Managed Service Provider in which hundreds of environments' credentials are stored in a password manager such as KeyPass, there are many potential threats to the clientele's systems and their clients if the credentials are not properly stored. In order to properly perform our assessment of this software for the purposes of the hypothetical environment, these threats must be taken in to account and acknowledged. Below is a list of perceived threats to the environment all will be assumed with malicious intent or purpose:
* Black Hat Hacker: A bad actor would try and gain access to the password database in order to obtain credentials to systems. Their motivation would be reputation or financial depending on their end goals and actions. Their targets would likely be easily accessible.
* Insider Threat (Employee): A bad actor could try and exfiltrate passwords to sell to hackers or other interested parties. Their motivation would be financial or revenge. Their target would be their own employer.
* Contributor: A bad actor may make a contribution to the open source project that would allow them access to the database of our environment. Their motivation would be reputation or financial depending on their end goal. This could also leverage greater threats. This is a particularly emphasized problem due to there being no security policy on the github. Their target would be the source of the software.
## Security Features
* Separate storage for TOTP secrets as passwords
* Option to compile without networking
* Hundreds of contributors on an open source platform with thousands of contribution
* Yubikey integration for MFA
* AES 256 encryption standard with TwoFish and ChaCha20 as additional choices
* Database health reports (Password strength, Have I been Pwnd checks, statistics)
* Secure password generation
## Team Motivation

## Open-Source Project Description

## Licensing Information
KeepassXC is licensed under [GNU General Public License Version 2](https://github.com/keepassxreboot/keepassxc/blob/develop/LICENSE.GPL-2), [GNU General Public License Version 3](https://github.com/keepassxreboot/keepassxc/blob/develop/LICENSE.GPL-3), [GNU Lesser General Public License Version 2.1](https://github.com/keepassxreboot/keepassxc/blob/develop/LICENSE.LGPL-2.1), and [GNU Lesser General Public License Version 3](https://github.com/keepassxreboot/keepassxc/blob/develop/LICENSE.LGPL-3). KeepassXC's primary license is the GNU GLP v2. This license allows for copying, distributing, and/or modification of the software it is licensing. Under this license the authors do not offer any warranty. If someone wants to take this source code and offer it for free, or for charge, they must share the source code with the recipient and give the recipient all the rights they (the seller/distributer) have. The licensing of the third party file's used in the repository is detailed [here](https://github.com/keepassxreboot/keepassxc/blob/develop/COPYING).
## Contributing

## Security Related History

## Repo Link
https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance

## Team Reflection
