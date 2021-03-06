Composer Preserve Paths
=======================

[![Build Status](https://travis-ci.org/drustack/composer-preserve-paths.svg?branch=master)](https://travis-ci.org/drustack/composer-preserve-paths)
[![Coverage Status](https://coveralls.io/repos/drustack/composer-preserve-paths/badge.svg?branch=master&service=github)](https://coveralls.io/github/drustack/composer-preserve-paths?branch=master)
[![Latest Stable Version](https://poser.pugx.org/drustack/composer-preserve-paths/v/stable.svg)](https://packagist.org/packages/drustack/composer-preserve-paths)
[![Total Downloads](https://poser.pugx.org/drustack/composer-preserve-paths/downloads.svg)](https://packagist.org/packages/drustack/composer-preserve-paths)
[![License](https://poser.pugx.org/drustack/composer-preserve-paths/license.svg)](https://packagist.org/packages/drustack/composer-preserve-paths)

Composer plugin for preserving custom paths and supporting nested packages.

This way you can:

-   Provide custom files or directories that will not be overwritten on `composer install` or `composer update`
-   Place packages within the directory of another package (using a composer installer like
    [composer/installers](https://packagist.org/packages/composer/installers))

Installation
------------

Simply install the plugin with composer:

    $ composer require drustack/composer-preserve-paths:~1.0

Configuration
-------------

For configuring the paths you need to set `preserve-paths` within the `extra` of your root `composer.json`.

    {
        "extra": {
            "preserve-paths": [
                "web/sites/all/modules/contrib",
                "web/sites/all/themes/contrib",
                "web/sites/all/libraries",
                "web/sites/all/drush",
                "web/sites/default/settings.php",
                "web/sites/default/files"
            ]
        }
    }

Example
-------

An example composer.json using [composer/installers](https://packagist.org/packages/composer/installers):

    {
        "config": {
            "vendor-dir": "vendor"
        },
        "extra": {
            "installer-paths": {
                "web/": [
                    "type:drupal-core"
                ],
                "web/profiles/{$name}/": [
                    "type:drupal-profile"
                ],
                "web/sites/all/drush/{$name}/": [
                    "type:drupal-drush"
                ],
                "web/sites/all/libraries/{$name}/": [
                    "type:drupal-library"
                ],
                "web/sites/all/modules/contrib/{$name}/": [
                    "type:drupal-module"
                ],
                "web/sites/all/modules/custom/{$name}/": [
                    "type:drupal-custom-module"
                ],
                "web/sites/all/themes/contrib/{$name}/": [
                    "type:drupal-theme"
                ],
                "web/sites/all/themes/custom/{$name}/": [
                    "type:drupal-custom-theme"
                ]
            },
            "preserve-paths": [
                "web/sites/all/modules/contrib",
                "web/sites/all/themes/contrib",
                "web/sites/all/libraries",
                "web/sites/all/drush",
                "web/sites/default/settings.php",
                "web/sites/default/files"
            ]
        },
        "repositories": [
            {
                "type": "composer",
                "url": "https://packages.drupal.org/7"
            }
        ],
        "require": {
            "composer/installers": "~1.0",
            "drupal/drupal": "~7.54",
            "drupal/views": "3.x-dev",
            "drustack/composer-preserve-paths": "~1.0"
        }
    }

License
-------

-   Code released under [GPL-2.0+](https://github.com/drustack/composer-preserve-paths/blob/master/LICENSE)
-   Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

Author Information
------------------

-   Wong Hoi Sing Edison
    -   <https://twitter.com/hswong3i>
    -   <https://github.com/hswong3i>

