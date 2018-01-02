# gitnote

## Settings

```bash
# global settings (replace --global with --local for doing local settings)
$ git config --global user.name "dokelung"
$ git config --global user.email "dokelung@gmail.com"
$ git config --global core.editor "emacs"
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.st status
$ git config --global alias.l "log --oneline --graph"
$ git config --global alias.ls 'log --graph --pretty=format:"%h <%an> %ar %s"'

# show current settings
$ git config --list
```

## Basic

```bash
# init
$ git init

# show info
$ git st

# add changes to staging area
$ git add welcome.html
$ git add *.html
$ git add -all # add all changes of this project to staging area
$ git add .    # add all changes under current directory to staging area

# commit
$ git commit -m "init commit"
$ git commit --allow-empty -m "empty" # commit with no change

# combine add and commit
$ git commit -a -m "update content" # add and commit changes(untracked files are ignored)

# add new empty directory
$ mkdir empty
$ touch empty/.keep
$ git add -all
$ git commit -m "add new empty directory"

# to ignore some files, put the file patterns to .gitignore to ignore them
$ git add -f welcome.html # force add to staging area no matter the status of .gitignore
$ git clean -fX           # remove all files which are ignored
```

## Log

```bash
# log
$ git log
$ git log --oneline --graph                               # simple expression

$ git log --oneline --author="dokelung"                   # search by author name
$ git log --oneline --author="dokelung\|dokelung2"        # search by multiple author name
$ git log --oneline --grep="wtf"                          # search by commit comment
$ git log -S "Python"                                     # search by file content
$ git log --since="9am" --until="12am"                    # search by time
$ git log --since="9am" --until="12am" --after="2018-01"  # search by date 

$ git log welcome.html    # see the log of specified file
$ git log -p welcome.html # see the diffs between each commits
```

## Remove and Rename

```bash
# basic remove
$ rm welcome.html
$ git add welcome.html
$ git commit -m "delete welcome.html"

# remove and add to staging area
$ git rm welcome.html
$ git commit -m "delte welcome.html"

# remove from git but not working directory
$ git rm welcome.html --cached

# basic rename
$ mv hello.html world.html
$ git add --all
$ git commit -m "renmae hello.html to world.html"

# rename and add to staging area
$ git mv hello.html world.html
$ git commit -m "renmae hello.html to world.html"
```

## Modify Last Commit

option `--amend` of command `commit` creates a new commit to replace original commit

```bash
# modify comment of last commit
$ git commit --amend -m "Welcome To Facebook"

# add more files to last commit
$ git add cinderella.html
$ git commit --amend --no-edit
```

## Find the author of one line

```bash
$ git blame index.html
$ git blame -L 5,10 index.html # ony show the info of the specified lines
```

## Get back deleted files/directories

```bash
$ git checkout cinderella.html
$ git checkout .
$ git checkout HEAD~2 welcome.html
```
