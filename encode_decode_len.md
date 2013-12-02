## Encoding and decoding the message lengths

The variable length encoding scheme uses a single byte for messages up to 127 bytes long. Longer messages are handled as follows. Seven bits of each byte encode the Remaining Length data, and the eighth bit indicates any following bytes in the representation. Each byte encodes 128 values and a "continuation bit". For example, the number 64 decimal is encoded as a single byte, decimal value 64, hex 0x40. The number 321 decimal (= 65 + 2*128) is encoded as two bytes, least significant first. The first byte 65+128 = 193. Note that the top bit is set to indicate at least one following byte. The second byte is 2.

The protocol specification has an example of how to do the length encoding/decoding but in some languages that can be a difficult function to implement.

Here's a working example in REXX.

	
	mqtt_length_encode: procedure
	
	   x = arg(1)
	   remlen = ""
	   do while(x > 0)
	
	      digit = x // 128
	      x = x % 128
	
	      if x > 0 then digit = digit + 128
	      remlen = remlen || d2x(digit) 
	
	   end
	
	   return x2c(remlen)
	`</code>`((d2x(decimal) converts a decimal value to hex.))
	
	`<code>`
	mqtt_length_decode: procedure
	
	   remlen = arg(1)
	   digits = c2x(remlen)
	
	   multiplier = 1
	   value = 0
	   done = 0
	   offset = 2
	   do i = 1 to length(digits) by 2
	
	      digit = x2d(substr(digits,i,2))
	      if digit > 128 then digit = digit - 128
	      else done = 1
	      value = value + (digit * multiplier)
	      if done = 1 then leave
	      multiplier = multiplier * 128
	      offset = offset + 1
	   end
	   ret = value offset
	   return ret
	`</code>`((x2d(hex) converts a hex value to decimal.))
	