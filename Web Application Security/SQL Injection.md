- Infamous and tricky
- easy money if found, but typically isn't found these days
# If you want to set up your own machine
- Start mysql
	- `sudo systmctrl stat mysql`
- login to mysql
	- `sudo mysql`
- Create DB and tables:
```
CREATE DATABASE sqldemo;
use sqldemo;
CREATE TABLE users(
	username varchar(255)
	password varchar(255)
	age int,
	PRIMARY KEY (username)
);
```
- Insert data into users table:
```
INSERT INTO users (username, password, age)
VALUES ("jeremy", "letmein", 30);

INSERT INTO users (username, password, age)
VALUES ("jessamy", "kittems", 31);
```
# The actual starter
- things are passed into a table and then data is pulled based on the argument
- basically SQL injections are just modifying queries
- Need some practice or a refresher?
	- https://www.w3schools.com/sql/
# Lab time
- we have a search bar that searches usernames
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240314_214809.png]]
- Put in a username, get information
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240314_215652.png]]
- but if we change what our query is, we can get all the users
	- `' or 1=1#` gives us this:
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240314_215805.png]]
- So what's happening is the search query has a preset query, and we can abuse the input of that to get everything from that table
	- likely a `select 'email' from 'users' where 'username = input'`
	- so we end what it's looking for with a `'`
	- and then put down something that always results in true
		- 1 will always equal 1
	- then we terminate the query with `#`
		- can also use `-- -` because this is mysql, but there are other terminators for other database programs
		- will get a cheatsheet later
- But what if we want...more
	- we're going to be using the `UNION` function of SQL
		- from [W3 Schools](https://www.w3schools.com/sql/sql_union.asp)
		- `The SQL UNION operator is used to combine the result-sets of two or more SELECT statements. It selects only distinct values by default and removes any duplicate rows between the statements.`
	- so with that we're going to select something from password column
	- the only issue is we can only select as many columns as from the original query
		- also, we need to make sure that we're querying the correct type of data
			- if we try to query a string where an integer is present, it won't work
			- fix this using `null(int)`
		- so let's find out how many columns
		- `jeremy' union select null#` will get us started
			- if this doesn't work, add another null until we get some feedback
		- success, we got something with three `null`
			- `jeremy' union select null,null,null#`
			- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240314_222018.png]]
			- so it's selecting 3 columns and probably only printing 2
	- Now we can cook
		- `jeremy' union select null,null,version()#` will give us a version of the database.
			- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240314_222252.png]]
		- `jeremy' union select null,null,table_name from information_schema.tables#` will spit out all the tables that we can select from
			- holy mother
			- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240314_222437.png]]
		- `jeremy' union select null,null,column_name from information_schema.columns#` will spit out all of the columns we can select from.
		- so now we have tables and columns, so we can select jeremy's password
			- `jeremy' union select null,null,password from injection0x01#`
				- the password column from the table "injection0x01" which has all the information for this lab.
			- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240314_223953.png]]
				- bingo bango
# [SQL Cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)

# Blind SQL injection attacks
- this time we have a username and password field
	- also valid credentials
	- entering the valid credentials gets us to our dashboard
- Testing out the User/PW field reveals that we can't inject in that field
	- checking content length is a good indicator of when we get something successful and when we get something unsuccessful
	- also is a search feature in burp for responses that we can double check
- we do have a cookie that is set however
	- checking content length and trying injections on that will help
- we got injection in the cookie!
	- the only way we know is because it changes the behavior of the website, it does not present information
- Because all this does is change the behavior of the website, this is a Blind SQLi
	- going to have to input queries that spit out true/false data and then we can start extracting data from it that way
	- 20 questions but from a database
- because of this guessing game, we're gonna use sqlmap
	- for fuzzing reasons
- You're gonna need to know [substrings](https://www.w3schools.com/sql/func_sqlserver_substring.asp) ^substring
	- "The SUBSTRING() function extracts some characters from a string."
	- we choose a character, a length and the position of that character
	- so from there we can start building out the password.
- Doing this manually takes a long time
	- so we send it to intruder
	- make the part we guess the attack itself
- Let's do this in sqlmap ^sqlmap
	- take the bare request and put it into sqlmap
	- `sqlmap -r request.txt --level=2 --dump -T injection0x02`
		- `sqlmap` name of the program
		- `-r` the specified request, which is `request.txt`
		- `--level=2` the level of the test we want to perform
			- [more details](https://github.com/sqlmapproject/sqlmap/wiki/Usage#level)
			- The higher the level, the more of the request it will test
			- we need level 2 to test cookies, which is our point of injection
		- `--dump` dumps all the tables from the database
		- `-T` the tables to enumerate
		- `injection0x02` from this database
	- answer a couple of questions about how to break down the request and we'll get a database
	- ![[240315_2249Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio.png]]
	- Success! `jessamy`'s password is `ZWFzdGVyZWdn`
		- note that while we did get the first character correct in burp, `z`, it was not the correct case
# Challenge Lab
- we got a website that has various AI generated products on it
- a search bar will take us to the specific page for that product
	- it takes only exact matches, probably where we can inject
	- I called it, an SQLi test shows it's good
- union search
	- took 4 nulls
	- using `version()` we get the version of 8.0.35
		- ![[240315_2315Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio.png]]
	- trying a specified query doesn't get us anywhere
- different encoding?
	- HTML doesn't work
	- URL doesn't work 
		- I thought this one would because the query is in URL
- Walkthough
	- basically everything I did until 2:52
- I FOUND WHAT I DID WRONG HOLY SHIT
	- the table name is "injection0x03_users"
	- `' union select null,null,null,password from injection0x03_users#`
	- we get the password "onigirigadaisuki"
# Second order SQLi
- where your payload is not executed until later
- example is creating a user
	- we can inject data into this user's UN/PW and have that executed later
	- likely the UN, because that shows
- [[SQL Injection#^sqlmap|sqlmap]] has a second order flag that you can use, check it out from 