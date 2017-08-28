FROM debian:latest

MAINTAINER  Agnaldo Marinho "agnaldoneto@ufpa.br"

COPY sources.list /etc/apt/sources.list

RUN groupadd -r mysql && useradd -r -g mysql mysql

ENV GOSU_VERSION 1.7

RUN set -x \
    && apt-get update && apt-get install -y --no-install-recommends dirmngr gpg ca-certificates wget && rm -rf /var/lib/apt/lists/* \
    && wget -O /usr/local/bin/gosu "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$(dpkg --print-architecture)" \
    && wget -O /usr/local/bin/gosu.asc "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$(dpkg --print-architecture).asc" \
    && export GNUPGHOME="$(mktemp -d)" \
    && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 \
    && gpg --batch --verify /usr/local/bin/gosu.asc /usr/local/bin/gosu \
    && rm -r "$GNUPGHOME" /usr/local/bin/gosu.asc \
    && chmod +x /usr/local/bin/gosu \
    && gosu nobody true \
    && apt-get purge -y --auto-remove ca-certificates wget

RUN mkdir /docker-entrypoint-initdb.d

RUN apt-get update; apt-get -y install  mariadb-server; rm -rf /var/lib/apt/lists/* ; sed -ri 's/^user\s/#&/' /etc/mysql/my.cnf /etc/mysql/conf.d/*; rm -rf /var/lib/mysql && mkdir -p /var/lib/mysql /var/run/mysqld; chown -R mysql:mysql /var/lib/mysql /var/run/mysqld ; chmod 777 /var/run/mysqld

RUN sed -Ei 's/^(bind-address|log)/#&/' /etc/mysql/my.cnf \
        && echo '[mysqld]\nskip-host-cache\nskip-name-resolve' > /etc/mysql/conf.d/docker.cnf 

VOLUME /var/lib/mysql

COPY docker-entrypoint.sh /usr/local/bin/

RUN chmod +x /usr/local/bin/docker-entrypoint.sh

RUN ln -s /usr/local/bin/docker-entrypoint.sh / # backwards compat

ENTRYPOINT ["docker-entrypoint.sh"]

EXPOSE 3306

CMD ["mysqld"]
