FROM php:8.2-fpm-alpine
# php -m lists
# php-Core
# php-ctype
# php-curl
# php-date
# php-dom
# php-fileinfo
# php-filter
# php-hash
# php-iconv
# php-json
# php-libxml
# php-mbstring
# php-mysqlnd
# php-openssl
# php-pcre
# php-pdo
# php-pdo_sqlite
# php-Phar
# php-posix
# php-random
# php-readline
# php-Reflection
# php-session
# php-SimpleXML
# php-sodium
# php-SPL
# php-sqlite3
# php-standard
# php-tokenizer
# php-xml
# php-xmlreader
# php-xmlwriter
# php-zlib

# setting up needed arguments
ARG MYUSER
ARG MYGROUP
ARG MYUID
ARG MYGID

# install needed libs
RUN apk update && apk add \
  curl \
  libpng-dev \
  libxml2-dev \
  zip \
  shadow # adduser && addgroup has some limitation

# install additional php-extensions
# see https://hub.docker.com/_/php/
RUN docker-php-ext-install mysqli pdo_mysql

# install composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# setting up user
RUN useradd -G $MYGROUP,root -u $MYUID -d /home/$MYUSER $MYUSER
RUN mkdir -p /home/$MYUSER/.composer && chown -R $MYUSER:$MYUSER /home/$MYUSER

USER $MYUSER

WORKDIR /app


EXPOSE 9000

