FROM php:7.0-fpm
MAINTAINER gabel <gabeldeluxe@gmail.com>

ENV PHALCON_VERSION=3.0.3

ENV TIMEZONE            UTC
ENV PHP_MEMORY_LIMIT    512M
ENV MAX_UPLOAD          50M
ENV PHP_MAX_FILE_UPLOAD 200
ENV PHP_MAX_POST        100M

# Compile Phalcon
RUN set -xe && \
        curl -LO https://github.com/phalcon/cphalcon/archive/v${PHALCON_VERSION}.tar.gz && \
        tar xzf v${PHALCON_VERSION}.tar.gz && cd cphalcon-${PHALCON_VERSION}/build && ./install && \
        echo "extension=phalcon.so" > /usr/local/etc/php/conf.d/phalcon.ini && \
        cd ../.. && rm -rf v${PHALCON_VERSION}.tar.gz cphalcon-${PHALCON_VERSION} && \
        # Insall Phalcon Devtools, see https://github.com/phalcon/phalcon-devtools/
        curl -LO https://github.com/phalcon/phalcon-devtools/archive/v${PHALCON_VERSION}.tar.gz && \
        tar xzf v${PHALCON_VERSION}.tar.gz && \
        mv phalcon-devtools-${PHALCON_VERSION} /usr/local/phalcon-devtools && \
        ln -s /usr/local/phalcon-devtools/phalcon.php /usr/local/bin/phalcon

# Remove if not needed
COPY config/custom.ini /usr/local/etc/php/conf.d/

# use proxy if needed
# RUN pear config-set http_proxy $HTTP_PROXY

RUN pecl install apcu && \
    docker-php-ext-enable apcu

RUN apt-get update && \
    apt-get install -y libssl-dev && \
    pecl install mongodb-1.2.2 && \
    docker-php-ext-enable mongodb

# Set locales
#RUN apt-get install -y libicu-dev locales && \
#        echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen && \
#        echo "de_DE.UTF-8 UTF-8" >> /etc/locale.gen && \
#        echo "en_GB.UTF-8 UTF-8" >> /etc/locale.gen && \
#        docker-php-ext-configure intl && \
#        docker-php-ext-install intl

# RUN locale-gen

RUN apt-get purge -y --auto-remove libssl-dev libicu-dev && \
    rm -rf /var/lib/apt/lists/*

