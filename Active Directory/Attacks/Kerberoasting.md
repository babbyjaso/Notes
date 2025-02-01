Pretend that you're a legitimate user to the Kerberos server to gain access to services and other computers on the domain.
- takes advantage of service accounts
- when you get the Ticket Granting Service (TGS) this will contain the server account's hash as well
	- from there, crack the hash
### Tools
- [[getuserspn.py]]

### Mitigation
- Strong passwords
- Least privilege
- don't make your service accounts domain admin!