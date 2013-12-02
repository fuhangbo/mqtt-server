# Ping Message ID

We should consider adding an optional message id to the PINGREQ and PINGRESP message types.

While the current PING functionality seems to primarily be to extend the keepalive timer - by adding an optional message id to this we could use the ping functionality for additional purposes such as network latency testing, detection of packet loss, etc to a better degree then is now possible.

## Alternative suggestion


A more general possibility would be for PINGRESP to return whatever was in the payload part of the PINGREQ message. At the moment, remaining length will always be equal to zero (although mosquitto at least will accept rl>0 but just discard the extra data) but with this proposal it could be anything. Too open to abuse?
