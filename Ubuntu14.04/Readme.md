##Building ONLYOFFICE DesktopEditors from source code on Ubuntu 14.04.

**Step 1**: Installing dependencies
	***Install common dependencies***
```
$ sudo apt-get -yq install \
	apt-transport-https \
	autoconf \
	build-essential \
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
```	
***Install nodejs***
```
$ sudo curl -sL https://deb.nodesource.com/setup_8.x | bash -
$ sudo apt-get update
$ sudo apt-get install nodejs
```

***Install grunt***
```
$ sudo npm install -g grunt-cli
```

***Install Qt***
```
$ sudo add-apt-repository ppa:beineri/opt-qt596-trusty
$ sudo apt-get update
$ sudo apt-get install qt59-meta-full
```

**Step 2**: Getting source code
	```
	$ git clone --recursive https://github.com/ONLYOFFICE/DesktopEditors.git
	```

**Step 3**: Compiling and assembling source code
```
$ cd DesktopEditors
$ make
```

**Step 4**: Installing ONLYOFFICE DesktopEditors
```
$ cd DesktopEditors
$ sudo QT_ICU=/usr/lib/x86_64-linux-gnu \
	QT_PATH=/opt/qt59/lib \
	QT_PLUGINS=/opt/qt59/plugins \
	make install
```

**Step 5**: Running ONLYOFFICE DesktopEditors
```
$ cd /opt/onlyoffice/desktopeditors
$ ./DesktopEditors
```