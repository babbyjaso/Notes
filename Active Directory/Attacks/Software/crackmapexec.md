AKA `netexec`
- Pushes valid creds to other machines on the network to see if they'll work
- Great for seeing if an admin has logins on other machines
- Uses SMB to communicate
- Will give you a "Pwn3d!" if you have local admin
Can also do this with hashes
- Use the `-H` flag to put in your hash
- be sure to have `--local-auth`
	- only if you're trying to log on to local accounts, not domain accounts
Can dump SAM from whatever you get onto
- `--sam`
- SAM file is important y'know
Can show was shares are available
- `--shares`
- Gimme the loot!
Can dump the LSA
- `--lsa`
Has modules
- Check with `-L`
	- `lsassy`
		- dump the lsass, see if anyone has any cached creds on it
	- `slinky`
		- can look up file shares on systems
