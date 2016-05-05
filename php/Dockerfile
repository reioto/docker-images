FROM php:7.0-apache
RUN apt-get update 

RUN apt-get install -y libbz2-dev
RUN docker-php-ext-install bz2 

RUN apt-get install -y libcurl4-openssl-dev
RUN docker-php-ext-install curl

RUN apt-get install -y libfreetype6-dev
RUN apt-get install -y libgd-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr
RUN docker-php-ext-install gd exif

RUN apt-get install -y libxml2-dev
RUN docker-php-ext-install dom simplexml xml xmlwriter

RUN apt-get install -y libxslt1-dev
RUN docker-php-ext-install xsl

RUN apt-get install -y libmcrypt-dev
RUN docker-php-ext-install mcrypt

RUN apt-get install -y libgettextpo-dev
RUN docker-php-ext-install gettext

RUN apt-get install -y libgmp-dev
RUN ln -s /usr/include/x86_64-linux-gnu/gmp.h /usr/local/include/
RUN docker-php-ext-install gmp

RUN apt-get install -y libc-client-dev libkrb5-dev
RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl
RUN docker-php-ext-install imap 

RUN docker-php-ext-install bcmath \
calendar \
ctype \
dba \
fileinfo \
ftp \
hash \
iconv \ 
json \
mbstring \
mysqli \
opcache \
phar \
pdo \
pdo_mysql

RUN apt-get install -y libpq-dev
RUN docker-php-ext-install pdo_pgsql pgsql

RUN apt-get install -y libsqlite3-dev
RUN docker-php-ext-install pdo_sqlite

RUN apt-get install -y libedit-dev
RUN docker-php-ext-install posix readline 

RUN docker-php-ext-install \ 
session \
soap \
sockets \
wddx \
zip
#spl \
#reflection \
#standard \
#filter

RUN a2enmod rewrite

RUN apt-get autoremove -y && apt-get clean all

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/bin --filename=composer

CMD apache2 -DFOREGROUND
