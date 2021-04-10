FROM wordpress:latest

# install XDebug
RUN pecl install -f xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    # Documentation for xdebug-3 https://xdebug.org/docs/upgrade_guide
    && echo "xdebug.client_host=localhost" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.client_port=9003" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.mode=debug,develop" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.start_with_request=yes" >> /usr/local/etc/php/conf.d/xdebug.ini;
    
# install Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - \
    && apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*;  

# install WP-CLI
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    # makes wp-cli.phar executable
    && chmod +x wp-cli.phar \
    && mv wp-cli.phar /usr/local/bin/wp;

# Wp coding standards https://github.com/WordPress/WordPress-Coding-Standards#standalone
# install WPCS 2.3.0
RUN curl -OL https://github.com/WordPress/WordPress-Coding-Standards/archive/refs/tags/2.3.0.tar.gz \
    && tar -xf 2.3.0.tar.gz --directory /;

# install PHP_CodeSniffer https://github.com/squizlabs/PHP_CodeSniffer#installation
# phpcs
RUN curl -OL https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar \
    && chmod +x phpcs.phar \
    && mv phpcs.phar /usr/local/bin/phpcs;

# phpcbf
RUN curl -OL https://squizlabs.github.io/PHP_CodeSniffer/phpcbf.phar \
    && chmod +x phpcbf.phar \
    && mv phpcbf.phar /usr/local/bin/phpcbf;

# set WPCS path
RUN phpcs --config-set installed_paths /WordPress-Coding-Standards-2.3.0;