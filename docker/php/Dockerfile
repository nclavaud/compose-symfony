FROM php:7.1.1-fpm

COPY config/php.ini /usr/local/etc/php/

# see https://github.com/docker-library/php/issues/307
RUN curl -sS -o /tmp/icu.tar.gz -L http://download.icu-project.org/files/icu4c/57.1/icu4c-57_1-src.tgz && \
    tar -zxf /tmp/icu.tar.gz -C /tmp && \
    cd /tmp/icu/source && \
    ./configure --prefix=/usr/local && \
    make && \
    make install
RUN docker-php-ext-configure intl --with-icu-dir=/usr/local && \
    docker-php-ext-install intl

RUN docker-php-ext-enable opcache.so

RUN curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony
RUN chmod a+x /usr/local/bin/symfony

WORKDIR /var/www
