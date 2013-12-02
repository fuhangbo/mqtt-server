# Will Message UTF8 Support

With regard to the Will Message, the spec says:

    Although the Will Message is UTF-8 encoded in the CONNECT message,
    when it is published to the Will Topic only the bytes of the message
    are sent, not the first two length bytes. The message must therefore
    only consist of 7-bit ASCII characters.

It is not clear why the requirement exists in the first place. Although the two length bytes are not sent, the length of the payload is known, which provides the same information. It seems like the requirement could be due to the expectation that the Java methods readUTF() and writeUTF() will be used, as mentioned in section 2.5, which seems unnecessarily limiting.

The will message should be treated in the same way as every other payload - just a blob of bytes.

The connect packet can contain a will message (set of bytes) that is encoded as follows: 

*  2 bytes that contain the length of the will message

*  A set of bytes that make up the will message

*  
When the LWAT is published only the set of bytes (not the two byte length) are put into the payload of the publication.
