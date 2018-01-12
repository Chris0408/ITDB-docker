FROM ubuntu:14.04
RUN sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/' /etc/apt/sources.list

RUN apt-get update && apt-get -y upgrade && DEBIAN_FRONTEND=noninteractive apt-get -y install \
    apache2 libapache2-mod-php5 php5-sqlite sqlite3


ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

EXPOSE 80


ADD itdb-1.23 /var/www/site

ADD apache.conf /etc/apache2/sites-enabled/000-default.conf

RUN cd /var/www \
    && chmod 775 site  \
    && cp site/data/pure.db site/data/itdb.db \
    && chown -R www-data:www-data site/data/ \
    && chown -R www-data:www-data site/translations/ \
    && chmod -R 775 site/data \
    && chmod -R 775 site/translations



CMD /usr/sbin/apache2ctl -D FOREGROUND
