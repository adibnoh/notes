# Cheat Sheet

## Initialize Git

`git init`

## You can clone git or add repo url

`git clone <repo_url>`

or

`git remote add origin <repo_url>`

## Show remote url

`git config --get remote.origin.url`

or

`git remote -v`

## Update Remote Url

`git remote set-url <remote_name> <new_path>`

## Fetching Remote

`git fetch origin`

## See if there are any incoming changes

`git log HEAD..origin/master --oneline`

If any commits are listed in the output above, then you have incoming changes -- you need to merge. If no commits are listed by git log then there is nothing to merge.

Note that this will work even if you are on a feature branch -- that does not have a tracking remote, since it explicitly refers to origin/master instead of implicitly using the upstream branch remembered by Git.

## Git pull aborted with error filename too long

`git config core.longpaths true`

## Git merge from another branch to master

`git checkout master`

`git pull origin master`

`git merge test`

`git push origin master`

## Git remove gitignore cache

when file is remove from git, other repo might still tracked those file, run this script to avoid that.

`git rm --cached . -r`

`git add .`

`git commit -m 'remove cache gitignore'`

`git push origin <remote_branch>`

## Merge repo

`cd path/to/project-b`

`git remote add project-a path/to/project-a`

`git fetch project-a`

`git merge --allow-unrelated-histories project-a/master`

or whichever branch you want to merge

`git remote remove project-a`

## Check file history

`gitk <filename>`

## Tag

### Checkout Tag to a new Branch

`git checkout tags/<tag_name> -b <branch_name>`

## Commit

### Delete recent commit

`git reset --soft HEAD~1` - keep changes

`git reset --hard HEAD~1` - remove changes

### Temporary switch commit

If you want to temporarily go back to it, fool around, then come back to where you are, all you have to do is check out the desired commit:

`git checkout 0d1d7fc32`

## Reference

* [How to checkout remote git tag](https://stackoverflow.com/questions/35979642/how-to-checkout-remote-git-tag)
* [Git Happens](https://about.gitlab.com/2018/08/08/git-happens/)
* [How to revert a Git repository to a previous commit](https://stackoverflow.com/questions/4114095/how-to-revert-a-git-repository-to-a-previous-commit)