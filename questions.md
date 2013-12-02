# Questions? Answers!

An assortment of questions (and answers) - most of which probably should be moved somewhere more useful and in context, over time.

# General

## Q: What is MQTT?

MQTT originally stood for **MQ** **T**elemetry **T**ransport, but is now just known as "MQTT". It is a publish/subscribe, extremely simple and lightweight messaging protocol, designed for constrained devices and low-bandwidth, high-latency or unreliable networks. The design principles are to minimise network bandwidth and device resource requirements whilst also attempting to ensure reliability and some degree of assurance of delivery. These principles also turn out to make the protocol ideal of the emerging “machine-to-machine” (M2M) or “Internet of Things” world of connected devices, and for mobile applications where bandwidth and battery power are at a premium.

## Q: Who invented MQTT?

MQTT was invented by Dr Andy Stanford-Clark of IBM, and Arlen Nipper of Arcom (now Eurotech), in 1999.

## Q: Where is MQTT in use?

MQTT has been widely implemented across a variety of industries since 1999. A few of the more interesting examples are listed on the [Projects](http://mqtt.org/projects) page.

## Q: Is MQTT a standard?

As of March 2013, MQTT is in the process of undergoing standardisation at OASIS.

The protocol specification has been [openly published](https///www.ibm.com/developerworks/webservices/library/ws-mqtt/) with a royalty-free license for many years, and companies such as [Eurotech](http://www.eurotech-inc.com/) (formerly known as Arcom) have implemented the protocol in their products.

In November 2011 IBM and Eurotech announced [their joint participation in the Eclipse M2M Industry Working Group](http://www.eclipse.org/org/press-release/20111101_m2msolutions.php) and [donation of MQTT code to the proposed Eclipse Paho project](http://www.marketwatch.com/story/eurotech-and-ibm-contribute-software-to-connect-next-generation-of-wireless-and-mobile-devices-2011-11-03-103900).

## Q: Is the specification of MQTT available?

Yes, please checkout the [Documentation](http://mqtt.org/documentation) page for details.

## Q: How does MQTT relate to SCADA protocol and MQIsdp?

The “SCADA protocol” and the “MQ Integrator SCADA Device Protocol” (MQIsdp) are both old names for what is now known as MQTT. The protocol has also been known as “WebSphere MQTT” (WMQTT), though that name is also no longer used.

## Q: What is WebSphere MQ Telemetry?

This is a product from IBM which implements the MQTT protocol in a very scalable manner and which interoperates directly with the WebSphere MQ family of products.

There are other implementations of MQTT listed on the [Software](software) page.

# Technical

## Q: Does MQTT support security?

You can pass a user name and password with an MQTT packet in V3.1 of the protocol. Encryption across the network can be handled with SSL, independently of the MQTT protocol itself (it is worth noting that SSL is not the lightest of protocols, and does add significant network overhead). Additional security can be added by an application encrypting data that it sends and receives, but this is not something built-in to the protocol, in order to keep it simple and lightweight.

## Q: Are there standard ports for MQTT to use?

Yes. TCP/IP port **1883** is reserved with [IANA](http://www.iana.org/) for use with MQTT. TCP/IP port **8883** is also registered, for using MQTT over SSL.

##  Q: What is a "bridge"? 

The [Really Small Message Broker](Really Small Message Broker) documentation refers to the concept of a "bridge" (not covered in the MQTT specification directly).

This is a simple concept. A bridge allows incoming, outgoing or bidirectional topics to be shared (depending on the broker implementation). They are just one broker connecting to another broker as a client. The second broker doesn't know that there is a broker on the other end, it just talks "normal" MQTT with it. 

## Q: mosquitto's mount_point option simplifies large layered systems using hierarchical bridges. Are their plans to incorporate mount_points into the MQTT protocol?

I think this is beyond the scope of the protocol - a broker implementation specific detail.

