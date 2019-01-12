FROM centos:centos7.4.1708

# update yum
RUN yum -y update
RUN yum -y install yum-utils
RUN yum clean all

RUN yum -y install epel-release
RUN yum -y groupinstall "Development Tools"
RUN yum -y install wget git vim zsh curl

# install remi repo
RUN wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN rpm -Uvh remi-release-7*.rpm
RUN yum-config-manager --enable remi-php70

# install apache2.4
RUN yum -y install httpd

# copy conf
COPY ./vhost.conf /etc/httpd/conf.d/vhost.conf

# enable service.
RUN systemctl enable httpd

# install php7
RUN \
  yum -y install \
    php php-common \
    php-mbstring \
    php-mcrypt \
    php-devel \
    php-xml \
    php-mysqlnd \
    php-pdo \
    php-cli \
    php-gd \
    php-xdebug \
    php-memcached \
    php-opcache --nogpgcheck \
    php-bcmath

# install composer
RUN curl -sS https://getcomposer.org/installer | php && \
  mv composer.phar /usr/local/bin/composer

# timezone setting
RUN cp /etc/localtime /etc/localtime.org
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

EXPOSE 80

CMD ["/sbin/init"]