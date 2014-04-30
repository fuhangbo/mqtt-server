# Purpose of this document

This page is meant to be find a common view on MQTT $SYS. At the moment, many broker implementations implement some kind of $SYS topic but there isn't a common definition of required and optional $SYS topics for broker implementations yet. 

# Definitions
* **Static** Topics: Messages on a static $SYS topic are not required to be sent on every $SYS topic update interval
* **Required** Topics: Every broker which claims to support the $SYS topics must support these topics. 
* **Optional** Topics: A broker implementation may decide if


# Topics

Most of the topics and descriptions are copied from: http://mosquitto.org/man/mosquitto-8.html

## Required Topics

* **$SYS/broker/bytes/received**:
The total number of bytes received since the broker started.

* **$SYS/broker/bytes/sent**:
The total number of bytes sent since the broker started.

* **$SYS/broker/clients/connected**:
The number of currently connected clients

* **$SYS/broker/clients/disconnected**:
The total number of persistent clients (with clean session disabled) that are registered at the broker but are currently disconnected.

* **$SYS/broker/clients/maximum**:
The maximum number of active clients that have been connected to the broker. This is only calculated when the $SYS topic tree is updated, so short lived client connections may not be counted.

* **$SYS/broker/clients/total**:
The total number of connected and disconnected clients with a persistent session currently connected and registered on the broker.

* **$SYS/broker/messages/inflight**:
The number of messages with QoS>0 that are awaiting acknowledgments.

* **$SYS/broker/messages/received**:
The total number of messages of any type received since the broker started.

* **$SYS/broker/messages/sent**:
The total number of messages of any type sent since the broker started.

* **$SYS/broker/messages/stored**:
The number of messages currently held in the message store. This includes retained messages and messages queued for durable clients.

* **$SYS/broker/messages/publish/dropped**:
The total number of publish messages that have been dropped due to inflight/queuing limits.

* **$SYS/broker/messages/publish/received**:
The total number of PUBLISH messages received since the broker started.

* **$SYS/broker/messages/publish/sent**:
The total number of PUBLISH messages sent since the broker started.

* **$SYS/broker/messages/retained/count**:
The total number of retained messages active on the broker.

* **$SYS/broker/subscriptions/count**:
The total number of subscriptions active on the broker.

* **$SYS/broker/time**:
The current time on the server.

* **$SYS/broker/uptime**:
The amount of time in seconds the broker has been online.

* **$SYS/broker/version**:
The version of the broker. Static.

## Optional Topics:

* **$SYS/broker/changeset**:
The repository changeset (revision) associated with this build. Static.

* **$SYS/broker/bridge/#**:
When bridges are configured to/from the broker, common practice is to provide a status topic that indicates the state of the connection. This is provided within $SYS/broker/bridge/ by default. If the value of the topic is 1 the connection is active, if 0 then it is not active.

* **$SYS/broker/load/connections/+**:
The moving average of the number of CONNECT packets received by the broker over different time intervals. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of connections received in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/load/bytes/received/+**:
The moving average of the number of bytes received by the broker over different time intervals. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of bytes received in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/load/bytes/sent/+**:
The moving average of the number of bytes sent by the broker over different time intervals. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of bytes sent in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/load/messages/received/+**:
The moving average of the number of all types of MQTT messages received by the broker over different time intervals. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of messages received in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/load/messages/sent/+**:
The moving average of the number of all types of MQTT messages sent by the broker over different time intervals. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of messages send in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/load/publish/dropped/+**:
The moving average of the number of publish messages dropped by the broker over different time intervals. This shows the rate at which durable clients that are disconnected are losing messages. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of messages dropped in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/load/publish/received/+**:
The moving average of the number of publish messages received by the broker over different time intervals. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of publish messages received in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/load/publish/sent/+**:
The moving average of the number of publish messages sent by the broker over different time intervals. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of publish messages sent in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/load/sockets/+**:
The moving average of the number of socket connections opened to the broker over different time intervals. The final "+" of the hierarchy can be 1min, 5min or 15min. The value returned represents the number of socket connections in 1 minute, averaged over 1, 5 or 15 minutes.

* **$SYS/broker/timestamp**:
The timestamp at which this particular build of the broker was made. Static.

* **$SYS/clients/[client-id]/ip**:
* **$SYS/clients/[client-id]/connectedtime**:
