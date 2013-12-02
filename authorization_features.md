Depending on the broker implementation, different users can then be a authorized to perform different actions. For example, some users may only be allowed to subscribe to certain topics, whilst others with more privileges can publish to them as well.

For example, the Mosquitto ACL implementation is documented here: [mosquitto.conf(5)](http://mosquitto.org/man/mosquitto-conf-5.html) 

RSMB ACLs are quite similar and are documented in the documentation included in the RSMB distribution.

Some attention must be paid to topic tree construction to maximize the value of ACLs.
