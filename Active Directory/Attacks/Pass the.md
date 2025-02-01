Tool: [[crackmapexexc]]
Tool: [[Metasploit]] (of course)
Tool: [[secretsdump.py]]

Take the creds you have
- Hash
- UN:PW 
Push them all around the network to see what bites.

Strategy is to get the local admin password
- typically local admin password is the same on all machines
- once you pop one, get the SAM for others
Dump the LSA as well
- could get lucky with an unchanged password

### Mitigation
- Limit account re-use
- Utilize strong passwords
- Privilege Access Management (PAM)