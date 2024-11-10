FROM debian:buster

RUN apt update && apt upgrade -y && apt install -y wget php7.3 php-fpm php-mysql mariadb-client default-mysql-client

RUN wget https://fr.wordpress.org/wordpress-6.6.2-fr_FR.tar.gz -P /var/www/html

RUN cd /var/www/html && tar -xzf wordpress-6.6.2-fr_FR.tar.gz && rm wordpress-6.6.2-fr_FR.tar.gz

RUN wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
	&& chmod +x wp-cli.phar \
	&& mv wp-cli.phar /usr/local/bin/wp

# RUN	chown -R root:root /var/www/wordpress

COPY ./tools/www.conf /etc/php/7.3/fpm/pool.d/www.conf
COPY ./tools/wpscript.sh ./
RUN chmod +x ./wpscript.sh
RUN chown -R www-data:www-data /var/www/*
RUN chmod -R 755 /var/www/*

EXPOSE 9000


# RUN wp config create --dbname=NOM_BD --dbuser=UTILISATEUR_BD --dbpass=MDP_BD --dbhost=HOTE_BD



# ENTRYPOINT ["bash", "./wpscript.sh"]

# RUN ls -ld /var/www/html/wordpress && ls -l /var/www/html/wordpress