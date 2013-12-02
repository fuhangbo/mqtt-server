A WebSocket is very similar to a TCP socket, the key difference is that it allows a web browser to open a bi-directional communication pipe to a server.  With this in place it is now possible to provide first class MQTT support for Web applications running in a web browser.  

There are a couple of options

 1.  IBM's [MQ 7.5](http://www-01.ibm.com/software/websphere/subscriptionandsupport/compare-mq-versions.html) comes with websockets support
 2.  The Mosquitto broker has [a Javascript client with an example running](http://test.mosquitto.org/ws.html)
 3.  The [HiveMQ MQTT broker](http://www.hivemq.com) has native websockets support.

The v3.1 protocol can flow as is but there are a couple of other WebSocket features that need to be specified to provide inter-operability. These are discussed on [the Eclipse Paho wiki](http://wiki.eclipse.org/Paho/Paho_Websockets) and both the IBM and Mosquitto implementations have collaborated on these. HiveMQ also implements these behaviours.

Typically a webserver will require an additional WebSockets module such as pywebsocket or [lighthttpd's mod_websocket](https///github.com/nori0428/mod_websocket) to do forwarding to an existing broker. 
