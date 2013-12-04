### Principles and Assumptions

MQTT was designed for low-bandwidth, high latency networks in the late 1990s/early 2000s. As a result, the designers made a number of key choices which influenced the way it "looks and feels".

 1.  Simplicity, simplicity, simplicity! Don't add too many "bells and whistles" but provide a solid building block which can easily be integrated into other solutions. Be simple to implement.
 2.  Publish/subscribe messaging. Useful for most sensor applications, and enables devices to come online and publish "stuff" that hasn't been previously known about or predefined.
 3.  Zero administration (or as close as possible). Behave sensibly in response to unexpected actions and enable applications to "just work" e.g. dynamically create topics when needed.
 4.  Minimise the on-the-wire footprint. Add an absolute minimum of data overhead to any message. Be lightweight and bandwidth efficient.
 5.  Expect and cater for frequent network disruption (for low bandwidth, high latency, unreliable, high cost-to-run networks)... -> Last Will and Testament
 6.  Continuous session awareness -> Last Will and Testament
 7.  Expect that client applications may have very limited processing resources available. 
 8.  Provide traditional messaging qualities of service where the environment allows. Provide "quality of service" 
 9.  Data agnostic. Don't mandate content formats, remain flexible.
