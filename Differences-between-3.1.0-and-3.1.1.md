Differences between versions 3.1.0 and 3.1.1 of the MQTT specification:

**3.1.0 specification:**
http://public.dhe.ibm.com/software/dw/webservices/ws-mqtt/mqtt-v3r1.html

**3.1.1 specification:**
http://docs.oasis-open.org/mqtt/mqtt/v3.1.1/mqtt-v3.1.1.html


| No. | Description                                          | Reference in 3.1.1 spec     |
|-----|------------------------------------------------------|-----------------------------|
| 1.  | Strings must all be verified to be valid UTF-8       | 1.5.3 UTF-8 encoded strings |
| 2.  | Must disconnect if string contains NULL              | 1.5.3 UTF-8 encoded strings |
| 3.  | Protocol name has changed to MQTT                    | 3.1.2.1 Protocol Name       |
| 4.  | Protocol level has changed to 0x04                   | 3.1.2.2 Protocol Level      |
| 5.  | ClientIds MAY contain more than 23 encoded bytes     | 3.1.3.1 Client Identifier   |
| 6.  | ClientId MAY be zero bytes long                      | 3.1.3.1 Client Identifier   |
| 7.  | ClientId MUST actually be UTF-8                      | 3.1.3.1 Client Identifier   |
| 8.  | ClientId MAY be restricted to alphanumeric chars     | 3.1.3.1 Client Identifier   |
| 9.  | CONNACK has new "session present" flag               | 3.2.2.2 Session Present     |
| 10. | Ensure that DUP isn't set for QoS 0                  | 3.3.1.1 DUP                 |
| 11. | SUBACK can now indicate failure                      | 3.9.3 Suback Payload        |
| 12. | Clients are allowed to send further Control Packets immediately after sending a CONNECT Packet | 3.1.4 Response


## Other more general changes

* Flags in the fixed header are now specific to the packet type.
* Clarifications to storing/clearing 0 byte retained messages

## Terminology changes

* MQTT **Broker** is now MQTT **Server**
* **Message ID** is now **Packet ID**
* **Message Type** is now **Packet Type**
* Subscribe and Unsubscribe take **Topic Paths**, rather than **Topic names**

