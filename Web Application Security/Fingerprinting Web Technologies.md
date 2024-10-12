Notes test!
Recon is everything, and this is about recon.
- There's a bunch of open programs on Intigriti
	- When you're getting started on Intigriti, look at the responsible disclosure ones because they're less populated
	- be sure to review the scope!
-  Time to enumerate the website!
	- Understand the methodology, not the tools
	- Tools
		- builtwith.com https://builtwith.com/
			- gives all the technology profiles for the website
		- wappalyzer https://www.wappalyzer.com/
			- in browser tool to analyze the website's technologies
			- breaks it down into categories
		- `curl -I` 
			- gives additional resolution when trying to look up the site
			- If you need to follow a redirect -L option
		- securityheaders.com https://securityheaders.com/
			- will tell you all the security headers that curl spits out, but clean
		- `nmap -p443 -A`
			- if you wanna get crazy, --script=http-server-header