# Docker image for PHP-fpm

## Tags

* latest, 7.0 [Dockerfile](https://github.com/aperezg/docker-alpine-php/blob/master/7/Dockerfile)
* 7-dev [Dockerfile](https://github.com/aperezg/docker-alpine-php/blob/master/dev/Dockerfile)

Image for php-fpm. It based on Alpine linux and so it's very small (~75MB).
Include the most common extensions and you can extend whatever you need.

## To run

```sh
docker run --rm -p 9000:9000 -v /your/app-directory:/app aperezg/php-alpine:latest
```

## Run with docker compose
```yml
version: '2'
services:
    php:
        image: aperezg/php-alpine:latest
        ports:
            - 9000:9000
        volumes:
            - /your/app-directory:/app
```

## Custom php settings
You can create your basic configuration for php and fpm. The current configurations you can find in the config
folder of each version.

For apply your configuration files you only need extend of my image.

```dockerfile
FROM aperezg/php-alpine:latest

COPY php.ini /etc/php7/conf.d/50-setting.ini
COPY php-fpm.conf /etc/php7/php-fpm.conf
```

And build your own image

```sh
docker build -t my-php-alpine .
docker run --rm -p 9000:9000 -v /your/app-directory:/app my-php-alpine:latest
```

## Add extensions
You maybe need a extension of php that not include in this image. 

As same that with settings, you'll need to extend from my image.
```dockerfile
FROM aperezg/php-alpine:latest

RUN apk --update add \
        php7-apcu \ 
    && rm -rf /var/cache/apk/*
```

### Extensions include in this image

* php7-fpm
* php7-mcrypt
* php7-mbstring
* php7-pdo
* php7-pdo_mysql
* php7-pdo_pgsql
* php7-pdo_sqlite
* php7-curl
* php7-openssl
* php7-gettext
* php7-bcmath
* php7-zip
* php7-mysqli
* php7-json
* php7-soap
* php7-zlib
* php7-xml
* php7-dom
* php7-ctype
* php7-gd
* php7-intl
* php7-posix
* php7-session
* php7-iconv
* php7-phar

## Fork this repo

If you think that you can improve this image, fork this repo, and send me a pull request. I'll be happy to add your new features.

This repository is under [GNU v3.0 License](https://github.com/aperezg/docker-alpine-php/blob/master/LICENSE) 



