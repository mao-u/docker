FROM mysql:5.7

COPY ./data/my.conf /etc/mysql/conf.d/my.cnf
COPY ./data/init.d/setup.sql /docker-entrypoint-initdb.d/setup.sql