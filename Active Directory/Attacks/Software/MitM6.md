`mitm6`
if it's not ready and available, `cd /opt/mitm6`, then `sudo pip2 install .`
Options
- `-d`
	- Needs this, it's the domain
	- `domain.local`
Before you launch it, you'll wanna fire up [[ntlmrelayx.py]] to relay information back to us
Once you launch, it should pop up with IPs that you are now the DNS for the network
Do not want to do this for long amounts of time, this will cause outages.
Once you get an administrator logging in, you will get a free account created for you.
- Can do a DCSync using secretsdump.py
	- Get the secrets file from the DC now
	- This is because this user is a part of the Enterprise Admins