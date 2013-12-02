Possible solutions to clients auto-discovering a broker:


*  Zeroconf / Multicast-DNS / DNS-SD
    * [a non-intrusive example using Avahi](http://pastebin.com/0RhJyZud)

*  Anycast / a well-known IPv6 address

*  DHCP option

The following sequence might be reasonable:


*  Use __user supplied values__ for server name or ip number

*  Use a server name or ip number received as __DHCP option__ (how can we apply for an official DHCP option assignment for MQTT? A: Application instructions at the end of [RFC 2132](http://www.ietf.org/rfc/rfc2132.txt).  List of all current  [DHCP Options](http://www.iana.org/assignments/bootp-dhcp-parameters/bootp-dhcp-parameters.xhtml).  Recommend Option 7 (Logging Server).
*  __Zeroconf__ to find the mqtt server

*  Try __mqtt.`<localdomain>`__ as server name

*  Try using the __ip address of the DHCP server__ 

*  Use a __vendor supplied server name__

Some steps may be skipped if not supported by the particular client.

[Discussion of using JmDNS and MQTT](http://joergwende.wordpress.com/2013/11/10/using-jmdns-and-mqtt-together/)

[autodiscovery for mosquitto (bug tracker)](https///bugs.launchpad.net/mosquitto/+bug/902916)
