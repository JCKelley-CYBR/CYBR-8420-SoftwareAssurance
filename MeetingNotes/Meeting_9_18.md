
# Meeting for 9/18/22 
All members present
## Discussions of Part 1, Identify five essential interactions of the application, meeting performed via discord
Group examined and listed the features available in KeePassXC for security evaluation and possible security issues with each. 

Selected features for further evaluation in assignment/misuse case diagrams are as listed below:

- Export Database(individual entries, Groups or entire Vault)
- Unlocking Database/DatabaseShare
- KeeShare
- haveIBeenPwned
- Usage of Password Generator
- Autotype 

Discussions to pare the list down to five entries.

Discussion regarding Autotype vs Password Generator vs Export Database vs KeeShare and their criticality to the function of KeePassXC within an organization.

Password generator is allows user to quickly create complex passwords for usage.

Autotype is a convenience feature but greatly affects the average user's usage of KeePassXC, and is therefore considered a critical feature.

Discussion of usecase/misusecase diagraming of the password generator 
- passphrases are user supplied and opens up all entries in the KeePassXC vault to dictionary attacks.
- password generation allows the import of a custom wordlist database which may create weak passwords.

The group reviews the hypothetical operating environment to determine which features should be prioritized.

- KeeShare is critical as a part of organizational usage
- Josh argues for the retention of autotype due to the common usage by average users within organization.
- Neil argues for keeping password export for backup and transfer purposes
- databaseshare unlocking and keysharing are determined to be critical.
- Password generation is to be dropped as the least important feature for software system security requirements evaluation(would be evaluation as organizational policy)

Final decision for splitting up the security requirements as via lots decided when Josh initially set up issues.
Neil - unlocking database
Aaron - haveIbeenpwned
Daniel - keeshare
Mitchell - export groups
Josh - autotype

All members will aim to draft their portions of the assignment before the instructor meeting on Wednesday, all work will be kept on individual branches for review prior to merging into main, this includes finding summary, oss doc review, relevant usecases. We will  reconvene post instructor meeting on Wednesday to complete part 2 of assignment.

Josh created all framework material, issues and folders in git repo.

### conclusion of meeting. 
