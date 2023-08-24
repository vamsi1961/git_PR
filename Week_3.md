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

* `git pull` only aborts the merge if ou have committed-changes that would be overwritten by git

* Anything can happen when merging in a topic branch can happen when merging in a tracking branch

* It fetches objects, then merges the current branch into the tracking branch.

* **MERGING OPTIONS**

    * `--ff` (default) -  fast forward if possible, otherwise perform a merge commit.
    * `--no-ff-` => always include a merge conflict.
    * `--ff--only` => cancel instead of doing a merge commit.
    * `--rebase` [--preserve-merges] - discussed later.

## **Push**

* `git push [-u] [<repository>] [<branch>]`

    *  `-u` Track this branch (--set-upstream)
    * you are pushing commits to a remote repository
    * A general rule is to do a pull/ fetch before pushing

## **Rebasing**

* **Rewriting commit history**
    * The topics discussed here rewrite the commit history 
    * This should be done with caution
    * General rule : Do not rewrite history that has been shared with others

### **REBASE**

* Moves commits to a new parent ( base )

    * The unique commits the featureX branch ( B and C) are reapplied to the tip of the master branch(D)
    * Because the ancestor chain is different, each of the reapplied commits has different commit D( B' and C')

    * When rebasing, git applies the diffs to the new parent commit
        * This is called "reapplying commits"

* **REBASING IS A MERGE**

    * Reapplying commits is a form of merge and is susceptible to merge conflicts
    * For example, commits B and C can change the same file, causing a merge conflict during the rebase

* **PROS**

    * You can incorporate changes from the parent branch
        * You can use the new features/bugfixes
        * Tests are on more current code
        * It makes the eventful merge into master fast-forwardable

    * Avoids "unnecessary" commits
        It allows you to shape/define clean histories

* **CONS**

    * Merge conflicts may need to be resolved
    * It can cause problems if your commits have been shared
    * You are not preserving the commit history 


### **Commands**

* `git rebase <upstream>` 
    * Changes the parent of the currently checked out branch to <upstream>

* `git rebase <upstream> <branch>`

    * Checks out <branch> and changes its parent <upstream>
    * This is a convenience to avoid issuing two commands

* Checkout the feature branch. Rebase onto the base branch

### **Fixing A Merge Conflict While Rebasing**

* `git checkout featureX`
* `git rebase main`
    * CONFLICT
* `git status`
    * Both modified file
* Fix file
* `git add file`
* `git rebase --continue`
-----------
* During conflict if you want to abort
    * `git rebase --abort`

### **git merge flow**

* `git checkout main`
* `git merge featureX`
    * Conflict
* `git status`
    * Both modified file
* Fix file
* `git add file`
* `git commit`


## **REWRITING HISTORY**

* You can change the most recent commit:

    * change the commit message
    * change the project files

* This creates a new SHA-1 ( rewrites history )

* `git commit --amend -m " updated commit message"`
    * SHA-1 changes

* Modify the commit by modifyinh staging area and amend a commit.
* Optionally use the `--no--edit` option to reuse the previous commit message

    * `git commit --amend -m --no--edit`

## **INTERACTIVE REASE**

* Interactive rebase lets you edit commits using commands
    * The commit can belong to any branch
    * The commit history is changed- do not use for shared commits
* `git rebase -i < after-this-commit>`
    * Commits in the current branch after <after-this-commit> are listed in an editor and can be modified

-----------------

* Use the commit as is
* Edit the commit message
* Stop and edit the commit
* Drop/Delete the commit
* Squash
* Fixup
* Reorder commits
* Execute shell commands


* **SQUASH**

    * Combine this commit with the older commit, creating a single commit
        * The work of both commits is included

* **DELETE**

    * No changes from this commit are applied 
        * The diff is thrown out
        * The work of this commit is lost
        * Greater chance of a merge conflict


* **SQUASH MERGE**

* Merges the tip of the feature branch (D) onto the tip of the base branch (C)
    * There is a chance of a merge conflict

* Places the result in the **staging area**
* The result can then be committed (E)

## **PERFORMING A SQUASH MERGE**

* `git checkout master`
* `git merge --squash featureX`
* `git commit`
    * accept or modify the squash message
* `git branch -D featureX` (OPTIONAL)










