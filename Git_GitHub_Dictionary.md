# Git & GitHub Dictionary

- Git: versioning system that keeps track of changes, allows for collab and is locally stored (on your computer)

- GitHub: online repo for projects and keeping different, backup for git projects, cloud based (remote)

## Initialize project

start your timeline: `git init`

do this in project repository

creates your git repo

**NOTES**: 

- don't do double `git init`

- don't remove the `.git` folder where your history is kept

## Commits

commiting = making a snapshot, creating a timepoint

messages should be informative: Why change, how adress issue, effects of the change, limitations

`git commit -m 'message'`

        when not adding `-m`, editor will open (set up editor: `git config --global core.editor nano`)

        add commit message to the end of this file and save

*Ungit: tracks that a file is changed (saved on your computer) but it is not saved in git*

*without commits: file is changed but there is not anything yet in* `.git`

create first timepoint: `git add Git_GitHub_Dictionary.md`

`git commit -m "meaningfull message"`

output: 

    `[main (root-commit) 0ba4a52] brief description of differences between git and github and how to get started with git`

 `1 file changed, 33 insertions(+)`

 `create mode 100644 Git_GitHub_Dictionary.md`

had to set these first: 

- `git config --global user.email "julie.de.man@skynet.be"`

- `git config --global user.name "Julie DM"`

git tracks files in subfolder

GitHub: online <=> git: on your computer

## Tracking

`git status` will allow me to check what files are changed, unstaged and untracked 

- to be staged: you have commited it before, made new changes but git recognizes that the new changes are not yet `add`ed or `commit`ed

- to be comitted: you have commited the file before, made new changes and git recognizes that you have `add`ed but not yet `commit`ed

- untracked: is a completely new file/folder that has never been `add`ed or `commit`ted

track your messages: in `.git/logs/HEAD`

easier alternative: `git log`

## Conceptual areas

### 01. Development area

where you develop your project, is on your computer, the folder where your project is developed => working directory

### 02. Staging area

place where you dump the things before sending to local `.git` repo

so first `git add` and then `git commit`

staging area as an organisation point: commiting all at once may be too confusing. You can commit in multiple parts and add specific messages for each of the commits. 

### 03. Local repository

the .git folder, where the snapshots are saved, where your timeline is 

! is local on your computer

check if there is already an initialized `.git` repo there, so that you dont initialize another one

`git commit` sends the snapshot to the local repo 

### 04. Remote repository

https://github.com

used as a backup: .git is your local repo so is not kept if your pc crashes

create new repo under repositories on github

github: limited upload, no data repo

project should always have:

- **README.md**: information about the project, code, main goals, usage, data links etc.

- **.gitignore**: sometimes you want all your files in a certain folder, eg. fasta files etc. but you do not want to create snapshots for them. Files listed in **.gitignore** cannot be staged and commited, you are not tracking them. `git status` will ignore the files in the **.gitignore** file. This file can be in your local repo as well but you can make git also ignore this file by adding **.gitignore** inside **.gitignore**.
  
  ! if you commited it before with all the files: delete it in GitHub and tick 'commit stages', then it is gone in GitHub => `git pull` => `git push`: **.gitignore** is not is not pushed to github
  
  ! if you commited it before on its own you can undo the commit
  
  ! if you staged but not committed it, you can do `git reset <file>` 
  
  this gave a lot of issues with pulling and pushing: `git checkout` and `git rebase --abort` solved it 
  
  ! `git push` => remove file in GitHub => `git pull` => file will now also be deleted locally => if then `git revert HEAD`, file will be back

**NOTE**: should not edit and commit both locally and online, then the pushing and pulling will give issues

connect to remote repo: `git remote add <name> <ssh>`

! ssh is *NOT YOUR* ssh key but the ssh key of the *PROJECT* !

**ssh** link when you are contributing and working on it

**https** when you are just using the repo

only commits can cross the bridge to the remote repo

Example: `git remote add folder_link git@github.com:JulieDeMan/VIB_git_training.git`

**NOTE**: should set up a password for the key (**<mark>TO DO</mark>**)

`git push`: put it on github

first: `git push --set-upstream folder_link main` to avoid fatal error

## Traveling through the timeline

`git show commitID1 commitID2`

        shows the full files

alterntive: `git diff commitID1 commitID2`

       shows line by line what is happening, is really comparing 

reverting commits: `git revert`

last commit = `HEAD`

    when reverting: `HEAD~3` = the 4th last commit

    before reverting: need everything staged and commited 

when reverting: editor will pop up and need to also add commit message


