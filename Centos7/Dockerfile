FROM centos:7

LABEL maintainer Ascensio System SIA <support@onlyoffice.com>

ARG GIT_BRANCH=develop

RUN yum -y updateinfo && \
	yum -y install epel-release && \
	yum -y updateinfo && \
	yum -y groupinstall 'Development Tools' && \
    yum -y install \
		atk-devel \
		autoconf \
		cairo-devel \
		curl \
		GConf2-devel \
		gdk-pixbuf2-devel \
		git \
		glib2-devel \
		gtkglext-devel \
		java-11-openjdk \
		libcurl-devel \
		libstdc++-static \
		libtool \
		libxml2-devel \
		libXScrnSaver-devel \
		p7zip \
		p7zip-plugins \
		qt5-qtbase-devel \
		qt5-qtmultimedia \
		qt5-qtsvg-devel \
		qt5-qtx11extras-devel \
		subversion \
		wget

RUN curl -sL https://rpm.nodesource.com/setup_8.x | bash - && \
	yum -y install nodejs

RUN npm install -g grunt-cli

RUN git clone -b $GIT_BRANCH --recursive https://github.com/ONLYOFFICE/DesktopEditors.git
RUN cd DesktopEditors && git submodule foreach --recursive git checkout $GIT_BRANCH

RUN cd DesktopEditors && PATH=$PATH:/usr/lib64/qt5/bin make

ENV QT_ICU=/usr/lib64 QT_LIBS=/usr/lib64 QT_PLUGINS=/usr/lib64/qt5/plugins
RUN cd DesktopEditors && make install

ENTRYPOINT /opt/onlyoffice/desktopeditors/DesktopEditors
