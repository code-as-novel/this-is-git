# this-is-git

> Goddamn idiotic truckload of sh*t

## Starting
- check version
```
git --version
```

## Configuration
- config name and email
```
git config --global user.name "codelist"
git config user.name

git config --global user.email "codelist@gmail.com"
git config user.email
```

## Git Commands
- git status : show the status of the current repository
- git init : create a new git repository
```
git status
git init
```

- git add : add file to stage area
```
git add file1 file2...
git add .
```

- git commit : commit to repository
```
git commit -m "message"
git commit --amend     # modify previous commit
```

- git add and commit
```
git commit -a -m "message"
```

- git log : show all git commit history
```
git log 
git log --oneline
```

- change git editor to vscode
```
git config --global core.editor "code --wait"
```

## Git ignore
- filename
- foldername - should end with \
- wildcard (*, **, ?, ...)

## Git Branches
- HEAD : current location (ex : HEAD -> main = current location is main)

```
git branch                       # view branches
git branch -v                    # more branch information
git branch -r                    # view remote branches

git branch <branch-name>         # create branch

git branch -d <branch-name>      # delete branch
git branch -D <branch-name>      # force delete

git branch -m <new-branch-name>  # HEAD should be at the branch to rename
```

## Switching Branches (Git Switch / Git Checkout)
- switching branches
```
git switch <branch-name>
git switch -c <new-branch-name>  # create + switch

git switch <remote-branch-name>  # switch to local branch which is connected to remote-branch
```

- checkout = switching + other function
```
git checkout <branch-name>         # old way to switch branch
git checkout -b <new-branch-name>  # create + switch
git checkout <remote-name>/<branch-name>  # checkout remote branch (then it is set as HEAD)
```

## Git Merge
- git always merge to HEAD branch
- fast-forward merge : only moves the HEAD to forward pointer
```
git switch <branch-name>   # go to target branch
git merge <branch-name>
```

- resolving conflicts
1. conflict message
2. open file which has a conflict
3. edit conflicts
4. git add edited files
5. commit files

## Git Diff
- view changes
```
git diff                  # compares working directory and staging area
git diff HEAD             # compares working directory and HEAD
git diff --staged         # compares staging area and last commit
git diff --cached         # compares staging area and last commit
git diff <filename>       # compares only <filename> (can use HEAD or --staged options)
git diff branch1..branch2 # compares two branches
git diff commit1..commit2 # compares two commits (can get commit id from git log)
```

### meaning inside git diff (example)
```
diff --git a/file.txt b/file.txt   # comparing file (alias of file)
index 22d1k31a.. ff332123 100444   # not important
--- a/file.txt                     # a is marked as -
+++ b/file.txt                     # b is marked as +
@@ -3,2 +3,3 @@                    # chunck header (2 lines started line 3)
 one
 two
-three                             # deleted from a
+four                              # added from b
```

## Git Stash
- save changes in a temporary memory
- stashes both working directory and staging area
```
git stash

git stash pop    # re-apply. removes stash
git stash apply  # pop without removing it

git stash list   # view stash list

git stash apply stash@{0}  # apply by stash reference
git stash drop stash@{0}   # delete particular stash
git stash clear  # delete all stash
```

## Git Checkout
- go to previous commit point
- can create a branch based on previos commit point
```
git checkout <commit-hash>   # go to the past commit point
git checkout HEAD~1          # go to the commit before HEAD
git checkout HEAD~2          # go to the 2 commit before HEAD

git switch -                 # go to the branch I left

git checkout HEAD <file>     # discard changes in <file>, reverting back to HEAD
git checkout -- <file>       # the same like HEAD
```

## Git Restore
- restore file to current or previous commit
- unstage file
```
git restore <file>                   # discard changes in <file>, reverting back to HEAD
git restore --source HEAD~1  <file>  # restore back to 1 commit before
git restore --staged <file>          # unstage file
```

## Git Reset
- reset to commit-hash point
- get rid of after the commit-hash point
- use `revert` when the code was shared to other colaborator
```
git reset <commit-hash>         # the changes are still in your source
git reset --hard <commit-hash>  # reset the source also
```

## Git Revert
- make a new commit and undo the `commit-hash` changes
```
git revert <commit-hash>
```

## Git Clone
- Copy remote branch to local
```
git clone <url>
```

## Git Remote
```
git remote -v                 # list remote list
git remote add <name> <url>   # map name and url (name the url)
git remote rename <old> <new> # rename remote
git remote remove <name>      # remove remote
```

## Git Push
```
git push <remote> <branch>    # push <branch> to <remote>
git push <remote> <local-branch>:<remote-branch>  # push <local-branch> to <remote-branch>
git push -u origin master     # sets the upstream of the local master branch
git push                      # can push if upstream is set
git push -M <new-name>        # rename branch
```

## Git Fetch
- fetch downloads changes to the local repository (not to the working directory)
```
git fetch
git fetch <remote>              # fetch all branch in remote
git fetch <remote> <branch>     # fetch specific branch
```

## Git Pull
- pull downloads changes to the working directory
- git fetch + git merge
```
git pull <remote> <branch>
git pull                    # short syntax (if the branch is tracked)
```

## Git Merge
```
git merge <source-branch>
```

## Git Rebase
- !!! Never rebase which has been shared(which has been pushed) !!!
- use it as merge / clean up git history
```
git rebase
```
- rebase rewrites the history
```
git switch feature
git rebase master   # rebase master to feature (merge and clean history)
```
- if there is a conflict after rebasing
- fix the conflict and continue
```
git rebase --continue
```

- rewriteing history (clean up git history)
```
git rebase -i HEAD~4
- pick : commit it
- reword : commit it and modify commit message
- edit :
- fixup : merge with previous commit and remove the commit message
- drop : remove commit
```

## Git Tags
- label commits

- view tag list
```
git tag
git tag -l "searchword *"   # view search word tag list
```
- checking out with tag name
```
check out <tag-name>
```
- compare changes between two tags
```
git diff <tag-name> <tag-name>
```
- pushing tag
```
git push <remote> <tag-name>   # pushing one tag to remote
git push <remote> --tags       # pushing all tags to remote
```

### lightweight tags
- only tag/label 
```
git tag <tag-name>
git tag <tag-name> <commit-hash>    # tag at previous commit
git tag -f <tag-name> <commit-hash> # force tag to other commit (tag name should be unique)
git tag -d <tag-name>               # delete tag
```

### annotated tags
```
git tab -a <tag-name>   # make an annotated tag
git show <tag-name>     # show the annotated tag
```

## README.md
- What the project does
- How to run the project
- Why it's noteworthy
- Who maintains the project

### mark down
- [Markdown-it Link](https://markdown-it.github.io/)

## command line

- ls : show files (-a all files)
```
ls -a
```

- touch : create empty file
```
touch "filename"
```

- start / open : opens window 
```
start .    # windows
open .     # mac
```

- pwd : print working directory
```
pwd
```

- rm "file" (r - recursive, f - force)
```
rm -rf "folder"
```