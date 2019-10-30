Laravel MongoDB Passport
===============

[![Latest Stable Version](http://img.shields.io/github/release/narwy/laravel-mongodb-passport.svg)](https://packagist.org/packages/narwy/laravel-mongodb-passport) [![Total Downloads](http://img.shields.io/packagist/dm/narwy/laravel-mongodb-passport.svg)](https://packagist.org/packages/narwy/laravel-mongodb-passport)

A service provider to add support for [Laravel Passport](https://github.com/laravel/passport) and [MongoDB](https://github.com/jenssegers/laravel-mongodb).

Table of contents
-----------------
* [Installation](#installation)

Installation
------------

Installation using composer:

```sh
composer require narwy/laravel-mongodb-passport
```

You need to have your `App\User` class extend `Narwy\Mongodb\Auth\User.php` instead of the default `Illuminate\Foundation\Auth\User`. This user class extends larvel-mongodb eloquent user as well as adding all the standard and required authentication and laravel passport traits.

```php
<?php

namespace App;

use Illuminate\Notifications\Notifiable;
use Narwy\Mongodb\Auth\User as Authenticatable;

class User extends Authenticatable
{
    use Notifiable;
}
```

### Laravel version Compatibility

 Laravel  | Passport                   | Package
:---------|:---------------------------|:----------
 5.5.x    | 4.0.x, 5.0.x, 6.0.x, 7.0.x | 1.1.x
 5.6.x    | 4.0.x, 5.0.x, 6.0.x, 7.0.x | 1.1.x
 5.7.x    | 4.0.x, 5.0.x, 6.0.x, 7.0.x | 1.1.x
 5.8.x    | 4.0.x, 5.0.x, 6.0.x, 7.0.x | 1.1.x
 6.0.x    | 7.5.x                      | 2.x.x
 6.1.x    | 7.5.x                      | 2.x.x
 6.2.x    | 7.5.x                      | 2.x.x
 6.3.x    | 7.5.x                      | 2.x.x
 6.x      | 7.5.x                      | 2.x.x

And add the service provider in `config/app.php`:

```php
Narwy\Mongodb\MongodbPassportServiceProvider::class,
```

For usage with [Lumen](http://lumen.laravel.com), add the service provider in `bootstrap/app.php`.

```php
$app->register(Narwy\Mongodb\MongodbPassportServiceProvider::class);
```

The service provider will override the default Laravel passport models in order to use mongodb's implementation of eloquent. There is no need to register any additional classes or add any additional configuration other than those outlined in [Laravel Passport](https://github.com/laravel/passport) and [MongoDB](https://github.com/jenssegers/laravel-mongodb).
