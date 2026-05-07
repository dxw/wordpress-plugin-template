# dxw-wordpress-plugin-template

This template should be used to create all new WordPress plugins.

Please replace this text with a brief description of your plugin.

## PHP compatibility

This plugin requires PHP version 8.2 or above.

## Development

Install the dependencies:

```shell
composer install
```

Run the tests:

```shell
vendor/bin/kahlan spec
```

Run the linters:

```shell
vendor/bin/psalm --show-info=true --find-unused-psalm-suppress
vendor/bin/php-cs-fixer fix
```

## Type analysis

Note that this project aims to create fully typed code, with no Psalm output.
We use a Psalm plugin to provide type annotation and stubs for WordPress
globals, so the need for explicit annotation should be minimal.

Developers should aim for the output of Psalm to look something like this using
the [strictest error level](https://psalm.dev/docs/running_psalm/error_levels/):

```shell
❯ vendor/bin/psalm --error-level=1 --find-unused-psalm-suppress
Target PHP version: 7.4 (inferred from composer.json).
Scanning files...
Analyzing files...


------------------------------

       No errors found!

------------------------------

Checks took 0.01 seconds and used 6.608MB of memory
No files analyzed
Psalm was able to infer types for 97.7273% of the codebase
```

## Modifying the template for a new plugin

To create a new plugin start by modify the following:

* `index.php` - Metadata for the plugin (name, version, etc)
* `composer.json` - Package Metadata and namespace (psr-4)
* `load.php` - Define the namespace

Note: As we're distributing the `vendor.phar` file it may be a good idea to add an [autoload-suffix](https://getcomposer.org/doc/06-config.md#autoloader-suffix)" to the `config` object in `composer.json` and then re-generate the lock file. This ensures that there are no other namespace clashes and a unique hash is generated from the composer.json. This is especially important if other plugins have been based off this template.