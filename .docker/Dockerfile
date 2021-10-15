FROM prestashop/prestashop-git:7.3


# XDebug extension
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# Enable XDebug
COPY /docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

# To run files with the same group as your primary user
RUN groupmod -g 1000 www-data \
  && usermod -u 1000 -g 1000 www-data -s /bin/bash

COPY /wait-for-it.sh /tmp/
COPY /docker_run_git.sh /tmp/

CMD ["/tmp/docker_run_git.sh"]
