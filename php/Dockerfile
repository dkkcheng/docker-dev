FROM php:7.2-fpm
# 设置容器的时间
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 常用的php扩展列表，方便安装
# bcmath bz2 calendar ctype curl dba dom enchant exif fileinfo filter ftp gd 
# gettext gmp hash iconv imap interbase intl json ldap mbstring mysqli oci8 
# odbc opcache pcntl pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc 
# pdo_pgsql pdo_sqlite pgsql phar posix pspell readline recode reflection 
# session shmop simplexml snmp soap sockets sodium spl standard sysvmsg sysvsem 
# sysvshm tidy tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zend_test zip

RUN apt update \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install ctype \ 
    && apt install -y libfreetype6-dev \
    && apt install -y libjpeg62-turbo-dev \
    && apt install -y libpng-dev \ 
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && apt install -y zip \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_mysql

# 安装redis的扩展&安装xdebug的扩展
RUN pecl install redis && docker-php-ext-enable redis 
# 把容器内的php配置文件清空，在yml文件使用外边的php.ini方便配置
RUN echo "" >> /usr/local/etc/php/php.ini
# 解决docker容器内的文件权限不一致的问题
RUN usermod -u 1000 www-data
# 暴露端口，提供服务
EXPOSE 9000
