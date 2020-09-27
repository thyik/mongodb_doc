# Basic Git

-   Initial system one time setup ( per-User account)

```sh
// Generate ssh key for ssh cloning
$ ssh-keygen -o

// copy the key to github to allow ssh login
$ cat ~/.ssh/id_rsa.pub

// setup global configuration to allow git commit
$ git config --global user.email "your@email.com"
$ git config --global user.name "Your Name"


```

-   basic git command

```bash

// create and init to a local repo
$ git init

// clone a remote
$ git clone <url>

$ cd <cloned project>

// check status of staging area
$ git status

// check commit logs
$ git log

// commit a change
$ git commit -m "Message#1 "

// push to remote branch
$ git push <remote> <branch>

// fetch and merge from remote repo
$ git pull

// fetch remote repo
$ git fetch

// merging
$ git merge <target-branch>

// rebase
$ git rebase <onto branch>

// one line summary log
$ git log --pretty=oneline

// with tree view
$ git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit

// create alias
$ git config --global alias.logline "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
$ git logline

```

-   branching / merging process

```
//
$ git checkout -b branchname <sha1-of-commit or HEAD~3>

// merging remote master
$ git pull

$ git checkout my-feature

$ git merge origin/feature

$ git push origin my-feature:feature

// merge conflict
// - to show conflict status
$ git status

// - to start resolve conflict. ope the file and resolve
$ nano <conflict file>

$ git add .
$ git commit
```

## Reference for git work flow

-   [Branching - Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
-   [Rebase](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
-   [Cherry Pick](https://git-scm.com/docs/git-cherry-pick)
