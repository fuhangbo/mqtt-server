While mosquitto has been officially added to the Fedora (incl. EPEL), Debian, and Ubuntu repositories, for other Linux distributions you will need to do some more work. 

#### General outline

You should setup the new repo by adding the .repo file to your system.

#### OpenSUSE

Run through the following steps as root:

*  ''cd /etc/yum.repos.d/''

*  ''wget -c http://download.opensuse.org/repositories/home:/oojah:/mqtt/openSUSE_12.3/home:oojah:mqtt.repo''

*  ''yum update''

You will be prompted if you wish to install the packages, answer yes.

If you should see a message like the one below. You should answer yes.

	
	Importing GPG key 0x49E1D0B1 "home:oojah OBS Project `<home:oojah@build.opensuse.org>`" from 
	http://download.opensuse.org/repositories/home:/oojah:/mqtt/CentOS_CentOS-5/repodata/repomd.xml.key


You may see the following warnings:

	
	useradd: unknown group mosquitto
	warning: user mosquitto does not exist - using root
	warning: group mosquitto does not exist - using root


They can be ignored or you can manually create the missing user group details. You should then edit the file ''/etc/mosquitto/mosquitto.conf'' to suit. 

Finally start ''mosquitto'' as a daemon with the line, ''/etc/init.d/mosquitto start''
