Take the temporary keys that get you around with no issue

Two types:
- Delegate
	- Created when logging into a machine including RDP
- Impersonate
	- "non-interactive"
	- attaching a network drive
	- domain logon script

Why is this bad?
- Meterpreter module "incognito"
	- copy any delegate tokens on the machine to impersonate users
- once we get a domain admin, we can do whatever we want
	- including making our own domain admin
### Tools
[[Metasploit]]
- User PSExec to get onto one of the workstations through metasploit
- once in metrepreter, load the incognito module
	- you'll need to log into the machine itself because we need to get the delegate token somehow

### Mitigation
- Limit token creation permission
- Account tiering
- Local admin restriction