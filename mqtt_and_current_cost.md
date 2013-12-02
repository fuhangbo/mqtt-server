# Current Cost Meters and MQTT Systems

[Current Cost](http://currentcost.com) meters publish XML data every 6 seconds. How is that information parsed, stored, re-read, re-published?

Probably the best way to do this is to not try to do too many things in one go. Think in terms of clients that publish, clients that subscribe and clients that process and re-publish.
 
You can read the XML data from the Current Cost and publish it as-is. This means that all of the information becomes available to any subscribers to do with as they please. The [mosquitto](mosquitto_message_broker) repository has examples of doing this in [Perl](http://bitbucket.org/oojah/mosquitto/src/tip/misc/currentcost/cc128_read.pl) and [Python](http://bitbucket.org/oojah/mosquitto/src/tip/misc/currentcost/cc128_read.py).

The second part of the puzzle is to process the data and re-publish it. This extracts the interesting information and presents it in a friendlier manner. For the Current Cost data, for example, this could mean separating out the temperature data and data for each of the monitor channels and publishing them on their own topics whilst ignoring any of the long-term sensor data. The mosquitto repository has an example of this in [perl](http://bitbucket.org/oojah/mosquitto/src/tip/misc/currentcost/cc128_parse.pl).

The final stage is storage. Because the sensor data is now on separate topics, it is easy to make a generic client to subscribe to an appropriate topic and store the data in some way, assuming the incoming data format is consistent across topics. This may be to a MySQL database, or to [Pachube](mqtt_and_pachube), as demonstrated in [this simple perl example](http://bitbucket.org/oojah/mosquitto/src/tip/misc/pachube_update.pl).

## example application

*  [CurrentCostGUI](https///code.google.com/p/currentcostgui/wiki/MQTT) on Google Code
