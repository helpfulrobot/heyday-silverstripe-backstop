# SilverStripe Backstop

[![Build Status](https://travis-ci.org/heyday/silverstripe-backstop.png)](https://travis-ci.org/heyday/silverstripe-backstop) [![Code Coverage](https://scrutinizer-ci.com/g/heyday/silverstripe-backstop/badges/coverage.png?s=bf1e5e214accff878d0e81cc8763f03f6a3d60dd)](https://scrutinizer-ci.com/g/heyday/silverstripe-backstop/)

Logging for responses with status codes 400-500

## Installation (with composer)

	$ composer require heyday/silverstripe-backstop:dev-master

## Usage

1. Create a config file in your `mysite`, e.g. "mysite/_config/logging.yml"
2. Set up a `PSR-3` logger service and add to the `Backstop` constructor

		Injector:
			Monolog:
				class: Monolog\Logger
				constructor:
					0: App
					1:
						- '%$StreamHandler'
			StreamHandler:
				class: Monolog\Handler\StreamHandler
				constructor:
					0: '../../error.log'
			Backstop:
				class: Heyday\Backstop\Backstop
				constructor:
					0: '%$Monolog'

## Unit testing
    $ composer install --dev
    $ vendor/bin/phpunit
    
---

##License

SilverStripe Backstop is released under the [MIT license](http://heyday.mit-license.org/)