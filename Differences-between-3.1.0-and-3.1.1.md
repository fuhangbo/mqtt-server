Differences between 3.1.0 and 3.1.1:

1. Protocol name has changed
2. Protocol level has changed
3. Client IDs MAY contain more than 23 encoded bytes.
4. Client IDs MAY be empty
5. Client IDs MUST actually be UTF-8
6. Client ID is now restricted to only alphanumeric characters
7. "session present" flag added to CONNACK
8. concept of a failed subscription in a SUBACK
9. validate that topics are correct UTF-8
