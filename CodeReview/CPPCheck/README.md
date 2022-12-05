# CPPCheck Analysis - Findings
[Back to CodeReview.md](https://github.com/JCKelley-CYBR/CYBR-8420-SoftwareAssurance/blob/main/CodeReview.md)
We performed an automated scan using the CPPCheck tool. This tool can scan a repository of a C or C++ project, and find flaws based on CWEs and can be found [here](http://cppcheck.net/). We used a clone of the GitHub repository for the scan and found 2 errors in the src files. 

## Errors
There was two instances of file allocations without closing them using fopen. Upon manual review, this was deemed ok, as it is setting the null file for the device that it is being run on. 