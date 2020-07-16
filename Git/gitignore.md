# GitIgnore

## Git remove gitignore cache

when file is remove from git, other repo might still tracked those file, run this script to avoid that.

`git rm --cached . -r`

`git add .`

`git commit -m 'remove cache gitignore'`

`git push origin <remote_branch>`