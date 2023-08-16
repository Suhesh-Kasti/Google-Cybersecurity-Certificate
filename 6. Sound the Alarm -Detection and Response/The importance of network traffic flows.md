In many organizations, network communication travels over multiple networks in different countries and across different devices. Data can get unintentionally sent and stored in insecure places, like personal email inboxes or cloud storage platforms. Users trust that their data is safely and securely sent and stored. And it's the job of security professionals like us to help protect these communications in transit and at rest.

### So what is network traffic? 
**Network traffic** is the amount of data that moves across a network. 
**Network data** is the data that's transmitted between devices on a network.

Depending on the size of a network, there can be a huge volume of network traffic at any given moment. For example, in a large, multinational organization, there may be thousands of employees sending and receiving emails at any given time. That's a lot of network traffic. With such large volumes of traffic being produced, how do we know what's normal behavior, or what's unusual and requires investigation as a potential security incident? We can detect traffic abnormalities through observation to spot **indicators of compromise**, also known as IoC, which are observable evidence that suggests signs of a potential security incident.

Take, for instance, **data exfiltration**, which is the unauthorized transmission of data from a system. Attackers use *data exfiltration to steal or leak data such as user names, passwords, or intellectual property*. By observing network traffic, we can determine if there's any indicators of compromise, such as large volumes of outbound traffic leaving a host. This is a sign of possible data exfiltration which can be further investigated.

# Maintain awareness with network monitoring

Network communication can be noisy! Events like sending an email, streaming a video, or visiting a website all produce network communications in the form of network traffic and network data. As a reminder, **network traffic** is the amount of data that moves across a network. It can also include the type of data that is transferred, such as HTTP. **Network** **data** is the data that's transmitted between devices on a network.

Network monitoring is essential in maintaining situational awareness of any activity on a network. By collecting and analyzing network traffic, organizations can detect suspicious network activity. But before networks can be monitored, you must know exactly what to monitor. In this reading, you'll learn more about the importance of network monitoring, ways to monitor your network, and network monitoring tools.

## Know your network

As you’ve learned, networks connect devices, and devices then communicate and exchange data using network protocols. Network communications provide information about connections such as source and destination IP addresses, amount of data transferred, date and time, and more. This information can be valuable for security professionals when developing a **baseline** of normal or expected behavior. 

![Line graph displaying a baseline running through the middle of data peaks.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/R-C-xmdWTRe8XfbJ4V9BMg_01d033967efe41ba898db5755db1f4f1_i-QtA3HA4BNT_yYXJ-qbty4-R8tuDG73XRllvRqnBMgcopHG7JmrlZYtjv-Jeorch1-w-rQhfh9u1ObkqF6KNsslNqhqyacRusAj38ehIjgImRN2lSB6DQ49MsFJCYgPdG2iBrOt-HEU99JuvC-070uPrh1M9UxFjb-Hvmfaa4yaGyn5kno71tlvVr_xgg?expiry=1691884800000&hmac=EWyDNjKw0V__gZSMg9YOW4RX9Io9Wuh2vVAV6087PjE)

A baseline is a reference point that’s used for comparison. You've probably encountered or used baselines at some point. For example, a grocery amount for a personal budget is an example of a baseline that can be used to help identify any patterns or changes in spending habits. In security, baselines help establish a standard of expected or normal behavior for systems, devices, and networks. Essentially, by knowing the baseline of _normal_ network behavior, you'll be better able to identify _abnormal_ network behavior.

## Monitor your network

Once you’ve determined a baseline, you can monitor a network to identify any deviations from that baseline. Monitoring involves examining network components to detect unusual activities, such as large and unusual data transfers. Here are examples of network components that can be monitored to detect malicious activity:

### **Flow analysis**

Flow refers to the movement of network communications and includes information related to packets, protocols, and ports. Packets can travel to ports, which receive and transmit communications. Ports are often, but not always, associated with network protocols. For example, port 443 is commonly used by HTTPS which is a protocol that provides website traffic encryption.

However, malicious actors can use protocols and ports that are not commonly associated to maintain communications between the compromised system and their own machine. These communications are what’s known as **command and control (C2)**, which are the techniques used by malicious actors to maintain communications with compromised systems.

For example, malicious actors can use HTTPS protocol over port 8088 as opposed to its commonly associated port 443 to communicate with compromised systems. Organizations must know which ports should be open and approved for connections, and watch out for any mismatches between ports and their associated protocols.

### **Packet payload information**

Network packets contain components related to the transmission of the packet. This includes details like source and destination IP address, and the packet payload information, which is the actual data that’s transmitted. Often, this data is encrypted and requires decryption for it to be readable. Organizations can monitor the payload information of packets to uncover unusual activity, such as sensitive data transmitting outside of the network, which could indicate a possible data exfiltration attack.

### **Temporal patterns**

Network packets contain information relating to time. This information is useful in understanding time patterns. For example, a company operating in North America experiences bulk traffic flows between 9 a.m. to 5 p.m., which is the baseline of normal network activity. If large volumes of traffic are suddenly outside of the normal hours of network activity, then this is considered _off baseline_ and should be investigated.

Through network monitoring, organizations can promptly detect network intrusions and work to prevent them from happening by securing network components.

## Protect your network

In this program, you’ve learned about **security operations centers** (**SOC**) and their role in monitoring systems against security threats and attacks. Organizations may deploy a **network operations center** (**NOC**), which is an organizational unit that monitors the performance of a network and responds to any network disruption, such as a network outage. While a SOC is focused on maintaining the security of an organization through detection and response, a NOC is responsible for maintaining network performance, availability, and uptime. 

![An analyst monitors system activity on multiple computer screens.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/JC9h-84YTn-cwOHf6MXVMg_b307457feef74f0e88f8664100b395f1_JqtN_UgxVYbwkx1IjuMN31PoUM5XlHpZ0M-Z2hBqScuHUv62R7AvZcqAGJGuoDUpYu6MnQiCL0FPB8tspDaKzNRvL6CxZv3oMo5cZfNfql0to1vR8Qt9Zam2ETRZLp_2w66Ah-JzQAF70EQdzN10PqSMOHbomP8LWvk5cigov8vPptnVpNVkzZAcaB_V7Q?expiry=1691884800000&hmac=bEWkO0DBb_5RlX8qTqiAX45-EgALTqbSi_2u7N9PKVk)

Security analysts monitor networks to identify any signs of potential security incidents known as **indicators of compromise** (**IoC**) and  protect networks from threats or attacks. To do this, they must understand the environment that network communications travel through so that they can identify deviations in network traffic. 

### **Network monitoring tools**

Network monitoring can be automated or performed manually. Some common network monitoring tools can include: 

- **Intrusion detection systems** (**IDS**) monitor system activity and alert on possible intrusions. An IDS will detect and alert on the deviations you’ve configured it to detect. Most commonly, IDS tools will monitor the content of packet payload to detect patterns associated with threats such as malware or phishing attempts.
    
- **Network protocol analyzers**, also known as packet sniffers, are tools designed to capture and analyze data traffic within a network. They can be used to analyze network communications manually in detail. Examples include tools such as tcpdump and Wireshark, which can be used by security professionals to record network communications through packet captures. Packet captures can then be investigated to identify potentially malicious activity.