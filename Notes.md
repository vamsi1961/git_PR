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
    * branch name
    * what changes to commit
 * `git status --short` => critical status infomation

    * A file... => A means added (staged)
    * AM file... => AM means added and modified.




 * `git add ` => add files to staging area.

 * `git add file.txt` => adds files.

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