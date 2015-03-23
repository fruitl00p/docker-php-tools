# PHP tools for easier docker based development

This is a `simple` docker image for running various PHP tools from the CLI / IDE.

## Usage

Go to your regular directory root of your app and choose what to do

### PHPUnit

``` docker run -it --rm -w /app -v $(pwd):/app kingsquare/php-tools:latest /phpunit ```

### PHPCodesniffer

``` docker run -it --rm -w /app -v $(pwd):/app kingsquare/php-tools:latest /phpcs ```

### PHPDocumentor

``` docker run -it --rm -w /app -v $(pwd):/app kingsquare/php-tools:latest /phpdoc ```

### Composer

``` docker run -it --rm -w /app -v $(pwd):/app kingsquare/php-tools:latest /composer ```

## Additional notes

### Xdebug

XDebug is loaded so no need to worry :)

### scripts
One handy trick is to create a few run commands for even easier use

i.e. ~/bin/phpunit

``` 
#!/bin/bash
docker run \
	-it \
	--rm \
	-v $(pwd):/app \
	-w /app \
	kingsquare/php-tools:latest /phpunit $*
```
for the other tools, you could replace ```phpunit``` with ```composer```, ```phpdoc``` or ```phpcs```

### ownership

One of the downsides of this way of using PHP tools is newly added files aren't owned by you. Thats something that leaves
to be desired. You _could_ use the ```-u $(id -u)``` flag for the ```docker run``` command but that way the group of the
newly created files would still be ```root```

### version information

In order to allow easier switching of the various tools between PHP versions. We've tagged the PHP version as the image tag.
Thus using ```php-tools:latest``` will use the latest PHP stable, but ```php-tools:5.4``` will use 5.4 ;)

# Feedback

Please post an issue on the issuetracker!
