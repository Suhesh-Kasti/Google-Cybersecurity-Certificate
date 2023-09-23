[**Suricata**](https://suricata.io/) is an open-source intrusion detection system, intrusion prevention system, and network analysis tool.

### **Suricata features**

There are three main ways Suricata can be used:

- **Intrusion detection system** (**IDS**): As a network-based IDS, Suricata can monitor network traffic and alert on suspicious activities and intrusions. Suricata can also be set up as a host-based IDS to monitor the system and network activities of a single host like a computer.
    
- **Intrusion prevention system** (**IPS**): Suricata can also function as an intrusion prevention system (IPS) to detect and block malicious activity and traffic. Running Suricata in IPS mode requires additional configuration such as enabling IPS mode.
    
- **Network security monitoring** (**NSM**): In this mode, Suricata helps keep networks safe by producing and saving relevant network logs. Suricata can analyze live network traffic, existing packet capture files, and create and save full or conditional packet captures. This can be useful for forensics, incident response, and for testing signatures. For example, you can trigger an alert and capture the live network traffic to generate traffic logs, which you can then analyze to refine detection signatures.
    

## Rules 

Rules or signatures are used to identify specific patterns, behavior, and conditions of network traffic that might indicate malicious activity. The terms rule and signature are often used interchangeably in Suricata. Security analysts use **signatures**, or patterns associated with malicious activity, to detect and alert on specific malicious activity. Rules can also be used to provide additional context and visibility into systems and networks, helping to identify potential security threats or vulnerabilities. 

Suricata uses **signatures analysis**, which is a detection method used to find events of interest. Signatures consist of three components:

#### 1.  Action: 
The **action** is the first part of the signature. It determines the action to take if all conditions are met. Actions differ across network intrusion detection system (NIDS) rule languages, but some common actions are `alert`, `drop`, `pass`, and `reject`.
![[suricataaction.png]]

Using our example, the file contains a single `alert` as the action. The `alert` keyword instructs to alert on selected network traffic. The IDS will inspect the traffic packets and send out an alert in case it matches.

Note that the `drop` action also generates an alert, but it drops the traffic. A `drop` action only occurs when Suricata runs in IPS mode.

The `pass` action allows the traffic to pass through the network interface. The pass rule can be used to override other rules. An exception to a drop rule can be made with a pass rule. For example, the following rule has an identical signature to the previous example, except that it singles out a specific IP address to allow only traffic from that address to pass:
```json
pass http 172.17.0.77 any -> $EXTERNAL_NET any (msg:"BAD USER-AGENT";flow:established,to_server;content:!”Mozilla/5.0”; http_user_agent; sid: 12365; rev:1;)
```

The `reject` action does not allow the traffic to pass. Instead, a TCP reset packet will be sent, and Suricata will drop the matching packet. A TCP reset packet tells computers to stop sending messages to each other.
    
#### 2. Header: 
The next part of the signature is the **header**. The header defines the signature’s network traffic, which includes attributes such as protocols, source and destination IP addresses, source and destination ports, and traffic direction.
![[suricataheader.png]]
The next field after the action keyword is the protocol field. In our example, the protocol is `http`, which determines that the rule applies only to HTTP traffic.

The parameters to the protocol `http` field are `$HOME_NET any -> $EXTERNAL_NET any`. The arrow indicates the direction of the traffic coming from the `$HOME_NET` and going to the destination IP address `$EXTERNAL_NET`.

`$HOME_NET` is a Suricata variable defined in `/etc/suricata/suricata.yaml` that you can use in your rule definitions as a placeholder for your local or home network to identify traffic that connects to or from systems within your organization.

In this lab `$HOME_NET` is defined as the 172.21.224.0/20 subnet.

The word `any` means that Suricata catches traffic from any port defined in the `$HOME_NET` network.

_**Note:** The `$` symbol indicates the start of a variable. Variables are used as placeholders to store values._

So far, we know that this signature triggers an alert when it detects any http traffic leaving the home network and going to the external network.
    
#### 3. Rule options:
The many available **rule options** allow you to customize signatures with additional parameters. Configuring rule options helps narrow down network traffic so you can find exactly what you’re looking for. As in our example, rule options are typically enclosed in a pair of parentheses and separated by semicolons.

Let's further examine the rule options in our example:
![[suricataruleop.png]]
- The `msg:` option provides the alert text. In this case, the alert will print out the text `“GET on wire”`, which specifies why the alert was triggered.
- The `flow:established,to_server` option determines that packets from the client to the server should be matched. (In this instance, a server is defined as the device responding to the initial SYN packet with a SYN-ACK packet.)
- The `content:"GET"` option tells Suricata to look for the word `GET` in the content of the `http.method` portion of the packet.
- The `sid:12345` (signature ID) option is a unique numerical value that identifies the rule.
- The `rev:3` option indicates the signature's revision which is used to identify the signature's version. Here, the revision version is 3.

To summarize, this signature triggers an alert whenever Suricata observes the text `GET` as the HTTP method in an HTTP packet from the home network going to the external network.

Here is an example of a Suricata signature:
![[surictsignture.png]]

Rule options have a specific ordering and changing their order would change the meaning of the rule.

**Note**: The terms rule and signature are synonymous.

**Note:** Rule order refers to the order in which rules are evaluated by Suricata. Rules are processed in the order in which they are defined in the configuration file. However, Suricata processes rules in a different default order: pass, drop, reject, and alert. Rule order affects the final verdict of a packet especially when conflicting actions such as a drop rule and an alert rule both match on the same packet.

### **Custom rules**

Although Suricata comes with pre-written rules, it is highly recommended that you modify or customize the existing rules to meet your specific security requirements.

There is no one-size-fits-all approach to creating and modifying rules. This is because each organization's IT infrastructure differs. Security teams must extensively test and modify detection signatures according to their needs.

Creating custom rules helps to tailor detection and monitoring. Custom rules help to minimize the amount of false positive alerts that security teams receive. It's important to develop the ability to write effective and customized signatures so that you can fully leverage the power of detection technologies.

## Configuration file

Before detection tools are deployed and can begin monitoring systems and networks, you must properly configure their settings so that they know what to do. A **configuration file** is a file used to configure the settings of an application. Configuration files let you customize exactly how you want your IDS to interact with the rest of your environment. 

Suricata's configuration file is suricata.yaml, which uses the YAML file format for syntax and structure.

## Log files

There are two log files that Suricata generates when alerts are triggered:

- **eve.json**: The eve.json file is the standard Suricata log file. This file contains detailed information and metadata about the events and alerts generated by Suricata stored in JSON format. For example, events in this file contain a unique identifier called flow_id  which is used to correlate related logs or alerts to a single network flow, making it easier to analyze network traffic. The eve.json file is used for more detailed analysis and is considered to be a better file format for log parsing and SIEM log ingestion.
    
- **fast.log**: The fast.log file is used to record minimal alert information including basic IP address and port details about the network traffic. The fast.log file is used for basic logging and alerting and is considered a legacy file format and is not suitable for incident response or threat hunting tasks.
    

The main difference between the eve.json file and the fast.log file is the level of detail that is recorded in each. The fast.log file records basic information, whereas the eve.json file contains additional verbose information.


## Trigger a custom rule in Suricata
`sudo suricata -r sample.pcap -S custom.rules -k none`
This command starts the Suricata application and processes the `sample.pcap` file using the rules in the `custom.rules` file. It returns an output stating how many packets were processed by Suricata.

_**Note:** _In this lab, using `sudo` is required to process packet capture files with Suricata, although it may not be required in a real-world environment.__

Now you’ll further examine the options in the command:

- The `-r sample.pcap` option specifies an input file to mimic network traffic. In this case, the `sample.pcap` file.
- The `-S custom.rules` option instructs Suricata to use the rules defined in the `custom.rules` file.
- The `-k none` option instructs Suricata to disable all checksum checks.

As a refresher, checksums are a way to detect if a packet has been modified in transit. Because you are using network traffic from a sample packet capture file, you won't need Suricata to check the integrity of the checksum. Suricata adds a new alert line to the `/var/log/suricata/fast.log` file when all the conditions in any of the rules are met.

The output returns alert entries in the log:
``` json
11/23/2022-12:38:34.624866  [**] [1:12345:3] GET on wire [**] [Classification: (null)] [Priority: 3] {TCP} 172.21.224.2:49652 -> 142.250.1.139:80
11/23/2022-12:38:58.958203  [**] [1:12345:3] GET on wire [**] [Classification: (null)] [Priority: 3] {TCP} 172.21.224.2:58494 -> 142.250.1.139:80
```
Each line or entry in the `fast.log` file corresponds to an alert generated by Suricata when it processes a packet that meets the conditions of an alert generating rule. Each alert line includes the message that identifies the rule that triggered the alert, as well as the source, destination, and direction of the traffic.

##### Examining eve.json output 
The `eve.json` file is the standard and main Suricata log file and contains a lot more data than the `fast.log` file. This data is stored in a JSON format, which makes it much more useful for analysis and processing by other applications.
The `jq` command to display the entries in an improved format:
```json
suhesh > jq . /var/log/suricata/eve.json | less
{
  "timestamp": "2022-11-23T12:38:34.624866+0000",
  "flow_id": 1119687577073813,
  "pcap_cnt": 70,
  "event_type": "alert",
  "src_ip": "172.21.224.2",
  "src_port": 49652,
  "dest_ip": "142.250.1.139",
  "dest_port": 80,
  "proto": "TCP",
  "tx_id": 0,
  "alert": {
    "action": "allowed",
    "gid": 1,
    "signature_id": 12345,
    "rev": 3,
    "signature": "GET on wire",
    "category": "",
    "severity": 3
  },
  "http": {
    "hostname": "opensource.google.com",
    "url": "/",
    "http_user_agent": "curl/7.74.0",
    "http_content_type": "text/html",
    "http_method": "GET",
    "protocol": "HTTP/1.1",
    "status": 301,
    "redirect": "https://opensource.google/",
    "length": 223
  },
  "app_proto": "http",
  "flow": {
    "pkts_toserver": 4,
    "pkts_toclient": 3,
    "bytes_toserver": 357,
    "bytes_toclient": 788,
    "start": "2022-11-23T12:38:34.620693+0000"
  }
}
{
  "timestamp": "2022-11-23T12:38:58.958203+0000",
  "flow_id": 2168516444853492,
  "pcap_cnt": 151,
  "event_type": "alert",
  "src_ip": "172.21.224.2",
  "src_port": 58494,
  "dest_ip": "142.250.1.102",
analyst@d5bab2667057:~$ jq . /var/log/suricata/eve.json | less
{
  "timestamp": "2022-11-23T12:38:34.624866+0000",
  "flow_id": 1119687577073813,
  "pcap_cnt": 70,
  "event_type": "alert",
  "src_ip": "172.21.224.2",
  "src_port": 49652,
  "dest_ip": "142.250.1.139",
  "dest_port": 80,
  "proto": "TCP",
  "tx_id": 0,
  "alert": {
    "action": "allowed",
    "gid": 1,
    "signature_id": 12345,
    "rev": 3,
    "signature": "GET on wire",
    "category": "",
    "severity": 3
  },
  "http": {
    "hostname": "opensource.google.com",
    "url": "/",
    "http_user_agent": "curl/7.74.0",
    "http_content_type": "text/html",
    "http_method": "GET",
    "protocol": "HTTP/1.1",
    "status": 301,
    "redirect": "https://opensource.google/",
    "length": 223
  },
  "app_proto": "http",
  "flow": {
    "pkts_toserver": 4,
    "pkts_toclient": 3,
    "bytes_toserver": 357,
    "bytes_toclient": 788,
    "start": "2022-11-23T12:38:34.620693+0000"
  }
}
{
  "timestamp": "2022-11-23T12:38:58.958203+0000",
  "flow_id": 2168516444853492,
  "pcap_cnt": 151,
  "event_type": "alert",
  "src_ip": "172.21.224.2",
  "src_port": 58494,
  "dest_ip": "142.250.1.102",
  "dest_port": 80,
  "proto": "TCP",
  "tx_id": 0,
  "alert": {
    "action": "allowed",
    "gid": 1,
    "signature_id": 12345,
    "rev": 3,
    "signature": "GET on wire",
    "category": "",
    "severity": 3
  },
  "http": {
    "hostname": "opensource.google.com",
    "url": "/",
    "http_user_agent": "curl/7.74.0",
    "http_content_type": "text/html",
    "http_method": "GET",
    "protocol": "HTTP/1.1",
    "status": 301,
    "redirect": "https://opensource.google/",
    "length": 223
  },
  "app_proto": "http",
  "flow": {
    "pkts_toserver": 4,
    "pkts_toclient": 3,
    "bytes_toserver": 357,
    "bytes_toclient": 797,
    "start": "2022-11-23T12:38:58.955636+0000"
  }
}
```

The `jq` command can be used to extract specific event data from the `eve.json` file:
``` json
analyst@d5bab2667057:~$ jq -c "[.timestamp,.flow_id,.alert.signature,.proto,.dest_ip]" /var/log/suricata/eve.json
["2022-11-23T12:38:34.624866+0000",1119687577073813,"GET on wire","TCP","142.250.1.139"]
["2022-11-23T12:38:58.958203+0000",2168516444853492,"GET on wire","TCP","142.250.1.102"]
```
*Note:** :The `jq` command above extracts the fields specified in the list in the square brackets from the JSON payload. The fields selected are the timestamp (`.timestamp`), the flow id (`.flow_id`), the alert signature or msg (`.alert.signature`), the protocol (`.proto`), and the destination IP address (`.dest_ip`).*

A network flow refers to a sequence of packets between a source and destination that share common characteristics such as IP addresses, protocols, and more. In cybersecurity, network traffic flows help analysts understand the behavior of network traffic to identify and analyze threats. Suricata assigns a unique `flow_id` to each network flow. All logs from a network flow share the same `flow_id`. This makes the `flow_id` field a useful field for correlating network traffic that belongs to the same network flows.
The `jq` command to display all event logs related to a specific `flow_id` from the `eve.json` file. The `flow_id` value is a 16-digit number and will vary for each of the log entries.
``` json
jq "select(.flow_id==X)" /var/log/suricata/eve.json
**X = flow_id
```


## Resources for more information
- [Suricata user guide](https://suricata.readthedocs.io/en/latest/index.html#)
- [Suricata features](https://suricata.io/features/)
- [Rule management](https://suricata.readthedocs.io/en/latest/rule-management/suricata-update.html)
- [Rule performance analysis](https://suricata.readthedocs.io/en/latest/configuration/suricata-yaml.html#engine-analysis-and-profiling)
- [Suricata threat hunting webinar](https://youtu.be/kaDGolhTu94)
- [Introduction to writing Suricata rules](https://youtu.be/tvoqFBVSShA)
- [Eve.json jq examples](https://suricata.readthedocs.io/en/latest/output/eve/eve-json-examplesjq.html)