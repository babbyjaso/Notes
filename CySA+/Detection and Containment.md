### OODA Loop ^ooda-loop
- Not required for the exam, but good to know
- Observe
	- Identify the problem or threat and gain an overall understanding of the internal and external environment
	- Data gathering
- Orient
	- Involves reflecting on what has been found during the observations and considering what should be done next
- Decide
	- Make suggestions towards an action or response plan while taking into considering all of the potential outcomes
- Act
	- Carry out the decision and related changes that need to be made in response to the decision
- made so you don’t become overcome by paralysis by analysis in observation
- just do something. can’t do nothing.
### Defensive Capabilities ^defensive-capabilities
- what defensive capabilities does your organization have?
- the 6 Ds
	- Detect
		- identify the presence of an adversary and the resources at their disposal
	- Destroy
		- render an adversary’s resources permanently useless or ineffective
	- Degrade
		- reduce an adversary’s capabilities or functionality, perhaps temporarily
	- Disrupt
		- Interrupt an adversary’s communications or frustrate or confuse their efforts
	- Deny
		- prevent an adversary from learning about your capabilities or accessing your information assets
	- Deceive
		- supply false information to distort the adversary’s understanding and awareness
### Detection and Analysis ^detcetion-and-analysis
- Determine if an incident has taken place, triage it, notify relevant stakeholders
- SIEM is going to be the place where you get the data for your detection and analysis
- Known IOCs will trigger an alert, which is automatic categorization and prioritization
	- most, if not all, security software will put out an alert
- once it has been detected it needs to be categorized
	- benign
	- suspicious
	- malicious
	- you know this shit
- automation can do a lot of the work (SOAR)
- how do you decide how to classify a certain indicator?
	- knowledge of the network, mostly
### Impact Analysis ^impact-analysis
- triage basically means priority list
- Gotta consider some stuff when triaging
	- damage to data integrity
	- unauthorized changes
	- theft of data or resources
	- disclosure of confidential data
	- interruption of services
	- system downtime
- Triage or categorization gonna be done based on one of two things;
	- Impact-based Approach
		- A categorization approach that focuses on the severity of an incident, such as emergency, significant, moderate, or low
	- Taxonomy-based approach
		- approach that defines incident categories at the top level, such as worm outbreak, phishing attempt, DDoS, external host/account compromise, or internal privilege abuse
- impact analysis is the preferred way in the industry (because of cost)
	- Organizational Impact
		- An incident that affects mission essential functions and therefore the the organization cannot operate as intended
	- Localized Impact
		- An incident that is limited in scope to a single department, small user group or a few systems
		- doesn’t mean it’s less important or less costly
	- Immediate Impact
		- An incident measurement based on the direct costs incurred because of an incident, such as downtime, asset damage, penalties, and fees
	- Total Impact
		- An incident measurement based on the costs that arise both during and following the incident, including damage to the company’s reputation
		- reputation tarnishing is categorized here.
### Incident Classification
- some orgs will add additional layers of incident classification
- Here’s some examples
	- Data integrity
		- any incident where data is modified or loses integrity
	- System process criticality
		- incidents that disrupt or threaten a mission essential business function
	- Downtime
		- an incident that degrades or interrupts the availability of an asset, system, or business process
	- Economic
		- an incident that creates short-term or long-term costs
	- Data correlation
		- an incident that is linked to the TTP of known adversary groups with extensive capabilities
	- Reverse engineering
		- an incident which the capabilities of the malware are discovered to be linked to an adversary group
	- Recovery time
		- an incident which requires extensive recovery time due to its scope or severity
	- Detection time
		- an incident which was not discovered quickly
- only 10% of data breaches were discovered within the first hour
	- 20% of the incidents took days
	- 40% took months to be discovered
- nearly 40% of adversaries had successfully exfiltrated data within minutes of starting an attack
### Containment
- Rapid containment is important to an incident response
- Limit the scope and magnitude of the incident by securing data and limiting impact to business operations and your customers
	- 5 steps
	- ensure the safety and security of all personnel
	- prevent an ongoing intrusion or data breach
	- identify if the intrusion is the primary or secondary attack
	- avoid alerting the attacker that the attack has been discovered
	- preserve any forensic evidence of the intrusion and attack
- these steps are in priority order
- two categories of containment
	- Isolation
		- mitigation strategy that involves removing an affected component from whatever larger environment it is a part of
		- ensure there is no interface between the asset and the internet
		- creating an air gap is the least stealthy option will reduce opportunities to analyze the malware
		- can also take away the permissions of an account or program
	- Segmentation
		- mitigation strategy that achieves the isolation of a host or group of hosts using network technologies and architecture
		- using firewalls, vlans, routing/subnets to prevent outside communications
		- also called “sandboxing”
		- segmentation can be used to reroute adversary traffic as part of the deception
			- honeypots, honeynets, etc
		- consult your boss for your plan