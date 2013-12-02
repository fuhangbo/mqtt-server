The MQTT topic specification is [in an Appendix of the spec](http://public.dhe.ibm.com/software/dw/webservices/ws-mqtt/mqtt-v3r1.html#appendix-a).

Roger Light noticed that the spec was not totally clear on the format of topic strings/hierarchies and what the behaviour should be with a trailing slash character.

Nick O'Leary clarified [via the MQTT Google Group](https///groups.google.com/d/msg/mqtt/tQxZjssBDGw/m1CQYZVyVmoJ).

   * a topic ending in a slash is considered equivalent to the same topic without the slash, which enables the wildcards to behave like this:
     * a subscription to A/# is a subscription to the topic A and all topics beneath A
     * a subscription to A/+ is a subscription to the topics directly beneath, but not A itself
     * a subscription to A/+/# is a subscription to all topics beneath A, but not A itself

While the difference between A/# and A/+ may appear inconsistent, it is consistent with how the two wildcard characters are defined:
\\ # matches zero or more levels
\\ + matches exactly one level

Ultimately, topics are arbitrary strings upon which we have said the '/' has an additional meaning. There is currently no such thing as an invalid topic (assuming it is valid UTF etc) (even an empty string is a valid topic - although whether that should be the case is a separate discussion) (of course it shouldn't contain wildcards unless it is in the context of a subscription) (any more caveats?) (nope).

MQTT v3 only has positive acknowledgements, it would not be possible to inform a client it had sent an invalid topic - so we would have to silently swallow them or kick the client off.

Removing the A/==A equivalence would mean you wouldn't be able to subscribe to A and all of its sub-topics in a single subscription request (A/# as above).

## Duplicate topic separators

The spec isn't clear on how topics/subscriptions with duplicated hierarchy separators should be handled, i.e. `////some////over/slashed///topic/etc/etc`

Both rsmb and mosquitto treat duplicate separators as single separators, i.e. `/some/over/slashed/topic/etc/etc`

## Topic Length

Appendix A says topics are limited to 64k. Section 2.2 says the topic is limited to 32k.

As topics are encoded using two bytes to represent length, that means the true limit is 64k. Section 2.2 needs to be corrected.
