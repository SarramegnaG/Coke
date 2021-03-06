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
 
# Only Git changed mode (optional - default: false)
only-git-changed=true
 
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
`--only-git-changed`             Check only changed files  
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
    "m6web/coke" : "~2.0"
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

## Git pre-commit hook

You can use a dedicated [pre-commit hook](https://gist.github.com/JJK801/5867810) :

```
$ wget --output-document=.git/hooks/pre-commit https://gist.githubusercontent.com/JJK801/5867810/raw/f26ec4778273b3f7140428252ab31951de2faba4/pre-commit.sh
```

Or

```
$ curl -L https://gist.githubusercontent.com/JJK801/5867810/raw/f26ec4778273b3f7140428252ab31951de2faba4/pre-commit.sh > .git/hooks/pre-commit
```

Then

```
$ chmod +x .git/hooks/pre-commit
```

## Credits

Developped by the [Cytron Team](http://cytron.fr/) of [M6 Web](http://tech.m6web.fr/).

## License

Coke is licensed under the [MIT license](LICENSE).
