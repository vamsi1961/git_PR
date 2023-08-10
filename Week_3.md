## Merge conflict Overview

* When a file is changed in branch and in main. while merging there will be a conflict. to solve that conflict we have to use editor.
* It occurs when desicion has to be made to commit

## Not a Merge Conflict -  Diiferent files

* Merge conflict can only occur if the same file changed.
----------

* Git automatically merges changes to different parts ( hunks ) of files.

    *  Branch 
        * feature 1 bug  
        * feature 2
        * feature 3

    *  main 
        * feature 1 
        * feature 2

    * **final**
        * feature 1  
        * feature 2
        * feature 3

    * git is smart enough to remove bug.

## Resolving a merge conflictm`

* Involves 3 commits:

    * The tip of the current branch (B) - "ours" or "mine".
    * The tip of branch to be merged (C) - "theirs".
    * A common ancestor (A) - "merge base".

----------
    THEIRS -> C <- FEATUREX
                |
                A <- MERGE BASE
                |
        OURS -> B <- MASTER <- HEAD
----------
### STEPS TO RESOLVE MERGE CONFLICT

* Checkout master
* merge featureX
    * CONFLICT - Both modified same file
* Fix file
* Stage file
* Commit the merge commit
* Delete the **branch** branch label


----------

* Merge conflicts occur when two branches modify the same hunk
* When a conflict occurs:
    * Git will create files in the working tree containing conflict markers
    * Fix, add and commit the conflicted files.

## Tracking branches

* It is a local branch that represents a remote branch.
    * <remote>/<branch>
* Committing is a local command

* `git branch -all` 
    * returns all brnaches ( remote and local branches)
* `git status` 
    * gives tracking branch status as well


* Tracking branches that represent remote branches
* Named <remote>/<branch>, for example origin/master
* Can become out of sync with local branches.
* Updated with network commands like `clone`, `fetch`, `pull` and `push`.


## Network Commands

`Clone` => Copies a remote repository
`Fetch` => Retrieves new objects and references from the remote repository
`Pull` => Fetches and merges commits locally
`Push` => Adds new objects and references to the remote

* **Fetch**

    * `git fetch <repository>`

        * Retrieves new objects and references from another repository
        * Tracking branches are updated.
        * If any changes are done in remote repository.
        * `git log origin/main --online --graph --all` it shows one commit ahead of local branch
        * local repository doesnt move to new commit.
        * `fetch` doesn't impact local branch labels
        * `git status` tells it is ahead of main branch and suggest to do `git pull` to retrieve data ( fast forward merge)


* **Pull**

* git pull [<repository>] [<branch>]

* Combines `git fetch` and `git merge FETCH_HEAD`
* If objects are fetched, the tracking branch is merged into the current local branch
* This is similar to a topic branch merging into a base branch.
* it automatically merges the local branch and sync with remote repository
* **MERGING OPTIONS**

    * `--ff` (default) -  fast forward if possible, otherwise perform a merge commit.
    * `--no-ff-` => always include a merge conflict.
    * `--ff--only` => cancel instead of doing a merge commit.
    * `--rebase` [--preserve-merges] - discussed later.

