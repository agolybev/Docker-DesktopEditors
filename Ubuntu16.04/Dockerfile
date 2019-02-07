FROM ubuntu:16.04

LABEL maintainer Ascensio System SIA <support@onlyoffice.com>

ARG GIT_BRANCH=develop

RUN apt-get -y update && \
    apt-get -yq install locales && \
    locale-gen en_US.UTF-8 && \
    apt-get -yq install \
        autoconf \
		build-essential \
		curl \
		default-jre \
		git \
		libatk1.0-dev \
		libcairo2-dev \
		libcurl4-gnutls-dev \
		libgconf2-dev \
		libgdk-pixbuf2.0-dev \
		libglib2.0-dev \
		libgtkglext1-dev \
        libtool \
		libxml2-dev \
		libxss-dev \
		p7zip-full \
		qtchooser \
		software-properties-common \
		subversion \
		wget

RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - && \
	apt-get -y update && \
	apt-get -yq install nodejs

RUN npm install -g grunt-cli

RUN add-apt-repository -y ppa:beineri/opt-qt596-xenial && \
	apt-get -y update && \
	apt-get -yq install qt59-meta-full

RUN git clone -b $GIT_BRANCH --recursive https://github.com/ONLYOFFICE/DesktopEditors.git
RUN cd DesktopEditors && git submodule foreach --recursive git checkout $GIT_BRANCH

ENV QT_SELECT=opt-qt59 QT_ICU=/usr/lib/x86_64-linux-gnu QT_PATH=/opt/qt59 QT_PLUGINS=/opt/qt59/plugins
RUN cd DesktopEditors && make
RUN cd DesktopEditors && make install

ENTRYPOINT /opt/onlyoffice/desktopeditors/DesktopEditors
