#+++++++++++++++++++++++++++++++++++++++
# Dockerfile for webdevops/php-dev:centos-7
#    -- automatically generated  --
#+++++++++++++++++++++++++++++++++++++++

FROM webdevops/php:centos-7

MAINTAINER info@webdevops.io
LABEL vendor=WebDevOps.io
LABEL io.webdevops.layout=8
LABEL io.webdevops.version=1.2.3

COPY conf/ /opt/docker/

# Install development environment
RUN wget -O - "https://packages.blackfire.io/fedora/blackfire.repo" | tee /etc/yum.repos.d/blackfire.repo \
    && /usr/local/bin/yum-install \
        # Install tools
        graphviz \
        # Install php development stuff
        php-pecl-xdebug \
        blackfire-php \
        blackfire-agent \
    && /opt/docker/bin/provision run --tag bootstrap --role webdevops-php-dev \
    && /opt/docker/bin/bootstrap.sh

