# Miscellaneous clarifications

A collection of clarifications that don't warrant entire pages on their own.

##### 2.2 Variable Header - Will Flag

The term "Last Will and Testament" is used in the abstract, but nowhere else. It should be used in other sections (such as 2.2) to tie the concepts together.

##### 3.3 Publish - Variable Header

The example table includes a row for QoS level - but that isn't a field that is part of the variable header of a PUBLISH. The level is included in the table to show it is qos 1, hence the MessageID is included in the variable header.
This could be made a bit clearer.
It should also be made clearer that the fixed header format here is only an example - QoS does not always have to be equal to 1.
