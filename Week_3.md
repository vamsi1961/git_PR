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

## Resolving a merge conflict

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



