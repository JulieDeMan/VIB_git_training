# Commands

- `git init` initializes timeline

- `git add` puts files in the staging areas

- set up user profile, every time you start a new project:
  
  - `git config --global user.email "julie.de.man@skynet.be"`
  
  - `git config --global user.name "Julie DM"`
  
  - `git config --global core.editor nano`

- `git commit -m 'message'` adds timestamp to the local `.git` repo

- `git config --list` shows the configs of your project like user name and e-mail

- `git status` track where files are, in what conceptual area

- `git log` check all your commit messages
  
  - `git log -n N`
  
  - `git log --help`
  
  - `git log --abbrev`

- `git show commitID1 commitID2` compares commits by showing the files separately

- `git diff commitID1 commitID2`compares commits side by side

- `git reset filename` will unstage your file

- `git remote add <name> <ssh>` make connection between the local and remote repo's

- `git rm <file>` removes files (requires commit afterwards)

- `git push` push what is in .git to GitHub

- `git pull` gets changes you made in GitHub (online)

- `git reset <file>` if you staged but not committed, and you want to unstage

- `git revert` revert commits

- `git clone <project_ssh>`: sets up connection to an existing project and you

- `git branch <branch_name>`: creates a new branch
  
  - `git branch --list`: lists all branches
  - `git switch -c <name>`: creates branch from the detached head
  - `git branch <newbranch_name> <detached_head_id>` : creates branch from the detached head

- `git checkout <branch_name>` and `git checkout <past_commit_id>`: switch branch/previous commit

- `git switch -`: prevents you from creating a detached head, undoes it

SOLVED THE CONFLICT
