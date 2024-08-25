- all about burp
- fire up burp and turn on the proxy
	- proxy is the only thing that stops the traffic, we can still passively monitor it.
- plug in your credentials
	- we're looking for `jeremy`
	- get kicked out, all we need is the authentication POST
![[vmplayer_smgZaq36pI.png]]
- time to send it to intruder, we're gonna use that to, well, intrude
![[vmplayer_8qS7sF7jEl.png]]
- once it's in intruder, we can analyze the request in detail
![[vmplayer_wf8yQta0wt.png]]
- now we can put in what we want to make into a payload
	- highlight and click the button
![[vmplayer_JTD4jMrTcP.png]]
- Now let's go assign a payload to what we wanna make a payload
![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240222_155501.png]]
- so now we put in either a wordlist or type in whatever passwords
![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240222_155859.png]]
- or we can put in a wordlist
![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240222_160033.png]]
- so now we can start attack and go 
![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240222_160627.png]]
- Burp is limited (on the community edition) so we'll use something different
- `ffuf`
	- Fuzz Faster U Fool
- let's write out a thing
- `ffuf -request req.txt -request-proto http -w /usr/share/seclists/Passwords/xato-net-10-million-passwords-10000.txt -fs 1814`
	- `ffuf` the program
	- `-request req.txt` the request that we saved into a text file from burp or whatever proxy that you can save it from
		- make sure this has the authentication request
	- `-request-proto http` what protocol are we using
		- in this case it's http
	- `-w /usr/share/seclists/Passwords/xato-net-10-million-passwords-10000.txt` the password list that we're using
	- `-fs 1814` filter the size of the response
		- will only show a specific size of what we want
		- in this case a successful login
- Let's attack
![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240222_161702.png]]
- gonna start running down the list, but as we can see here, we already have the password: `letmein`
- go try it
- authentication success!
- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240222_161838.png]]
horray!

# Brute Force MFA
- so what if the account has an MFA?
- We start off with valid creds
	- `jessamy:pasta`
- But we wanna get into a different account
	- `jeremy`
- Let's log in and see what we get:
-  ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240307_165924.png]]
- so we get a normal request, now we're gonna request the MFA
- ![[Pasted image 20240307170150.png]]
	- Weird, the username is in the webpage too. funky.
- This is also going to be in the request
	- ![[Pasted image 20240307170341.png]]
- so, what if we edited the request to have our target account when we get the correct mfa?
- Log in again, get to MFA
	- now, we're gonna become Jeremy
	- turn Interceptor on in Burp
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240307_170738.png]]
	- We're Jeremy now, forward it along
	- Success!
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240307_170910.png]]
# Challenge Lab
- Let's try and do this without a walkthrough
- We have a webpage
	- Username/Login 
	- rate limited to 5 attempts _**per account**_ before we're locked out
	- we have no username
		- let's try more usernames and less passwords
- send it to burp
	- try a junk logon just to get the creds
	- send that to Intruder
- So now that we got our template, let's make some payloads
	- We're gonna be using two payloads
		- username
		- password
	- have to select something that uses two payloads:
		- Pitchfork ^pitchfork
			- goes through payloads in pairs
				- Request one:
					- Position 1 = First payload from Set 1.
					- Position 2 = First payload from Set 2.
				- Request two:
				    - Position 1 = Second payload from Set 1.
				    - Position 2 = Second payload from Set 2.
				- Request three:
				    - Position 1 = Third payload from Set 1.
				    - Position 2 = Third payload from Set 2.
		- Cluster Bomb ^cluster-bomb
			- goes through payloads in 1:1, 1:2 pairs
				- Request one:
				    - Position 1 = First payload from Set 1.
				    - Position 2 = First payload from Set 2.
				- Request two:
				    - Position 1 = First payload from Set 1.
				    - Position 2 = Second payload from Set 2.
				- Request three:
				    - Position 1 = First payload from Set 1.
				    - Position 2 = Third payload from Set 2.
	- For this we'll go with Cluster bomb, because we wanna try every username with every password.
- Assign your payloads to the example
	- ![[Pasted image 20240307181821.png]]
	- now go set up the payloads
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240307_181912.png]]
		- we loaded in a short list of usernames
	- because we're gonna be locked out per user after 5 attempts, let's just put in some trash passwords and hope we get lucky.
		- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240307_182057.png]]
	- We're all set up, let's attack
	- Because it's so short, this doesn't take long at all
- Got two accounts
	- root
	- admin
	- eventually we get to the combo `admin:letmein`
	- Success?!
	- Let's give it a go
- try your new found credentials on the page
	- yeehaw
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240307_182255.png]]
- To do this ffuf, just make the example with ffuf:
	- change the text file to have `FUZZUSER` and `FUZZPASSWORD` to have two injection points
	- then make the user lists and pw lists
	- put it all together, you get a fuzz!
	- Also, don't forget to reset the lockouts before going for it
- appsecexplained.gitbook.io
	- our instructor's notes and some checklists