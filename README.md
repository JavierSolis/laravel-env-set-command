# Notes to update Laravel 9

```
{
    "name": "laravel/laravel",
    "type": "project",
    "description": "The Laravel Framework.",
    "keywords": [
        "framework",
        "laravel"
    ],
    "license": "MIT",
    "require": {
        "php": "^8.0",
        "doctrine/dbal": "^3.5",
        "guzzlehttp/guzzle": "^7.2",
        "laravel/framework": "^9.19",
        "laravel/tinker": "^2.7",
        "nesbot/carbon": "^2.62"
    },
    "require-dev": {       
        "javiersolis/laravel-env-set-command": "^1.0.1",
        "fakerphp/faker": "^1.9.1",
        "laravel/pint": "^1.0",
        "laravel/sail": "^1.0.1",
        "mockery/mockery": "^1.4.4",
        "nunomaduro/collision": "^6.1",
        "phpunit/phpunit": "^9.5.10",
        "spatie/laravel-ignition": "^1.0"
    },
    "autoload": {
        "psr-4": {
            "App\\": "app/",
            "Database\\Factories\\": "database/factories/",
            "Database\\Seeders\\": "database/seeders/"
        }
    },
    "autoload-dev": {
        "psr-4": {
            "Tests\\": "tests/"
        }
    },
    "scripts": {
        "post-autoload-dump": [
            "Illuminate\\Foundation\\ComposerScripts::postAutoloadDump",
            "@php artisan package:discover --ansi"
        ],
        "post-update-cmd": [
            "@php artisan vendor:publish --tag=laravel-assets --ansi --force"
        ],
        "post-root-package-install": [
            "@php -r \"file_exists('.env') || copy('.env.example', '.env');\""
        ],
        "post-create-project-cmd": [
            "@php artisan key:generate --ansi"
        ]
    },
    "extra": {
        "laravel": {
            "dont-discover": []
        }
    },
    "config": {
        "optimize-autoloader": true,
        "preferred-install": "dist",
        "sort-packages": true,
        "allow-plugins": {
            "pestphp/pest-plugin": true
        }
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {
            "type":"git",
            "url":"git@github.com:JavierSolis/laravel-env-set-command.git"
        }
    ]
}
```




# Laravel `env:set` Command

[![Latest Version on Packagist](https://img.shields.io/packagist/v/imliam/laravel-env-set-command.svg)](https://packagist.org/packages/imliam/laravel-env-set-command)
[![Total Downloads](https://img.shields.io/packagist/dt/imliam/laravel-env-set-command.svg)](https://packagist.org/packages/imliam/laravel-env-set-command)
[![License](https://img.shields.io/github/license/imliam/laravel-env-set-command.svg)](LICENSE.md)
[![CI Status](https://github.com/imliam/laravel-env-set-command/workflows/Run%20Tests/badge.svg)](https://github.com/imliam/laravel-env-set-command/actions)

Set a .env file variable from the command line.

![Example command output](./screenshot.png)

<!-- TOC -->

- [Laravel `env:set` Command](#laravel-setenv-command)
    - [Installation](#installation)
    - [Usage](#usage)
    - [Changelog](#changelog)
    - [Contributing](#contributing)
        - [Security](#security)
    - [Credits](#credits)
    - [License](#license)

<!-- /TOC -->

## Installation

You can install the package with [Composer](https://getcomposer.org/) using the following command:

```bash
composer require imliam/laravel-env-set-command:^1.0
```

## Usage

When running the `env:set` artisan command, you must provide both a key and value as two arguments.

```bash
$ php artisan env:set app_name Example
# Environment variable with key 'APP_NAME' has been changed from 'Laravel' to 'Example'
```

You can also set values with spaces by wrapping them in quotes.

```bash
$ php artisan env:set app_name "Example App"
# Environment variable with key 'APP_NAME' has been changed from 'Laravel' to '"Example App"'
```

The command will also create new environment variables if an existing one does not exist.

```bash
$ php artisan env:set editor=vscode
# A new environment variable with key 'EDITOR' has been set to 'vscode'
```

Instead of two arguments split by a space, you can also mimic the `.env` file format by supplying `KEY=VALUE`.

```bash
$ php artisan env:set app_name=Example
# Environment variable with key 'APP_NAME' has been changed from 'Laravel' to 'Example'
```

The command will do its best to stop any invalid inputs.

```bash
$ php artisan env:set @pp_n@me Laravel
# Invalid environment key @pp_n@me! Only use letters and underscores
```

You can specify the external `.env` file in the third optional argument.

```bash
$ php artisan env:set APP_NAME TestApp /var/www/my_own_env.env
# Environment variable with key 'APP_NAME' has been changed from 'Laravel' to 'TestApp'
```

Or in the second parameter if you use key=value syntax.
```bash
$ php artisan env:set APP_NAME=TestApp /var/www/my_own_env.env
# Environment variable with key 'APP_NAME' has been changed from 'Laravel' to 'TestApp'
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email liam@liamhammett.com instead of using the issue tracker.

## Credits

- [Liam Hammett](https://github.com/imliam)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
