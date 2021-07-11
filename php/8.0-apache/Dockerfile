FROM php:8.0-apache

RUN apt-get update && apt-get -y install apt-utils zip unzip && apt-get -y upgrade

RUN a2enmod rewrite

# PHP install helper
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions && sync

# PHP setup
RUN install-php-extensions dba \
        exif \
        mysqli \
        pdo_mysql \
        sockets \
        pcntl \
        bz2 \
        zip \
        soap \
        xsl \
        pspell \
        ldap \
        gd \
        gmp \
        imap \
        pdo_pgsql \
        pgsql \
        apcu \
        @composer

RUN apt-get autoremove -y && apt-get clean all

COPY ./php.ini /usr/local/etc/php
