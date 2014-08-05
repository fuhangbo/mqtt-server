Differences between 3.1.0 and 3.1.1:

# Protocol name has changed
# Protocol level has changed
# Client IDs MAY contain more than 23 encoded bytes.
# Client IDs MAY be empty
# Client IDs MUST actually be UTF-8
# Client ID is now restricted to only alphanumeric characters
# "session present" flag added to CONNACK
# concept of a failed subscription in a SUBACK
# validate that topics are correct UTF-8
