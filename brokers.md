# Servers/Brokers

## IBM Websphere MQ Telemetry

The Telemetry MQTT feature is built-in optionally licensed feature in 
[WebSphere MQ](http://www-01.ibm.com/software/integration/wmqfamily/telemetry/ ) version 7.1 and above. It provides full MQTT v3.1 support, IBM MQ and JMS support. IBM WebSphere MQ Advanced includes the MQTT license at no charge. It ships with reference Java (MIDP and above), C and JavaScript (MQTT over WebSocket) clients.  Eclipse Paho is highly recommended by IBM.

## IBM MessageSight

[ IBM MessageSight](http://www.ibm.com/messagesight ) is a DMZ secure MQTT appliance with hardware messaging acceleration for M2M and mobile applications requiring extreme volume, low latency, FIPS 140-2 and NSA Suite B security. Messaging provider for MQTT, HTML5 WebSockets, JMS. Includes C, Java, JavaScript, Apache Cordova/PhoneGap, ObjectiveC clients. Also connects/bridges IBM MQ, IBM Integration Bus, WebSphere MessageBroker.

## IBM Integration Bus

[ IBM Integration Bus](http://www-03.ibm.com/software/products/us/en/integration-bus/ ) V9 has Telemetry feature built-in as optional licensed feature.  IBM WebSphere MessageBroker V7 & V8 also include it as optionally licensed feature.

[ Really Small Message Broker](http://www.alphaworks.ibm.com/tech/rsmb )\\
75KB MQTT broker runtime free download as binaries from IBM alphaWorks, RSMB is a C implementation of a tiny MQTT server suitable for development, embedded systems, concentrators or small to medium sized deployments. It provides complete MQTT v3.1 support, bridging, and a C client API.

## Mosquitto

[ Mosquitto](http://mosquitto.org ) is an Open Source MQTT server with C, C++, Python.  For JavaScript, Mosquitto recommends the Eclipse Paho Javascript client. A public, hosted test server is also available ([more information](public_brokers))

## Eclipse Paho

The [ Eclipse Paho](http://www.eclipse.org/paho/ ) project hosts an instance of the mosquitto broker as a public test sandbox for the [Machine-to-Machine Industry Working Group](http://m2m.eclipse.org/) ([more information](public_brokers)).

## Eurotech Everywhere Device Cloud

[Eurotech Everywhere Device Cloud](http://www.eurotech.com/en/solutions/device+to+cloud/mqtt+protocol) is a cloud-based service provided by [Eurotech](http://www.eurotech.com).

## Xively

The [ Xively](http://xively.com ) service, formerly known as Cosm, formerly known as Pachube, provides a data cloud for the Internet of Things, with MQTT support in beta. This is not a generic MQTT broker implementation; it uses MQTT as a transport for publishing and subscribing to your already existing data feeds ([more information](mqtt_and_pachube)).

## eMQTT

An [ Erlang MQTT](https///github.com/emqtt/emqtt ) broker.

## m2m.io

[ m2m.io](http://m2m.io ) is a cloud messaging service ([more information](public_brokers)).

## webMethods Nirvana Messaging

[ webMethods Nirvana Messaging](http://www.my-channels.com/products/nirvana.html ) provides a messaging engine with support for many different transports. Their MQTT support is described in their [blog](http://blog.my-channels.com/2012/01/27/mqtt-support-in-nirvana-7/).

## RabbitMQ

[ RabbitMQ](http://rabbitmq.com/ ) is an AMQP message broker – with an [MQTT plugin](http://www.rabbitmq.com/blog/2012/09/12/mqtt-adapter/) (bundled in version 3.x onwards). A public test server is also available ([more information](public_brokers)).

## Apache ActiveMQ

Details of “classic” [ ActiveMQ’s](http://activemq.apache.org/index.html ) support for MQTT are available [here](http://activemq.apache.org/mqtt.html).

## Apache Apollo

The “next generation” of ActiveMQ, [ Apache Apollo](http://activemq.apache.org/apollo/ ), supports MQTT via a [plugin](https///github.com/fusesource/fuse-extra/tree/master/fusemq-apollo/fusemq-apollo-mqtt).

## Moquette

[ Moquette](http://code.google.com/p/moquette-mqtt/ ) is a Java MQTT broker based on an eventing model with Apache Mina.

## HiveMQ

[ HiveMQ](http://www.hivemq.com/ ) is a MQTT broker which was built from the ground up with maximum scalability and enterprise-ready security in mind. It comes with native web socket support and an open source plugin SDK to extend its functionality or integrate it with other components. A public test server is also available ([more information](public_brokers)).

## Mosca

As node.js MQTT broker can [ Mosca](https///github.com/mcollina/mosca ) be plugged on top of Redis, AMQP, MQTT, or ZeroMQ.

## Litmus Automation Loop

[ Loop](http://litmusautomation.com ) is a cloud based MQTT broker with scalability, high availability and security at core. Loop provides full MQTT 3.1 support and JMS connectivity. It can handle extremely large numbers of connected clients. On the other side it can be connected to any ERP, CRM and enterprise architecture with ESB or NoSQL databases for blazing fast data storage.


**More information on brokers**


*  [compare the capabilities](server_support) of different brokers

*  see some of the [public brokers](public_brokers) available for testing on the wiki
