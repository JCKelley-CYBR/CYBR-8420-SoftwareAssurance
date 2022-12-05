# FlawFinder Analysis - Findings
[Back to CodeReview.md](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview.md)

We performed an automated scan using the OSS FlawFinder, a tool that examines C/C++ source code and reports potential security weaknesses using CWEs. The Tool can be found [here](https://dwheeler.com/flawfinder/).

Errors
Flawfinder tagged 179 issues and potential security flaws, with a vast number of them being CWE-362 issues present within the Qt framework that is used to implement the KeePassXC GUI.
