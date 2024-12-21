We got a hash from [[LLMNR Poisoning]], time to use it to gain access to another machine via SMB. This is especially effective if you can't crack the hash for a password.
- SMB signing must not be disabled or enforced
	- Default:
		- Workstations it is not enabled
		- Servers it is enabled
	- be sure to double check
- User creds must be local admin to really do anything
- Good news: there's an [[NMap scripts|nmap script]] for this:
	- `nmap --script=smb2-security-mode.nse`
	- Looking for "Message signing enabled but not required"
	- if the machine can't be pinged, do a `-Pn`
- Wait for an event, then get the hashes
## Software
[[Impacket]]

## How to stop it
- Enable SMB Signing on all devices
	- completely stops the attack
	- can cause performance issues with file moving
- Disable NTLM authentication on network
	- completely stops the attack
	- if Kerberos stops working, Windows will go back to NTLM
- Account tiering
	- Limits domain admins to specific tasks
	- Building/enforcing policy
- Local admin restriction
	- Can prevent a lot of lateral movement
	- Potential increase in service desk tickets