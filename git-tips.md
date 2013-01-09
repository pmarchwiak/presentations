# Git Tips

---

# Overview

![git] (http://git-scm.com/images/logo@2x.png)

- Command review
- Workflow tips
- Git and Eclipse

---

# clone

---

# clone

Retrieves copy of repository including all history.    

---

# status

---

# add

---

# add

Add file contents to the index.

- Add new files
- Stage modified files for commit
- Mark conflicts as resolved

---

# commit

---

# commit

Commit staged files to your local repository.

---

# add / commit

![lifecycle](http://git-scm.com/figures/18333fig0201-tn.png)

---

# merge

---

# merge

Merge changes from another branch into your current branch.

Merge a local branch:

`git merge other-branch-name`

Merge a remote branch:

`git merge origin/develop`

---

# fetch

---

# fetch 

Fetch changes from another repository. Does not affect your working directory.

>Fetches named heads or tags from one or more other repositories, along with the objects necessary to complete them.

---

# pull

---

# pull

Incorporates changes from a remote repository into the current branch.

In its default mode, git pull is shorthand for 

`git fetch` 

followed by 

`git merge FETCH_HEAD` 

---

# push

---

# push

Push your committed changes to a remote repository.

>Updates remote refs using local refs, while sending objects necessary to complete the given refs. 

Without any options

`git push`

will push changes from your current branch to the remote branch with a matching name. Being more explicit can be helpful:

`git push origin develop` - Push your current branch to `develop` branch on the remote named `origin`.

---

# log

---

# log

Bonus: try out `gitk` if you haven't.


---

# Workflow

## Branching is cheap!

- Fast - Creation, merging, deletion takes seconds (literally)
- Simple - Git (like other DVCSs) stores a DAG of commits rather than a linear history. 

---

# Workflow

## "Git Flow"

<img alt="git flow" src="http://nvie.com/img/2009/12/Screen-shot-2009-12-24-at-11.32.03.png" height="500">

---

# Workflow

## Our Workflow - The Basics

- `master` branch represents production
- `develop` branch contains current line of development
- Branch off `develop` for new features / bug fixes
    - Merge back in when done
---

# Workflow

Branch for all but the most trivial changes. 

This frees your `develop` branch to track the remote.

Push local branches to:

- deploy an unfinished feature
- back up an unfinished feature
- collaborate

---

# stash

---

# stash

Things can get messy when you want to switch contexts (branches). You may not want to commit your half-done work.

`git stash` to the rescue!

---

# stash

Stashing takes the dirty state of your working directory (modified tracked files and staged changes) and saves it on stack of unfinished changes.

`git stash`

`git stash save "some description"`

This frees you to switch branches to work on something else. To return to your previous work in progress apply your stashed changes with

`git stash pop`

or 

`git stash apply stash@{2}`

---

# Amending commits

Have you ever committed something and then realized you missed a file?

Or wanted to change the commit message?

---

# Amending commits

`git commit --amend` will amend your staged changes to the previous commit and/or allow you to update the commit message.

Note: if you have already pushed your changes, then it is too late. 

---

# Eclipse and Git

<img alt="egit logo" src="http://www.eclipse.org/egit/egit2.png" height="100">

EGit is the Eclipse plugin for git.

- Included with Eclipse since Juno release.
- Very active development (read: can be buggy) so use the most recent
version of Eclipse you can. ( As of Jan 2013, I recommend Spring Tool Suite based on 3.8.1)

---

# EGit - Staging View

`Window`->`Show View`->`Other…`->`Git Staging`

Easily review, stage, and commit changes from one place.

<img src="http://wiki.eclipse.org/images/6/60/Egit-1.2-staging-view.png">

---

# EGit - History View

Make sure to "Show All Branches" and "Follow Renames".

---

# Bash Auto-Completion

Tab completion for commits, branch names, tags, etc.

    !bash
    $ git co<tab><tab>
    commit config

Mac install [instructions](https://github.com/bobthecow/git-flow-completion/wiki/Install-Bash-git-completion)

---

# Resources

![pro git book](http://git-scm.com/images/books/pro-git@2x.jpg)

http://git-scm.com/book is a great read.


