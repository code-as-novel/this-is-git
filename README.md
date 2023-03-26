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
git config --global user.name "Sang Kim"
git config user.name

git config --global user.email "sang@gmail.com"
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