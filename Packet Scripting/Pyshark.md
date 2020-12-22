# PyShark
_(import pyshark)_

#### _Purpose: _
- TShark, but for Python (acts as a wrapper)

Reading .pcap file:
`cap = pyshark.FileCapture(
		“capture.pcap”
		display_filter=[wireshark filter])`

#### Wireshark filters
Regular wireshark filters can be used in `display_filter`, e.g. `tcp.stream eq %d', %i.` This will iterate over all TCP streams when used in a for loop in conjunction with p = cap.next. 

#### Examples:
```icmp && ip.src != 185.245.99.2 && !icmp.resp_not_found
Iterating:
while True
	try:
p = cap.next
except StopIteration:
	break;

Extracting:
output = open('output.txt', 'wb')

```
....
```
try:
	output.write(p.data.data.binary_value)
	except AttributeError:
		pass

Keywords:
	*.binary_value: converts hex to ASCII character
	.data:
	.data.data:
```

