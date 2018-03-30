# iStat Server

iStat Server is a system monitoring daemon that is used in conjunction with [iStat View for iOS](https://bjango.com/ios/istat/) and [iStat View for macOS](https://bjango.com/mac/istat/) to remotely monitor computers.

-----

### Quick Install
```
curl -fsSL https://files.bjango.com/istatserverlinux/istatserverlinux.sh -o istatserverlinux.sh && sh istatserverlinux.sh
```

Quick install will install and update any required packages. If you do not want packages installed or updated automatically then please perform a manual install using the instructions below

-----

### Supported OSs
- Linux
- FreeBSD, DragonFly BSD, OpenBSD, NetBSD and other BSD based OSs
- AIX
- Solaris
- HP-UX (Still in development and not tested)

-----

### Requirements
- C and C++ compilers such as gcc and g++.
- Auto tools (autoconf and automake).
- OpenSSL/libssl + development libraries.
- sqlite3 + development libraries.
- libxml2 + development libraries.

We have a [package guide available](https://github.com/bjango/istatserverlinux/wiki/Package-Guide) to help you install all the required packages for your OS.

-----

### Building and starting iStat Server
- [Download](https://download.bjango.com/istatserverlinux) and decompress source
- cd /path/to/istatserver
- ./autogen
- ./configure
- make
- sudo make install
- sudo /usr/local/bin/istatserver -d (daemon mode)


A 5 digit passcode is generated by the install script. It can be found in the preference file, which is generally located at **/usr/local/etc/istatserver/istatserver.conf**. iStat View will ask for this passcode the first time you connect to your computer.

-----

### Upgrading iStat Server
Upgrades follow the same process as standard installs. Please stop istatserver if it is running then run the normal build process.

-----

### Starting iStat Server at boot
iStat Server does not install any scripts to start itself at boot. Sample scripts for rc.d, upstart and systemd are included in the resources directory. You may need to customize them depending on your OS.

### Starting with systemd
- sudo cp ./resource/systemd/istatserver.service  /etc/systemd/system/istatserver.service
- sudo service istatserver start

### Starting with upstart
- sudo cp ./resource/upstart/istatserver.conf  /etc/init/istatserver.conf
- sudo start istatserver

### Starting with rc.d
- sudo cp ./resource/rc.d/istatserver  /etc/rc.d/istatserver
- sudo /etc/rc.d/istatserver start

-----

iStat Server is based on [istatd](https://github.com/tiwilliam/istatd) by William Tisäter.

-----

```
        :::::::::   :::::::     ::::      ::::    :::   ::::::::    ::::::::
       :+:    :+:      :+:    :+: :+:    :+:+:   :+:  :+:    :+:  :+:    :+:
      +:+    +:+      +:+   +:+   +:+   :+:+:+  +:+  +:+         +:+    +:+
     +#++:++#+       +#+  +#++:++#++:  +#+ +:+ +#+  :#:         +#+    +:+
    +#+    +#+      +#+  +#+     +#+  +#+  +#+#+#  +#+   +#+#  +#+    +#+
   #+#    #+#  #+# #+#  #+#     #+#  #+#   #+#+#  #+#    #+#  #+#    #+#
  #########    #####   ###     ###  ###    ####   ########    ########
```
