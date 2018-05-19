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

# home server
Host home.example.com
    HostName example.com
    User root
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/home

```

### Terminal Access

`ssh <username>@<alias_host>`

example:

`ssh root@home.example.com`

### Github / Bitbucket Access

* In any of your project edit their remote url, example:

`git@work.github.com:my-project/api.git`

use `work.github.com` alias instead of original url `github.com`

## Reference

* [https://confluence.atlassian.com/bitbucket/set-up-additional-ssh-keys-271943168.html#SetupadditionalSSHkeys-ssh2](https://confluence.atlassian.com/bitbucket/set-up-additional-ssh-keys-271943168.html#SetupadditionalSSHkeys-ssh2)