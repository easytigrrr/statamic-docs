---
id: c51a5de8-4b02-4240-8195-3ff7987c43cf
title: 'Installing a Starter Kit'
intro: Installing a Starter Kit is a pretty simple thing, but like with many things in life, there are a few different ways you can do it. Let's cover them all.
template: page
blueprint: page
nav_title: Installing
---
## Read this first

Most (but not all) Starter Kits are intended to be used in a brand new, empty site. Be sure to read each Kit's documentation before installing into an existing site so you know what to expect and how to get the most out of it.

## Installing from the command line

You can spin up a **new** install of Statamic along with a Starter Kit at the all in one command by using the [Statamic CLI Tool](https://github.com/statamic/cli):

``` shell
statamic new my-site vendor/starter-kit
```

You can alternatively install a Starter Kit into an _existing site_ by running the following command while inside that install's root directory:

``` shell
php please starter-kit:install vendor-name/starter-kit-name
```

### Installing a paid starter kit {#paid}

If you are installing a paid starter kit, you will be prompted to purchase and/or validate a single-use license. Once successfully installed, this license will be marked as used and cannot be used on future Statamic sites.

### When to clear your site first

If you are installing into a fresh Statamic installation (a pre-built site, for example), you may wish to clear your site of any sample or placeholder content first.

If you are installing a more _modular_ or functionality-driven type Starter Kit into an existing Statamic site (like an icon set or e-commerce checkout), you will want to skip this step!

The installer will ask you if you wish to clear your site first, but you can also force clear by running with the `--clear-site` install option.

### Installing without dependencies

If you wish to install without bundled dependencies, you can run with the `--without-dependencies` install option.
