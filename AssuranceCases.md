# Assurance Case Report

# Team Let Me Make Sure Nobody is Breaking into My House Real Fast, One Sec



## Claims, Arguments, and Detailed Alignment Assessments
* Claim 1 - 
* Claim 2 - 
* Claim 3 - 
* Claim 4 - The system minimizes information disclosure during communication
* Claim 5 - 

## Alignment Assessment Summary
* Assurance Claim 1 - 

* Assurance Claim 2 - 

* Assurance Claim 3 - 

* Assurance Claim 4 - The system minimizes information disclosure during communication

    *Overview*: KeePassXC takes some steps to minimize information disclosure during communication. The first of the major ways this is done is by  keeping the communication solely local. There is never a time where the communication traffic is sent outside of the local network, which can be seen by inspecting the source of the software. The second major way the software does this is by clearing the clipboard after 10 seconds by default if any credentials are copied to it. This however only works if the credentials are copied by the software and not an outside source such as the Windows copy function. This can be seen by a live system test or in the source code. A few other areas exist where KeePassXC could improve the assurance claim, including autotype, and copying. In autotype the software could encrypt its keystrokes to ensure no malicious software present can read typed credentials. For copying, the software could also block any copy function other than that of KeePassXC itself so that it can always clear the clipboard.

    *Conclusion*: Overall, the software does a good job to prove assurance claim 4. There is some ways to improve the software, but as it is, KeePassXC does a good job of minimizing information disclosure during communication. The gaps that remain are the lack of protection of autotype, and the software allows circumnavigation of copy protections.  

* Assurance Claim 5 - 

## Reflection

## Teamwork

Project Board: [Assurance Case](https://github.com/users/JCKelley-CYBR/projects/1)

## Open-Source Project: KeePassXC

KeePassXC: [GitHub](https://github.com/keepassxreboot/keepassxc)
