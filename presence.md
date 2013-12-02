It is often useful to know which clients are currently connected to a broker. MQTT places no requirements on the broker to provide such information, so individual broker implementations may provide their own ways of doing so. But it is possible to build a presence awareness mechanism within the capabilities of MQTT.

When a client connects, it publishes a retained message to a well-defined topic that identifies the client, such as 'clients/`<client-id>` with a payload of '1'. The client also establishes a Will (LWT) message, to be published when the client loses its connection, to the same topic, also retained, but this time with a payload of '0'.

Anyone subscribed to 'clients/+' will be notified as clients come and go. The fact the connection state is published as a retained message means it is possible to get a complete list of clients at any time by resubscribing to the topic.

For scalability reasons, it may be desirable to use the LWT to clear the retained message, rather than replace it. Of course, this would rely on a convention rather than protocol feature mentioned [here](clear_topic).
