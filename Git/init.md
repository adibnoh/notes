# Init

## Generate SSH key

### Basic

`ssh-keygen -t`

### Custom Identifier

`ssh-keygen -t <identifier> -C "<email>"`

eg:

`ssh-keygen -t adib -C "adib@example.com"`

After creating SSH key with custom identifier you need to update your SSH configuration file. Configuration file usually located at `.ssh/config`. If config file is missing, you may created it yourself.

`nano .ssh/config`

Append this line

```conf

Host home.github.com # custom host
        HostName github.com # original host
        User git # user that to interact to host
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/adib ## your private ssh key location

```