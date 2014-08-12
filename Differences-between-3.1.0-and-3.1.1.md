Differences between versions 3.1.0 and 3.1.1 of the MQTT specification:

**3.1.0 specification:**
http://public.dhe.ibm.com/software/dw/webservices/ws-mqtt/mqtt-v3r1.html

**3.1.1 specification:**
http://docs.oasis-open.org/mqtt/mqtt/v3.1.1/mqtt-v3.1.1.html


| No. | Description                                          | Reference in 3.1.1 spec     |
|-----|------------------------------------------------------|-----------------------------|
| 1.  | Strings must all be verified to be valid UTF-8       | 1.5.3 UTF-8 encoded strings |
| 2.  | Protocol name has changed to MQTT                    | 3.1.2.1 Protocol Name       |
| 3.  | Protocol level has changed to 0x04                   | 3.1.2.2 Protocol Level      |
| 4.  | ClientIds MAY contain more than 23 encoded bytes     | 3.1.3.1 Client Identifier   |
| 5.  | ClientId MAY be zero bytes long                      | 3.1.3.1 Client Identifier   |
| 6.  | ClientId MUST actually be UTF-8                      | 3.1.3.1 Client Identifier   |
| 7.  | ClientId MAY be restricted to alphanumeric chars     | 3.1.3.1 Client Identifier   |
| 8.  | CONNACK has an extra byte for "session present" flag | 3.2.2.2 Session Present     |
| 9.  | SUBACK can now indicate failure                      | 3.9.3 Suback Payload        |


## Terminology changes

* MQTT **Broker** is now MQTT **Server**
