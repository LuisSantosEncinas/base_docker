FROM ubuntu:18.04

RUN apt-get update

RUN apt-get install apache2 -y

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y install tzdata

RUN apt-get install php php-cli php-common -y

RUN echo "PHP version $(php --version)"

RUN useradd luis

ENV archivo docker

WORKDIR /var/www/html

EXPOSE 90

LABEL version=1

USER luis

RUN echo "Yo soy $(whoami)"

USER root

VOLUME var/www/html

CMD apachectl -DFOREGROUND