# Git notes

* Git manages versions of projects

* Each version is a commit.
* Each commit is a snapshot of the entire project.
* The collection of commits contain projrct's history

* we can review the history
* We can undo a change

* All commits belong to a branch. By default there is only one bramch -> master branch

## Pull Requests

* It helps to test the branch.
* During pull request we can discuss review and approve changes. 

## Version control

* complete history tracked and available
* supports many workflows 
* Collaboration
* Quality through team communication and reviews.
* Manages small changes
* Easily test, fix or undo ideas and changes

### Commands
    git [command] [--flags] [arguments]

 * `git --version` => version information of git.
 * `git status` 
    * view the status of files in the working tree and staginf area
    * branch name
    * what changes to commit
 * `git status --short` => critical status infomation

    * A file... => A means added (staged)
    * AM file... => AM means added and modified.


*  `git commit` 
    * Adds staaged cintent to the local repo as a commit.
    * Previously commited files are also included
    * Creates a snapshot of the entire project.
    *  `git commit -m "initial commit"` => Commits with a message. if `-m " "` is not given then a editor opens to give a message 

* `git log` => local repo commit history.
    * see commit message

* `git log --online` => condense version.

* `git log --online -n` => to see last n commits

 * `git add ` 
    * add files to staging area.

 * `git add file.txt` 
    * adds files.

        git help [command]

* `git help init` => displays help for init command
* `git help` => displays overall got help
* `git init -h` => concise help
    
        git fakecommand ( -p | --patch) [<id>] [--] [<paths>...]

* `-f or --flag` =>  A dash and double dash is used to set a flag for a command.
* `|` => or 
* `[]` => optional
* `<>`=> place holders
* `[<>]` => optional placeholders
* `()` => grouping
* -- Disagments the command.
* `...` => multiple occurences possible. 


        git config [--local | --global | --system] <key> [<value>]
    
* `git config --global user.name name` => configuring your repo name
* `git config --global user.email abc@gmail.com` => configure github gmail
* `--system` flag applies to every repo for all users on your computer.
* `--global` flag applies to every repo that you use on your computer
* `--local` or **no flag** applies to the current repo.
    
        git config --global core.editor nano

* git sometimes open an editor for you to type a message.
* For example, an editor will open if you dont specify a commit message.
* To set your preferred git editor, you can set the vakue of the **code.editor** key.

## Steps

* Install the Git command line Interfaece
* Verify your git version
* Explore Git help
* configure your username, email address and default editor

## Git Locations

* ### Working tree

    * working tree is the location on your machine that contains the directories and files of a single commit or snap shot of your project.

* ### Staging area

    * Staging area contains a lot of files that are plan to be included in next commit. 
    *So next commit will be proper

* ### Local Repository
    * Contains all of the commits that have been made fot the project.
    * These commits represent the version history of project

* ### Project Directory
    * It contains above working tree
    * It also contains a hidden directory **.git**
    * **.git** here staging area and local repositor are located.
    * If we delete project directory you are also deleting your local repository and staging area.
* ### Remote Repository 
    * It is usually located in a data center or in the cloud.
    * It contains the commits of the project.
    * It is often considered as a source of truth or official state of the project.

A modified file is a file that has been prevously been added to the stage or commited to the local repository but since then has been changed in the working trees.


# Remote Repository

* A professionally manafed repository that is hosted in a data center or in the cloud.

* It often acts as the central source of the truth or official state of the project.

* It oftens integrates with other systems like issue trackers and continous delivery pipelines

* **Hosted options**
    * Bigbucket
    * Github

* **On premise Options**

    * Bitbucker Server
    * Github Enterprise
    * Open Source Software
        * these can be options can be hosted in a data center or in the cloud

* The root directory of the remote repository is similar to ***.git*** of the local repository.
* **URL** of the remote repository ends with ***.git***

* `git clone`
    * It is used to create a local copy of remote repository.


* `git remote `
    * displays information  about remote repository associated with local repository.
* `git remote --verbose` or `git remote --v` 
    * give detailed info

* `git remote add` <name> <url>

    * This adds ino about the remote repo to local repo

## Branches

* All commits belong to a branch
* By default, there is a single branch and it is called master

* `git push` 
    * Writes commit for a branch to a remote repository
* A successful push synchronizes the branches on the local and remote repositories so that they contain exactly the same commits.
* Pushing to the remote repository is primary done to share your work with team, and also serves as a good backup of the local repository.

* `git push [-u] [<repository>] [<branch>]` 

    * <repository> can be a name(shortcut) or URL
    * `-u` track this branch

* `git push -u origin main` there is only one branch(main) so push directly to main branch

    * After writing objects to the remote repository git informs that a tracking relationship has been setup between the local and remote branches because of `-u` flag



# Git graph model

* merge occur when a commit has more than one parent
* git uses a direct acyclic graph (DAG) to represent commit history
* Commits point to their **parent** commits



## Git merging



