# Extended ClientID


The current specification only allows 23 UTF8 chars in a client ID. This should possibly be changed to a recommendation rather than a requirement.

While this legitimately allows for an amazingly large number of unique client ID's (6,132,610,415,680,998,648,960 or so), I think we can expect that in practice people will want to use a more meaningful/readable client ID.  

It is not hard to imagine scenarios where client IDs longer than 23 chars would be very useful.

Neither mosquitto nor rsmb reject clients that connect with an ID longer than 23 characters.
