FROM aperezg/php-alpine:latest

RUN apk --update add \
        php7-xdebug \
    && rm -rf /var/cache/apk/*
COPY config/xdebug.ini /etc/php7/conf.d/xdebug.ini