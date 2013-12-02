#  Mosquitto 

## Introduction

[Mosquitto](http://mosquitto.org/) is an Open Source MQTT v3.1 message broker written by Roger Light. It aims to provide the same features (and more) as IBM's [Really Small Message Broker](Really Small Message Broker) but as fully Open Source software.


*  [Getting started with Mosquitto on Ubuntu](http://michaelconnors.net/article/462/hello-mqtt)

*  [Getting Started with MQTT](http://nathanborror.tumblr.com/post/31046947556/mqtt)  
## Installation

Mosquitto is available at [http://mosquitto.org/download](http://mosquitto.org/download) and can also be installed on recent versions of Ubuntu from the normal package repository. The latest version is always available from the Mosquitto PPA.

To add the ppa and install Mosquitto on ubuntu 9.10+:

''sudo add-apt-repository ppa:mosquitto-dev/mosquitto-ppa && sudo apt-get update && sudo apt-get install mosquitto''

If installed from the ppa or Debian package Mosquitto will start automatically

For Fedora and its downstream (Red Hat Enterprise Linux/Scientific Linux/CentOS) mosquitto is available out of the [official repository](https///admin.fedoraproject.org/pkgdb/acls/name/mosquitto).

''sudo yum -y install mosquitto''

For OpenSUSE installation details see [rpminstalls](rpminstalls). Still needs some work but drop a line on the irc channel #mqtt if something looks incorrect.

For Alpine Linux mosquitto is available as aport.

''sudo apk add mosquitto''
## Installation on Raspberry Pi

Download the latest tar from [http://mosquitto.org/download](http://mosquitto.org/download)
Currently mosquitto-0.15.tar.gz

The following instructions are for the Debian install

	
	$ sudo apt-get install libwrap0-dev
	$ tar zxf mosquitto-0.15.tar.gz
	$ cd mosquitto-0.15
	$ make
	$ sudo make install
	$ sudo ldconfig

## Usage

Included with Mosquitto are two basic command line clients: mosquitto_pub and mosquitto_sub. They can be used testing of the broker, and combined with a scripting language to implement many pub/sub functions. Mosquitto can also interface with other MQTT clients.

## Detailed reference information

Full manpage documentation covering configuration and usage is available via the [mosquitto website](http://mosquitto.org/documentation/)

## Differences from RSMB

Currently mosquitto is largely similar in functionality to RSMB, but it does not support the following options (these may be added in future; an up-to-date list is maintained at the end of the shipped mosquitto.conf file):

	
	autosave_on_changes
	addresses
	notification_topic
	round_robin
	ffdc_output
	max_log_entries
	trace_level
	trace_output
	try_private


The Mosquitto client library also does not support multiple topic Subscribe/Unsubscribe actions within a single message.
