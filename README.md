# mediawiki-pages-BootstrapTest
A collection of pages created to visualize bootstrap elements in MediaWiki, whether with the active bootswatch or without it.

# Requirements
* Extension:Bootstrap
* Extension:Widgets
* Extension:PageExchange or Extension:PagePort

# Pre-configuration

## Pure Bootstrap
To simply enable Bootstrap styles on all pages add the following code to your `LocalSettings.php` file: 
```php
$wgHooks['SetupAfterCache'][] = function(){
	\Bootstrap\BootstrapManager::getInstance()->addAllBootstrapModules();
	return true;
};
$wgHooks['ParserAfterParse'][]=function( Parser &$parser, &$text, StripState &$stripState ){
	$parser->getOutput()->addModuleStyles( 'ext.bootstrap.styles' );
	$parser->getOutput()->addModules( 'ext.bootstrap.scripts' );
	return true;
};
```
## Pure Bootstrap (bundled)
Bootstrap comes bundled with the Chameleon skin, just install and enable Chameleon.

## Bootswatch
Pure Bootstrap methods will let the package will display the default Bootstrap elements. To apply a **Bootswatch** for Bootstrap 4, put the files (`_variables.scss` and `_bootswatch.scss`) in:
```php
path/relative/to/wikiroot/bootswatch
```

Add the following to the `LocalSettings.php` for PHP 7.3 Chameleon < 3.4:
```php
$egChameleonExternalStyleModules = [
     $IP . '/path/relative/to/wikiroot/bootswatch/_variables.scss' => 'afterFunctions', 
     $IP . '/path/relative/to/wikiroot/bootswatch/_bootswatch.scss' => 'afterMain'
];
```

Add the following to the `LocalSettings.php` for PHP 7.4 Chameleon ^3.4:
```php
$egChameleonThemeFile = $IP . '/path/relative/to/wikiroot/bootswatch/_variables.scss';
$egChameleonExternalStyleModules = [
        $IP . '/path/relative/to/wikiroot/bootswatch/_bootswatch.scss' => 'afterMain',
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

# Usage
Navigate to `Project:Bootswatch` and see the sample elements with the Bootstrap/Bootswatch styling.
