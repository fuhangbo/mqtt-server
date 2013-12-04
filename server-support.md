This page attempts to document the features that various MQTT servers (brokers) support. This is specific to their MQTT support; many of these servers have much wider capabilities beyond just MQTT.

# Capabilities

Server | QoS 0 | QoS 1 | QoS 2 | auth | [bridge](bridge_protocol) | [$SYS](conventions#$sys) | SSL | [dynamic topics](are_topics_dynamic) | cluster | websockets | plugin system
------ | ----- | ----- | ----- | ---- | ------------------------- | ------------------------ | --- | ------------------------------------ | ------- | ---------- | ------------- | 
[mosquitto](mosquitto_message_broker)                                             | ✔   | ✔   | ✔   | ✔  | ✔                       | ✔                      | ✔ | ✔                                  | ✘     | ✘        | ✔           | 
RSMB                                                                              | ✔   | ✔   | ✔   | ✔  | ✔                       | ✔                      | ✘ | ✔                                  | ✘     | ✘        | ?             | 
WebSphere MQ                                                                      | ✔   | ✔   | ✔   | ✔  | ✔                       | ✔                      | ✔ | ✔                                  | ?       | ?          | ?             | 
[HiveMQ](http://www.hivemq.com)                                                   | ✔   | ✔   | ✔   | ✔  | ✘                       | ✔                      | ✔ | ✔                                  | ✔     | ✔        | ✔           | 
[Apache Apollo](http://activemq.apache.org/apollo)                                | ✔   | ✔   | ✔   | ✔  | ✘                       | ✘                      | ✔ | ✔                                  | ?       | ✔        | ?             | 
Apache ActiveMQ                                                                   | ✔   | ✔   | ✔   | ?    | ?                         | ?                        | ?   | ?                                    | ?       | ✔        | ?             | 
[my-Channels Nirvana Messaging](http://www.my-channels.com/products/nirvana.html) | ✔   | ✔   | ✔   | §   | ✘                       | ✘                      | ✔ | ✘                                  | ?       | ?          | ?             | 
[RabbitMQ](http://www.rabbitmq.com/blog/2012/09/12/mqtt-adapter/)                 | ✔   | ✔   | ✘   | ✔  | ✘                       | ✘                      | ✔ | ✔                                  | ?       | ?          | ?             | 
[MQTT.js](https///github.com/adamvr/MQTT.js)                                      | ✔   | ✘   | ✘   | §   | ✘                       | ✘                      | ✔ | ✔                                  | ✘     | ?          | ✘           | 
[moquette](http://code.google.com/p/moquette-mqtt/)                               | ✔   | ✔   | ✘   | ?    | ?                         | ?                        | ?   | ?                                    | ✘     | ✘        | ✘           | 
[mosca](mosca)                                                                    | ✔   | ✔   | ✘   | ✔  | ?                         | ?                        | ?   | ?                                    | ✘     | ✔        | ✘           | 

Key: ✔ supported ✘ not supported ? unknown § see limitations
# Limitations


*  Both MQTT.js and my-Channels Nirvana Messaging will accept connections with username and password supplied, but do not actually authenticate the connection

Potentially should add columns to track: LWT; additional protocols (WMQ, AMQP, MQTTs etc)

_This is in need of expanding. Please add known information about known brokers to this table and include any known limitations below it._
