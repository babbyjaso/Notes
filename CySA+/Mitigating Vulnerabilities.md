### Remediation and Mitigation
- can’t get risk down to 0, need to remediate it
- Vulnerabilities must be prioritized and remediated
- Remediation
	- overall process of reducing exposure to the effects of risk factors
- Vulnerability report offer recommended mitigations and fixes to security problems
- what is the goal of conducting remediation
	- to mitigate risk exposure to a digestible level.
	- How critical is the system?
	- How difficult is the remediation?
	- How risky is the issue?
- we’re here to reduce risk, not eliminate it
- change control is an important part of risk mitigation
	- you wanna make sure you don’t just install stuff willy nilly, gotta go through proper channels
- Risk Acceptance
	- no countermeasure put into place because the level of risk is low enough or the risk doesn’t justify the cost to mitigate the associated risk
	- just because you accept it doesn’t mean you stop monitoring it.
- scan, patch, scan
	- vulnerability should be rescanned and verified after a mitigation is put into place to verify the residual risk
### Configuration Baselines
- Configuration Baseline
	- Settings for services and policy configuration for a server operating in a particular application role
	- the “normal” when you ask “what is normal?”
- find normal, scan, patch, scan
	- that’s the new normal
	- any deviation from the baseline must be remediated or its risk accepted
- Security templates and baselines exist from vendors, third-parties and regulatory organizations
	- can get these from Center for Internet Security (CIS)
		- not for profit org that publishes the well-known “Top 20 Critical Security Controls”
	- Top 5:
		- inventory of authorized and unauthorized devices
		- inventory of authorized and unauthorized software
		- secure configurations for hardware and software on mobile devices, laptops, workstations and servers
		- continuous vuln assessment and remediation
		- controlled use of admin privileges
	- has benchmarks for all of these and the top 20
	- some a free, some are paid
- Compensating control
	- type of security control that acts as a substitute for a principal control
	- must give the same level of security assurance as the control it is replacing
	- if you need to patch something but you can’t, what do you do?
### Hardening and Patching
- Hardening
	- the process by which a host or other device is made more secure through the reduction of that device’s attack surface
- Attack Surface
	- the services and interfaces that allow a user or program to communicate with a target system
- any service or interface that is enabled through the default installation and left unconfigured should be considered a vulnerability.
- System Hardening Security Checklist:
	- Remove or disable devices that are not needed or used
	- Install OS, application, firmware, and driver patches regularly
	- Uninstall all unnecessary network protocols
	- Uninstall or disable all unnecessary services and shared folders
	- Enforce Access Control Lists on all system resources
	- Restrict user accounts to the least privileges needed
	- Secure the local admin or root account by renaming it and changing password
	- Disable unnecessary default user and group accounts
	- Verify permissions on system accounts and groups
	- Install antimalware software and update its definitions regularly
- consider how to also harden systems against availability attacks
	- battery backups
	- backup internet connections
	- lots more to consider
- patch management
	- identifying, testing, and deploying OS and application updates
	- often classified as:
		- critical
		- security-critical
		- recommended
		- optional
- lots of tools to help with patch management
	- MS endpoint Manager
	- MS SCCM (Microsoft System Center Configuration Manager)
- installing a patch can be an availability risk to a critical system that requires the system to be rebooted
- Patches may not exist for some stuff
### Remediation Issues
- numerous issues can arise during attempts to remediate a vulnerability
- is the risk high enough tto spend the time and money on it?
- can a compensating control be used instead?
- pain points
	- Legacy systems and proprietary systems
		- Legacy Systems
			- Computer system that is no longer supported by its vendor and so no longer provided with security updates and patches
		- Proprietary System
			- a system owned by its developer or vendor where lack of vendor support may be an inhibitor to remediation
	- organizational governance
		- a system by which an organization makes and implements decisions in pursuit of its objectives
	- Business process interruption
		- a period of time when an organization’s way of doing operations is interrupted
	- degrading functionally
		- a period of time when an organization’s systems are not performing at peak functionality, which could lead to business process interruption
	- MOU and SLA
		- Memorandum of Understanding (MOU)
			- usually a preliminary or exploratory agreement to express and intent to work together that is not legally binding and does not involve the exchange of money
			- handshake deals
		- Service Level Agreement (SLA)
			- contractual agreement setting out the detailed terms under which an ongoing service is provided.