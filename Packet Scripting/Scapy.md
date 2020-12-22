# Scapy 
_(from scapy.all import *)_
#### _Purpose:_
- Send, sniff and dissect network packets




### Examples of Scapy Data Extraction

```
from scapy.all import *

packets = rdpcap('data.pcap')

with open('out.raw', 'wb') as f:
    for p in packets:
        if UDP in p:
            chunk = bytes(p[Raw])
            f.write(chunk)
```