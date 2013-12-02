An application created a topic and "left" a retained publication on it - but you no longer want that topic to exist.

The solution depends on the broker, but several brokers support the following:

Publish a message with an empty payload and the retained flag set.
This clears any previously retained message on that topic.

Is this a security issue? Not necessarily, but if you don't want "just any" client to be able to do this then it is possible to use ACLs to control who can publish on a topic.

There's a [mailing list discussion on this topic](https///groups.google.com/d/topic/mqtt/EvWKV5eUF_o/discussion).
