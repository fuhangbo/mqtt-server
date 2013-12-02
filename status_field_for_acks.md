# Add a status field to acknowledgements.

It's been talked about before - but we should consider adding a status field (byte?) to acknowledgement messages.  

The reason we would want this is that the current version silently ignores errors (don't have permission to publish/subscribe, etc.)  Silent failures cannot be logged, reported or reacted to.

CONNACK already has this.  It should be added to PUBACK, SUBACK and UNSUBACK.
