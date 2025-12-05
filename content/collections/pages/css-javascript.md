---
id: a92ce050-2c17-4b4d-8a69-c099759c1502
blueprint: page
title: 'CSS & JavaScript'
intro: 'Statamic can load custom stylesheets and Javascript files located in the `public/vendor/` directory, or from external sources.'
---
:::tip
This guide is intended for apps adding CSS & JavaScript to the Control Panel. If you're building an addon, please see our [Vite Tooling](/addons/vite-tooling) guide instead.
:::

## Using Vite (recommended) {#using-vite}
[Vite](https://vite.dev) is the recommended frontend build tool in the Statamic and Laravel ecosystems. 

To set up Vite for the Control Panel, run the setup command:

```bash
php please setup-cp-vite
```

It will install the necessary dependencies, create a `vite-cp.config.js` file, and publish any necessary stubs.

You can add any CSS to the `resources/css/cp.css` file, and any JavaScript to the `resources/js/cp.js` file. 

To start Vite, run `npm run cp:dev` and to build for production, run `npm run cp:build`.

## HMR and Vue Devtools

To use Hot Module Reloading (HMR) or the [Vue Devtools](https://devtools.vuejs.org) browser extension, you will need to publish a special "dev build" of Statamic.

You can do this via the `vendor:publish` command:

```
php artisan vendor:publish --tag=statamic-cp-dev
```

Alternatively, it can be symlinked:

```
ln -s /path/to/vendor/statamic/cms/resources/dist-dev public/vendor/statamic/cp-dev
```

Statamic will use the dev build as long as `APP_DEBUG=true` in your `.env` and the `public/vendor/statamic/cp-dev` directory exists. You **shouldn't** commit these or use this on production.

## Using `<script>` tags in the Control Panel

For externally-hosted scripts, you may register assets to be loaded in the Control Panel with the `externalScript` method. This method accepts the URL of an external script.


```php
use Statamic\Statamic;

class AppServiceProvider
{
    public function boot()
    {
        Statamic::externalScript('https://kit.fontawesome.com/5t4t4m1c.js');
    }
}
```

Otherwise, for inline scripts, you may use the `inlineScript` method. You should omit the `<script>` tags.

```php
use Statamic\Statamic;

class AppServiceProvider
{
    public function boot()
    {
        Statamic::inlineScript('window.Beacon("init", "abc123")');
    }
}
```