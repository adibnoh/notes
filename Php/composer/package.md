# Package

## Create New Package

`composer init`

Update Autoload

`composer dump`

## Use Packages

### Locally

Add this line in your composer.json

```json

...

"repositories": [
        {
            "type": "path",
            "url": "../../packages/graduan-sso"
        }
    ]
...

```

### Private Repo

Add this line in your composer.json

```json

...

"repositories": [
        {
            "type": "vcs",
            "url": "https://gitlab.com/developer.graduan/chuck-norris-jokes"
        }
    ]
...

```