FROM wordpress:4.9-php7.0-apache

RUN apt-get update

RUN apt-get install -y locales

RUN sed -i 's/^# *\(pt_BR.UTF-8 \)/\1/' /etc/locale.gen

RUN locale-gen

RUN rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
	&& echo "xdebug.idekey = PHPSTORM" >> /usr/local/etc/php/conf.d/xdebug.ini \
	&& echo "xdebug.default_enable = 0" >> /usr/local/etc/php/conf.d/xdebug.ini \
	&& echo "xdebug.remote_enable = 1" >> /usr/local/etc/php/conf.d/xdebug.ini \
	&& echo "xdebug.remote_autostart = 0" >> /usr/local/etc/php/conf.d/xdebug.ini \
	&& echo "xdebug.remote_connect_back = 0" >> /usr/local/etc/php/conf.d/xdebug.ini \
	&& echo "xdebug.profiler_enable = 0" >> /usr/local/etc/php/conf.d/xdebug.ini