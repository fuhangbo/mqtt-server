## Client ID autogeneration

# For clients

[Roger Light proposed](http://groups.google.com/d/topic/mqtt/y6fY1FmGfu0/discussion):

> I'd like to propose something to be added to the spec as a suggestion for people implementing MQTT clients. If a client automatically generates a client id based on a random or non-repeatable value, it should refuse to run if the clean session flag is set to false. Clients with clean session set to false (durable/persistent clients) with a random id will be unable to reconnect using the same id and so leave persistent subscriptions on the server that can never be fulfilled.

# For servers

This is an enhancement to the spec rather than a clarification.

The ability for the server to generate client ids would be useful in some situations. This could be achieved by the client sending a CONNECT with a zero length id. The server would generate an id and send it to the client as part of the CONNACK message. The client would always have the clean session feature enabled regardless of the setting in its CONNECT.
