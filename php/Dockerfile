FROM php:7.0.4-fpm


RUN apt-get update 

#安装PHP ext-mbstring modules
RUN docker-php-ext-install mbstring

# Install opcache
RUN docker-php-ext-install opcache

# Install APCu
RUN pecl install apcu
RUN echo "extension=apcu.so" > /usr/local/etc/php/conf.d/apcu.ini

# Install bcmath
RUN docker-php-ext-install bcmath

# Install dba
RUN docker-php-ext-install dba

# Install GD
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install gd

RUN apt-get install -y libmcrypt-dev
RUN docker-php-ext-install mcrypt

# Install PDO
RUN docker-php-ext-install pdo_mysql
RUN apt-get install -y libpq-dev
RUN docker-php-ext-install pdo_pgsql

# Install XSL
RUN apt-get install -y libxslt-dev
RUN docker-php-ext-install xsl

# Install xmlrpc
RUN docker-php-ext-install xmlrpc


# Install ftp
RUN docker-php-ext-install ftp

# Install intl
RUN apt-get install -y libicu-dev
RUN pecl install intl
RUN docker-php-ext-install intl

#安装composer
WORKDIR /usr/local/php/etc/
ADD  www.conf /usr/local/etc/php-fpm.d/www.conf
ADD  php.ini /usr/local/etc/php/php.ini
RUN php -r "readfile('https://getcomposer.org/installer');" | php
RUN mv composer.phar /usr/local/bin/composer
ENV PATH ~/.composer/vendor/bin:$PATH

#从私有仓库git clone代码 
RUN apt-get install -y git 

#更新compsoer
WORKDIR /Code/project
RUN usermod -u 1000 www-data
RUN composer --global config process-timeout 2000 \
    && composer config -g repo.packagist composer https://packagist.phpcomposer.com \
    && composer --global config secure-http false 
VOLUME ["/Code/project"]



