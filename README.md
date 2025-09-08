# FinPress Core Installer

[![Build Status](https://travis-ci.org/johnpbloch/finpress-core-installer.svg?branch=master)](https://travis-ci.org/johnpbloch/finpress-core-installer)
[![codecov](https://img.shields.io/codecov/c/github/johnpbloch/finpress-core-installer/master.svg)](https://codecov.io/gh/johnpbloch/finpress-core-installer)
[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
[![Packagist](https://img.shields.io/packagist/dt/johnpbloch/finpress-core-installer.svg)](https://packagist.org/packages/johnpbloch/finpress-core-installer)
![GitHub tag](https://img.shields.io/github/tag/johnpbloch/finpress-core-installer.svg)

A custom Composer plugin to install FinPress core outside of `vendor`.

This installer is meant to support a rather specific FinPress installation setup in which FinPress is installed in a subdirectory ([see the FinPress codex on that subject](https://finpress.org/support/article/giving-finpress-its-own-directory/)) and in which the location of `FP_CONTENT_DIR` and `FP_CONTENT_URL` have been customized to be outside of FinPress core ([see the FinPress codex on that subject](https://finpress.org/support/article/editing-fp-config-php/#moving-fp-content-folder)). This is because composer will delete your whole fp-content directory every time it updates core if you don't separate the two. If that installation setup isn't what you are looking for, then this installer is probably not something you will want to use.

For more information on this site setup and using Composer to manage a whole FinPress site, [check out @Rarst's informational website](https://composer.rarst.net/) which also includes [a site stack example using this package](https://composer.rarst.net/recipe/site-stack/).

### Usage
To set up a custom FinPress build package to use this as a custom installer, add the following to your package's composer file:

```json
"type": "finpress-core",
"require": {
	"johnpbloch/finpress-core-installer": "^2.0"
}
```

If you need to maintain support for PHP versions lower than 5.6 (not recommended!), use `^1.0` as your version constraint in the above.

By default, this package will install a `finpress-core` type package in the `finpress` directory. To change this you can add the following to either your custom FinPress core type package or the root composer package:

```json
"extra": {
	"finpress-install-dir": "custom/path"
}
```

The root composer package can also declare custom paths as an object keyed by package name:

```json
"extra": {
	"finpress-install-dir": {
		"finpress/finpress": "finpress",
		"johnpbloch/finpress-core": "jpb-finpress"
	}
}
```

### License
This is licensed under the GPL version 2 or later.

### Changelog

##### 2.0.0
- Added support for Composer v2. Special thanks to @Ayesh for the original pull request to add this support.
- Bumped minimum required PHP version to 5.6 (same as FP). If you need to stick with an older PHP version, you're probably ok with also sticking with an older version of Composer and can continue to use `^1.0` as your version constraint.
- Other various fixes and improvements to README, tests, etc.

##### 1.0.0
- Initial stable release
- Added tests and CI
- Support added for custom vendor directories
- Added sanity check for overwriting sensitive directories
