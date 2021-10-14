# Issues

There are several issues you will encounter when running Laravel Homestead on Windows platform.

## Storage Link not working

```
 symlink(): Protocol error
```

This error might occur happen when you're trying to create symbolic link inside vagrant, to overcome this run `php artisan storage:link` in local machine instead

## No Input File Specified

Re-create homestead

`homestead destroy && homestead up`

need to reinstall certificate to browser

[Using Laravel Homestead: 'no input file specified'](https://stackoverflow.com/questions/24274387/using-laravel-homestead-no-input-file-specified)

## cross-env not found on npm run dev

`sudo npm install cross-env -g`

`npm run watch`

## Timed out while waiting for the machine to boot.

This error popup while vagrant trying to establish connection from local machine to virtual machine.

Some of the solution: 

* Enabled virtualization in BIOS
* Rerun `vagrant up --provision`
* Disabled Hyper-V