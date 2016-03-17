FROM alpine

ENV TERM ansi

EXPOSE 3306

RUN apk update
RUN apk add mariadb mariadb-client

USER mysql

ENTRYPOINT ["mysqld"]