- Two types:
- Local File Inclusion (LFI)
	- files that are already on the target server
	- you go and find them via directory traversal, etc.
	- exploit a vuln to view database file
- Remote File Inclusion (RFI)
	- allows an attacker to include a file from somewhere else
	- leads to RCE or arbitrary code execution
- typical path is whenever someone is taking information from a user, then using that path to a file without sanitizing it.
	- might ask for a language, but if it doesn't validate the input, we can get directory traversal.
		- very DBWA esque stuff.
# Local File Inclusion
- Looking for local files
- webpage that allows you to show a recipe from a drop down
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_184440.png]]
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_184452.png]]
- From there we can send the traffic into burp and see how it works
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_184606.png]]
- It has the file name in the address, so we can probably do some directory traversal
- Send to Repeater and edit the request it's making
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_184645.png]]
- Send it out and see what happens
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_184703.png]]
	- Success! We got account information and hashes.
- Can also do this with Intruder with built in requests, but it's pro version only
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_190831.png]]
# Remote file inclusion
- Now let's see if we can get an external script running
- same page, but we see something different this time:
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_192745.png]]
	- We got a bit of a different request now, they might be filtering it
- let's check the filters
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_192916.png]]
	- we get an error when we try some directory traversal
- Let's see if we can get around that first:
	- we can remove the filter for `../` by putting a `../` between our `../` to create `..././` so that when it removes the `../`, we get the `../`
		- `..././..././..././..././..././etc/passwd` for the whole ding dang thing.
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_193029.png]]
	- Success! Let's see if we can get something else injected into this as well:
- Trying out some RFI stuff
	- Let's see if google will be called when we plug it into the address bar:
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_194034.png]]
	- oh hell yeah son
- This means we can now use PHP filters to read PHP files and get database or WordPress credentials
	- https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion#wrapper-phpfilter for your php filter attempts
	- Let's give it a shot
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_195128.png]]
	- looks like that didn't work, let's try going up a directory and give it another shot
		- remember that we have to do this via `..././` to bypass the filter.
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_195800.png]]
	- We got something!
		- B64 encoded string.
		- Burp has a built-in decoder
	- ![[Kali-Linux-2022.2-vmware-amd64_-_VMware_Workstatio240309_200030.png]]
		- we got creds!
# Challenge
- any request you can plug in the fuzzing lists and find out
- Use `ffuf` this time
- get the request from Burp and save it locally
	- right click, save as files
- Then we edit the request and put `FUZZ` where we want to be fuzzing
	- `nano api.txt`
- After we do that, plug the command and go:
- `ffuf -request api.txt -request-proto http -w /usr/share/seclists/Fuzzing/LFI/LFI-Jhaddix.txt -fw 19,20`
	- `-request` specifies the request file
		- In this case it's `api.txt` the file we edited earlier
	- `-request-proto` specifies the protocol of the request
		- In this case, it's `http`
	- `-w` specifies the wordlist
		- We'll be using `/usr/share/seclists/Fuzzing/LFI/LFI-Jhaddix.txt` a list from Jason Haddix, a bug bounty OG.
	- `-fw` filters out key words
		- In this case, anything that is the size `19` or `20` because those don't work
		- the bigger the size, the more likely the juicy bits we have
- Found some requests that work
- Plug them into Burp and get the account creds for the server
### File Inclusion Lists ^file-inclusion-lists
- /usr/shared/seclists/Fuzzing/LFI