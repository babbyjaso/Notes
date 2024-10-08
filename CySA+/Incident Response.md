### Phases
- what is an Incident?
	- The Act of violating an explicit or implied security policy
- Commonly used frame: NIST’s Guide 800-61
	- Preparation
	- Detection & Analysis
	- Containment, Eradication & Recovery
	- Post-Incident Activity
- Procedures
	- procedures and guidelines covering and appropriate priorities, actions, and responsibilities in the event of security incidents, divided into preparation, detection/analysis, containment, eradication/recovery, and post-incident stages
- CompTIA incident response cycle
	- Preparation
		- make the system resilient to attack by hardening systems, writing policies and procedures, and setting up confidential lines of communication
	- Detection & Analysis
		- Determine if an incident has taken place, triage it, notify relevant stakeholders
	- Containment
		- Limit the scope and magnitude of the incident by securing data and limiting impact to business operations and your customers
	- Eradication & Recovery
		- remove the cause of the incident and bring the system back to a secure state
	- Post-incident Activity
		- analyze the incident and responses to identify whether procedures or systems could be improved
- What is an Incident response team?
	- key people that are available to respond to any incident that meets the severity and priority thresholds set out by the incident response plan
- Positions on the team:
	- Manager
		- soft skills, is conveying managers and assigning tasks.
		- is also the face of the team to either media or law enforcement.
	- Security analysts
		- detectives to find out what happened
		- Sub-roles
			- Triage analyst
				- filter out false positives, monitor network during the investigations
			- Forensic analyst
				- builds the story of the attack
			- Threat Researcher
				- provides intelligence and context during the response
	- Cross functional support
		- other people from other departments
	- This team is known as the CSIRT
- You’re 24/7 when you’re on the Incident Response team
	- gotta think about burnout and to rotate people
### Documenting Procedures
- Writing is important for preparation.
- most orgs have incident response plans on file
- Make Sure You Have A Playbook
- Who You Gonna Call?
	- not Ghostbusters, sadly
	- Call List
		- who, when, how to contact someone
- Incident Form
	- records the detail about the reporting of an incident and assigns it a case or job number
		- Date, time, location
		- Reporter and handler names
		- how incident was observed/detected
		- type of incident
		- scope of incident
		- incident description and event logging
### Data Criticality
- basically, data hierarchy
- private or confidential data takes precedence over the excel file where you keep your boat names
- Data types
	- PII
		- Personally Identifiable Information
		- data that can be used to identify, contact or impersonate an individual
	- SPI
		- Sensitive Personal Information
		- subject’s opinions, beliefs and nature that is afforded specially protected status by privacy legislation
		- GDPR - General Data Personal something
		- America doesn’t really have legislation about this
	- PHI
		- Personal Health Information
		- information that identifies someone as the subject of medical records, insurance records, hospital results, or lab test results
		- HIPPA stuff
		- Protected Health Information is a thing too
		- this information is valuable for insurance fraud
	- Financial info
		- data stored about bank accounts, investment accounts, payroll, tax returns, credit card data, and other data about commercial transactions
		- money information
		- payment card data standard: PCI DSS: Payment Card Industry Data Security Standard
	- Intellectual Property
		- information created by an organization, usually about the products or services that it makes or provides
		- lots of things fall under this umbrella
			- copyright
			- patent
			- trademark
			- trade secret
			- e.g.: the 11 herbs and spices in KFC
				- can’t patent it, because then it becomes public and it has experations
				- two separate labs make half the blend and then it’s combined in the restaurant holy crap
			- e.g.: The Dion training video you’re watching now!
				- can’t download it for piracy reasons
	- Corporate Information
		- confidential data owned by a company like product, sales, marketing, legal, and contract information
		- it’s about profit, cash flow, salaries, market shares, and key customers
		- value to competitors
		- can also be used to manipulate the markets
	- High Value Assets
		- information system that processes data critical to a mission essential function
		- good to know which server to check first.
### Communication Plan
- How we gonna talk to each other?
	- need a secure method of communicating and managing incidents
- Out-of-band Communication
	- Signals that are sent between two parties or two devices that are sent via a path or method different from that of the primary communication between the two parties or devices.
	- e.g.: WhatsApp, Signal, OffTheRecord
- What is your backup communication plan?
- Maintain an up-to-date contact list
- what is the escalation procedure
- how are you going to notify people
	- email
	- web portals
	- phone calls
	- in-person updates
	- voicemail
	- formal report
	- most people would use a phone call or in-person
- Prevent unauthorized release of information outside of CSIRT
	- keep a tight lip on what’s going on
### Reporting Requirements
- Notifications that must be made to affected parties in the event of a data breach, as required by legislation or regulation
- 5 types of breaches
	- Data exfiltration
		- attacker breaks into a system and transfers data to another system
	- Insider data exfiltration
		- employee or ex-employes with privileges on the system transfers data to another system
	- Device theft/loss
		- a device (smartphone, laptop) containing data is lost or stolen
	- Accidental Data Breach
		- public disclosure of information or unauthorized transfer caused by human error or a misconfiguration
	- Integrity/Availability Breach
		- corruption of data or destruction of a system containing data.
- depending on the type of breach, laws or regulations governing this tells you how to report this
	- HIPAA example, you have to report to:
		- affected individuals
		- secretary of health and human services
		- media (if over 500 people)
	- GDPR example, you have to report to:
		- notification within 72 hours of becoming aware of the breach of personal data
- How are you going to tell the person affected?
	- emails, statements, etc.
	- key information:
		- what data
		- who to contact
		- consequences
		- response
### Response Coordination
- How are you going to coordinate your response?
- who are the affected stakeholders
	- senior leadership
		- executives and managers who are responsible for business operations and functional areas
	- regulatory bodies
		- governmental organizations that oversee the compliance with specific regulations and laws
	- legal
		- the business or organization’s legal counsel is responsible for mitigating risk from civil lawsuits
	- law enforcement
		- may provide services to assist in your incident handling efforts or to prepare for legal action against the attacker in the future
		- decision to involve law enforcement must be made by managers and legal
	- human resources
		- Used to ensure no breaches of employment law or employee contracts is made during an incident response
	- public relations
		- used to manage negative publicity from a serious incident
- CSIRT will be asked for information regarding the estimated downtime, scope of systems and data affected, and other details
### Training and Testing
- Training
	- education to ensure employees and staff understand processes, procedures and priorities during an incident response
	- be sure to know who you’re giving training to
	- bring up lessons learned and bring them up multiple times.
- Testing
	- Practivial exercising of incident response procedures
	- Tabletop or pentest:
	- TTX Table Top Exercise
		- exercise that uses an incident scenario against a framework of controls or a red team
		- just talking about situations that would happen.
	- Penetration Test
		- Red team attempts to conduct an intrusion of the network using a specific scenario based on threat modeling
		- Also have to agree on a clear methodology and rules of engagement before it’s performed.
	- Pentest tools:
		- metasploit
		- cobalt strike
		- Kali Linux
		- ParrotOS
		- Commando OS