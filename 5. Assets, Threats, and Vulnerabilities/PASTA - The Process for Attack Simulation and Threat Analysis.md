PASTA is a popular threat modeling framework that's used across many
industries. PASTA is short for **Process for Attack Simulation and Threat Analysis**.
There are seven stages of the PASTA framework viz.

##### 1. Define business and security objectives.
Before starting the threat model, the team needs to ***decide what their goals are***.
The main objective of for example a fitness company app is protecting customer data.
The team starts by *asking a lot of questions* at this stage. They'll need to understand things like *how personally identifiable information* is handled. Answering these questions is a key to evaluate the impact of threats that they'll find along the way.

##### 2. Define the technical scope
Here, the team's focus is ***to identify the application components*** that must be
evaluated. For a mobile app, this will include technology that's involved while data is at rest and in use. This includes *network protocols*, *security controls*, and *other data interactions*.


##### 3. Decompose the application
In other words, we need to ***identify the existing controls*** that will protect user data from threats. This normally means working with the application developers to *produce a data
flow diagram*. A diagram like this will show how data gets from a user's device to the company's database. It would *also identify the controls in place* to protect this data along the way.

##### 4. Perform a threat analysis
This is where the team gets into their attacker mindset. Here, research is done to ***collect the most up-to-date information on the type of attacks*** being used. Like other technologies, mobile apps have many attack vectors. These change regularly, so the team would reference resources to stay up-to-date.

**Internal threats** are those that come from within an organization, such as from *employees*, *contractors*, or *business partners*. These threats can be intentional, such as when an employee steals data or sabotages a system, or unintentional, such as when an employee clicks on a malicious link and infects the network.
Some of the most common internal threats include:
- **Employee negligence:** This is when an employee makes a mistake that leads to a security breach, such as clicking on a malicious link or failing to follow security procedures.
- **Insider attacks:** This is when an employee intentionally steals data or sabotages a system. Insider attacks can be motivated by financial gain, revenge, or ideology.
- **Misconfiguration:** This is when a system or network is not properly configured, which can leave it vulnerable to attack.

**External threats** are those that come from outside an organization, such as from hackers or malware distributors. These threats are often more sophisticated and targeted than internal threats.
Some of the most common external threats include:
- **Hacking:** This is when an attacker gains unauthorized access to a system or network. Hackers can steal data, install malware, or disrupt operations.
- **Malware:** This is software that is designed to harm a computer system. Malware can be spread through email, malicious websites, or USB drives.
- **Phishing:** This is a social engineering attack that tricks the victim into giving up sensitive information, such as their username and password.

##### 5. Vulnerability analysis
In this stage, the team more deeply ***investigates potential vulnerabilities*** by considering the root of the problem.

##### 6. Attack modeling
This is where the team ***tests the vulnerabilities*** that were analyzed
in stage five by simulating attacks. The team does this *by creating an attack tree*, which looks like a flow chart. For example, an attack tree for our mobile app might look like this.
![[Pasted image 20230729090949.png]]
Customer information, like user names and passwords, is a target. This data is normally stored in a **database**. We've learned that databases are vulnerable to attacks like **SQL injection**. So we will add this attack vector to our attack tree. A threat actor might exploit vulnerabilities caused by **unsanitized inputs** to attack this vector.
The security team uses attack trees like this to *identify attack vectors* that need to be tested to validate threats. This is just one branch of this attack tree. An application, like a fitness app, typically has *lots of branches with a number of other attack vectors*.

##### 7. Analyze risk and impact
Here, the team ***assembles all the information*** they've collected in stages one through six. By this stage, the team is in position to *make informed risk management recommendations* to business stakeholders that align with their goals. 