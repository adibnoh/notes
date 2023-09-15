# Prettier

Prettier is a opinionated code style fixer for minimalists. It support html, js, css, json and etc. It doesn't support php.

## Installation

`yarn add --dev --exact prettier`

### Config

create config file

`node --eval "fs.writeFileSync('.prettierrc','{}\n')"`

### Ignore

We may exclude any folders in our project to prevent Prettier to run on them.

`nano .prettierignore`

Prettier ignore node_modules folder by default.

## Blade Support

Blade file is not supported by Prettier by default. We need to install additional plugin to allow Prettier to support blade.

`yarn add --dev @shufo/prettier-plugin-blade`

then inside Prettier config file, we need to update it:

`nano .prettierrc`

```json
{
    "plugins": ["@shufo/prettier-plugin-blade", "prettier-plugin-tailwindcss"],
    "overrides": [
        {
            "files": ["*.blade.php"],
            "options": {
                "parser": "blade",
                "tabWidth": 1
            }
        }
    ]
}

```

## Usage

`yarn prettier --write .`

If blade plugin is installed, we need to change the command:

`yarn prettier --write resources/**/*.blade.php .`

