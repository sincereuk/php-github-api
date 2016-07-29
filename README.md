# PHP GitHub API 2.0

In 2.0 lib no longer uses guzzle 3.7, instead it has an HTTPlug abstraction layer. 

For old version please check:

* [branch](https://github.com/KnpLabs/php-github-api/tree/1.7)
* [readme](https://github.com/KnpLabs/php-github-api/tree/1.7/README.md)
* [docs](https://github.com/KnpLabs/php-github-api/tree/1.7/doc)

[![Build Status](https://travis-ci.org/KnpLabs/php-github-api.svg?branch=master)](https://travis-ci.org/KnpLabs/php-github-api)
[![StyleCI](https://styleci.io/repos/3948501/shield?style=flat)](https://styleci.io/repos/3948501)

A simple Object Oriented wrapper for GitHub API, written with PHP5.

Uses [GitHub API v3](http://developer.github.com/v3/). The object API is very similar to the RESTful API.

## Features

* Follows PSR-4 conventions and coding standard: autoload friendly
* Light and fast thanks to lazy loading of API classes
* Extensively tested and documented

## Requirements

* PHP >= 5.5
* [Guzzle](https://github.com/guzzle/guzzle) library,
* (optional) PHPUnit to run tests.

## Autoload

The new version of `php-github-api` using [Composer](http://getcomposer.org).
The first step to use `php-github-api` is to download composer:

```bash
$ curl -s http://getcomposer.org/installer | php
```

Then run the following command to require the library:
```bash
$ php composer.phar require knplabs/github-api php-http/guzzle6-adapter
```

Why `php-http/guzzle6-adapter`? We are decoupled form any HTTP messaging client with help by [HTTPlug](http://httplug.io/). Read about clients in our [docs](doc/customize.md).

## Using Laravel?

[Laravel GitHub](https://github.com/GrahamCampbell/Laravel-GitHub) by [Graham Campbell](https://github.com/GrahamCampbell) might interest you.

## Basic usage of `php-github-api` client

```php
<?php

// This file is generated by Composer
require_once 'vendor/autoload.php';

$client = new \Github\Client();
$repositories = $client->api('user')->repositories('ornicar');
```

From `$client` object, you can access to all GitHub.

## Cache usage

```php
<?php

// This file is generated by Composer
require_once 'vendor/autoload.php';

use Cache\Adapter\Redis\RedisCachePool;

$client = new \Redis();
$client->connect('127.0.0.1', 6379);
// Create a PSR6 cache pool
$pool = new RedisCachePool($client);

$client = new \Github\Client();
$client->useCache($pool);
```

Using cache, the client will get cached responses if resources haven't changed since last time,
**without** reaching the `X-Rate-Limit` [imposed by github](http://developer.github.com/v3/#rate-limiting).


## Documentation

See the [`doc` directory](doc/) for more detailed documentation.

## License

`php-github-api` is licensed under the MIT License - see the LICENSE file for details

## Credits

### Sponsored by

[![KnpLabs Team](http://knplabs.com/front/images/knp-labs-logo.png)](http://knplabs.com)

### Contributors

- Thanks to [Thibault Duplessis aka. ornicar](http://github.com/ornicar) for his first version of this library.
- Thanks to [Joseph Bielawski aka. stloyd](http://github.com/stloyd) for his contributions and support.
- Thanks to [noloh](http://github.com/noloh) for his contribution on the Object API.
- Thanks to [bshaffer](http://github.com/bshaffer) for his contribution on the Repo API.
- Thanks to [Rolf van de Krol](http://github.com/rolfvandekrol) for his countless contributions.
- Thanks to [Nicolas Pastorino](http://github.com/jeanvoye) for his contribution on the Pull Request API.
- Thanks to [Edoardo Rivello](http://github.com/erivello) for his contribution on the Gists API.

Thanks to GitHub for the high quality API and documentation.
