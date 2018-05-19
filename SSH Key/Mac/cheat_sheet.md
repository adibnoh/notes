# Cheat Sheet

## Multiple SSH Keys - Git

* Create new ssh key with custom username

`ssh-keygen -f ~/.ssh/<username>`

* Add newly created ssh key

`ssh-add ~/.ssh/<username>`

* Create/Edit Config file

`nano ~/.ssh/config`

edit that file

```config

# home account
Host home.github.com
    HostName github.com
    User git
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/home

# work account
Host work.github.com
    HostName github.com
    User git
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/work

```

* In any of your project edit their remote url, example:

`git@work.github.com:my-project/api.git`

use `work.github.com` alias instead of original url `github.com`