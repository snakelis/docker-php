FROM php:7.1-fpm

# Install env

ADD sources.list /etc/apt/sources.list
RUN echo "nameserver 223.5.5.5" > /etc/resolv.conf
RUN apt-get update && apt-get install -y \
	git \
    libmcrypt-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libz-dev \
    libmemcached-dev \
    libxml2-dev \
    #添加ssh连接配置
    initscripts \
    net-tools \
    openssh-server \
    vim \
    && rm -r /var/lib/apt/lists/*

#设置root账号允许ssh连接配置
#cp -r /etc/ssh/sshd_config.bak /etc/ssh/sshd_config
# Install PHP extensions
# COPY xdebug.tgz /home/xdebug.tgz

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
        && docker-php-ext-install gd \
        && docker-php-ext-install zip \
        && docker-php-ext-install mbstring \
        && docker-php-ext-install tokenizer \
        && docker-php-ext-install bcmath \
        && docker-php-ext-install mcrypt \
        && docker-php-ext-install mysqli \
        && docker-php-ext-install pdo_mysql \
        && docker-php-ext-install soap 

#安装redis扩展
RUN pecl install -o -f redis \
&&  rm -rf /tmp/pear \
&&  docker-php-ext-enable redis

#安装swoole扩展
RUN pecl install -o -f swoole \
&&  rm -rf /tmp/pear \
&&  docker-php-ext-enable swoole

# PHP config
ADD php.ini /usr/local/etc/php/php.ini
ADD php-fpm.conf /usr/local/etc/php-fpm.conf

#Composer
ADD composer.phar /usr/local/bin/composer
RUN chmod 755 /usr/local/bin/composer

WORKDIR /web

# Write Permission
RUN usermod -u 1000 www-data

#允许ssh连接配置
ADD sshd_config.bak /etc/ssh/sshd_config
RUN echo "root:root" | chpasswd
RUN /etc/init.d/ssh start

# php-fpm:8000 xdebug:9000
EXPOSE 9000
VOLUME ["/web"]
