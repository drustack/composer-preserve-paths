Composer Preserve Paths
=======================

Composer plugin for preserving paths while installing, updating or uninstalling packages.

This way you can:

-   provide custom files or directories that will not be overwritten on `composer install` or `composer update`
-   place packages within the directory of another package (using a composer installer like
    [composer/installers](https://packagist.org/packages/composer/installers))

Installation
------------

Simply install the plugin with composer: `composer require drustack/composer-preserve-paths`

Configuration
-------------

For configuring the paths you need to set `preserve-paths` within the `extra` of your root `composer.json`.

    {
        "extra": {
            "preserve-paths": [
                "web/.htaccess",
                "web/profiles",
                "web/sites",
                "web/web.config"
            ]
        }
    }

Example
-------

An example composer.json using [composer/installers](https://packagist.org/packages/composer/installers):

    {
        "repositories": [
            {
                "type": "composer",
                "url": "https://packages.drupal.org/7"
            }
        ],
        "require": {
            "composer/installers": "~1.0",
            "drupal/drupal": "~7.53"
            "drupal/views": "3.x-dev",
            "drustack/composer-preserve-paths": "~1.0",
        },
        "extra": {
            "installer-paths": {
                "web": [
                    "type:drupal-core"
                ],
                "web/profiles/{$name}": [
                    "type:drupal-profile"
                ],
                "web/sites/all/libraries/{$name}": [
                    "type:drupal-library"
                ],
                "web/sites/all/modules/contrib/{$name}": [
                    "type:drupal-module"
                ],
                "web/sites/all/themes/contrib/{$name}": [
                    "type:drupal-theme"
                ]
            },
            "preserve-paths": [
                "web/.htaccess",
                "web/profiles",
                "web/sites",
                "web/web.config"
            ]
        }
    }
