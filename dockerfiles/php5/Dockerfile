FROM php:5.6-apache
 
MAINTAINER Christian Traub
 
RUN apt-get update
RUN docker-php-ext-install mysql mysqli pdo pdo_mysql mbstring

# Copy Config
COPY config/php.ini /etc/php5/apache2/php.ini

VOLUME /var/www/html

# Enable apache mods.
RUN a2enmod rewrite

RUN service apache2 restart
 
# Manually set the apache environment variables in order to get apache to work immediately.
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

EXPOSE 80

#ENTRYPOINT ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]