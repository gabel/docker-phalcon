FROM php:7.0-alpine
MAINTAINER gabel <gabeldeluxe@gmail.com>

ENV PHALCON_VERSION=3.0.3

ENV TIMEZONE            UTC
ENV PHP_MEMORY_LIMIT    512M
ENV MAX_UPLOAD          50M
ENV PHP_MAX_FILE_UPLOAD 200
ENV PHP_MAX_POST        100M

# Compile Phalcon
RUN set -xe && \
        # Add virtual packages. It will remove when done.
        apk add --no-cache --virtual .build-deps autoconf g++ make && \
        curl -LO https://github.com/phalcon/cphalcon/archive/v${PHALCON_VERSION}.tar.gz && \
        tar xzf v${PHALCON_VERSION}.tar.gz && cd cphalcon-${PHALCON_VERSION}/build && sh install && \
        echo "extension=phalcon.so" > /usr/local/etc/php/conf.d/phalcon.ini && \
        cd ../.. && rm -rf v${PHALCON_VERSION}.tar.gz cphalcon-${PHALCON_VERSION} && \
        apk del .build-deps && \
        # Insall Phalcon Devtools, see https://github.com/phalcon/phalcon-devtools/
        curl -LO https://github.com/phalcon/phalcon-devtools/archive/v${PHALCON_VERSION}.tar.gz && \
        tar xzf v${PHALCON_VERSION}.tar.gz && \
        mv phalcon-devtools-${PHALCON_VERSION} /usr/local/phalcon-devtools && \
        ln -s /usr/local/phalcon-devtools/phalcon.php /usr/local/bin/phalcon

RUN apk add --no-cache \
        php7-apcu \
        php7-intl \
        php7-mongodb
