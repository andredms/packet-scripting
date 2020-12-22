# Packet Scripting

# TShark

Command line Wireshark.

## Example (Basics)

```
tshark -r 'capture-1.pcap' -T fields -e data -Y 'ip.src == 192.168.50.1'
```

Prints out all payloads of the packets that come from 192.168.50.1.

### Flags
>-r: read a .pcap file.


>-T: sets output format (e.g. fields)


>-e: specify field to extract (e.g. -e ‘data')


>-Y: specify display filter

Often, you’ll need to add some extra formatting via piping in ``tr``, ``awk``, ``cut`` or ``xxd`` commands. If you want to get one continuous stream of characters with TShark newline characters will need to be deleted:

```
tshark -r 'capture-1.pcap' -T fields -e data -Y 'ip.src == 192.168.50.1' | tr -d '\n'
```

``tr`` stands for ‘text replace’, the ``-d`` flag deletes the character in the next argument (e.g. '\n')

xxd is also useful for manipulating hex output and format. 

```
tshark -r 'capture-1.pcap' -T fields -e data -Y 'ip.src == 192.168.50.1' | tr -d '\n' | xxd -p -r
```

>-p removes the line numbers and ASCII decoded hex (super useful!!!) 


>-r turns the hex data into binary (‘reverse’)

If you want to save data from tshark output simply redirect it:

```
tshark -r 'capture-1.pcap' -T fields -e data -Y 'ip.src == 192.168.50.1' | tr -d '\n' | xxd -p -r > output.txt
```

## Example (DNS)

```
tshark -r 'capture-2.pcap' -T fields -e dns.qry.name -Y 'dns.qry.name contains "apache"' | cut -d. -f1 | tr -d '\n'
```

Prints out all DNS query names if they contain ``apache``. The ``cut`` command the sets the delimiter to '.' via ``-d .`` and ``-f 1`` makes it so only the first element before the first '.' is printed out, in this case, it'd print out subdomains (e.g. **lists**.apache and **bugs**.apache).

![image](https://i.imgur.com/miWUICH.png)

If we were to change this to ``-f 2`` we'd get a different result:

![image](https://i.imgur.com/BvLz63M.png)

# PyShark

# Scapy
