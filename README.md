# Coder

[![Build Status](https://travis-ci.org/klausi/coder.svg?branch=8.x-2.x)](https://travis-ci.org/klausi/coder)

Coder is a library for automated Drupal code reviews and coding standard fixes. It
defines rules for [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)

Built-in support for:
- "Drupal": Coding Standards https://www.drupal.org/coding-standards
- "DrupalPractice": Best practices for Drupal module development

Online documentation: https://www.drupal.org/node/1419980


## Installation

First, make sure Composer is installed correctly:
```
which composer
```

Until CiviCRM Coder is listed in Packagist, you may need to manually add it to
your `~/.composer/composer.json` with something like this:
```
{
    "require": {
        "civicrm/civicrm-coder": "2015-01-19"
    },
    "repositories": [
        {
            "type": "vcs",
            "url":  "https://github.com/xurizaemon/civicrm-coder.git"
        }
    ]
}
```

To make the phpcs and phpcbf commands available globally, add the composer bin path
to your $PATH variable in ~/.profile, ~/.bashrc or ~/.zshrc:
```
export PATH="$PATH:$HOME/.composer/vendor/bin"
```

Register the CiviCRM Coder Standard with PHPCS:
```
phpcs --config-set installed_paths ~/.composer/vendor/civicrm/civicrm-coder/coder_sniffer
```

Or if you want both Drupal and CiviCRM standards, you might need to expand the tildes when providing both, eg:
```
phpcs --config-set installed_paths /home/chris/.composer/vendor/drupal/coder/coder_sniffer,/home/chris/.composer/vendor/civicrm/civicrm-coder/coder_sniffer
```

## Usage

Check Drupal coding standards
```
phpcs --standard=Drupal --extensions=php,module,inc,install,test,profile,theme /file/to/drupal/example_module
```

Check Drupal best practices
```
phpcs --standard=DrupalPractice --extensions=php,module,inc,install,test,profile,theme /file/to/drupal/example_module
```

Automatically fix coding standards
```
phpcbf --standard=Drupal --extensions=php,module,inc,install,test,profile,theme /file/to/drupal/example_module
```


## Working with Editors

Drupal Code Sniffer can be used with various editors.

Editors:

* Eclipse: https://www.drupal.org/node/1420004
* Komodo: https://www.drupal.org/node/1419996
* Netbeans: https://www.drupal.org/node/1420008
* Sublime Text: https://www.drupal.org/node/1419996
* vim: https://www.drupal.org/node/1419996


## Automated Testing (PHPUnit)

Coder Sniffer comes with a PHPUnit test suite to make sure the sniffs work correctly.
Use Composer to install the dependencies:

```
composer install
```

Then execute the tests:
```
./vendor/bin/phpunit
```


## Maintainers
Klaus Purer, https://www.drupal.org/u/klausi


## Credits

Greg Sherwood and Squiz Pty Ltd, many sniffs are modified copies of their original
work on [PHPCS](https://github.com/squizlabs/PHP_CodeSniffer).
