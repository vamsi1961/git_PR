## **PULL REQUEST**

* A feature of git hosting sites
* The ultimate goal is to merge a branch into the project
*  Enable team communication related to the work of the branch
    * Notifications sent to team members
    * Feedback or comments
    * Approval of the content (code review)    


# **STEPS**

* `git checkout -b "featureX"`
* touch file.txt 
* `git add file.txt`
* `git commit -m " added feature"`
* `git push --set-upstream origin featureX`
----------

* **MERGE**
    * `merge --no-ff`
        * we can merge form github or bigbucket

## **Forking**

* Forking-copying a remote repository to your own online account.
* Both repositories are remote repositories
* The upstream repository is usually the " source of truth"

### **USES**

* Experiment with/learn from the upstream repository
* Issue pull requests to the upstream repository
* Creatr a different source of truth

* A fork is a remote copy of an upstream remote repository
* A fork is created using an online git hosting provider
* Forks and upstream repositories may become out of sync
* Pull requests can be made from forks and merged into the upstream repositories