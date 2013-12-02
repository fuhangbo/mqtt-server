A retained message for a specific topic is sent as "last well known" message when a new client connects for the first time (on that topic).
In some scenarious if the retained message is too old, it can be not useful send it to new clients.
It can be useful to set a Time To Live for a retained message, so that it can be deleted when TTL expires.
