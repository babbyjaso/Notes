If something has IPv6 turned on but not using it, we can pretend to be the DNS
Things we can get this way:
- LDAP creds
- NTLM creds
- maybe some traffic and external creds??
Software: [[MitM6]]
## How to mitigate
- You could just disable IPv6 but it could be problematic
- Three blocks you can put instead:
	- Core Networking DHCPv6-In
	- Core Networking ICMPv6-In
	- Core NEtworking DHCPv6-Out
- Disable WPAD if you don't use it
- Relaying LDAP and LDAPS can only be mitigated by enabling LDAP signing and LDAP channel binding
- Add Administrators to the Protected Users group or marking them sensitive and cannot be delegated
	- Latter prevents impersonation