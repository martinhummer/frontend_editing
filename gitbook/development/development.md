# Development

Instructions for how to develop the frontend editing.

## Dependencies
We rely on node.js for a lot of our tooling. So if you haven't got it installed(shame on you!!) go to http://nodejs.org/ and fetch it.

To install tooling dependencies, run:

    npm install

Composer must also be installed. Download it and install it from the composer website, then move it to your binary path.
If you are unsure of where it is try echo "$PATH", it will usually be /usr/local/bin or /usr/local.

    curl -sS https://getcomposer.org/installer | php
    sudo mv ./composer.phar /usr/bin/

Make it executable and link to it:

    sudo chmod +x /usr/bin/composer.phar
    sudo ln -s /usr/bin/composer.phar /usr/bin/composer

Then install the composer dependencies:

    composer install
    
> NOTE: On Ubuntu be sure to have php5 and php5-curl installed
>
> When asked for a token, goto to your github account and into settings->personal access tokens and click Generate new token, copy-paste the token into the input
    
## Workflow
For working with the extension, the following can be run to accomplish common tasks.

### Test

To run the PHP codesniffer run the following command:

    npm run php:codesniffer

To run the PHP Unit tests run the following command:

    npm run php:unittests

To simulate the full build process locally, then run this packaged command:

    npm run build:suite --silent

### Add node_modules to Public/Resources folder

Add the ckeditor node_module to Public/Resources folder:

    npm run add:resource:ckeditor

Add the toastr (notifications) node_module to Public/Resources folder:

    npm run add:resource:toastr

Add the immutable (https://facebook.github.io/immutable-js/) node_module to Public/Resources folder:

    npm run add:resource:immutable

Add the alertify.js (modals) node_module to Public/Resources folder:

    npm run add:resource:alertify

### Styling

The extension are using SASS for compiling into CSS. 

To build the stylesheets use the following command: 

    npm run build:css

While developing use the following watch command:

    npm run watch:css

### Publish

To build the extension before a publish to TER use the following command to copy all necessary
node_modules into Public/Resources folder (is a bundle of all **add:resource** commands) and compile the SASS:

    npm run build:extension