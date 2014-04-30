# Purpose of this document

This page is meant to be find a common view on MQTT $SYS. At the moment, many broker implementations implement some kind of $SYS topic but there isn't a common definition of required and optional $SYS topics for broker implementations yet. 

# Definitions
* **Static** Topics: Messages on a static $SYS topic are not required to be sent on every $SYS topic update interval
* **Required** Topics: Every broker which claims to support the $SYS topics must support these topics. 
* **Optional** Topics: A broker implementation may decide if
