### Avoiding PCAP tools altogether
Sometimes it can be easy to just run a quick. . .

>`strings capture.pcap | grep -i flag`

If you just want to try to extract any files within the PCAP without using Wireshark by just taking advantage of binwalk

>`binwalk -e capture.pcap`

