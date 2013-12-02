Bridges are essentially just client connections to another broker.

RSMB added (and Mosquitto followed) a non-spec feature that allows an RSMB to recognise an inbound connection as another RSMB bridge. From a [thread on the google group](http://groups.google.com/group/mqtt/browse_thread/thread/8f523d160fb91bef):

> You are right, RSMB recognizes when another RSMB connects to it via a
> bridge by using a different protocol version number (when try_private
> is true, which is the default).  If that connect fails, then the
> bridge will fall back to MQTT 3.1.   This internal protocol is the
> same as MQTT 3.1 except that:
>
> 1) the retained flags are propagated on publish packets, and
> 2) the subscriptions are nolocal (in the JMS sense), to reduce the
> chances of infinite message loops.

This behaviour is easy to apply when the broker is the one making the bridge (outgoing topics) because it knows that the client is a bridge. For incoming topics the different protocol number is used. The protocol number is the actual protocol number (3) OR'd with 128 (bit 8).

Both RSMB and Mosquitto implement this behaviour - but it is not a formal part of the protocol specification.
