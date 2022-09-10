# CYBR 8420 - Project Proposal

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## Open-Source Project: KeyPass 

## Hypothetical Operation Environment

## System Engineering Diagram

## Perceived Threats
In our selected environment of a Regional Managed Service Provider in which hundreds of environments' credentials are stored in a password manager such as KeyPass, there are many potential threats to the clientele's systems and their clients if the credentials are not properly stored. In order to properly perform our assessment of this software for the purposes of the hypothetical environment, these threats must be taken in to account and acknowledged. Below is a list of perceived threats to the environment all will be assumed with malicious intent or purpose:
* Hacker: A bad actor would try and gain access to the password database in order to obtain credentials to systems. Their motivation would be reputation or financial depending on their end goals and actions. Their targets would likely be easily accessible.
* Employee: A bad actor could try and exfiltrate passwords to sell to hackers or other interested parties. Their motivation would be financial or revenge. Their target would be their own employer.
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

## Contributing

## Security Related History

## Repo Link
https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance

## Team Reflection
