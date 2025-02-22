First thing's first:
- Fire up [[Responder]]
- Fire up [[MitM6]]
Second thing's second:
- Do some scans to generate some traffic
	- This is for Responder to have traffic to listen to
- If that doesn't work, we can look at some internal websites as well
	- port 80/443 open from your nmap scan? hit the browser
	- Metasploit `http_version`
- Look for default creds on web logins
	- google the device for default login, someone's posted it somewhere
- Look for printers to do a [[Passback]]
- Always gather as much information as you can
You've got a user: now what?
- Enumerate
- Enumerate
- Enumerate
- Here's some things you can do:
	- bloodhound
	- plumhound
	- ldapdomaindump
	- pingcastle
Third things third:
- got creds, got machines, time to get some secrets
	- [[secretsdump.py]]
	- [[crackmapexec]]
- You'll get local accounts from this
- take those local accounts and go over the same machines again
- Find hash? Crack hash
Fourth things fourth:
- We got an account
	- What's next?
- Quick wins
	- [[Kerberoasting]]
	- [[secretsdump.py]]
	- [[Pass the]]
- More digging
	- [[bloodhound]]
	- [[ldapdomaindump]]
	- where can you go?
	- old vulns die hard
We've got the domain
- dump NTDS.dit
	- crack some passwords
- Enumerate enumerate enumerate
- Put in some persistence
	- What happens if we lose access?
		- ur screwed m8
	- Create a DA account
		- be sure to delete it
		- don't leave a mess
	- get a golden ticket