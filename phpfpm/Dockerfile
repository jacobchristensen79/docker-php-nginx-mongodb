FROM php:5.6-fpm

RUN apt-get update \

    && curl -sSL https://deb.nodesource.com/setup_6.x | bash - \

    # Install packages
    && apt-get install -y --no-install-recommends libssl-dev nodejs \
    && apt-get clean \
    && apt-get install -y git \

    ## Docker
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install bcmath mbstring \
    && docker-php-ext-enable opcache \

    # Peal installs php mongo driver with pecl
    && pecl install mongo \
    && echo 'extension=mongo.so' > /usr/local/etc/php/conf.d/mongo.ini \

    # X-Debug
    && pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=1" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_connect_back=1" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.max_nesting_level=1000" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.profiler_enable_trigger=1" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.profiler_output_dir = \"/var/log\"" > /usr/local/etc/php/conf.d/xdebug.ini \

    # Install composer
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \

    # Set higher memory limit due to the need of SF2
    && touch /usr/local/etc/php/conf.d/phplimits.ini \
    && echo "max_execution_time=120" > /usr/local/etc/php/conf.d/phplimits.ini \
    && echo "upload_max_filesize=512M" > /usr/local/etc/php/conf.d/phplimits.ini \
    && echo "date.timezone=Europe/Zurich" > /usr/local/etc/php/conf.d/phplimits.ini \
    && echo "memory_limit=2048M" > /usr/local/etc/php/conf.d/phplimits.ini \


    # Reset ownership
    && chown -R www-data:www-data /var/www/

EXPOSE 9000

