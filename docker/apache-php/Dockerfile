FROM php:7.0.8-apache
ENV DEBIAN_FRONTEND noninteractive
ENV PHP_MEMCACHED_VERSION php7

RUN apt-get update && apt-get install -y libmemcached-dev zlib1g-dev
RUN curl -L -o /tmp/memcached.tar.gz https://github.com/php-memcached-dev/php-memcached/archive/$PHP_MEMCACHED_VERSION.tar.gz \
  && tar xfz /tmp/memcached.tar.gz \
  && rm -r /tmp/memcached.tar.gz \
  && mkdir -p /usr/src/php/ext \
  && mv php-memcached-$PHP_MEMCACHED_VERSION /usr/src/php/ext/memcached \
  && echo memcached >> /usr/src/php-available-exts \
  && docker-php-ext-install memcached

RUN { \
  echo 'session.save_handler = memcached'; \
  echo 'session.save_path = memcached:11211'; \
  } >> /usr/local/etc/php/conf.d/docker-php-ext-memcached.ini

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
