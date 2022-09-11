# CYBR 8420 - Project Proposal

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec

## Open-Source Project: KeyPass 

## Hypothetical Operation Environment

## System Engineering Diagram

## Perceived Threats

## Security Features

## Team Motivation

## Open-Source Project Description

[KeePassXC](https://keepassxc.org/) is a cross-platform password manager for anyone to use. The application is built and tested on Windows, MacOS, and Linux. KeePassXC contains numerous features beyond simply storing passwords, including secure password generation, auto-typing into desktop applications, and auto-fill on websites. KeePassXC uses 256-bit AES to store information, and is stored completely offline on your device, with no internet connection needed. It then falls on the user to back up the offline database either locally, or with a cloud storage provider they trust. KeePassXC also includes many security features like YubiKey support, entry history, database reports, and more. 

To adequately scope our teams software audit, we chose to limit our project to only the desktop appication for KeePassXC. KeePassXC has other applications for mobile, as well as extensions for major browsers, which our team will not be auditing. The software we will be looking at is comprised of 96.6% C++, 1.2% CMake, 0.8% Shell, 0.7% C, 0.3% Objective-C++, and 0.3% Powershell code. 

The [open-source project](https://github.com/keepassxreboot/keepassxc), hosted on Github, has 314 active [contributors](https://github.com/keepassxreboot/keepassxc/graphs/contributors). The project is sponsored by 2 individuals, Johnathan White and Janek Bevendorff, as well as 2 companies, OpenCollective and Liberapay. The project remains highly-active, with the [latest push](https://github.com/keepassxreboot/keepassxc/commit/dd15db721a3d8d9e276e6363ae5d51e35c33e4c7) happening just 7 hours before the time of writing. The repository as a whole has over 4,300 [commits](https://github.com/keepassxreboot/keepassxc/commits/develop), and 12 branches for the development of different features. there are 535 open [issues](https://github.com/keepassxreboot/keepassxc/issues) at the time of writing, none of which appear to be security related. The [latest release](https://github.com/keepassxreboot/keepassxc/releases/tag/2.7.1) of KeePass XC is version 2.7.1 on April 5th 2022, which appears to be mostly bug fixes. 

The KeePassXC repository contains extensive documentation on the application, which can be viewed as a web page [here](https://keepassxc.org/docs/KeePassXC_UserGuide.html). This set of documentation is aimed towards the KeePassXC end-user. In addition, the [Github Wiki](https://github.com/keepassxreboot/keepassxc/wiki) page conatins extensive documentation for KeePassXC developers and contributors. This documentation will likely be more relevant for our teams security audit. 

## Licensing Information

## Contributing

## Security Related History



## Repo Link
https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance

## Team Reflection
