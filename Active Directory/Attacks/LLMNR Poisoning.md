Link Local Multicast Name Resolution (LLMNR)
Essentially a MitM attack
- Used to identify hosts when DNS fails
- Key feature is that services utilize a user's username an NTLMv2 hash when appropriately responded to
- Flow breakdown:
	- DNS does not know how to connect to your computer
	- DNS asks all how to connect to your computer
	- Your computer responds with "yes, I do. Send your hash to connect"
	- Hash get, pwned
### Critical tool: [[Responder]]
- Make sure HTTP and SMB is on for this
	- `responder -I eth0 -dwPv`
- if you're just training, you can just make some traffic to get some hashes
	- shows that whenever network activity happens, we'll probably get a hash
### How to stop it
- Turn it off:
	- "Turn OFF Multicast Name Resolution"
- if you can't turn it off:
	- Require Network Access Control
	- Require strong passwords