## Initialize git

`git init`

## You can clone git or add repo url

`git clone <repo_url>`

or

`git remote add origin <repo_url>`

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

`git rm --cached . -r`

`git add .`

`git commit -m 'remove cache gitignore'`

`git push origin <remote_branch>`
