This page exists to document things that are not part of the formal specification but which are widely used or agreed upon.

## $SYS

The specification says nothing about the particulars of the topic tree beyond delimiters, wildcards, and min/max length.

Both the RSMB and mosquitto brokers have created a $SYS topic space for "internal" or system-monitoring and statistic topics. This is generally a "read only" space for client applications but is used to provide useful information about e.g. how many clients are connected, broker version, etc etc. 

There's no defined format (although the mosquitto documentation is very clear about the $SYS topics it provides).

There is no requirement that all brokers implement $SYS but this has become a common pattern.
