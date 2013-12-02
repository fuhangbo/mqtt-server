The keepAlive timer section of the spec (http://public.dhe.ibm.com/software/dw/webservices/ws-mqtt/mqtt-v3r1.html#keep-alive-timer) does not properly identify the important of the keepalive for the client knowing that the server is still alive.

In the case of QoS0 messages, the client could be happily sending them well within the KA interval and never know the server was hung. As it is currently worded in the spec, that would be acceptable.

The spec needs to make it clear that a client should send a PINGREQ packet if it hasn't received anything from the server within the KA interval, regardless of what it is doing send-wise.

The language also needs to make the idea of a grace period a bit more in keeping with the definition of a fixed timeout. It is possibly more accurate to say the keepalive value is a declaration by the client for how often it will contact the server. The server then applies a grace period to allow for factors outside of the clients control - eg slow network.
