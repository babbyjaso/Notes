- For more technical controls: [[Technical Data and Privacy Controls]]
### Data Classification
- Data Governance
	- the process of managing information over its lifecycle from creation to destruction
	- creation, storage, distribution, retention/destruction
- Data Classification
	- process of applying confidentiality and privacy labels to information
	- assigned at creation
- Typical assign chart
	- military:
		- unclassified
			- no restrictions on viewing the data and it presents no risk to the organization is disclosed to the public at large
		- classified
			- viewing is restricted to authorized persons within the owner organization or to third parties under a non-disclosure agreement
		- confidential
			- highly sensitive data that is for viewing only by approved persons within the organization
			- lowest level of “classified”
		- secret
			- information that is valuable and must be protected by severely restricting its viewing
		- top secret
			- information that would cause grave danger if inadvertently disclosed
- orgs use a simpler classification scheme, typically
- classifications may be applied manually or automatically
- Declassification
	- the downgrading of a classification label over time due to the information no longer requiring the additional security protections provided by that classification
### Data Types
- data can also be tagged by it’s data type
	- a tag or label to identify a piece of a data under a subcategory of a classification
- some common unclassified categories::
	- Personally Identifiable Information (PII)
	- Sensitive Personal Information (SPI)
	- Personal Health Information (PHI)
	- Financial Information
- Microsoft’s DLP solution uses over 70 sensitive information types under the unclassified classification category
- Data Format
	- the organization of information into preset structures or specifications
	- unstructured or structured
- structured data: comma separated value list. a specific order
- unstructured data: email, chat log, power point. any order.
- Data State
	- The location of data in a processing system
	- Different states of data
		- [[Technical Data and Privacy Controls#^data-at-rest|Data at rest]]
		- [[Technical Data and Privacy Controls#^data-in-motion|Data in motion]]
		- [[Technical Data and Privacy Controls#^data-in-use|Data in use]]
### Legal Requirements
- any type of information or asset should consider how a compromise of that information can threaten the three core security attributes of the CIA triad
	- Confidentiality = Encryption
	- Integrity = Hashing
	- Availability = Redundancy
- this is going to be focused on privacy vs security
	- security controls focus on the CIA attributes of the processing system
	- Privacy
	- data governance requirement that arises when collecting and processing personal data to ensure the rights of the subject’s data
	- don’t have to have it encrypted, technically
		- it’s a good idea tho
- legal requirements will affect your corporate governance and policies in regards to privacy of your user’s data
- General Data Protection Regulation (GDPR)
	- personal data cannot be collected, processed, or retained without the individual’s informed consent
	- also provides the right for a user to withdraw consent, to inspect, amend or erase data held about them.
	- …only in Europe
	- Requires data breach notification within 72 hours
	- Data breaches can happen accidentally or through malicious interference
	- sometimes its just a dude who made a mistake
- Now, let’s talk about American privacy/data retention
- Sarbanes-Oxley Act (SOX)
	- Sets for the requirements for the storage and retention of documents relating to an organization’s financial and business operation, including the type of documents to be stored and their retention periods
- Gramm-Leach-Bliley Act (GLBA)
	- sets for the the requirements that help protect the privacy of an individual’s financial information that is held by financial institutions and others
- Federal Information Security Management Act (FISMA)
	- Sets forth the requirements for federal organizations to adobe information assurance controls
- Health Insurance Portability and Accountability Act (HIPAA)
	- sets forth the requirements that help protect the privacy of an individual’s health information that is held by healthcare providers, hospitals, and insurance companies
- Committee of Sponsoring Organizations of the Treadway Commission (COSO)
	- provides guidance on a variety of governance-related topics including fraud, controls, finance, and ethics and relies on COSO’s ERM-integrated framework
	- best practices of dealing with fraud and such
- there are countless other laws and regulations around the globe
### Data Policies
- Purpose Limitation
	- the principle that personal information can be collected and processed only for a stated purpose to which the subject has consented
	- will restrict your ability to transfer data to third parties
- Data Minimization
	- the principle that only necessary and sufficient personal information can be collected and processed for the stated purpose
	- each process that uses personal data should be documented
	- data minimization can affect the data retention policy
- Data Sovereignty
	- the principle that countries and states may impose individual requirements on data collected or stored within their jurisdiction
	- some states and nations may respect data privacy more or less than others
		- affects where you put your servers
### Data Retention
- the process an organization uses to maintain the existence of and control over certain data in order to comply with business policies and/or applicable laws and regulations
- Retention
	- a set of policies, procedures, and tools for managing the storage of persistent data
	- “how long should I keep this?”
- orgs may be legally bound to retain certain types of data for a specified period to meet compliance and e-discovery requirements
- always included legal counsel when developing your data retention policies
- Data Preservation
	- refers to information that is kept for a specific purpose outside of an organization’s data retention policy
	- backup and archiving tools are used to fulfill the requirements of data retention
- two types of retention:
- short term retention
	- determined by how often the youngest media sets are overwritten
- long term retention
	- data moved to an archive storage to prevent being overwritten
- business continuity planning should define the recovery point objective and that should drive the recovery window and backup plans
- retention policy is based on either redundancy or a recovery window
- once data expires, you have to securely dispose of it
### Data Ownership
- the process of identifying the persons responsible for the confidentiality, integrity, availability, and privacy of information assets
	- data owner
		- a senior or executive role with ultimate responsibility for maintaining the confidentiality, integrity, and availability of the information asset
		- responsible for labeling the asset and ensuring that is i protected with appropriate controls
	- data steward
		- role focused on the quality of the data and associated metadata
		- data is appropriately labeled
	- data custodian
		- responsible for handling the management of the system on which the data assets are stored
	- privacy officer
		- tole responsible for the oversight of any PII/SPI/PHI assets managed by the company
		- doing all the stuff we’ve been talking about in this section
- who should own the data?
	- should be somebody from the business side, IT is custodians
	- someone who knows what the data is
### Data Sharing
- you can outsource a service or activity, but not the legal responsibility for it
- four types of agreements
- Service Level Agreement (SLA)
- contractual agreement setting out the detailed terms under which a service is provided
- Can outsource the task, but can’t outsource the responsibility
- Interconnection Security Agreement (ISA)
- agreement used by federal agencies to set out a security risk awareness process and commit the agency and supplier to implementing security controls
- Non-Disclosure Agreement (NDA)
- contract that sets forth the legal basis for protecting information assets between two parties
- Data Sharing and Use Agreements
- an agreement that sets forth the terms under which personal data can be shared or used
- all of these datasets may be subject to pseudonymization or deidentification to remove personal data