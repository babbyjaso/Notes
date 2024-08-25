Basic oversights
	• Not thoroughly reading the scope before testing
	• Not strictly following the scope
	• Misunderstanding the importance of the scope
	• Reviewing the asset scope while forgetting the bug scope
	• Assuming all subdomains are in-scope
	• Not verifying if third-party services are in-scope
	• Improperly configuring tools to adhere to scope
		○ Be sure to set up your burp regex correctly so you're not testing out of scope
	• Reporting out of scope findings
		○ You'll get less karma
Commonly out of scope vulns:
	• Physical attacks
	• Social engineering
	• DoS
	• Outdated software
		○ These probably have vulnerabilities, but are excluded because of risk management
		○ Rip, F, coffin emoji, etc.
		○ If you can find the vuln and demonstrate that it has a security issue, then it can be reported.
	• Missing headers / cookie flags
		○ Unless it leads you to being able to execute an attack, it's low on the need
	• Brute force
	• Username enumeration
	• Fingerprinting
	• Theoretical attacks
	• Leaked creds
		○ Does not exclude default creds
		○ There's more information on the community FAQ page
Let's take a look at a red bull bounty
	• You will need a intigriti.me email to do the requests
	• Limit to 5 requests/sec
	• No user agent needed, no request header needed
	• Stick to what they want and you won't be legally prosecuted
	• Be sure to read the Out of Scope!
		○ A lot of the stuff here is common, so eventually you'll just know the stuff naturally.
		○ A lot of these are "prove that it's a security issue"
			§ "proven impact"
			§ "proven business impact"
		○ Recently discovered zero-days within an allotted time
			§ Give companies time to patch their systems
		○ Don't install backdoors lol
	• You can ask a question about the scope sometimes