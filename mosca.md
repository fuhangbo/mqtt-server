[Mosca](http://mcollina.github.io/mosca/) is a multi-transport MQTT broker. It aims to support every publish/subscribe broker or protocol out there. This list currently includes:


*  [RabbitMQ](http://www.rabbitmq.com/) and all implementations of the [AMQP](http://www.amqp.org/) protocol.

*  [Redis](http://redis.io/) is an advanced key-value store.

*  [Mosquitto](http://mosquitto.org/) and all implementations of the MQTT protocol, including itself.

*  [ZeroMQ](http://www.zeromq.org/) without a central broker, so Mosca can also be used in a P2P fashion.

# Installation

For the installation you need ''npm'' because mosca is a [node.js](http://nodejs.org/) application,

''npm install mosca -g''

# Usage

Without configuration ''mosca'' is running and listening on localhost.

''mosca -v''
