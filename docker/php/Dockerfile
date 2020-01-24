FROM phpstorm/php-72-apache-xdebug-27:latest


RUN apt-get -y update \
    && apt-get install -y libicu-dev\
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install pdo_mysql && docker-php-ext-install intl

RUN echo "memory_limit=512M" >> "/usr/local/etc/php/conf.d/extra.ini" && echo "max_execution_time=300" >> "/usr/local/etc/php/conf.d/extra.ini"

RUN a2enmod rewrite

RUN apt-get install -y zlib1g-dev libpng-dev
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install zip
RUN docker-php-ext-install gd

RUN apt-get install -y libjpeg-dev && docker-php-ext-configure gd --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd
# Install OpenJDK-8
#RUN apt-get update && \
#    apt-get install -y openjdk-8-jdk && \
#    apt-get install -y ant && \
#    apt-get clean;


# Hack for debian-slim to make the jdk install work below.
#RUN mkdir -p /usr/share/man/man1
#
## repo needed for jdk install below.
#RUN echo 'deb http://deb.debian.org/debian stretch-backports main' > /etc/apt/sources.list.d/backports.list
#
## Install OpenJDK-8
#RUN apt-get update && apt-get install -y openjdk-8-jdk
