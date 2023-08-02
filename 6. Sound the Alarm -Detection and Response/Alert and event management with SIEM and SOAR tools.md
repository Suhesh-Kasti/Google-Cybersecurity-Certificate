## SIEM
**SIEM** is a tool that *collects and analyzes log data to monitor critical activities* in an organization. SIEM provides security professionals with a high-level overview of what goes on in their networks. 
For example: A car's dashboard notifies us about the status of the car's components, so that we can take action to fix it. SIEM tools work in a similar way. Just like cars have many different components, a network can have thousands of different devices and systems, which make monitoring them quite the challenge. A car's dashboard gives the driver a clear picture of the status of their car, so they don't have to worry about inspecting each component themselves. Similarly, a SIEM looks at data flows between all the different systems in the network and analyzes them to provide a real-time picture of any potential threats to the network. It does this by ingesting massive amounts of data and categorizes this data, so that it's easily accessible through a centralized platform similar to a car's dashboard.

A **security information and event management** (**SIEM**) tool is an application that collects and analyzes log data to monitor critical activities in an organization. You might recall that SIEM tools help security analysts perform **log analysis** which is the process of examining logs to identify events of interest.

## SIEM advantages

SIEM tools collect and manage security-relevant data that can be used during investigations. This is important because SIEM tools provide awareness about the activity that occurs between devices on a network. The information SIEM tools provide can help security teams quickly investigate and respond to security incidents. SIEM tools have many advantages that can help security teams effectively respond to and manage incidents. Some of the advantages are:

- **Access to event data:** SIEM tools provide access to the event and activity data that happens on a network, including real-time activity. Networks can be connected to hundreds of different systems and devices. SIEM tools have the ability to ingest all of this data so that it can be accessed.
    
- **Monitoring, detecting, and alerting:** SIEM tools continuously monitor systems and networks in real-time. They then analyze the collected data using detection rules to detect malicious activity. If an activity matches the rule, an alert is generated and sent out for security teams to assess.
    
- **Log storage:** SIEM tools can act as a system for data retention, which can provide access to historical data. Data can be kept or deleted after a period depending on an organization's requirements. 
    

## The SIEM process

The SIEM process consists of three critical steps:

1. **Collect and aggregate data**
    
2. **Normalize data** 
    
3. **Analyze data**
    

By understanding these steps, organizations can utilize the power of SIEM tools to gather, organize, and analyze security event data from different sources. Organizations can later use this information to improve their ability to identify and mitigate potential threats.

### **Collect and aggregate data**

SIEM tools require data for them to be effectively used. During the first step, the SIEM collects event data from various sources like firewalls, servers, routers, and more. This data, also known as logs, contains event details like timestamps, IP addresses, and more. **Logs** are a record of events that occur within an organization’s systems. After all of this log data is collected, it gets aggregated in one location. Aggregation refers to the process of consolidating log data into a centralized place. Through collection and aggregation, SIEM tools eliminate the need for manually reviewing and analyzing event data by accessing individual data sources. Instead, all event data is accessible in one location—the SIEM. 

![Puzzle pieces representing data sources are ingested into a SIEM and processed as a completed puzzle.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/S4RVzsQNTH62x3KYJ85Uxg_95172ee75d1c4665927dcb44cc168ff1_S35G010.png?expiry=1691107200000&hmac=Yol-B-ELTk8ORslblh9_-09ePCI7cscI2TemtJY6B2o)

Parsing can occur during the first step of the SIEM process when data is collected and aggregated. _Parsing_ maps data according to their fields and their corresponding values. For example, the following log example contains fields with values. At first, it might be difficult to interpret information from this log based on its format:

`April 3 11:01:21 server sshd[1088]: Failed password for user nuhara from 218.124.14.105 port 5023`

In a parsed format, the fields and values are extracted and paired making them easier to read and interpret:

- host = server
    
- process = sshd
    
- source_user = nuhara
    
- source ip = 218.124.14.105
    
- source port = 5023
    

### **Normalize data**

SIEM tools collect data from many different sources. This data must be transformed into a single format so that it can be easily processed by the SIEM. However, each data source is different and data can be formatted in many different ways. For example, a firewall log can be formatted differently than a server log.

![A SIEM solution ingests raw data and normalizes it into structured data.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/sO_SKjBLQ624WVuvgg9p_w_22b55ac3196c4b508dd1df3572065ff1_S35G009.png?expiry=1691107200000&hmac=qmQ9Q9K8pOPgB_lWxNuaLJa-PQOVWQbsMYtIrDxnInk)

Collected event data should go through the process of normalization. _Normalization_ converts data into a standard, structured format that is easily searchable. 

### **Analyze data**

After log data has been collected, aggregated, and normalized, the SIEM must do something useful with all of the data to enable security teams to investigate threats. During this final step in the process, SIEM tools analyze the data. Analysis can be done with some type of detection logic such as a set of rules and conditions. SIEM tools then apply these rules to the data, and if any of the log activity matches a rule, alerts are sent out to cybersecurity teams.

**Note**: A part of the analysis process includes correlation. _Correlation_ involves the comparison of multiple log events to identify common patterns that indicate potential security threats.

## SIEM tools 

There are many SIEM tools. The following are some SIEM tools commonly used in the cybersecurity industry:

- AlienVault® OSSIM™
    
- Chronicle
    
- Elastic
    
- Exabeam
    
- IBM QRadar® Security Intelligence Platform
    
- LogRhythm
    
- Splunk

###### Process TL;DR
1. SIEM tools *collect and aggregate data*. This data is typically in the form of logs, which are basically a record of all the events that happened on a given source. Data can come from multiple sources such as IDS or IPS, databases, firewalls, applications, and more. 
2. After the data gets collected, it gets *aggregated*. **Aggregation** simply means all this data from different data sources gets centralized in one place. Depending on the number of data sources a SIEM collects from, a huge volume of raw unedited data can get collected. And not all data that's collected by a SIEM is relevant for security analysis purposes.
3. Next, SIEM tools *normalize data*. **Normalization** takes the raw data that the SIEM has collected and cleans it up by removing non essential attributes so that only what's relevant is included. Data normalization also creates consistency in log records, which is helpful when you're searching for specific log information during incident investigation.
4. Finally, the normalized data gets *analyzed according to configured rules*. SIEM analyzes the normalized data against a rule set to detect any possible security incidents, which then get categorized or reported as alerts for security analysts to review.

## SOAR
**Security orchestration, automation, and response**, or SOAR, is a collection of applications, tools, and workflows that uses automation to respond to security events.
While SIEM tools collect, analyze, and report on security events for security analysts to review, SOAR *automates analysis and response to security events and incidents*. SOAR can also be used to track and manage cases. Multiple incidents can form a case, and SOAR offers a way to view all of these incidents in one centralized place.

