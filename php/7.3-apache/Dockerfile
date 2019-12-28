FROM php:7.3-apache

RUN apt-get update && apt-get -y install apt-utils zip unzip && apt-get -y upgrade

RUN a2enmod rewrite

# PHP setup
RUN docker-php-ext-install dba \
        exif \
        fileinfo \
        mbstring \
        mysqli \
        pdo \
        pdo_mysql \
        sockets \
        pcntl

RUN apt-get install -y libssl-dev && docker-php-ext-install ftp
RUN apt-get install -y libbz2-dev && docker-php-ext-install bz2
RUN apt-get install -y libzip-dev && docker-php-ext-install zip
RUN apt-get install -y libcurl4-openssl-dev && docker-php-ext-install curl
RUN apt-get install -y libxml2-dev && docker-php-ext-install dom simplexml xml xmlwriter soap
RUN apt-get install -y libxslt1-dev && docker-php-ext-install xsl
RUN apt-get install -y libedit-dev && docker-php-ext-install posix readline
RUN apt-get install -y libpspell-dev && docker-php-ext-install pspell

RUN apt-get install -y libldap2-dev && \
        docker-php-ext-configure ldap --with-libdir=/lib/x86_64-linux-gnu && \
        docker-php-ext-install ldap

RUN apt-get install -y libfreetype6-dev libgd-dev && docker-php-ext-install gd
RUN apt-get install -y libgmp-dev && \
        ln -s /usr/include/x86_64-linux-gnu/gmp.h /usr/local/include/ && \
        docker-php-ext-install gmp

RUN apt-get install -y libc-client-dev libkrb5-dev && \
        docker-php-ext-configure imap --with-kerberos --with-imap-ssl && \
        docker-php-ext-install imap

RUN apt-get install -y libsqlite3-dev sqlite3 && docker-php-ext-install pdo_sqlite
RUN apt-get install -y libpq-dev && docker-php-ext-install pdo_pgsql pgsql

RUN pecl channel-update pecl.php.net && pecl install apcu

RUN apt-get autoremove -y && apt-get clean all

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/bin --filename=composer

COPY ./php.ini /usr/local/etc/php
