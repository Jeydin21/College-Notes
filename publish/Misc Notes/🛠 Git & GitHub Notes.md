# git Basics

### What is git?

- git is a Version Control System (VCS) for tracking changes in computer files
    - Distributed version control
    - Coordinate work between devs
    - Track change details
    - Revert to old versions
    - Local & remote repos

### What Does “Distributed” Mean?

- You keep your files in a **repository** on your local machine
- You synchronize your repository with a repository on a server
- If you move from one machine to another, you can pick up the changes by syncing with the server
- If your partner uploads some changes to your files, you can pick those up by syncing to the server

### Key Concepts of git

- Keep track of code history
- Takes “snapshots” of your files by making a commit
- Visit/view any snapshot at any time
- Stage files before committing

### git Local View

- In your local copy on git, files can be:
    - In your local repo, i.e. committed
    - Checked out and modified, but not yet committed, i.e. a working copy
    - In-between, in a “staging” area
        - Staged files are ready to be committed, saving a snapshot of all staged states

![[Untitled.png]]

# Using git

### Basic Commands

```Bash
git init # Initialize local repository
git add <file> # add file(s) to index
git status # check status of working tree
git commit # commit changes in index
git push # push to remote repository
git pull # pull latest from remote repository
git clone # clone repository into a new directory
```

### git Availability

- git is available on all operating systems from [here](http://git-scm.com/download)
- git is free to use 😄

### Creating a New git Repo

```Bash
git init # intializes the current folder as a git repo
```

- The command above creates a folder named “.git”
    - This folder contains all the internal files necessary
    - Never change its contents
- Also best to setup personal information using the following command:
    
    ```Bash
    git config # allows you to setup your info
    git config --global user.name "First Last"
    git config --global user.email "email"
    ```
    
- The following command lists all files/folders not tracked by git
    
    ```Bash
    .gitignore
    ```
    

### Cloning an Existing git Repo

```Bash
git clone "url" [localDirectoryName]
```

- This creates the given local directory containing a working copy of the files from the repo, as well as a .git directory used to hold the staging area & your actual local repo

### git Commands

![[Untitled 1.png]]

### Add & Commit a File

- The first time we ask a file to be tracked, as well as before each time we commit a file, we must add it to the staging area:
    
    ```Bash
    git add Hello.java Goodbye.java
    ```
    
    - Takes a snapshot of these files & adds them to the staging area
- To move staged changes into the repo, we commit:
    
    ```Bash
    git commit -m "Fixing bug #22"
    ```
    

### git Branch

- Before working on a file, it’s a good idea to create a branch
    
    ```Bash
    git branch <name of branch> # create branch
    git checkout <name of branch> # position self in branch
    git merge <name of branch> # merge branch while in master
    ```
    

### GitHub

- To link a remote repository to a local repo:
    
    ```Bash
    git remote add <name of repo> <url of repo>
    ```
    
- The initial initialization form the remote repo:
    
    ```Bash
    git clone <name of repo>
    ```
    
- Pull changes from remote repo:
    
    ```Bash
    git pull
    ```
    

### Cheat Sheet

![[git-cheat-sheet-education.pdf]]