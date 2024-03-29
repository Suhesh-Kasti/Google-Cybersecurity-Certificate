- A **network protocol analyzer (packet sniffer)** is a tool designed to capture and analyze data traffic within a network.
    
- **Packet sniffing** is the practice of capturing and inspecting data packets across a network. 
     
## What is tcpdump?

**Tcpdump** is a command-line network protocol analyzer. Recall that a **command-line interface (CLI)** is a text-based user interface that uses commands to interact with the computer. 

Tcpdump is used to capture network traffic. This traffic can be saved to a **packet capture (p-cap)**, which is a file containing data packets intercepted from an interface or network. The p-cap file can be accessed, analyzed, or shared at a later time. Analysts use tcpdump for a variety of reasons, from troubleshooting network issues to identifying malicious activity. Tcpdump comes pre-installed in many Linux distributions and can also be installed on other Unix-based operating systems such as macOS®. 

**Note**: It's common for network traffic to be encrypted, which means data is encoded and unreadable. Inspecting the network packets might require decrypting the data using the appropriate private keys. 

## Capturing packets with tcpdump

A Linux **root user (or superuser)** has elevated privileges to modify the system. The **sudo** command temporarily grants elevated permissions to specific users in Linux. Like many other packet sniffing tools, we’ll need to have administrator-level privileges to capture network traffic using tcpdump. This means we will need to either be logged in as the root user or have the ability to use the sudo command. Here is a breakdown of the tcpdump syntax for capturing packets:

sudo tcpdump [-i interface] [option(s)] [expression(s)]

- The sudo tcpdump command begins running tcpdump using elevated permissions as sudo. 
    
- The -i parameter specifies the network interface to capture network traffic. we must specify a network interface to capture from to begin capturing packets. For example, if we specify *-i any* we’ll sniff traffic from all network interfaces on the system. 
    
- The option(s) are optional and provide us with the ability to alter the execution of the command. The expression(s) are a way to further filter network traffic packets so that we can isolate network traffic. 

**Note**: Before we can begin capturing network traffic, we must identify which network interface we'll want to use to capture packets from. we can use the -D flag to list the network interfaces available on a system.

## Options

With tcpdump, we can apply options, also known as flags, to the end of commands to filter network traffic. Short options are abbreviated and represented by a hyphen and a single character like -i. Long options are spelled out using a double hyphen like --interface. Tcpdump has over fifty options that we can explore using [the manual page](https://www.tcpdump.org/manpages/tcpdump.1.html)

**Note**: Options are case sensitive. For example, a lowercase -w is a separate option with a different use than the option with an uppercase -W.

**Note**: tcpdump options that are written using short options can be written with or without a space between the option and its value. For example, sudo tcpdump -i any -c 3 and sudo tcpdump -iany -c3 are equivalent commands.

### **-w**

Using the -w flag, we can write or save the sniffed network packets to a packet capture file instead of just printing it out in the terminal. This is very useful because we can refer to this saved file for later analysis. In this command, tcpdump is capturing network traffic from all network interfaces and saving it to a packet capture file named packetcapture.pcap:

##### sudo tcpdump -i any -w packetcapture.pcap

### **-r**

Using the -r flag, we can read a packet capture file by specifying the file name as a parameter. Here is an example of a tcpdump command that reads a file called packetcapture.pcap:

##### sudo tcpdump -r packetcapture.pcap

### **-v**
Packets contains a lot of information. By default, tcpdump will not print out all of a packet's information. This option, which stands for verbose, lets us control how much packet information we want tcpdump to print out.

There are three levels of verbosity we can use depending on how much packet information we want tcpdump to print out. The levels are -v, -vv, and -vvv. The level of verbosity increases with each added v. The verbose option can be helpful if we’re looking for packet information like the details of a packet’s IP header fields. Here’s an example of a tcpdump command that reads the packetcapture.pcap file with verbosity:

### sudo tcpdump -r packetcapture.pcap -v

### **-c**

The -c option stands for count. This option lets we control how many packets tcpdump will capture. For example, specifying -c 1 will only print out one single packet, whereas -c 10 prints out 10 packets. This example is telling tcpdump to only capture the first three packets it sniffs from any network interface:

### sudo tcpdump -i any -c 3

### **-n**  

By default, tcpdump will perform name resolution. This means that tcpdump automatically converts IP addresses to names. It will also resolve ports to commonly associated services that use these ports. This can be problematic because tcpdump isn’t always accurate in name resolution. For example, tcpdump can capture traffic from port 80 and automatically translates port 80 to HTTP in the output. However, this is misleading because port 80 isn’t always going to be using HTTP; it could be using a different protocol.

Additionally, name resolution uses what’s known as a reverse DNS lookup. *A reverse DNS lookup is a query that looks for the domain name associated with an IP address*. If we perform a reverse DNS lookup on an attacker’s system, they might be alerted that we are investigating them through their DNS records.

Using the -n flag disables this automatic mapping of numbers to names and is considered to be best practice when sniffing or analyzing traffic. Using -n will not resolve hostnames, whereas -nn will not resolve _both_ hostnames or ports. Here’s an example of a tcpdump command that reads the packetcapture.pcap file with verbosity and disables name resolution:

##### sudo tcpdump -r packetcapture.pcap -v -n

**Pro tip:** we can combine options together. For example, -v and -n can be combined as -vn. But, if an option accepts a parameter right after it like -c 1 or -r capture.pcap then we can’t combine other options to it.

## Expressions

Using filter expressions in tcpdump commands is also optional, but knowing how and when to use filter expressions can be helpful during packet analysis. There are many ways to use filter expressions. 

If we want to specifically search for network traffic by protocol, we can use filter expressions to isolate network packets. For example, we can filter to find only IPv6 traffic using the filter expression ip6.

we can also use boolean operators like and, or, or not to further filter network traffic for specific IP addresses, ports, and more. The example below reads the packetcapture.pcap file and combines two expressions ip and port 80 using the and boolean operator:

##### sudo tcpdump -r packetcapture.pcap -n 'ip and port 80'

**Pro tip:** we can use single or double quotes to ensure that tcpdump executes all of the expressions. we can also use parentheses to group and prioritize different expressions. Grouping expressions is helpful for complex or lengthy commands. For example, the command ip and (port 80 or port 443) tells tcpdump to prioritize executing the filters enclosed in the parentheses before filtering for IPv4.

## Interpreting output

Once we run a command to capture packets, tcpdump will print the output of the command as the sniffed packets. In the output, tcpdump prints one line of text for each packet with each line beginning with a timestamp. Here’s an example of a command and output for a single TCP packet: 

###### sudo tcpdump -i any -v -c 1

This command tells tcpdump to capture packets on -i any network interface. The option -v prints out the packet with detailed information and the option -c 1 prints out only one packet. Here is the output of this command: 

![Sortie d'une commande tcpdump avec des étiquettes pour l'horodatage, l'adresse IP source, le port source, l'adresse IP de des](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/3LnHDkkeQ2-a-KjHKXkBCQ_940eb009d1674c7595f8361adf48c1f1_89by7cw_y0GWsyGI4iK19PqNyVHpVO4reyeIO0v-xYeZDBID0JG0PzpqRSA7fWjmD88HKjaZ8PhlONjdsKMLrUlx0lM9lPGBVSNqO87rZPPHt00BahLIQmfBNpRTyBAgjUklW2nn3hCB5Z-x_0HC56AKW7g2hk4tXgWyjInXVJYMosY9D4pyuX2VzerrhA?expiry=1695168000000&hmac=vhRGngMtOWVjFnb9TcXfgSwyxX74VAOWtlPuY1Mwe9g)

1. **Timestamp**: The output begins with the timestamp, which starts with hours, minutes, seconds, and fractions of a second. 
    
2. **Source IP:** The packet’s origin is provided by its source IP address.
    
3. **Source port:** This port number is where the packet originated.
    
4. **Destination IP:** The destination IP address is where the packet is being transmitted to.
    
5. **Destination port:** This port number is where the packet is being transmitted to.
    

The remaining output contains details of the TCP connection including flags and sequence number. The options information is additional packet information that the  -v option has provided.