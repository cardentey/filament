---
title: Installation
---

## Requirements

Filament has a few requirements to run:

- PHP 8.0+
- Laravel v8.0+
- Livewire v2.0+

This package is compatible with other Filament v2.x products. The [form builder](/docs/forms) and [table builder](/docs/tables) come pre-installed with the package, and no other installation steps are required to use them within the admin panel.

## Installation

To get started with the admin panel, you can install it using the command:

```bash
composer require filament/filament:"^2.0"
```

If you don't have one, you may create a new user account using:

```bash
php artisan make:filament-user
```

Visit your admin panel at `/admin` to sign in, and you're now ready to start [building resources](resources)!

[<img src="https://user-images.githubusercontent.com/41773797/147615302-daec5d1c-e3ac-428a-98c2-c3fb40d945b5.png">](https://demo.filamentphp.com)

## Deploying to production

By default, all `App\Models\User`s can access Filament locally. To allow them to access Filament in production, you must take a few extra steps to ensure that only the correct users have access to the admin panel.

Please see the [Users page](users#authorizing-access-to-the-admin-panel).

If you don't complete these steps, there will be a 404 error when you try to access the admin panel in production.

## Publishing the configuration

If you wish, you may publish the configuration of the package using:

```bash
php artisan vendor:publish --tag=filament-config
```

## Publishing the translations

If you wish to translate the package, you may publish the language files using:

```bash
php artisan vendor:publish --tag=filament-translations
```

## Upgrade Guide

To upgrade the package to the latest version, you must run:

```bash
php artisan config:clear
php artisan livewire:discover
php artisan route:clear
php artisan view:clear
```

Alternatively, you may use the `filament:upgrade` command to do this all at once:

```bash
composer update
php artisan filament:upgrade
```

We recommend adding these commands to your `composer.json`'s `post-update-cmd`:

```json
"post-update-cmd": [
    // ...
    "@php artisan filament:upgrade"
],
```
