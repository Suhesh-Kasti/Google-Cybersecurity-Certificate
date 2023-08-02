Incident lifecycle frameworks provide a *structure to support incident response operations*. Frameworks help organizations develop a standardized approach to their incident response process, so that incidents are managed in an effective and consistent way. There are many different types of frameworks that organizations can adopt and modify according to their needs.
The five core functions of the NIST CSF are: **identify**, **protect**, **detect**, **respond**, and **recover**. We will explore the last three steps of this framework: detect, respond, and recover. These last three steps are critical stages during incident response, and as an analyst, we'll detect and respond to incidents and implement actions for recovery.
The NIST incident response lifecycle is another NIST framework with additional substeps dedicated to incident response. It begins with preparation. Next, detection and analysis, and then containment, eradication and recovery, and finally post-incident activity. *Incident lifecycle isn't a linear process, steps can overlap as new discoveries are made.*

### What is an incident?
According to NIST, an incident is "*an occurrence that actually or imminently jeopardizes, without lawful authority, the confidentiality, integrity, or availability of information or an information system; or constitutes a violation or imminent threat of violation of law, security policies, security procedures, or acceptable use policies."* 
All security incidents are events, but not all events are security incidents. What are events? An **event** is an observable occurrence on a network, system, or device.

An example of an event can be a user attempts to log into their email account, but they can't because they forgot their password. The user then requests a password reset and successfully changes their password. This is an observable event because systems and applications log password reset requests and logs provide evidence that something happened. We know that someone successfully requested a password reset and that they did not violate security policies to access the account.
Now, imagine that instead of the rightful owner of the account, a malicious actor trying to gain access to the account, successfully initiated the password change request and changed the account password. This would be considered both an event and a security incident. It's an event because it's an observable occurrence. It's also a security incident because a malicious actor violated the security policy to unlawfully access an account that is not rightfully theirs. Remember, all security incidents are events, but not all events are security incidents.

An incident investigation reveals critical information about the five W's of an incident: ***who triggered the incident, what happened, when the incident took place, where the incident took place, and why the incident occurred***. Keeping track of this information is essential not only during an incident investigation, but also during the closure of an investigation when it comes time to write the final report. We then need a method to document and reference this information for easy access when we need it. A great way to do this is to use an **incident handler's journal**, which is a form of documentation used in incident response. 

The NIST Incident Response Lifecycle is a **cyclical process**. This means that phases in the lifecycle can be revisited or repeated as incident investigations progress.

###### 1. Preparation: the planning and training process

The organization takes action to ensure it has the correct tools and resources in place:  
- Set up uniform company email conventions
- Create a collaborative, ethical environment where employees feel comfortable asking questions
- Provide cybersecurity training on a quarterly basis

###### 2. Detection and analysis: the detect and assess process

Security professionals create processes to detect and assess incidents:  
- Identify signs of an incident
- Filter external emails to flag messages containing attachments such as voicemails
- Have an incident response plan to reference

###### 3. Containment, eradication, and recovery: the minimize and mitigate process

Security professionals and stakeholders collaborate to minimize the impact of the incident and mitigate any operational disruption.  
- Communicate with sender to confirm the origin of the voice message
- Provide employees with an easy way to report and contain suspicious messages

###### 4. Post-incident activity: the learning process

New protocols, procedures, playbooks, etc. are implemented to help reduce any similar incidents in the future.  
- Update the playbook to highlight additional red flags employees should be aware of
- Review processes and workflows related to permissions and adjust oversight of those permissions

