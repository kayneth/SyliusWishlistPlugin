<h1 align="center">
    <a href="http://bitbag.shop" target="_blank">
        <img src="doc/BitBagSyliusWishlistPlugin.png" />
    </a>
    <br />
    <a href="https://packagist.org/packages/bitbag/wishlist-plugin" title="License" target="_blank">
        <img src="https://img.shields.io/packagist/l/bitbag/wishlist-plugin.svg" />
    </a>
    <a href="https://packagist.org/packages/bitbag/wishlist-plugin" title="Version" target="_blank">
        <img src="https://img.shields.io/packagist/v/bitbag/wishlist-plugin.svg" />
    </a>
    <a href="http://travis-ci.org/BitBagCommerce/SyliusWishlistPlugin" title="Build status" target="_blank">
            <img src="https://img.shields.io/travis/BitBagCommerce/SyliusWishlistPlugin/master.svg" />
        </a>
    <a href="https://scrutinizer-ci.com/g/BitBagCommerce/SyliusWishlistPlugin/" title="Scrutinizer" target="_blank">
        <img src="https://img.shields.io/scrutinizer/g/BitBagCommerce/SyliusWishlistPlugin.svg" />
    </a>
    <a href="https://packagist.org/packages/bitbag/wishlist-plugin" title="Total Downloads" target="_blank">
        <img src="https://poser.pugx.org/bitbag/wishlist-plugin/downloads" />
    </a>
</h1>

## Overview

This plugin allows you to integrate wishlist features with Sylius platform app.

## Support

We work on amazing eCommerce projects on top of Sylius and Pimcore. Need some help or additional resources for a project?
Write us an email on mikolaj.krol@bitbag.pl or visit [our website](https://bitbag.shop/)! :rocket:

## Demo

We created a demo app with some useful use-cases of the plugin! Visit [demo.bitbag.shop](https://demo.bitbag.shop) to take a look at it. 
The admin can be accessed under [demo.bitbag.shop/admin](https://demo.bitbag.shop/admin) link and `sylius: sylius` credentials.

## Installation
```bash
$ composer require bitbag/wishlist-plugin
```
    
Add plugin dependencies to your AppKernel.php file:

```php
public function registerBundles()
{
    return array_merge(parent::registerBundles(), [
        ...
        
        new \BitBag\SyliusWishlistPlugin\BitBagSyliusWishlistPlugin(),
    ]);
}
```

Import required config in your `app/config/config.yml` file:

```yaml
# app/config/config.yml

imports:
    ...
    
    - { resource: "@BitBagSyliusWishlistPlugin/Resources/config/config.yml" }
```

Import routing **on top** of your `app/config/routing.yml` file:

```yaml
# app/config/routing.yml

bitbag_sylius_wishlist_plugin:
    resource: "@BitBagSyliusWishlistPlugin/Resources/config/routing.yml"
```

Update your database

```
$ bin/console doctrine:migrations:diff
$ bin/console doctrine:migrations:migrate
```

**Note:** If you are running it on production, add the `-e prod` flag to this command.

## Usage

### Rendering the wishlist

<div align="center">
    <img src="doc/index.jpg" />
</div>

You can  use `@BitBagSyliusWishlistPlugin/_addToWishlist.html.twig`, `@BitBagSyliusWishlistPlugin/_removeFromWishlist.html.twig` and `@BitBagSyliusWishlistPlugin/_removeFromWishlist.html.twig`
templates to enable adding/removing/displaying wishlist from the Twig UI.  

For an example on how to do that, take a look at [these source files](https://github.com/BitBagCommerce/SyliusWishlistPlugin/tree/master/tests/Application/app/Resources/SyliusShopBundle/views).

## Customization

### Available services you can [decorate](https://symfony.com/doc/current/service_container/service_decoration.html) and forms you can [extend](http://symfony.com/doc/current/form/create_form_type_extension.html)

Run the below command to see what Symfony services are shared with this plugin:
 
```bash
$ bin/console debug:container bitbag_sylius_wishlist_plugin
```

### Parameters you can override in your parameters.yml(.dist) file

```yml
wishlist_cookie_id                                                        bitbag_sylius_wishlist
```

## Testing

```bash
$ composer install
$ cd tests/Application
$ yarn install
$ yarn run gulp
$ bin/console assets:install web -e test
$ bin/console doctrine:schema:create -e test
$ wishlist 
$ bin/console server:run 127.0.0.1:8080 -d web -e test
$ open http://localhost:8080
$ bin/behat
$ bin/phpspec run
```

## Contribution

Learn more about our contribution workflow on http://docs.sylius.org/en/latest/contributing/.
