# Polygon Coding Standards

PHP Coding Standards based on the WordPress Coding Standards and PHP Compatibility. It includes all the important rules defined in the WordPress Handbook. By default, the ruleset includes WordPress-Core, WordPress-Docs, WordPress-Extra, PHP-Compatibility, and PHP-Compatibility-WP.

The following rules are ignored:

- Use Yoda conditions
- Missing translators comment
- Each PHP statement must be on a line by itself
- Line indented incorrectly; expected X tabs, found Y
- Functions must not contain multiple empty lines in a row
- There must be exactly one empty line after the file comment
- Stand-alone post-increment statement found. Use pre-increment instead: ++$variable
- If control structure block found as the only statement within an "else" block. Use elseif instead
- Filenames should be all lowercase with hyphens as word separators (disabled only for filenames that contain version numbers)

If you need to disable or exclude certain rules while writing code, use the following comments:

- // phpcs:ignore
- // phpcs:enable
- // phpcs:disable

To disable the coding standards for an entire file, add one of the comments below at the top of your file.

- // phpcs:ignoreFile
- // phpcs:ignoreFile -- reason to ignore

## Install Stable Packages

The code standards can be installed via Composer. If you want a stable configuration, use the commands below to install all packages from the stable branch. This doesn't support PHP 8 and the latest WordPress sniffs.

```
composer global config repositories.polygon-coding-standards github https://github.com/EusebiuOprinoiu/polygon-coding-standards
composer global config allow-plugins.dealerdirect/phpcodesniffer-composer-installer true
composer global config minimum-stability dev
composer global config prefer-stable true

composer global require --dev "polygon/polygon-coding-standards:dev-master"
```

As an alternative, you can copy and paste the following `composer.json` configuration.

```JSON
{
	"repositories": [
		{
			"url": "https://github.com/EusebiuOprinoiu/polygon-coding-standards",
			"type": "github"
		}
	],
	"config": {
		"allow-plugins": {
			"dealerdirect/phpcodesniffer-composer-installer": true
		}
	},
	"require-dev": {
		"polygon/polygon-coding-standards": "dev-master"
	},

	"minimum-stability": "dev",
	"prefer-stable": true
}
```

## Install Unreleased Packages

The code standards can be installed via Composer. If you want the latest additions of PHPCS and PHP 8 sniffs before they are officially released, use the commands below.

```
composer global config repositories.polygon-coding-standards github https://github.com/EusebiuOprinoiu/polygon-coding-standards
composer global config allow-plugins.dealerdirect/phpcodesniffer-composer-installer true
composer global config minimum-stability dev
composer global config prefer-stable true

composer global require --dev "polygon/polygon-coding-standards:dev-master"
composer global require --dev "wp-coding-standards/wpcs:dev-develop as 3.99.99"
composer global require --dev "phpcompatibility/php-compatibility:dev-develop as 9.99.99"
```

As an alternative, you can copy and paste the following `composer.json` configuration.

```JSON
{
	"repositories": [
		{
			"url": "https://github.com/EusebiuOprinoiu/polygon-coding-standards",
			"type": "github"
		}
	],
	"config": {
		"allow-plugins": {
			"dealerdirect/phpcodesniffer-composer-installer": true
		}
	},
	"require-dev": {
		"polygon/polygon-coding-standards": "dev-master",
		"wp-coding-standards/wpcs": "dev-develop as 3.99.99",
		"phpcompatibility/php-compatibility": "dev-develop as 9.99.99"
	},

	"minimum-stability": "dev",
	"prefer-stable": true
}
```

## Set Default Ruleset

If you would like to set `Polygon` as your default conding standard, add the section below to your configuration.

You should also call the PHPCS Composer Installer plugin during development or in CI environments.

```JSON
{
	"scripts": {
		"phpcs-install": [
			"PHPCSStandards\\Composer\\Plugin\\Installers\\PHPCodeSniffer\\Plugin::run"
		],
		"phpcs-config": [
			"phpcs --config-set default_standard Polygon"
		],
		"post-install-cmd": [ "@phpcs-install", "@phpcs-config" ],
		"post-update-cmd": [ "@phpcs-install", "@phpcs-config" ]
	}
}
```

## Add to Your Projects

Use the coding standards in your projects by creating a file named `phpcs.xml` or `.phpcs.xml` with the content below. Extend the rules as needed by adding additional rules to this file.

```XML
<?xml version="1.0"?>
<ruleset name="Polygon Project Name">
	<description>Custom WordPress Coding Standards for Polygon Project Name</description>

    <rule ref="Polygon"/>
</ruleset>
````
