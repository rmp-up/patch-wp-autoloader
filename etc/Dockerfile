FROM php:7.3-apache

RUN apt update

# PHP
RUN pecl install xdebug && echo "\
zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20180731/xdebug.so \n\
xdebug.remote_host=10.221.13.1\n\
xdebug.idekey=PHPSTORM\n\
xdebug.remote_enable=1\n\
xdebug.remote_autostart=1\n\
xdebug.profiler_enable_trigger=1\n\
" > /usr/local/etc/php/conf.d/custom.ini

# WP-CLI
RUN apt install -y mysql-client less

# WordPress
RUN a2enmod rewrite

RUN apt-get install
RUN apt-get install -y \
    libwebp-dev \
    libjpeg62-turbo-dev \
    libpng-dev libxpm-dev \
    libfreetype6-dev

RUN docker-php-ext-configure gd \
    --with-gd \
    --with-webp-dir \
    --with-jpeg-dir \
    --with-png-dir \
    --with-zlib-dir \
    --with-xpm-dir \
    --with-freetype-dir

RUN docker-php-ext-install gd

# Using NodeJs 11 because the Sass-Package is not compatible with Node12+
RUN curl -sL https://deb.nodesource.com/setup_11.x | bash - \
    && apt-get install -y nodejs
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

# Composer
RUN apt install -y zip libzip-dev && docker-php-ext-install zip && docker-php-ext-enable zip
RUN curl -o composer-setup.php https://getcomposer.org/installer \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === 'a5c698ffe4b8e849a443b120cd5ba38043260d5c4023dbf93e1558871f1f07f58274fc6f4c93bcfd858c6bd0775cd8d1') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

# NPM
RUN apt install -y git

WORKDIR /var/www
