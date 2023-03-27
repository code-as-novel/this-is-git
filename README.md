# this-is-git

- Goddamn idiotic truckload of sh*t

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

- view branches
```
git branch
git branch -v    # more branch information
```

- create new branch
```
git branch <branch-name>
```

- delete branch
```
git branch -d <branch-name>
git branch -D <branch-name>   # force delete
```

- rename branch
```
git branch -m <new-branch-name>  # HEAD should be at the branch to rename
```

- switching branches
```
git switch <branch-name>
git switch -c <new-branch-name>  # create + switch
```

- checkout branched (old way to switch branches)
- checkout = switching + other function
```
git checkout <branch-name>
git checkout -b <new-branch-name>  # create + switch
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