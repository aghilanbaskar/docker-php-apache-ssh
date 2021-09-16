FROM php:7.4-apache

RUN apt-get update

RUN a2enmod rewrite

RUN a2enmod headers

RUN service apache2 restart

# Install PDO and PGSQL Drivers
RUN apt-get install -y libpq-dev \
  && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
  && docker-php-ext-install pdo pdo_pgsql pgsql mysqli


RUN apt-get update && apt-get install -y ca-certificates socat openssh-server vim
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN mkdir /root/.ssh
RUN chmod o-rwx /root/.ssh

# EXPOSE 22
# EXPOSE 80

# RUN echo "root:lrl2002*" | chpasswd

# RUN service ssh restart


####################
#https://github.com/tom-doerr/docker-ssh
# Build Image
#docker build -t apache-php-ssh .

# docker run --name apache-php-ssh-test -p 2222:22 -p 8080:80 -t -d apache-php-ssh
###################