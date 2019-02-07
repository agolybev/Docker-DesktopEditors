## Building ONLYOFFICE DesktopEditors from source code on Centos 7

**Step 1**: Installing dependencies

***Install EPEL repo***
```
$ sudo yum install epel-release
$ sudo yum updateinfo
```
***Install developer tools***
```
$ sudo yum groupinstall 'Development Tools'
```
***Install common dependencies***
```
$ sudo yum install \
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
```	
***Install nodejs***
```
$ sudo curl -sL https://rpm.nodesource.com/setup_8.x | bash -
$ sudo yum install nodejs
```

***Install grunt***
```
$ sudo npm install -g grunt-cli
```

**Step 2**: Getting source code
```
$ git clone --recursive https://github.com/ONLYOFFICE/DesktopEditors.git
```

**Step 3**: Compiling and assembling source code
```
$ cd DesktopEditors
$ PATH=$PATH:/usr/lib64/qt5/bin make
```

**Step 4**: Installing ONLYOFFICE DesktopEditors
```
$ cd DesktopEditors
$ sudo QT_ICU=/usr/lib64 \
	QT_LIBS=/usr/lib64 \
	QT_PLUGINS=/usr/lib64/qt5/plugins \
	make install
```

**Step 5**: Running ONLYOFFICE DesktopEditors
```
$ cd /opt/onlyoffice/desktopeditors
$ ./DesktopEditors
```