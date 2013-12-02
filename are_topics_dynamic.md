## Topics - are they dynamic?

One of the [design principles](design principles) of MQTT is that it should be "zero-admin" (as far as possible).

Therefore, topics on a broker are always expected to be "dynamic" and to require no administrative setup.

i.e. a client subscribes on topic x without knowing whether it exists; it doesn't, so broker silently creates that topic; and the client receives publications on that topic, should they be sent (which, of course, in a pub/sub world, they may never be).

Here's [a discussion of this subject on the mailing list](https///groups.google.com/d/topic/mqtt/YWvg62LTbLE/discussion). A future or clarified version of the specification may make this explicit.


It remains a question of whether this should be a requirement or a recommendation. I think making this a requirement would potentially be restrictive to those adding MQTT support to their existing systems. But dynamic topics are very much in the spirit and ethos of MQTT  --- //[Nick O'Leary](nick.oleary@gmail.com) 2012/01/31 15:25//
