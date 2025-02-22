AD database
Stores:
- User info
- Group info
- Security descriptors
- Password hashes

## Tools
[[secretsdump.py]]
- We're using the switch `-just-dc-ntlm`
	- dumps the ntlm hashes for all accounts
Neat Idea:
- When you get account info, put it into excel
	- text to columns
	- delimiter `:`
	- get all the NTs in a row
- can use `vlookup` to combine all your things together