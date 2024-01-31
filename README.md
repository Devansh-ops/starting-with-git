# starting-with-git

Cheatsheet link: https://education.github.com/git-cheat-sheet-education.pdf

Installing Git: https://git-scm.com/downloads

Git Book: https://git-scm.com/book/en/v2

## Installing

### on Linux and mac:

Install git, it would mostly be preinstalled. check with 
```bash
git --version
```

if not, to install

## on linux (Debain): 
```bash
sudo apt update && sudo apt install git -y
```

## on mac:
```bash
brew install git
```

### on windows

Download and Install the git-scm from the link provided (https://git-scm.com/downloads) 

Mostly, follow the graphical installation steps
- choose your default editor
- Override the default branch to `main` 
(Do not worry, this can be changed later, if not done)

Test the installation via 
`git --version`

Note: will not work in a pre-existing terminal is open, have to open a new terminal

## First time configs

Do the following first-time configs:
Your Identity
`git config --global user.name "Devansh Sehgal"`
`git config --global user.email devanshsehgal02@gmail.com`

Your github settings
`git config --global credential.username Devansh-ops`

More at https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup

## For Password / credential storage 
We will be using GCM (https://github.com/git-ecosystem/git-credential-manager)
Download: https://github.com/git-ecosystem/git-credential-manager/releases/latest

## In Linux

Install seahorse
`sudo apt update && sudo apt install seahorse -y`

then, set up to use secret service 
`git config --global credential.credentialStore secretservice`

Get the debain package (for Debain distributions only, use other methods for other dists)
using `wget` from the download link (https://github.com/git-ecosystem/git-credential-manager/releases/latest)

As on 31 Jan 2024, the command would be 
`wget https://github.com/git-ecosystem/git-credential-manager/releases/download/v2.4.1/gcm-linux_amd64.2.4.1.deb`

install the `.deb` package and configure
```bash
sudo dpkg -i gcm-linux_amd64.2.4.1.deb  # use the correct package name
git-credential-manager configure
```

Now, when you push the repo for the first time, or pull a private repo, you would need to login and / or put a code in `github.com/login/device`

In wsl, you might need to reload the terminal, and / or install some packages
To reload the terminal
```bash
exit
wsl --shutdown
wsl
```
install the packages missing on trying to push, but mainly
```bash
sudo apt update && sudo apt install libice6 -y && sudo apt install libsm6 -y
```

## In Windows

If installed graphically, GCM will be installed by default. As such, the first time you push, or pull a private repo, you would need to sign-in via browser, or put the displayed code in `github.com/login/device`

## In Mac
`TODO: Add mac GCM installation steps`

-----

## Difference between git and github

GIT
❑ Installed locally
❑ Version control
system used on your
computer
❑ Focused on version
control and code
sharing
❑ No user-management
features

Github
❑ Hosted in the cloud
❑ Hosting service for git
projects
❑ Focused on
centralized code
source hosting
❑ Built in user
management features

## VARIOUS GITHUB ALTERNATIVES
❑ Bitbucket
❑ GitLab
❑ Google Cloud Source Repositories.
❑ Phabricator
❑ RhodeCode
❑ SourceForge

## GIT ESSENTIALS
- Repositories
- Commit
- Branches
- Pull Requests

Two ways:
1. Convert a local directory to repository
2. Clone an existing repository from somewhere 

#### GETTING A REPOSITORY

Initializing a repository in an existing directory
Windows: `$ cd C:/Users/user/my_project`
Linux and MAC: `$ cd /Users/user/my_project`
and type : `$ git init -b main`


The directory is not supposed to be empty to commit and push it. To create a blank file, linux / mac users can type 'touch README.md' Then, add to staging area and commit:
```bash
git add README.md
git commit -m "first commit"
```
Now, to upload it on GitHub, create a new (empty) repository, and type
```bash
git remote add origin [link to new repo]
git push -u origin main
```

Note: 
1. we can add the entire folder to the staging area via `git add .`
2. only the first time we push, we need to type in the whole thing. From the next time, we can just commit, and then push via `git push`

##### Cloning 

The `git clone` command is used to create a copy of an existing Git Repository

Example:
```bash
git clone https://github.com/Devansh-ops/starting-with-git
```
Replace url with your required repository url.

## BASICS OF MARKDOWN
reference link: https://www.markdownguide.org/basic-syntax/

\# Heading  
Heading  
\=======  
\#\# Heading 2  
Heading 2  
\---------------  
\*italic\* or \_italic\_  
\*\*bold\*\* or \_\_bold\_\_  
breakline &lt;br&gt; or double space enter  
numbered list, start with 1.  
unordered list, use *  

### PUSHING TO A REPOSITORY
A git push command is used to transfer or push the commit, which is made on a local branch in your computer to a remote repository like GitHub

`git add .`
Adds everything in the directory to the staging state

`git status`
Shows modified files in working directory, staged for your next commit

`git commit -m <commit message>`
Records or snapshots the file permanently in the version history

`git push origin master`
Sends the committed changes of main branch to your remote repository

To add just one file or a set of files replace the “.” with your filename in first command

`git diff`
diff of what is changed but not staged

`git diff --staged`
diff of what is staged but not yet committed

`git commit -m “[descriptive message]”`
commit your staged content as a new commit snapshot

## CHECK WHERE YOUR REPOSITORY REMOTE IS

`git remote -v`
Output should have the repository URL similar to this:
```bash
origin https://github.com/Devansh-ops/starting-with-git.git
(fetch)
origin https://github.com/Devansh-ops/starting-with-git.git
(push)
```
