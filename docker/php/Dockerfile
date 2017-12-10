FROM php:7.2.0-fpm

COPY config/php.ini /usr/local/etc/php/

# see https://github.com/docker-library/php/issues/307
RUN curl -sS -o /tmp/icu.tar.gz -L http://download.icu-project.org/files/icu4c/59.1/icu4c-59_1-src.tgz && \
    tar -zxf /tmp/icu.tar.gz -C /tmp && \
    cd /tmp/icu/source && \
    ./configure --prefix=/usr/local && \
    make && \
    make install
RUN docker-php-ext-configure intl --with-icu-dir=/usr/local && \
    docker-php-ext-install intl

RUN docker-php-ext-enable opcache.so

RUN apt-get update && \
    apt-get install -y libpq-dev && \
    docker-php-ext-install pdo_pgsql

RUN curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony
RUN chmod a+x /usr/local/bin/symfony

RUN mkdir /var/www/var
RUN mkdir /var/www/var/cache && chown www-data:www-data /var/www/var/cache
RUN mkdir /var/www/var/logs && chown www-data:www-data /var/www/var/logs
RUN mkdir /var/www/var/sessions && chown www-data:www-data /var/www/var/sessions

USER www-data

WORKDIR /var/www
