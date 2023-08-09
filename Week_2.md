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





