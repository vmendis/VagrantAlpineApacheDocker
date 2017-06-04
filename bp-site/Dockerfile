# Simple nignix service for Alpine Linux

FROM alpine:latest

MAINTAINER Virantha Mendis Version 0.1

ENV ALPINE_FRONTEND noninteractive

RUN apk update
RUN apk add nginx
RUN adduser -D -u 1000 -g 'www' www
RUN mkdir /www
RUN chown -R www:www /var/lib/nginx
RUN chown -R www:www /www
RUN mv /etc/nginx/nginx.conf /etc/nginx/nginx.conf.orig

COPY ./nginx.conf /etc/nginx
COPY ./index.html /www

EXPOSE 80

CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
