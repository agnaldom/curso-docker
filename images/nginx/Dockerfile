FROM debian:latest

MAINTAINER Agnaldo Marinho "agnaldoneto@ufpa.br"

COPY sources.list /etc/apt/sources.list

RUN apt-get update; apt-get -y install nginx; apt-get clean

RUN ln -sf /dev/stdout  /var/log/nginx/access.log

RUN ln -sf /dev/stderr  /var/log/nginx/error.log

RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf

EXPOSE 8080

STOPSIGNAL SIGTERM

#CMD ["/usr/sbin/nginx"]
CMD ["nginx"]
