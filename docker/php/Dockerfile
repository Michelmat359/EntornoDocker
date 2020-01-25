FROM phpstorm/php-72-apache-xdebug-27:latest

RUN apt-get -y update \
    && apt-get install -y libicu-dev\
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install pdo_mysql && docker-php-ext-install intl

RUN echo "memory_limit=512M" >> "/usr/local/etc/php/conf.d/extra.ini" s&& echo "max_execution_time=300" >> "/usr/local/etc/php/conf.d/extra.ini"

RUN a2enmod rewrite

RUN apt-get install -y zlib1g-dev libpng-dev
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install zip
RUN docker-php-ext-install gd

RUN apt-get install -y libjpeg-dev && docker-php-ext-configure gd --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

