# Git & GitHub Dictionary

- Git: versioning system that keeps track of changes, allows for collab and is locally stored (on your computer)

- GitHub: online repo for projects and keeping different, backup for git projects, cloud based (remote)

- [GitHub - vibbits/introduction-github: This is a test-repository for the GitHub tutorial.](https://github.com/vibbits/introduction-github)

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

[https://github.com](https://github.com)

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

**NOTE**: should set up a password for the key (**TO DO**)

`git push`: put it on github

first: `git push --set-upstream folder_link main` to avoid fatal error

`git push origin --all` to push all updated branches at once

**Trick**: go to file in github and press '.' => online vscode will open

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

## Troubleshooting

- add and commit something that you don't want, `git revert HEAD` brings you to the previous state
  
  - example: if you added something to a file => `git add` => `git commit` => regret what you added so `git revert HEAD` => what you added is gone

- repo is deleted locally but is still in GitHub:
  
  - `git clone <project_ssh>`
  
  - the **ssh link** sets up the local bridge (no need for doing `git init`, `git remote` etc.)
  
  - if you would use the **url/https** => use this for projects you want to use but not edit (will not allow you to push)

- failing to push: can be that you dont have remote files (files that are in github are not locally) => to solve this you can pull of push again but can lead to issues

- changed file in local repo and changed file in GitHub (remote repo):
  
  - commit and push in GitHub (using online vscode)
  
  - try to push from local repo (after staging and committing ofc.)
  
  - git in terminal local says: first do git pull
  
  - another issue pops up: conflict and branch problem `You have divergent branches and need to specify how to reconcile them.`
  
  - do `git config pull.rebase false`
  
  - `git pull` now results in: `Auto-merging Git_commands.md`
    
    `CONFLICT (content): Merge conflict in Git_commands.md`
    
    `Automatic merge failed; fix conflicts and then commit the result.`
  
  - now in the file you have both versions with info which one comes from where
    
    - <<<<<<< HEAD
      
      adding unintentional conflict - doc 1
      
      =======
      
      add new text to create conflict - doc 2
      
      '>>>>>>>>> '5ccf97681334c7bbd30b20fb51551f294f1beeee
  
  - manually delete it locally => save => stage => commit => push => is fixed

- conflict by merging: `git merge <branch_name>`
  
  - solve in a similar way as above

## Collaboration

settings => collaborators => add nickname or email => accept invite => now the invited person has push rights

collaborators can do anything in the project

## Branching

branches correspond to different timelines (but can be merged back)

connection between branches: latest common point

`git branch <branch_name>`

OG branch = master/main

`git log` will show you the commits of the branch you re in

`git checkout <branch_name>` lets you choose your branch

   ! you can move between branches but also between commits

make new branch: `git branch <branch_name>` and then `git checkout <branch_name>`

list al branches by doing `git branch --list`

staging and commiting stays the same, you are now working on a separate branch

**NOTE**: the file version you will see on the pc will depend on the branch you are in

**NOTE**: before checking out you should close the file

when pushing: push in **both branches**

to get your colleagues folder: `git pull --all`

when doing `git branch --list`, you will only see the main/master branch

If there is an other branch, you will not see that branch if you have not yet used it locally, but you can checkout to that branch (can be solved with `git branch -a`)

when going then back to the main/master branch and listing all the branches, you can see the other branches as well

`git checkout <past_commit_id>` to switch

**detached head**: if you checkout to a previous commit and start commiting from there

    there is no real branch so you will create a 'detached head'

-  `git switch -c <new_branch>` can solve this by making a new branch name

- `git branch <newbranch_name> <detached_head_id>` creates a new branch with detached head if you already have several commits (in the tree, it 'aligns' the commits to the point where you started from)

- `git switch -` prevents the creation of a detached head and undoes the operation

    detached heads can also be created by other, unexplainable ways

**NOTE**: detached heads without branch will not be found back by listing branches

### merge branches

merging branches: `git merge <branch_name>`

the `<branch_name>` will be added to the branch you are on

    this might create conflicts but these can be solved similar to how you solve the file conflicts

## Tagging

`git tag <give_it_a_name>`

if you tag a commit, you can go back to that commit by doing `git checkout <tag_name>` instead of doing `git checkout <commit_id>`

it will add the tag to the 'place you are'

with this, you can tag an earlier version and people can use it via getting it from github

to use a specific tag: download the files manually or clone the whole repo and checkout to that specific tag to use it

## Forking

another way of working in someone elses repo and not messing it up 

but in the end if you have made some good changes, you can ask them to incorporate it 

you add/copy it to your GitHub and you own it => need to still clone it to get it locally

    difference with clone: you make a local copy

in GitHub repo: fork 

    will look like you are creating a new project but you are actually just copying someone elses project

then clone to your local machine

can check if someone forked your project and if they are working on it (see: active/inactive)
