<h2 align="center">
    Nexmo Package for Laravel
</h2>

<p align="center">
    <a href="https://packagist.org/packages/nexmo/laravel"><img src="https://poser.pugx.org/nexmo/laravel/v/stable?format=flat-square" alt="Latest Stable Version"></a>
    <a href="https://packagist.org/packages/nexmo/laravel"><img src="https://poser.pugx.org/nexmo/laravel/v/unstable?format=flat-square" alt="Latest Unstable Version"></a>    
    <a href="https://packagist.org/packages/nexmo/laravel"><img src="https://poser.pugx.org/nexmo/laravel/license?format=flat-square" alt="License"></a>
    <a href="https://packagist.org/packages/nexmo/laravel"><img src="https://poser.pugx.org/nexmo/laravel/downloads" alt="Total Downloads"></a>
</p>

## Introduction

This is a simple Laravel Service Provider providing access to the  [Nexmo PHP Client Library][client-library].

Installation
------------

To install the PHP client library using Composer:

```bash
composer require nexmo/laravel
```

Alternatively, add these two lines to your composer require section:

```json
{
    "require": {
        "nexmo/laravel": "^1.0"
    }
}
```

### Laravel 5.5+

If you're using Laravel 5.5 or above, the package will automatically register the `Nexmo` provider and facade.

### Laravel 5.4 and below

Add `Nexmo\Laravel\NexmoServiceProvider` to the `providers` array in your `config/app.php`:

```php
'providers' => [
    // Other service providers...

    Nexmo\Laravel\NexmoServiceProvider::class,
],
```

If you want to use the facade interface, you can `use` the facade class when needed:

```php
use Nexmo\Laravel\Facade\Nexmo;
```

Or add an alias in your `config/app.php`:

```php
'aliases' => [
    ...
    'Nexmo' => Nexmo\Laravel\Facade\Nexmo::class,
],
```

Configuration
-------------

You can use `artisan vendor:publish` to copy the distribution configuration file to your app's config directory:

```bash
php artisan vendor:publish
```

Then update `config/nexmo.php` with your credentials. Alternatively, you can update your `.env` file with the following:

```dotenv
NEXMO_KEY=my_api_key
NEXMO_SECRET=my_secret
```

Usage
-----
   
To use the Nexmo Client Library you can use the facade, or request the instance from the service container:

```php
Nexmo::message()->send([
    'to'   => '14845551244',
    'from' => '16105552344',
    'text' => 'Using the facade to send a message.'
]);
```

Or

```php
$nexmo = app('Nexmo\Client');

$nexmo->message()->send([
    'to'   => '14845551244',
    'from' => '16105552344',
    'text' => 'Using the instance to send a message.'
]);
```

For more information on using the Nexmo client library, see the [official client library repository][client-library].

[client-library]: https://github.com/Nexmo/nexmo-php
