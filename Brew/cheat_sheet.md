# Cheat Sheet

## View list of services that available

`brew services list`

## Restart a service

`brew services restart <package_name>`

example

`brew services restart php@7.2`

## Option is removed

[Read more here](https://github.com/Homebrew/homebrew-core/issues/31510)

## Issues

### You should find replacements for the following formulae: ilmbase php@7.4

`brew uses --installed ilmbase`

`brew uninstall ilmbase`

[https://apple.stackexchange.com/a/435422](https://apple.stackexchange.com/a/435422)