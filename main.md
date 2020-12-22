# Packet Scripting

# TShark

Command line Wireshark.

### Example

```tshark -r ‘capture.pcap’ -T fields -e ‘ip.src == 192.168.50.1’ ```

Prints out all packet fields with the filter ``ip.src == 192.168.50.1`` applied.

### Flags
>-r: read a .pcap file.


>-T: sets output format (e.g. fields)


>-e: specify filters (e.g. -e ‘ip.src == 192.168.50.1’)

Often, you’ll need to add some extra formatting via piping in ``tr``, ``awk`` or ``xxd`` commands. If you want to get one continuous stream of characters with TShark newline characters will need to be deleted:

```tshark -r ‘capture.pcap’ -T fields -e ‘ip.src== 192.168.50.1’ | tr -d “\n”```

``tr`` stands for ‘text replace’, the ``-d`` flag deletes the character in the next argument (e.g. ‘\n’)

If you want to save data from tshark output simply redirect it:

```tshark -r ‘capture.pcap’ -T fields -e ‘ip.src== 192.168.50.1’ | tr -d “\n” > output.txt```

xxd is also useful for manipulating hex output and format. 

```tshark -r ‘capture.pcap’ -T fields -e ‘ip.src== 192.168.50.1’ | tr -d “\n” | xxd -p -r > output.txt```

>-p removes the line numbers and ASCII decoded hex (super useful!!!) 


>-r turns the hex data into binary (‘reverse’)


# PyShark

# Scapy
