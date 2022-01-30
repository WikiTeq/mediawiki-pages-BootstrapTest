# mediawiki-pages-BootstrapTest
A collection of pages created to visualize bootstrap elements in MediaWiki, whether with the active bootswatch or without it.

# Requirements
* Extension:Bootstrap
* Extension:Widgets
* Extension:PageExchange or Extension:PagePort

# Pre-configuration

## Pure Bootstrap (bundled)
Bootstrap comes bundled with the Chameleon skin. Once installed and enabled Chameleon, the package will display the default Bootstrap elements.

## Bootswatch
To apply a Bootswatch for Bootstrap 4, put the files (`_variables.scss` and `_bootswatch.scss`) in:
```php
extensions/CONTRACTHOLDER/skins/SKINNAME/bootswatch
```
where:
* `CONTRACTHOLDER` = WikiTeq or WikiWorks depending on the project
* `SKINNAME` = chameleon or other Bootstrap enabled skin

Add the following to the `LocalSettings.php` for PHP 7.3 Chameleon < 3.4:
```php
$egChameleonExternalStyleModules = [
     "$IP/extensions/WikiTeq/skins/chameleon/bootswatch/_variables.scss" => 'afterFunctions', 
     "$IP/extensions/WikiTeq/skins/chameleon/bootswatch/_bootswatch.scss" => 'afterMain'
];
```

Add the following to the `LocalSettings.php` for PHP 7.4 Chameleon ^3.4:
```php
$egChameleonThemeFile = __DIR__ . '/skins/chameleon/bootswatch/_variables.scss';
$egChameleonExternalStyleModules = [
        __DIR__ . '/skins/chameleon/bootswatch/_bootswatch.scss' => 'afterMain',
];
```

# Setup

## via PagePort
* Download the repository
* Run 
```php
php extensions/PagePort/maintenance/importPages.php --source ~/mediawiki-pages-BootstrapTest
```

## via PageExchange
* Add the following line to your LocalSettings.php:
```php
$wgPageExchangePackageFiles[] = 'https://raw.githubusercontent.com/WikiTeq/mediawiki-pages-BootstrapTest/master/page-exchange.json';
```
* Navigate to Special:Packages and install the package
