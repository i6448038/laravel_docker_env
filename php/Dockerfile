FROM php:5.6-fpm


# Install PHP extensions and PECL modules.
RUN buildDeps=" \
        libbz2-dev \
        libmemcached-dev \
        libmysqlclient-dev \
        libsasl2-dev \
    " \
    runtimeDeps=" \
        libfreetype6-dev \
        libicu-dev \
        libjpeg-dev \
        libmcrypt-dev \
        libmemcachedutil2 \
        libpng12-dev \
        libpq-dev \
    " \
    && apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y $buildDeps $runtimeDeps \
    && docker-php-ext-install bz2 calendar iconv intl mbstring mcrypt mysql mysqli pdo_mysql pdo_pgsql pgsql zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && pecl install memcached redis \
    && docker-php-ext-enable memcached.so redis.so \
    && apt-get purge -y --auto-remove $buildDeps \
    && rm -r /var/lib/apt/lists/*

#安装composer
WORKDIR /usr/local/php/etc/
ADD  www.conf /usr/local/etc/php-fpm.d/www.conf
ADD  php.ini /usr/local/etc/php/php.ini
RUN php -r "readfile('https://getcomposer.org/installer');" | php
RUN mv composer.phar /usr/local/bin/composer
ENV PATH ~/.composer/vendor/bin:$PATH

#从私有仓库git clone代码
RUN apt-get update  
RUN apt-get install -y git 
#WORKDIR /Code
#RUN git clone http://liugang:liugang521@gitlab.chuanty.com/backend/taurus.git


#更新compsoer
WORKDIR /Code/taurus
#RUN chown www-data /Code/taurus/storage
#RUN chmod -R 777 /Code/taurus/storage
RUN usermod -u 1000 www-data
#ADD .env /Code/taurus/.env
RUN composer --global config process-timeout 2000 \
    #&& composer config repo.packagist composer http://packagist.phpcomposer.com \
    && composer config -g repo.packagist composer https://packagist.phpcomposer.com \
    && composer --global config secure-http false 
VOLUME ["/Code"]




