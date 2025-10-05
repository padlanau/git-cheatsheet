# git-cheatsheet

 

## Introduction

A simple guide on using Git and GitHub commands (status, push, pull, etc.). This repository is still under development — updates and improvements are ongoing.
 
<details>
<summary>
  Tutorials
</summary> <br />

```bash
$ git help
$ git tutorial


```
 
</details>

## Setup Name and Email Address 

It's highly recommended to configure the author name and email.  
You will get an error "No such file or directory" 

<details>
<summary>
  Tutorials
</summary> <br />

```bash
# check if the git configuration file has been initialized 
$ git config --global --list

# initialize git configuration file
$ git config --global user.name "<your name>"
$ git config --global user.email "<your email>"

$ vi ~/.gitconfig
$ cat ~/.gitconfig
```
 
</details>

## Setup Git 

It's highly recommended to configure the author name and email.  
You will get an error "No such file or directory" 

<details>
<summary>
  Windows
</summary> <br />

```bash
#
$ cd ~
$ pwd

# set up our command prompt so that we can again can see written to set up our command using git 
$ curl -O https://raw/githubusercintent.com/git/git/master/contrib/completion/git-prompt.sh
 
# add a command to a particular file so everytime we start this git bash shell, the script that we downloaded is run. This command opens the batch file:
$ vi .bashrc
then press I, and start typing
then type the following:

. ~/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='[\u@\h \W$(__git_ps1 " (%s)")]\$ '

press colon, then type x
press ENTER 

$ cat .bashrc
$ exit 

# Reopen git bash. It will show that it has been configured correctly if you see :
- user name
- host name
- current directory
- git branch name
- repo status indicator
- end in $
```

```bash
# set Path
Windows:
1.Find the Git installation path: This is typically C:/Program Files/Git/bin and C:/Program Files/Git/cmd. Verify this on your system.
2.Search for "environment variables": Open the Start menu, type "environment variables," and select "Edit the system environment variables."
3.Open Environment Variables: In the System Properties window, click the "Environment Variables..." button.
4.Edit Path variable:•Under "User variables" (for the current user) or "System variables" (for all users), find the variable named Path and select it.•Click "Edit...".
5.Add Git paths:
• Click "New" and add the path to your Git bin directory (e.g., C:/Program Files/Git/bin).
• Click "New" again and add the path to your Git cmd directory (e.g., C:/Program Files/Git/cmd). 
```

```bash
$ git --version
```

```bash
# gitignore

# Dotenv file
.env
broadcast/
lib/
```

</details>

<details>
<summary>
  Mac
</summary> <br />

```bash
# 
$ 
```
</details>

<details>
<summary>
  Linux
</summary> <br />

```bash
#  
$ cd ~
$ pwd

# download this file to configure the command prompt
$ curl -O https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
$ vi .bashrc
then press I, and get to the bottom of the file
then type the following:

. ~/git-prompt.sh + press ENTER, type the following:
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='[\u@\h \W$(__git_ps1 " (%s)")]\$ '

press ENTER then ESC
type :x + press ENTER. This means it is saved.

$ cat .bashrc
$ exit
```
 
</details>

## Method 1. From an existing project/repository from Github/Bitbucket. 

<details>
<summary>
  Tutorials
</summary> <br />

- Style 1. Download the existing repository in zip file

```bash
# 
$ cd <main-directory-name>
<main-directory-name> $ ls

# copy the downloaded into this main-directory-name
<main-directory-name> $ cp <location of the zip file> 
<main-directory-name> $ ls -al
<main-directory-name> $ unzip <type the first 3 letters of the file and press TAB>
<main-directory-name> $ ls  (you will see sortedCollections)
<main-directory-name> $ ls -al
<main-directory-name> $ rm <type the first 3 letters of the file and press TAB>
<main-directory-name> $ ls -al (the zip file has been removed.)
<main-directory-name> $ clear

# rename sortedCollections
<main-directory-name> $ mv sortedCollections/ converted-git-repo
<main-directory-name> $ ls -al
<main-directory-name> $ cd converted-git-repo

# your are now in converted-git-repo directory
<converted-git-repo> $ ls -l
<converted-git-repo> $ cd src (optional)
<converted-git-repo> $ git init (creates an empty repository)
 
```
 
</details>

## Method 2. From scratch. Creating a folder from local environment

By executing the "git init" command in an empty folder, which will become the root directory of your repository. This will create a blank repository, which later you can add new artifacts to.

<details>
<summary>
Creating an empty project folder
</summary> <br />

```bash
$ pwd

# Create a Main Directory
$ mkdir <main-directory-name>
$ cd <main-directory-name>
<main-directory-name> $ ls
<main-directory-name> $ pwd

# Create a sub-directory (folder of the new project)
<main-directory-name> $ mkdir new-project-folder
<main-directory-name> $ cd new-project-folder
<new-project-folder> $ pwd
``` 
</details>

<details>
<summary>
Initialize project folder
</summary> <br />
##

1. Initialize through the command line:
```bash
$ pwd

# git initialize. This creates .git file and you will see master branch as default
# or you can simply execute : git init new-project-folder OR $ git init -b main [or master]

<new-project-folder> git init -b main
Initialized empty Git...........new-project-folder/.git

# list all hidden files
<new-project-folder (master #)> $ ls -al
<new-project-folder (master #)> $ cd .git
.git (GIT_DIR!) $ ls -l

# return to the sub-directory
.git (GIT_DIR!) $ cd ..
<new-project-folder (master #)> $ 
```

2. Initialize through IDE (Android Studio)
```bash
- click Version control > Share Project On > Github (no need to do git init) 
- connect Github account
- a screen "Share Project On Github" will pop-up > Click Share
- a screen "Add Files For Initial Commit" will pop-up > click Add with a commit message "Initial commit"
```
</details>

<details>
<summary>
Adding/Committing existing Files to Local Repository
</summary> 
     
##

```bash
# step 1. Go to the new-project-folder directory
$ cd <main-directory-name>
<main-directory-name> $ ls
new-project-folder
<main-directory-name> $ cd new-project-folder
<new-project-folder (master #)> $ ls

# step 2. Add the file. 
<new-project-folder (master #)> $ vi <new-file>. Then type the changes. Press ESC then colon (:)

<new-project-folder (master #)> $ ls
<new-project-folder (master #)> $ cat <new-file>
OR
add the codebase directly

# step 3. Check what files or folders we are going to push to github. You will see files ready for staging.
<new-project-folder (master #)> $ git status (always check if .env is included)
<new-project-folder (master +)> $ git diff (see the difference you have done)

# step 4. add files/folders locally
<new-project-folder (master #)> $ git add <new-file> OR <file/s> Or git add README.md
<new-project-folder (master +)> (see the + sign that it has been added)
<new-project-folder (master +)> $ git status (all greens are to be committed)
<new-project-folder (master +)> $ git diff (see the difference you have done)
OR
<new-project-folder (master #)> $ git add . (period means add all folders and files)
<new-project-folder (master +)> $ git status
<new-project-folder (master +)> $ git diff (see the difference you have done)

# step 5. remove added files/folders locally
git rm --cached <file
git reset <file)

# step 6. commit locally
<new-project-folder (master #)> $ git commit -m 'Initial commit"  OR
<new-project-folder (master #)> $ git commit -m "<message>"
<new-project-folder (master +)> $ git status
On branch <branch-name>
nothing to commit, working tree clean

<new-project-folder (master +)> $ git log

# step 7. Amend message of the last commit
<new-project-folder (master +)> $git log
<new-project-folder (master +)> $git commit --amend -m <message>

# step 4 and 6. combination
<new-project-folder (master #)> $ git commit -am "<message>"
<main-directory-name (master)> $ git status

NOTE: Apply Step 8a and 8b if you don't have remote repository yet.

```
```bash
# step 8a. Import a Git repository with the command line/Adding a local repository to Github
```
- [Creating a repository on Github](https://github.com/padlanau/readme/edit/main/READMEGit.md#:~:text=Creating%20a%20repository%20on%20Github)

```bash
# step 8b. copy and paste the remote URL from step 8a

<new-project-folder (master #)> $ git remote add origin <REMOTE_URL> 
<new-project-folder (master #)> $ git remote -v (you will see different places we can push our codes OR verifies the new remote URL)
origin https://github.com/lpadlan/git-bootcamp.git (fetch)
origin https://github.com/lpadlan/git-bootcamp.git (push)

<new-project-folder (master #)> $ git push -u origin main (this is the branch)

# if you see an error like below, change it to 'master':
 error: src refspec main does not match any
 error: failed to push some refs to 'https://github.com/padlanau/MyApplication2.git'

<new-project-folder (master #)> $ git push -u origin master

```
</details>



<details>
<summary>
OTHERS
</summary> <br />
 

```bash
# For Modified files
- git add <file> (every you execute this, you will see "git reset HEAD <file>" command to unstage when you execute git status) 
- git checkout -- <filename>

## For Modified files - option 2. Checkout (to discard or reverting)
<main-directory-name (master)> $ git status
<main-directory-name (master)> $ git checkout -- <filename>
<main-directory-name (master)> $ git status
```
- Reverting Changes From a Git Repository

```bash
# For Modified files after executing "git add". Take note, the command "git status" hasn't been executed
modify a file
<main-directory-name (master)> $ git add <file/s>
<main-directory-name (master)> $ git status (here you will see get reset HEAD <file>)
<main-directory-name (master)> $ git reset HEAD <filename>
<main-directory-name (master)> $ git status
showing the following again:
- git add <file>  
- git checkout -- <filename>

<main-directory-name (master)> $ git checkout -- <filename>

# For newly added directory and file OR it hasn't been tracked 
add a file
<main-directory-name (master)> $ git add <file/s>
<main-directory-name (master)> $ git status  (you will see git rm --cached <file>..." to unstage)
<main-directory-name (master)> $ git rm --cached <filename>
<main-directory-name (master)> $ git status (this shows "Untracked files" )
<main-directory-name (master)> $ rm <filename>
<main-directory-name (master)> $ git status (this shows "Initial commit")

```

- Viewing the Git Commit History

```bash
# Showing the recent ones
<main-directory-name (master)> $ git log

# consolidated log history 
<main-directory-name (master)> $ git log --oneline

# get last three commits
<main-directory-name (master)> $ git log -n 3

# consolidated log history, last 3 commits 
<main-directory-name (master)> $ git log --oneline -n 3

# check log of a particular file
<main-directory-name (master)> $ git log <filename>

# shows HEAD and the latest commit
<main-directory-name (master)> $ git log --oneline --decorate
```

- Git Branches

```bash
# check current or all branches. The green one will be the current branch.
<converted-git-repo (master)> $ git branch

# create a new branch
<converted-git-repo (master)> $ git branch <new-feature-branch>
<converted-git-repo (master)> $ git branch

# switch to a new branch
<converted-git-repo (master)> $ git checkout <new-feature-branch>
<converted-git-repo (master)> $ git branch (this shows <new-feature-branch>)
You can start adding/modifying files
<converted-git-repo (master)> $ git add <new files>
<converted-git-repo (master)> $ git commit -m "mesage"  
<main-directory-name (master)> $ git log --oneline

# switch to master branch
<converted-git-repo (master)> $ git checkout master  
<converted-git-repo (master)> $ git branch

# merging changes made from the branch to the master
<converted-git-repo (master)> $ git merge <new-feature-branch>
<converted-git-repo (master)> $ git log --oneline --decorate (shows the latest commit)

# delete the branch. Take note on the directory where you created the branch
<converted-git-repo (master)> $ git branch -d <new-feature-branch>
<converted-git-repo (master)> $ git branch
<converted-git-repo (master)> $ git log --oneline --decorate

```
###

</details>


## Method 3. Cloning remote repository 

You can clone a remote repository from a remote server. For example from Github to your local machine. Github is arguably the most popular web based Git repository hosting service in the world.

To get started with Amplication, the hosted version of the product can be used. You can get started immediately at [app.amplication.com](https://app.amplication.com). After the login page, you will be guided through creating your first service. The [website](https://amplication.com) provides an overview of the application, additional information on the product and guides can be found in the [docs](https://docs.amplication.com).

<details>
<summary>
  Tutorials
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

## Method 4. Creating branches

You can clone a remote repository from a remote server. For example from Github to your local machine. Github is arguably the most popular web based Git repository hosting service in the world.

To get started with Amplication, the hosted version of the product can be used. You can get started immediately at [app.amplication.com](https://app.amplication.com). After the login page, you will be guided through creating your first service. The [website](https://amplication.com) provides an overview of the application, additional information on the product and guides can be found in the [docs](https://docs.amplication.com).

 <details>
<summary>
  Push Changes to Github
</summary> <br />

```bash
<main-directory-name (master)> $ ls 
new-project-folder

<main-directory-name (master)> $ cd new-project-folder
<new-project-folder (master #)> $ git remove -v  (listed all remote references. If this is your first time, it won't show anything)
```
</details>



## Github  jojo

<details>
<summary>
  Creating a repository on Github 
</summary> <br />

- **Step 1**: Provide "Repository name" for example 'git-bootcamp'
- **Step 2**: Add Description (optional)
- **Step 3**: Select Public or Private
- **Step 4**: Initialize this repository with: tick "Add a README file"
- **Step 5**: add .gitignore (optional)
- **Step 6**: Add a license (optional)
- **Step 7**: click "Create repository" 
- **Step 8**: copy the remote repository URL
> [!see this]
> HTTPS or SSH : https://github.com/lpadlan/git-bootcamp.git.

</details>

<details>
<summary>
  Push Changes to Github
</summary> <br />

```bash
<main-directory-name (master)> $ ls 
new-project-folder

<main-directory-name (master)> $ cd new-project-folder
<new-project-folder (master #)> $ git remove -v  (listed all remote references. If this is your first time, it won't show anything)
```
```bash
# case 1. First time push.
<new-project-folder (master #)> $ ls

# push an existing repository from the command line. Remote establishes connection
<new-project-folder (master #)> $ git remote add origin https://github.com/lpadlan/xxx-xxxx.git
<new-project-folder (master #)> $ git branch -M main    --> converts master to main branch
<new-project-folder (master #)> $ git push -u origin main
<new-project-folder (master #)>> $ git remote
origin

<new-project-folder (master #)>(master)> $ git remote -v
origin https://github.com/lpadlan/xxx-xxxx.git (fetch)
origin https://github.com/lpadlan/xxx-xxxx.git (push)

OR
<new-project-folder (master #)> $ git remote add origin https://github.com/lpadlan/xxx-xxxx.git
<new-project-folder (master #)> $ git push -u origin master

# finally push it. This pushes from local to the remote repository
<new-project-folder (master #)> $ git push -u origin master

Username for 'https://github.com':
Password for 'https://lpadlan@github.com':

< pending : what if I change a source and push it, is this still same command. What about for branches,same? >
< change title: Push Changes to Github TO Push Changes to Github. First time 'master'

```

```bash
# case 2. Subsequent push + Add a new file
<new-project-folder (master #)> $ ls

<new-project-folder (master #)> $ git status
<new-project-folder (master #)> $ git add .
<new-project-folder (master #)> $ git status
<new-project-folder (master #)> $ git commit -m "message"  (OR git commit -am "message")
<new-project-folder (master #)> $ git push

```

</details>

<details>
<summary>
  Pulling Changes from Github. Get the latest changes from repository
</summary> <br />

This means, someone has made changes from Github. It is different to your local. Good practice to 'git pull' before 'git push'

```bash
<main-directory-name (master)> $ ls 
new-project-folder

<main-directory-name (master)> $ cd new-project-folder
<new-project-folder (master)> $ git status
On branch main
Your branch is up to date with 'origin/main'

<new-project-folder (master)> $ git pull (get latest version of the files) 

<new-project-folder (master)> $ ls (check the newly added from github)
<new-project-folder (master)> $ cat <file that was added> 
<new-project-folder (master)> $ git log
```
 
</details>

<details>
<summary>
  Forking and Cloning a Github Repository
</summary> <br />

```bash
# Forking
click fork button

# Cloning
click Clone button
<main-directory-name (master)> $ git clone <URL>

<main-directory-name (master)> $ ls
<main-directory-name (master)> $ ls -al
<main-directory-name (master)> $ git branch -a
<main-directory-name (master)> $ git remote -v

```
 
</details>

<details>
<summary>
  git log
</summary> <br />

```bash
 commit <hash> (HEAD -> main, origin -> main)

	HEAD -> main	---> local pointer
	origin -> main  ---> remote pointer, updated in the remote repository

# to see the commit details:
<new-project-folder (master #)> git log
<new-project-folder (master #)> git show <commit code or the hash>

```
</details>

<details>
<summary>
  git status
</summary> <br />

```bash
  > red   : files that needs to be added
  > green : files that were just added and to be committed

```
</details>


## Case#4. Creating a repository from Github 

xxxx
 

<details>
<summary>
  Tutorials
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>


## Case#5. Creating a repository from Github 

 xxx

<details>
<summary>
  Tutorials
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

## Using Git With Android 

xxx
 

<details>
<summary>
  Setting up for Git usage
</summary> <br />

```bash
1. Settings > Git > Path to Git executable = C:\Program Files\Git\cmd\git.exe > click Test > Apply > OK
2. Settings > GitHub > Add account > GitHub > > Apply > OK
```
 
</details>

<details>
<summary>
  Importing an Android Studio Project into Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>


<details>
<summary>
  Push Changes From Android Studio Project to Github
</summary> <br />

```bash
1. Add or Modify a File
2. click Commit 
2.  
```
 
</details>

<details>
<summary>
  Clone a repository from Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Puliing Changes from Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
   Branching
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Merge Branches
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

## Using Git With Jetbrain's IntelliJ IDEA 

xxx 
<details>
<summary>
  Setting up for Git usage
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Importing an Android Studio Project into Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>


<details>
<summary>
  Push Changes From Android Studio Project to Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Clone a repository from Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Puliing Changes from Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
   Branching
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Merge Branches
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

## Using Git With Eclipse 

xxx 

<details>
<summary>
  Setting up for Git usage
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Importing an Android Studio Project into Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>


<details>
<summary>
  Push Changes From Android Studio Project to Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Clone a repository from Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Puliing Changes from Github
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
   Branching
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

<details>
<summary>
  Merge Branches
</summary> <br />

```bash
docker run --network=internal --name k6 --rm -i grafana/k6 run - <test.js
```
 
</details>

## Resources

- **[git](https://git-scm.com/)** Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.


<a name="contributing_anchor"></a>
## Contributing

xxx 

- Bug Report: If you see an error message or encounter an issue while using xxxx 

- Feature Request: If you have an idea xxx 

- Documentation Request: If you're reading the xxx 

Not sure where to start? Join our discord and we will help you get started!



## Contributors

 

## License

A large part of this project is licensed under the xxx 
