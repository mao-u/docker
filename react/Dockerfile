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

# nodejs install
RUN yum -y install https://rpm.nodesource.com/pub_11.x/el/7/x86_64/nodesource-release-el7-1.noarch.rpm
RUN yum -y install nodejs

# copy react project
COPY ./data/react-redux-todo /var/www/html/react-redux-todo

# react install
RUN cd /var/www/html/react-redux-todo && \
  npm install --save redux react-redux redux-logger

EXPOSE 3000

# nmp start
RUN cd /var/www/html/react-redux-todo && \
  npm start

# install php7
# RUN \
#   yum -y install \
#   php php-common \
#   php-mbstring \
#   php-mcrypt \
#   php-devel \
#   php-xml \
#   php-mysqlnd \
#   php-pdo \
#   php-cli \
#   php-gd \
#   php-xdebug \
#   php-memcached \
#   php-opcache --nogpgcheck \
#   php-bcmath

# install composer
# RUN curl -sS https://getcomposer.org/installer | php && \
#   mv composer.phar /usr/local/bin/composer

# timezone setting
# RUN cp /etc/localtime /etc/localtime.org
# RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# EXPOSE 80

# CMD ["/sbin/init"]