**Documentation** is any form of recorded content that is used for a specific purpose, and it is essential in the field of security. Security teams use documentation to support investigations, complete tasks, and communicate findings. This reading explores the benefits of documentation and provides we with a list of common practices to help we create effective documentation in our security career.
## Documentation benefits
As a security engineer who deals with detection rules, it is critical to document what it means when those rules are activated, what severity to assign, what might lead to false positives, and how the analysts can confirm the alert is legitimate. Without this documentation, a security operations team can never scale beyond one or two analysts.


As a security professional, we'll likely juggle documentation responsibilities
alongside other tasks. By taking the time to write down our actions, we'll recall facts and
information. We may even notice some gaps in the previous actions we took. The time we spend documenting is valuable not only for us, but for the entire organization. 


Effective documentation has three benefits:

1. Transparency:
		If something was documented, then there's a record of it happening. This means that relevant information can be accessed. This is known as *transparency*. Transparent documentation is useful as a source of evidence for security insurance claims, regulatory investigations, and legal proceedings. 
    
2. Standardization:
		Documentation also provides *standardization*. This means that there's an established set of guidelines or standards that members of an organization can follow to complete a task or workflow. An example of creating standardization through documentation is establishing an organization's security policy, processes, and procedures. This helps in maintaining quality of work since there are set rules to follow.
    
3. Clarity: 
		Documentation also improves *clarity*. Effective documentation not only gives team members a clear understanding of their roles and duties, but it also provides information on how to get the job done. For example, playbooks that provide detailed instructions prevent uncertainty and confusion during incident response. The security field is constantly changing, attacks evolve, and regulatory requirements might change. This is why it's important to maintain, review, and update documentation regularly to keep up with any changes.
    

### **Transparency**

In security, transparency is critical for demonstrating compliance with regulations and internal processes, meeting insurance requirements, and for legal proceedings. **Chain of custody** is the process of documenting evidence possession and control during an incident lifecycle. Chain of custody is an example of how documentation produces transparency and an audit trail.

### **Standardization**

Standardization through repeatable processes and procedures supports continuous improvement efforts, helps with knowledge transfer, and facilitates the onboarding of new team members. **Standards** are references that inform how to set policies.

we have learned how NIST provides various security frameworks that are used to improve security measures. Likewise, organizations set up their own standards to meet their business needs. An example of documentation that establishes standardization is an **incident response plan**, which is a document that outlines the procedures to take in each step of incident response. Incident response plans standardize an organization’s response process by outlining procedures in advance of an incident. By documenting an organization’s incident response plan, we create a standard that people follow, maintaining consistency with repeatable processes and procedures.

### **Clarity**

Ideally, all documentation provides clarity to its audience. Clear documentation helps people quickly access the information they need so they can take necessary action. Security analysts are required to document the reasoning behind any action they take so that it’s clear to their team why an alert was escalated or closed.

## Best practices

As a security professional, we’ll need to apply documentation best practices in our career. Here are some general guidelines to remember:

### **Know our audience**

Before we start creating documentation, consider our audience and their needs. For instance, an incident summary written for a security operations center (SOC) manager will be written differently than one that's drafted for a chief executive officer (CEO). The SOC manager can understand technical security language but a CEO might not. Tailor our document to meet our audience’s needs.

### **Be concise**

we might be tasked with creating long documentation, such as a report. But when documentation is too long, people can be discouraged from using it. To ensure that our documentation is useful, establish the purpose immediately. This helps people quickly identify the objective of the document. For example, executive summaries outline the major facts of an incident at the beginning of a final report. This summary should be brief so that it can be easily skimmed to identify the key findings. 

### **Update regularly** 

In security, new vulnerabilities are discovered and exploited constantly. Documentation must be regularly reviewed and updated to keep up with the evolving threat landscape. For example, after an incident has been resolved, a comprehensive review of the incident can identify gaps in processes and procedures that require changes and updates. By regularly updating documentation, security teams stay well informed and incident response plans stay updated.


### Chain of Custody
During incident response, evidence must be accounted for during the entire incident's lifecycle. Tracking evidence is important if the evidence is requested as part of any legal
proceedings. How can security teams ensure that this is done? They use a form called **chain of custody.** Chain of custody is the process of documenting evidence possession and
control during an incident lifecycle.  As soon as evidence gets collected, chain of custody forms are introduced. The forms should be filled out with details as the evidence is handled. 
Let's examine a very simple example of how chain of custody is used during digital forensic analysis. Digital forensics is the practice of collecting and analyzing data to determine what has happened after an attack. During an incident response, Anjila verified that a compromised hard drive requires examination by the forensics team. First, she ensures that the hard drive is write protected, so the data on the disk can't be edited or erased. Then, she calculates and records a cryptographic hash function of an image of the hard drive. Hash function is an algorithm that produces a code that can't be decrypted. Anjila is then instructed to transfer it to Colin in the forensics department. Colin examines it and sends it off to Nav, another analyst. Nav receives the compromised hard drive and sends it to her manager, Arman. 
Each time the hard drive is transferred to another person, they need to log it in the chain of custody form, so that movement of evidence is transparent. Tampering with the data on the hard drive can be detected using the original hash that Anjila documented at the beginning of the process. This ensures that there's a paper trail describing who handled the evidence, and why, when, and where they handled it.
Just like other documentation types, there is no standard template of what the chain of custody form should look like, but they do contain common elements. This is what we might examine on a chain of custody log form. 
First, there should be a description of the evidence, which includes any identifying
information, like the location, hostname, MAC address, or IP address. Next is the custody log, which details the name of the people who transferred an  received the evidence. It also includes the date and time the evidence was collected or transferred and the purpose of the transfer. 
###### What happens if evidence gets logged incorrectly? Or, if there's a missing entry?
This is what's known as a **broken chain of custody**, which occurs when there are inconsistencies in the collection and logging of evidence in the chain of custody. In the court of law, chain of custody documents help establish proof of the integrity, reliability, and accuracy of the evidence. For evidence related to security incidents, chain of custody forms are used to help meet legal standards so that this evidence can be used in legal proceedings. If a malicious actor compromised a system, evidence must be available to determine their actions so that appropriate legal action can be taken. However, in some cases, major breaks in the chain of custody can impact the integrity, reliability, and accuracy of the evidence. This affects whether or not the evidence can be a trusted source of information and used in the court of law. Chain of custody forms provide us with a method of maintaining evidence, so that malicious actors can be held responsible for their actions.   