# Overlapping Topics

## Scenario 1

(all commands are sent by the same client):
 1.  Subscribe to A/#
 2.  Subscribe to A/B
 3.  Publish message M to topic A/B

The client will receive the message once.

## Scenario 2

(all commands are sent by the same client):
 1.  Publish message M1 to topic A/B with retain
 2.  Publish message M2 to topic A/C with retain
 3.  Publish message M3 to topic A/D with retain
 4.  Subscribe to A/#

The client will receive all three of the retained messages.

## Scenario 3

Given the topic tree: 
   test
   test/one 
   test/two/two

   - Subscribe to test/#
   - Unsubscribe from test/one
   - Unsubscribe from test/two

The client will still receive messages sent to test/one and test/two. You can only unsubscribe from a topic you have explicitly subscribed to; you cannot punch holes in previous subscription.
