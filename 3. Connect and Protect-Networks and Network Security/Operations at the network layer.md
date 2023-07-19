Functions at the network layer organize the addressing and delivery of data packets across the network and internet from the host device to the destination device. This includes directing the packets from one router to another router across the internet, based on the internet protocol (IP) address of the destination network. The destination IP address is contained within the header of each data packet. This address will be stored for future routing purposes in  routing tables along the packet’s path to its destination.

All data packets include an IP address; this is referred to as an IP packet or datagram. A router uses the IP address to route packets from network to network based on information contained in the IP header of a data packet. Header information communicates more than just the address of the destination. It also includes information such as the source IP address, the size of the packet, and which protocol will be used for the data portion of the packet. 

## Format of an IPv4 packet

![An IP packet divided into two parts: a section on the left marked “header,” and section on the right marked “data”](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/XYVgpBoaQ12ra83WbLw5fg_6fbd3ca7d6b9433ba8dfa8712c89fdf1_CS_R-044_IP-packet-header-and-data.png?expiry=1689897600000&hmac=2v2Llc0v6QFJv6ugrsWoL90VzZiv3uCu2bqcTlCgjtw)

Next, you can review the format of an IP version 4 (IPv4) packet and review a detailed graphic of the packet header. An IPv4 packet is made up of two sections, the header and the data:

- The size of the IP header ranges from 20 to 60 bytes. The header includes the IP routing information that devices use to direct the packet. The format of an IP packet header is determined by the IPv4 protocol.
    
- The length of the data section of an IPv4 packet can vary greatly in size. However, the maximum possible size of an IP packet is 65,536 bytes. It contains the message being transferred to the transmission, like website information or email text.
    

![Diagram of an IPv4 packet header 13 fields and bit size](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/pLNClMeQTaOZkEzun-CKVw_0c6ca1eb0acd43c88ba90fbb09ce67f1_CS_R-044_Pv4-packet-header-14-field.png?expiry=1689897600000&hmac=Nsheronga7gqsL-g5DtDXWPFCdrdU6MqlxUN_q8vRaE)

There are 13 fields within the header of an IPv4 packet:

- **Version:** The first 4-bit header tells receiving devices what protocol the packet is using. The packet used in the illustration above is an IPv4 packet.
    
- **IP Header Length (HLEN):** HLEN is the packet’s header length. This value indicates where the packet header ends and the data segment begins. 
    
- **Type of Service (ToS):** Routers prioritize packets for delivery to maintain quality of service on the network. The ToS field provides the router with this information.
    
- **Total Length:** This field communicates the total length of the entire IP packet, including the header and data. The maximum size of an IPv4 packet is 65,535 bytes.
    
- **Identification:** For IPv4 packets that are larger than 65, 535 bytes, the packets are divided, or fragmented, into smaller IP packets. The identification field provides a unique identifier for all the fragments of the original IP packet so that they can be reassembled once they reach their destination. 
    
- **Flags:** This field provides the routing device with more information about whether the original packet has been fragmented and if there are more fragments in transit.
    
- **Fragmentation Offset:** The fragment offset field tells routing devices where in the original packet the fragment belongs.
    
- **Time to Live (TTL):** TTL prevents data packets from being forwarded by routers indefinitely. It contains a counter that is set by the source. The counter is decremented by one as it passes through each router along its path. When the TTL counter reaches zero, the router currently holding the packet will discard the packet and return an ICMP Time Exceeded error message to the sender. 
    
- **Protocol:** The protocol field tells the receiving device which protocol will be used for the data portion of the packet.
    
- **Header Checksum:** The header checksum field contains a checksum that can be used to detect corruption of the IP header in transit. Corrupted packets are discarded.
    
- **Source IP Address:** The source IP address is the IPv4 address of the sending device.
    
- **Destination IP Address:** The destination IP address is the IPv4 address of the destination device.
    
- **Options:** The options field allows for security options to be applied to the packet if the HLEN value is greater than five. The field communicates these options to the routing devices.
    

## Difference between IPv4 and IPv6

In an earlier part of this course, you learned about the history of IP addressing. As the internet grew, it became clear that all of the IPv4 addresses would eventually be depleted; this is called IPv4 address exhaustion. At the time, no one had anticipated how many computing devices would need an IP address in the future. IPv6 was developed to mitigate IPv4 address exhaustion and other related concerns. 

One of the key differences between IPv4 and IPv6 is the length of the addresses. IPv4 addresses are numeric, made of 4 bytes, and allow for up to 4.3 billion possible addresses. IPv4 addresses are made up of four strings and the numbers range from 0 to 255. An example of an IPv4 address would be: 198.51.100.0. IPv6 addresses are hexadecimal, made up of 16 bytes, and allow for up to 340 undecillion addresses (340 followed by 36 zeros). An example of an IPv6 address would be: 2002:0db8:0000:0000:0000:ff21:0023:1234.

There are also some differences in the layout of an IPv6 packet header. The IPv6 header format is much simpler than IPv4. For example, the IPv4 Header includes the HLEN, Identification, and Flags fields, whereas the IPv6 does not. The IPv6 header introduces different fields not included in IPv4 headers, such as the Flow Label and Traffic Class.  

![Side by side diagrams of an IPv4 packet header and a simplified IPv6 packet](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/PNld6YkmQNWyhZjFFHvC-Q_eb474e5ee3b3416fbc06a639503342f1_CS_R-044_IPv4-and-IPv6.png?expiry=1689897600000&hmac=NqwWrOEip5wD5mDdjCpxdQ1zHylc0SCcETJ0_vFp7gA)

There are some important security differences between IPv4 and IPv6. IPv6 offers more efficient routing and eliminates private address collisions that can occur on IPv4 when two devices on the same network are attempting to use the same address.