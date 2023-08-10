# Graph

* Direction is represented with arrow. Arrow direction in a directed graph depends on how you define the relationship
* ACyclic means no cycles in branch
* Cyclic is circular branches are connected

## Directed Acyclic Graph (DAG)

* Contains nodes connected with arrows and has no cycles

* git models the relationship of commits with a DAG
* The arrow point a commit's parent.

* `git log --online --graph` 
    * view graph

* git uses DAG to represent commit history
* Commit points to their parent commits

## GIT Objects

* git object

    * commit user information
    * commit message
    * SHA-1 values are unique for a given piece of content ( statistically speaking)
    * They are often shorten to first 4 or more characters
    * reference to the commit parent or parents and a reference to the root tree

* Annotated tag

    * A permanent reference to a commit

* Tree
    * Directories and filenames in the project

* Blob
    * The content of a file in the project


## GIT ID's

* A git object's name is same as its git ID
* they are known as secure hash algorithm or SHA-1 values. It is unique for every piece of content.

* `git log` 

    * The  **name** of a git object
    * 40-charecter hexadecimal string
    * Also known as Object ID, SHA-1,hash and checksum.

* `git hash-object file` 
    * returns a hash object
    * different SHA-1 for different edits in file no to edits contain same SHA-1


## Shortenings GIT ID's

* `git log --online` => id gets shorten

* `git show partial_id` => by giving partial id we can get respective commit. make sure partial_id is unique in given id's


# References

## Overview 

* User-friendly name that points to
    * a commit SHA-1 hash
    * Another reference
        * known as a symbolic reference

* in `git log` gives 2 references associated with them ( HEAD and MASTER)

* `git show HEAD/MASTER` 
    * Details about commit object

## Master

Master is the default name of the main branch in the repository
Any commits that we would make at this point would be to this branch


## Branch Label

* Points to the most recent commit in the branch
    * The `tip of the branch`

* Implemented as a reference

* In the `.git/refs/tags` branches are available

## HEAD

* A reference to the current commit
* Usually points to the current branch label of the current branch
* One Head per repository
* HEAD is implemented in git as a reference
* `cat /.git/HEAD` points to `ref: refs/heads/master`
    * When a reference points to another reference it is called a symbolic reference

* HEAD always points to current commit


## Referencing prior commits with ~ , and , ^


* In git commands, the `~` charecter can be appended to git ID's and reference to refer to prior commits.

* `~` or `~1` = parent
* `~2` or `~~` = parent's parent

* `git log --oneline --graph`
    *  displays graph

* `git show HEAD`
    * current commit object

* `git show HEAD~`
    * current commit parent

* `git show master~3` 
    * returns object 3 commits before
    * we can pass name of object

* `^^-` first parent's first parent
    * It is appended to ID's and referemce in git commands primarily to refer to  specific parent in a merge commit
    * Merge commit have multiple parents

* `git show master^` => refers to the first parent  whose SHA-1 

* `git show HEAD^2` => refer the current commit's second parent.If there is only one parent it will show error

* `git show HEAD^^` => refer first parent's first parent

## TAGS

* A tag is a reference attached to a specific comment
* It acts as a user-friendly label for the commit

* **LIGHTWEIGHT**
    * A simple reference to a commit
* **ANNOTATED**
    * A full git object that references a commit
    * Includes tag author information, tag date , tag delete, tag message, the commit ID
    * Optionally can be signed and verified with GNU Privacy gaurd (GPG)

* `git tag` => view all tags in repository
* A tag is a reference to a branch label

* Tag a commit with an annotated flag:
    *`git tag -a [-m <msg> | -F <file>] <tagname> [<commit>]`
    * <commit> defaults to HEAD

* `git push` does not automatically transfer tags to the remote repository

    * `git push <remote> <tagname>`
        * To transfer a single tag

    * `git push <remote> --tags`
        * To transfer a single tag

* A branch label is a reference that points to the tip od the branch
* HEAD is a reference that points to the current commit
* In git commands, use `~` and `^` to conveniently refer to previous commits
* Create tags to place labels on specific commits
* Tags are not automatically pushed to remote repositories.

## BRANCH

* The set of commits that track back to the project's first commit

* **Benifits**

* Fast and easy to create
* Enable experimentation
* Enable team development
* Support multiple project versions


* Topic
    * A fetaure, a bugfix, a hotfix, a configuration change etc.

* Long-lived
    * master , develop , release

* `git branch` => list of branches

* `git branch <name>` => creates a new branch

## Checkout

* It switch the current commit which is the commit that HEAD reference points to the checkout branch label or commit
* Updates the working tree with the commit's files from the checkout commit

* `git checkout <branch_name>` => to checkout a branch or commit
    * to checkout commit give SHA-1 of the commit

* `git checkout -b new_branch_name`

## DETACHED HEAD

checking out a commit rather than a branch leads to a detached HEAD state. Instead of the HEAD reference pointing to a branch label. HEAD points directly to the SHA-1 of a commit.

## Deleting a branch label

* If we immediately delete **feature X** branch and all that happens is that feature X label is denied

* `git branch -d featureX` => deletes branch feature1

## Dangling commits

* **What happens if you tried deleting a branch label with unmerged work**

    * Let's say featureX branch is created of commit C of master branch as shown.
    * commit D is is done for featureX
    * when featureX branch is deleted using `git branch -D featureX` commit D becomes dangling commit. 

    * If a branch label is deleted accidentally which resulted in dangling commits. we can undi it by `git reflog`

* `git reflog` => returns a local list of recent HEAD commits
* A branch is a set of commits that trace backs ti the project's first commit
* Creating a branch creates a branch label
* Checkout involves updating HEAD and updating the work tree
* A detached HEAD reference points directly to a commit
* Fix a detached HEAD by creating a branch
* Deleting a branch deletes a branch label
* Dnagling commits will eventually be garbage collected


## Merging

### Merging Overview

* combines work of independent branches
* Involves merging a topic branch, such as the featureX branch

* 4 types of merges

    * Fast-farword merge
    * Merge commit
    * Squash merge*
    * Rebase*

* **Fast-farword merge**

* A fast-forward merge moves the base branch label to the tip of topic branch
* A fast-forward merge is possible only if no other commits have been made to the base branch since the topic branch was created. 
* If any commits are done to base branch git will not allow to do it.
* git will always do a fast forward merge if you not tell to

* **steps**

    * `git checkout main`
    * `git merge featureX` or `git merge --no-ff featurex`
        * accept or modify the merge message
    * `git branch -d featureX` => delete the branch it is entire optional

* Merging combines the work of multiple branches
* A fast-forward merge moves the base branch label to the tip of the topic branch
* A merge is fast-forwardable if no other commits have been made to the base branch sinve branching
* A merge ci=ommit is the result of combining the work of multiple commits
* A merge commit has multiple parents


    






