FROM php:8.2-fpm

WORKDIR /var/www

RUN apt-get update && apt-get upgrade -y \
    unzip \
    libaio1 \
    wget \
    alien

RUN wget -O /tmp/oracle-client.rpm https://download.oracle.com/otn_software/linux/instantclient/2115000/oracle-instantclient-basic-21.15.0.0.0-1.el8.x86_64.rpm \
    && alien -i /tmp/oracle-client.rpm

RUN wget -O /tmp/oracle-client-sdk.rpm https://download.oracle.com/otn_software/linux/instantclient/2115000/oracle-instantclient-devel-21.15.0.0.0-1.el8.x86_64.rpm \
    && alien -i /tmp/oracle-client-sdk.rpm

# Somente para testes dentro do container
RUN wget -O /tmp/oracle-sqlplus.rpm https://download.oracle.com/otn_software/linux/instantclient/2115000/oracle-instantclient-sqlplus-21.15.0.0.0-1.el8.x86_64.rpm \
    && alien -i /tmp/oracle-sqlplus.rpm

RUN ldconfig

RUN apt-get update && apt-get upgrade -y \
    build-essential \
    mariadb-client \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl \
    libxml2-dev \
    libicu-dev \
    libonig-dev \
    libzip-dev \
    git \
    libssl-dev

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Tentei juntar todas extensões do php/Dockerfile do projeto FIERGS, exceto pdo_mysql
RUN docker-php-ext-install \
    mbstring \
    zip \
    exif \
    pcntl \
    gd \
    intl \
    soap \
    sockets \
    oci8

# RUN docker-php-ext-configure gd \
#     intl

RUN docker-php-ext-enable \
    soap \
    oci8






