FROM ubuntu:bionic

COPY docker-entrypoint.sh /usr/local/bin
RUN ln -s /usr/local/bin/docker-entrypoint.sh /entrypoint.sh
RUN mkdir /docker-entrypoint-initdb.d
RUN mkdir /var/run/mysqld

RUN apt-get update && TZ="Etc/UTC" DEBIAN_FRONTEND="noninteractive" apt-get install -y tzdata gosu mysql-server && rm -rf /var/lib/apt/lists/*

RUN chown -R mysql:mysql /var/lib/mysql /var/run/mysqld
RUN rm -rf /etc/mysql
COPY mysql /etc/mysql

ENV PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
ENV GOSU_VERSION="1.10-1ubuntu0.18.04.1"
ENV MYSQL_MAJOR="5.7"
ENV MYSQL_VERSION="5.7.35-0ubuntu0.18.04.2"

EXPOSE 3306
EXPOSE 33060

RUN rm -rf /var/lib/mysql/*
RUN rm -rf /var/lib/mysql-files/*
run rm -rf /var/lib/mysql-keyring/*

VOLUME /var/lib/mysql

CMD ["mysqld"]
ENTRYPOINT ["docker-entrypoint.sh"]
