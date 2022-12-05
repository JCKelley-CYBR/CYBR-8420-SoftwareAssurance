# Github Scanner Analysis - Findings
[Back to CodeReview.md](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview.md)
One of the automated scanners we used to review KeePassXC was the [GitHub Code Scanner](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning). The Github Code Scanner uses a proprietary analysis tool named "CodeQL", developed and maintained by Github. This tool allowed us to fork the KeePassXC repository, and automatically search the code for flaws. 

The Github Code Sanner scanned all of the C++, Go, Javascript, and Python code separately. The Github Code Scanner was not able to identify any security issues in KeePassXC. You can find the Github Code Scanner Results [here](https://github.com/AaronVigal/keepassxc/security/code-scanning).
