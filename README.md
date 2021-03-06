# Coke - Enjoy sniffing your code

Coke is a Shell/Bash command using PHP Code Sniffer allowing rules management per project.

## Configuration file

Create a `.coke` file at your project root :

```
# Command used to launch PHP CodeSniffer (optional - default: phpcs)
command=phpcs
 
# Path used to load Standards (optional)
standard-path=path/to/PHPCS/Standards/

# Standard used by PHP CodeSniffer (required)
standard=Symfony2
 
# Verbose mode (optional - default: false)
verbose=true
 
# White list of files and directories (optional)
src/
test.php
 
# Black list of files and directories (optional)
!Tests
!src/OldFile.php
```

and just launch the command :

```shell
$ coke
```

## Run the command with arguments

You can override `.coke` settings by passing directly configuration as arguments to the command :

```shell
$ coke src test.php --standard=Symfony2 --ignore=Tests,src/OldFile.php -v
```

The order of arguments is not important

`src test.php`                   Files/Directories to include in the check  
`--standard=Symfony2`            Standard to use for check  
`--ignore=Tests,src/OldFile.php` URL patterns to ignore in the check  
`-v`                             Use verbose mode  


## Additional arguments

You can use any phpcs arguments ([documentation](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Configuration-Options))

For example if you want to generate a report with your favorite CI tools you can run 

```shell
$ coke --report-checkstyle=checkstyle.xml
```

## Installation via composer

Add coke in the require-dev section of your composer.json :

```
"require-dev": {
    "m6web/coke" : "~1.0"
}
```

By default composer will add a symlink to coke in vendor/bin/coke.

If you want to change it, add this in your composer.json (more information about this in the [composer documentation](http://getcomposer.org/doc/articles/vendor-binaries.md)) :

```
"config": {
    "bin-dir": "bin"
}
```

Then you can call coke via :

```
./bin/coke
```

## Credits

Developped by the [Cytron Team](http://cytron.fr/) of [M6 Web](http://tech.m6web.fr/).

## License

Coke is licensed under the [MIT license](LICENSE).
