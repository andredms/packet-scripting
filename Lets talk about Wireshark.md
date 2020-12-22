# Wireshark

### Shit you should know

1. File -> Export -> Objects -> HTTP
	- Yeet those objects from the port 80 traffic, good to see if someone is brute forcing
2. String frame searching `frame contains flag` and the base64 encoded forms as well.
	- Meaning like the start of a flag format could be `pix_CtF{` you should also check `cGl4X0N0Rg==` or similar
3. `pkt_comment` -> Sometimes people are lazy and leave interesting information behind.

4. Decrypting SSL/TLS Traffic should you somehow get a key
	- -> Edit -> Preferences -> RSA Keys -> Add new keyfile...
