#+++++++++++++++++++++++++++++++++++++++
# Dockerfile for webdevops/php-apache:debian-7
#    -- automatically generated  --
#+++++++++++++++++++++++++++++++++++++++

FROM webdevops/php:debian-7

MAINTAINER info@webdevops.io
LABEL vendor=WebDevOps.io
LABEL io.webdevops.layout=8
LABEL io.webdevops.version=1.2.3

ENV WEB_DOCUMENT_ROOT  /app
ENV WEB_DOCUMENT_INDEX index.php
ENV WEB_ALIAS_DOMAIN   *.vm
ENV WEB_PHP_SOCKET  127.0.0.1:9000

COPY conf/ /opt/docker/

# Install apache
RUN /usr/local/bin/apt-install \
        apache2 \
        apache2-mpm-worker \
        libapache2-mod-fastcgi \
	&& sed -ri ' \
		s!^(\s*CustomLog)\s+\S+!\1 /proc/self/fd/1!g; \
		s!^(\s*ErrorLog)\s+\S+!\1 /proc/self/fd/2!g; \
		' /etc/apache2/apache2.conf \
	&& rm -f /etc/apache2/sites-enabled/* \
	&& a2enmod actions fastcgi ssl rewrite headers expires \
	&& /opt/docker/bin/provision run --tag bootstrap --role webdevops-apache --role webdevops-php-apache \
    && /opt/docker/bin/bootstrap.sh


EXPOSE 80 443
