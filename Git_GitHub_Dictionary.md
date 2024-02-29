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

Ungit: tracks that a file is changed (saved on your computer) but it is not saved in git

without commits: file is changed but there is not anything yet in `.git`

create first timepoint: `git add Git_GitHub_Dictionary.md`

`git commit -m "brief description of differences between git and github and how to get started with git"`

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

## Conceptual areas

### 01. Development area

where you develop your project, is on your computer, the folder where your project is developed => working directory

### 02. Staging area

place where you dump the things before sending to local `.git` repo

so first `git add` and then `git commit`

### 03. Local repository

the .git folder, where the snapshots are saved, where your timeline is 

! is local on your computer

check if there is already an initialized `.git` repo there, so that you dont initialize another one

`git commit` sends the snapshot to the local repo

### 
