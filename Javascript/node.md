# Node

## Manage Node Installation using NVM

It is good idea to remove any existing Node installation in your system before using NVM

### Installation

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash`

Reload terminal profile `source ~/.zshrc`

Verify installation `command -v nvm`

### Install desired node version

View available node version `nvm ls-remote`

Install node `nvm install 14.7.0` or 16.3.0, 12.22.1, etc

or install latest version `nvm install node`

### Remove existing Node installed via Brew

```
brew uninstall --ignore-dependencies node 
brew uninstall --force node 
```

## References

https://tecadmin.net/install-nvm-macos-with-homebrew/

https://github.com/nvm-sh/nvm