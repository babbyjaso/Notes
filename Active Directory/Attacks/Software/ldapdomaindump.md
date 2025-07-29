`ldapdomaindump`
You have a way in, dump the ldap
- `sudo ldapdomaindump ldap://[domain IP] -u 'domain\user' -p Password`
	- we're `ldapdomaindump`ing the `[domain IP]`
	- with the user (`-u`) `'domain\user'`
	- and their password (`-p`) `Password1`
	- This will dump to the current directory, can specify directory with `-o`
This comes in handy for whenever you can see all the information about accounts in the domain