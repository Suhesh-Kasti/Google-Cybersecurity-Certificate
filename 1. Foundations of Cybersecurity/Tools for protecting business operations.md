## Security information and event management (SIEM) tools
A **SIEM tool** is an application that collects and analyzes log data to monitor critical activities in an organization.
SIEM tools provide a series of dashboards that visually organize data into categories, allowing users to select the data they wish to analyze.
A **Log** is a record of events that occur within an organization’s systems.

### Network protocol analyzers (packet sniffers)
A **network protocol analyzer**, also known as a **packet sniffer**, is a tool designed to capture and analyze data traffic in a network. This means that the tool keeps a record of all the data that a computer within an organization's network encounters

**Chain of custody** is the process of documenting evidence possession and control during an incident lifecycle.
**Protecting and preserving** evidence is the process of properly working with fragile and volatile digital evidence.

### Playbooks
A **playbook** is a manual that provides details about any operational action, such as how to respond to a security incident. Organizations usually have multiple playbooks documenting processes and procedures for their teams to follow. The main objective of a playbook is: To guide analysts through a series of steps to complete specific security-related tasks.

Playbooks are similar to travel itineraries. They provide security analysts with instructions
on exactly what to do when an incident occurs. Playbooks provide security professionals
with a clear picture of their tasks during the entire incident response life cycle. Responding to an incident can be unpredictable and chaotic at times. Security teams are expected to
act quickly and effectively. Playbooks offer structure and order during this time by clearly
outlining the actions to take when responding to a specific incident. By following a playbook,
security teams can reduce any guesswork and uncertainty during response times. This allows security teams to act quickly and without any hesitation. Without playbooks, an effective and swift response to an incident is nearly impossible. 
Within playbooks, there may be *checklists* that can also help security teams perform effectively during stressful times by helping them remember to complete each step in
the incident response life cycle. Playbooks outline the steps that are necessary in response to an attack like ransomware, data breach, malware, or DDoS. 

![[/images/playbookflowchart.png]]
Here's an example of a playbook that uses a flowchart diagram with the steps to take during
the detection of a DDoS attack. This depicts the process for detecting a DDoS and begins with determining the indicators of compromise, like unknown incoming traffic. Once the indicators of compromise are determined, the next step is to collect the logs and finally analyze the evidence. 
There are three different types of playbooks:
1. **Non-automated:**
	The DDoS playbook we just explored is an example of a non-automated playbook, which  requires step-by-step actions performed by an analyst.
2. **Automated:**
		Automated playbooks automate tasks in incident response processes. For example, tasks such as categorizing the severity of the incident or gathering evidence can be done using an automated playbook Automated playbooks can help lower the time to resolution during an incident. SOAR and SIEM tools can be configured to automate playbooks.
3. **Semi-automated:**
	Semi-automated playbooks combine a person's action with automation. Tedious, error-prone, or time-consuming tasks can be automated, while analysts can prioritize their time with other tasks. Semi-automated playbooks can help increase productivity and decrease time to resolution.

As a security team responds to incidents, they may discover that a playbook needs updates or changes. Threats are constantly evolving and for playbooks to be effective, they must be maintained and updated regularly. A great time to introduce changes to playbooks is during the post-incident activity phase. 
