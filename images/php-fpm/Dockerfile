FROM debian:latest

MAINTAINER  Agnaldo Marinho "agnaldoneto@ufpa.br"

COPY sources.list /etc/apt/sources.list

RUN apt-get update; apt-get -y install php php-fpm php-cli php-mcrypt php-intl php-mysql php-curl php-gd php-soap php-xml php-zip php-readline php-opcache php-json php-gd 

RUN rm -rf /var/lib/apt/lists/*

RUN sed -i -e "s/;daemonize\s*=\s*yes/daemonize = no/g" /etc/php/7.0/fpm/php-fpm.conf 
RUN sed -i 's/;extension=mysql.so/extension=mysql.so/g' /etc/php/7.0/fpm/php.ini
RUN sed -i 's/;extension=pdo_mysql.so/extension=pdo_mysql.so/g' /etc/php/7.0/fpm/php.ini

RUN usermod -u 1000 www-data

EXPOSE 9000

CMD ["php-fpm7.0", "-F"]



