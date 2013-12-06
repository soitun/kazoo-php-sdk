# PHP Kazoo API

[![Build Status](https://secure.travis-ci.org/2600hz/kazoo-php-sdk.png)](http://travis-ci.org/2600hz/kazoo-php-sdk)

A simple Object Oriented wrapper for Kazoo API, written with PHP5.

## Features

* Follows PSR-0 conventions and coding standard: autoload friendly
* Light and fast thanks to lazy loading of API classes
* Extensively tested and documented

## Requirements

* PHP >= 5.3.2 with [cURL](http://php.net/manual/en/book.curl.php) extension,
* [Guzzle](https://github.com/guzzle/guzzle) library,
* (optional) PHPUnit to run tests.

## Autoload

The new version of `kazoo-php-sdk` using [Composer](http://getcomposer.org).
The first step to use `kazoo-php-sdk` is to download composer:

```bash
$ curl -s http://getcomposer.org/installer | php
```

Then we have to install our dependencies using:
```bash
$ php composer.phar install
```
Now we can use autoloader from Composer by:

```yaml
{
    "require": {
        "2600hz/kazoo-php-sdk": "*"
    },
    "minimum-stability": "dev"
}
```

> `kazoo-php-sdk` follows the PSR-0 convention names for its classes, which means you can easily integrate `kazoo-php-sdk` classes loading in your own autoloader.

## Basic usage of `kazoo-php-sdk` client

```php
<?php

// This file is generated by Composer
require_once 'vendor/autoload.php';

$client = new \Kazoo\Client();
$accounts = $client->api('account')->get();
```

From `$client` object, you can access to all Kazoo.

## Cache usage

```php
<?php

// This file is generated by Composer
require_once 'vendor/autoload.php';

$client = new \Kazoo\Client(
    new \Kazoo\HttpClient\CachedHttpClient(array('cache_dir' => '/tmp/kazoo-api-cache'))
);

// Or select directly which cache you want to use
$client = new \Kazoo\HttpClient\CachedHttpClient();
$client->setCache(
    // Built in one, or any cache implementing this interface:
    // Kazoo\HttpClient\Cache\CacheInterface
    new \Kazoo\HttpClient\Cache\FilesystemCache('/tmp/kazoo-api-cache')
);

$client = new \Kazoo\Client($client);
```

## Documentation

See the `doc` directory for more detailed documentation.

## License

`kazoo-php-sdk` is licensed under the MIT License - see the LICENSE file for details

## Credits

### Sponsored by

[![2600hz](http://2600hz.com/images/logo.png)](http://2600hz.com)

### Contributors
- Ben Wann
- Karl Anderson
- James Aimonetti
- Darren Schreiber
- Francis Genet
- Peter Defebvre
- Thanks to [KnpLabs/php-github-api](https://github.com/KnpLabs/php-github-api) for their work on the Php github api, which inspired this library

Thanks to GitHub for the high quality API and documentation.