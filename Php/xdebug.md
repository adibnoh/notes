# Xdebug

## Install

Install via `pecl`

`sudo pecl install xdebug`

Locate `xdebug.so` file

`locate xdebug.so`

Edit `php.ini`

```conf

zend_extension=<xdebug.so path>
xdebug.remote_enable=1
xdebug.remote_autostart=1


```

Restart php

## Wizard

[Run wizard](https://xdebug.org/wizard.php)

## IDE Setup

### VSCode

edit `~/.bashrc` or `~/.zshrc`.

add this line `export XDEBUG_CONFIG="idekey=VSCODE"`

reload profile `source ~/.bashrc` or `source ~/.zshrc`

## Toggle Xdebug

Xdebug may cause your php script to run very slow. If you're in hurry, you can disable them at `php.ini` but it will take so much work to do so

You may try to install this plugin [xdebug-osx](https://github.com/w00fz/xdebug-osx)

### Quick Installation

`curl -L https://raw.githubusercontent.com/w00fz/xdebug-osx/master/xdebug-toggle > /usr/local/bin/xdebug-toggle`

### Make Xdebug Toggle Command Executeable

`chmod +x /usr/local/bin/xdebug-toggle`

### Setup

You need to find Brew Php conf.d directory location

`php -i | grep "conf.d"` - it should show lists of conf.d directory, pick the correct one depend on your Php version

Create `ext-xdebug.ini` inside conf.d directory

`nano ext-xdebug.ini`

```ini

zend_extension=<xdebug.so path>
xdebug.remote_enable=1
xdebug.remote_autostart=1


```

Ensure inside your `php.ini` file does not contain all line above.

Restart your Php and you may toggle your Xdebug using this command below:

`xdebug-toggle` - check Xdebug status
`xdebug-toggle on` - enable Xdebug
`xdebug-toggle off` - disable Xdebug

### Custom Xdebug Toggle Script

If somehow command above does not work, it may cause from Xdebug Toggle script itself

This is my custom script for Xdebug Toggle, inside it also contain command to restart Laravel Valet after toggle command executed

```bash

#!/usr/bin/env bash
# http://github.com/w00fz/xdebug-osx
#
# @author   Djamil Legato http://github.com/w00fz/xdebug-osx
# @license  MIT
# @version  1.2

app="$(basename "$0")"
command="$1"
options="$2"
php_version_dot=$(php -r "\$v=explode('.', PHP_VERSION ); echo implode('.', array_splice(\$v, 0, -1));")
php_version="${php_version_dot//./}"

xdebug_conf_path="$(brew --prefix)/etc/php/$php_version_dot/conf.d"
xdebug_conf_file="ext-xdebug.ini"
xdebug_conf=${xdebug_conf_path}/${xdebug_conf_file}
extension_dir=$(php -r "echo PEAR_EXTENSION_DIR;")
echo $extension_dir
if [ -f "$extension_dir"/xdebug.so ]; then
    if [ ! -f "$xdebug_conf" ] && [ ! -f "$xdebug_conf.disabled" ]; then
        echo ""
        echo "The ini file for Xdebug was not found at '$xdebug_conf_path'"
        echo "Did you install Xdebug via PECL?"
        echo "For more informations: http://github.com/w00fz/xdebug-osx/blob/master/README.md"
        echo ""

        exit 1
    else
        STATUS="enabled"
        IS_PHP_FPM=false
        SERVER_NAME="apache"

        if [ -f "$xdebug_conf" ] && [ -f "$xdebug_conf.disabled" ]; then
            echo ""
            echo "Detected both enabled and disabled Xdebug ini files. Deleting the disabled one."
            echo ""

            rm -rf "$xdebug_conf.disabled"
            STATUS="enabled"
        elif [ -f "$xdebug_conf.disabled" ]; then
            STATUS="disabled"
        fi

        if [ $# -ge 1 ] && [ "$command" == "on" ] || [ "$command" == "off" ]; then
            if [ "$command" == "on" ]; then
                mv "$xdebug_conf.disabled" "$xdebug_conf" 2> /dev/null
                STATUS="enabled"
            elif [ "$command" == "off" ]; then
                mv "$xdebug_conf" "$xdebug_conf.disabled" 2> /dev/null
                STATUS="disabled"
            fi

            current_stable_php_path="/usr/local/opt/php/bin/php"
            if [ -f $(eval echo ${current_stable_php_path}) ]; then
                current_stable_php_version=$(${current_stable_php_path} -r "\$v=explode('.', PHP_VERSION ); echo implode('.', array_splice(\$v, 0, -1));")
            fi

            php_plist_file="~/Library/LaunchAgents/homebrew.mxcl.php@$php_version_dot.plist"
            if [ "${php_version_dot}" == "${current_stable_php_version}" ]; then
                php_plist_file="~/Library/LaunchAgents/homebrew.mxcl.php.plist"
            fi

            if [ -f $(eval echo ${php_plist_file}) ]; then
                IS_PHP_FPM=true
                SERVER_NAME="php-fpm"
            fi

            if [ "$options" == '--no-server-restart' ]; then
                echo ""
                echo "Xdebug has been $STATUS. Will not restart $SERVER_NAME"
            else
                if [ "$IS_PHP_FPM" == true ]; then
                    echo ""
                    echo "Xdebug has been $STATUS, restarting $SERVER_NAME"

                    brew services restart php"${php_version}"

		    echo "Restart valet"
		    { 
			/usr/local/bin/valet restart

			echo "Restart valet success"
		    } || {
			echo "Restart valet failed"  
		    }
                else
                    echo ""
                    echo "Xdebug has been $STATUS, restarting $SERVER_NAME (it might ask for your password)"

                    sudo pkill -9 httpd
                    sudo apachectl -k restart > /dev/null 2>&1
                fi
            fi
        else
            echo ""
            echo "Usage: ${app} <on | off> [--no-server-restart]"
        fi

        echo ""
        echo "You are running PHP v$php_version_dot with Xdebug $STATUS"
        echo ""
    fi
else
    echo ""
    echo "Xdebug for PHP $php_version_dot was never installed or not installed via PECL."
    echo "For more informations: http://github.com/w00fz/xdebug-osx/blob/master/README.md"
    echo ""
    exit 1
fi


```

## Issues

To test out if xdebug is working or not, try run any index.php file at browser.

```php

var_dump('test');

```

With Xdebug enable the styling should look different

## Reference

* [Debugging: Configure VS Code + XDebug + PHPUnit](https://tighten.co/blog/configure-vscode-to-debug-phpunit-tests-with-xdebug)
* [xdebug-osx](https://github.com/w00fz/xdebug-osx)