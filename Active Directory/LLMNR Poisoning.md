Link Local Multicast Name Resolution (LLMNR)
Essentially a MitM attack
- Used to identify hosts when DNS fails
- Key feature is that services utilize a user's username an NTLMv2 hash when appropriately responded to
- Flow breakdown:
	- DNS does not know how to connect to a computer
	- DNS asks all how to connect to said computer
	- Hacker machine responds with "yes, I do. Send your hash to connect"
	- Hash get, pwned
### Critical tool: Responder ^responder
- Responds to traffic to get hashes, as described above
- Launch when traffic is going to be happening a lot
	- Morning
	- after lunch
- We can also just make the traffic ourselves if we want
	- try to access a file share that points to our machine
	- Because Responder responds, we get a response with a hash and username
	- Use Hashcat to crack (if it's weak enough), pwned
- `sudo responder -I eth0 -dwPv`
	- need to run responder with elevated privs
	- `-I` specifies interface
	- `-d` will answer DHCP broadcast requests
	- `-w` starts the WPAD rogue proxy server
	- `-P` to force authentication for the proxy
	- `-v` makes it verbose
- Make sure HTTP and SMB is on
- if you're just training, you can just make some traffic to get some hashes
	- shows that whenever network activity happens, we'll probably get a hash
### How to stop it
- Turn it off:
	- "Turn OFF Multicast Name Resolution"
- if you can't turn it off:
	- Require Network Access Control
	- Require strong passwords