Whether it's an employee sending an email or a malicious actor attempting to exfiltrate confidential data, actions that are performed on a network can be identified through examining network traffic flows. Understanding these network communications provides valuable insight into the activities happening in a network. This way, we can better understand what's going on in an environment and defend against potential threats.

### How to record network traffic through packet captures
When data is sent, it's divided into packets. Just like an addressed envelope in the mail, *packets contain delivery information* which is used to route it to its destination.
This information includes a sender and receiver's IP address, the type of packet that's being sent, and more. *Packets can provide lots of information about the communications happening between devices over a network*.
You may also recall that a packet has multiple components. There's the header, which includes information like the type of network protocol and port being used. Imagine this as being the name and mailing address located on an envelope.

**Network protocols** are a set of rules that determine the transmission of data between devices on a network. Ports are non-physical locations on a computer that organize data transmission between devices on a network.
The *header also contains the packet's source and destination IP address*. We'll explore more information contained in the header in a later section.

Next, there's the **payload**, which contains the actual data that's being delivered. This is like the content of a letter inside of an envelope. And there's the footer, which signifies the end of the packet.
So how exactly can you observe a network packet? Just like scents are invisible but can be smelled, packets are invisible but can be captured using tools called packet sniffers.
A **network protocol analyzer, or packet sniffer**, is a tool designed to capture and analyze data traffic within a network. 
Through packet sniffing, we can grab a detailed snapshot of packets that travel over a network in the form of a packet capture. A **packet capture, or P-cap**, is a file containing data packets intercepted from an interface or network. It's sort of like intercepting an envelope in the mail.
Packet captures are incredibly useful during incident investigation. By having access to the *communications happening between devices over a network*, we can observe network interactions and start to build a storyline to determine what exactly happened.

# More about packet captures

The role of security analysts involves monitoring and analyzing network traffic flows. One way to do this is by generating packet captures and then analyzing the captured traffic to identify unusual activity on a network.
## Packets
A **data packet** is a basic unit of information that travels from one device to another within a network. *Detecting network intrusions begins at the packet level*. That's because packets form the basis of information exchange over a network. Each time we perform an activity on the internet—like visiting a website—packets are sent and received between your computer and the website’s server. These packets are what help transmit information through a network. For example, when uploading an image to a website, the data gets broken up into multiple packets, which then get routed to the intended destination and reassembled upon delivery. 

In cybersecurity, packets provide valuable information that helps add context to events during investigations. Understanding the transfer of information through packets will not only help you develop insight on network activity, it will also help you identify abnormalities and better defend networks from attacks.
Packets contain three components: *the header*, *the payload*, and *the footer* viz..

### Header

Packets begin with the most essential component: the header. Packets can have several headers depending on the protocols used such as an Ethernet header, an IP header, a TCP header, and more. Headers provide information that’s used to route packets to their destination. This includes information about the source and destination IP addresses, packet length, protocol, packet identification numbers, and more.

An IPv4 header with the information it provides:

![An IPv4 header with its thirteen fields](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Mi_kryGkRiyYUOJDIwnPCw_ac942d1eec284467a5ca533cb99c4bf1_S20G003.png?expiry=1691884800000&hmac=rBklXd4q-JUfXmouZwUut1bHjDhmTs6lgAZKHwiVRVc)

### Payload

The payload component directly follows the header and contains the actual data being delivered. Think back to the example of uploading an image to a website; the payload of this packet would be the image itself.

### Footer

The footer, also known as the trailer, is located at the end of a packet. The Ethernet protocol uses footers to provide error-checking information to determine if data has been corrupted. In addition, Ethernet network packets that are analyzed might not display footer information due to network configurations.

**Note:** Most protocols, such as the Internet Protocol (IP), _do not_ use footers.

## Network protocol analyzers

**Network protocol analyzers** **(packet sniffers)** are tools designed to capture and analyze data traffic within a network. Examples of network protocol analyzers include tcpdump, Wireshark, and TShark. 

Beyond their use in security as an investigative tool used to monitor networks and identify suspicious activity, network protocol analyzers can be used to collect network statistics, such as bandwidth or speed, and troubleshoot network performance issues, like slowdowns. 

Network protocol analyzers can also be used for malicious purposes. For example, malicious actors can use network protocol analyzers to capture packets containing sensitive data, such as account login information.

Here’s a network diagram illustrating how packets get transmitted from a sender to the receiver. A network protocol analyzer is placed in the middle of the communications to capture the data packets that travel over the wire.

![Computer A sends data packets to Computer B. The network protocol analyzer is located in the middle of the network’s path.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/EjVePDcSRvmzvvtk8lQlXw_43c1eaf1c9f3444e99c62361ecd078f1_S29G004.png?expiry=1691884800000&hmac=slIWg2ShBS4XA9BvE9WpiKwp4Ur62TvyweaNophcuII)

### How network protocol analyzers work

Network protocol analyzers use both software and hardware capabilities to capture network traffic and display it for security analysts to examine and analyze. Here’s how:

1. First, packets must be collected from the network via the **Network Interface Card (NIC)**, which is hardware that connects computers to a network, like a router. NICs receive and transmit network traffic, but by default they only listen to network traffic that’s addressed to them. To capture all network traffic that is sent over the network, a NIC must be switched to a mode that has access to all visible network data packets. In wireless interfaces this is often referred to as monitoring mode, and in other systems it may be called promiscuous mode. This mode enables the NIC to have access to all visible network data packets, but it won’t help analysts access all packets across a network. A network protocol analyzer must be positioned in an appropriate network segment to access all traffic between different hosts.
    
2. The network protocol analyzer collects the network traffic in raw binary format. Binary format consists of 0s and 1s and is not as easy for humans to interpret. The network protocol analyzer takes the binary and converts it so that it’s displayed in a human-readable format, so analysts can easily read and understand the information.  
    

### Capturing packets

**Packet sniffing** is the practice of capturing and inspecting data packets across a network. A **packet capture (p-cap)** is a file containing data packets intercepted from an interface or network. Packet captures can be viewed and further analyzed using network protocol analyzers. For example, you can filter packet captures to only display information that's most relevant to your investigation, such as packets sent from a specific IP address.

**Note**: Using network protocol analyzers to intercept and examine private network communications without permission is considered illegal in many places.

P-cap files can come in many formats depending on the packet capture library that’s used. Each format has different uses and network tools may use or support specific packet capture file formats by default. You should be familiar with the following libraries and formats:

1. **Libpcap** is a packet capture library designed to be used by Unix-like systems, like Linux and MacOS®. Tools like tcpdump use Libpcap as the default packet capture file format. 
    
2. **WinPcap** is an open-source packet capture library designed for devices running Windows operating systems. It’s considered an older file format and isn’t predominantly used.
    
3. **Npcap** is a library designed by the port scanning tool Nmap that is commonly used in Windows operating systems.
    
4. **PCAPng** is a modern file format that can simultaneously capture packets and store data. Its ability to do both explains the “ng,” which stands for “next generation.”
    

**Pro tip:** Analyzing your home network can be a good way to practice using these tools.

## Interpret network communications with packets

If a packet capture is like intercepting an envelope in the mail, then packet analysis is like reading the letter inside of the envelope. We know that, networks are noisy. There's an enormous volume of communications happening between devices at any given time. And because of this, packet captures can contain large amounts of network communications, making analysis challenging and time-consuming.

As a security professional, you'll be working against the clock to protect networks and computer systems from potential attacks. You may analyze network evidence in the form of packet captures to identify indicators of compromise. Having the ability to filter network traffic using packet sniffers to gather relevant information is an essential skill to have. For example, let's say that you were tasked with analyzing a packet capture to find any indication of data exfiltration. How would you go about this?

Using a network analyzer tool, you can filter the packet capture to sort packets. This can help you quickly identify an event associated with data exfiltration, like large amounts of data leaving a database. There are many other filters you can apply to packet captures to find the information you need to support an investigation efficiently.

Examples of network analyzer tools include tcpdump and Wireshark. tcpdump is accessed through a command line while Wireshark has a graphical user interface, or GUI. Both tools are useful for security analysts, and soon you'll have the opportunity to explore both.