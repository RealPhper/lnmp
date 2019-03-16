FROM bitnami/php-fpm:7.1
RUN install_packages git autoconf build-essential

WORKDIR /app

#替换custom.ini
COPY ./conf/custom.ini /opt/bitnami/php/etc/conf.d/custom.ini
#添加xdebug
COPY ./extension/xdebug-2.7.0_php7.1.tgz /app/extension/xdebug-2.7.0_php7.1.tgz
# 安装xdebug扩展
RUN tar -xzf /app/extension/xdebug-2.7.0_php7.1.tgz -C /app/extension && \
    cd /app/extension/xdebug-2.7.0/ && \
    phpize && \
    ./configure --enable-xdebug && \
    make && make install && \
    cd .. && \
    rm -rf xdebug-2.7.0_php7.1.tgz


# 安装redis扩展
# RUN wget http://pecl.php.net/get/redis-3.1.3.tgz  && \
#     tar -xvf redis-3.1.3.tgz  && \
#     cd redis-3.1.3  && \
#     phpize && \
#     ./configure && \
#     make && make install

#安装php composer 如果无法安装可以下面的hash无法对应 到网站获取最新的hash值 https://getcomposer.org/download/
# RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
# RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
# RUN php composer-setup.php --install-dir=/bin --filename=composer
