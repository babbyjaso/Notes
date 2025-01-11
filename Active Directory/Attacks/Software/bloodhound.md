GUI database for Domain information

`sudo pip install bloodhound`
- for the latest and greatest
`sudo neo4j console`
- Spins up the bloodhound console
- after this, you get a browser
- gotta log in with neo4j:neo4j
	- will change password after you log in
`sudo bloodhound`
- Bloodhound is now running
- log in through the browser
Once needed to gather the information from the host and export it, but no longer. We use Injectors.
- `sudo bloodhound-python -d domain.local -u [username] -p [password] -ns [nameserver] -c all`
	- We are running `bloodhound-python`
	- on the `-d` domain `domain.local`
	- using the `-u` user `username`
	- with their `-p` password `[password]`
	- on the `-ns` name server `[nameserver]`
		- typically the domain controller
	- and we're collecting (`-c`) everything (`all`)
You got all the .json files, time to import
- import all the json info into the database
- go up to the menu and find all your data
Analysis tab
- we can do various queries to find information in a GUI environment
