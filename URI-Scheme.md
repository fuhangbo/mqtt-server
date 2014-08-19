Using URIs to connect to a MQTT broker
======================================

URIs are useful to provide serval pieces of information in a single compact string. They can be used to convey all the information required to connect to a MQTT broker.

The format is like this:

    mqtt[s]://[username][:password]@host.domain[:port]

A typical use for this is to provide the details of a MQTT broker in an environment variable. The suggested name for this variable is 'MQTT_SERVER'.

### Scheme
The scheme part describes the protocol to use to communicate with the server. It can either be 'mqtt' for unencrypted communication or 'mqtts' to wrap up to MQTT protocol in a secure TLS encrypted connection.

Some implementations may also support the 'tcp' and 'ssl' scheme names.

### Username
The second section of the URI is the username to be put into the CONNECT packet, send directly after opening the socket. If no username is given or it is an empty string, then the user name flag should not be set in the CONNECT packet.

### Password
Optionally a password may be given in the URI. This is also passed into the CONNECT packet. A colon separates the username and password. If the username is an empty string, then the password should still be sent.

### Host and Domain
Other than the scheme, this the only required component of a MQTT URI. This is the DNS name or IP address of the MQTT broker to connect to.

### Port
The TCP port of the MQTT broker to connect to. If no port is given, then the default port number, 1883, is used for the 'mqtt' scheme and port 8883 is used by default for the 'mqtts' scheme.
