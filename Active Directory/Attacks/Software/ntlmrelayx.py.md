This is to set up a fake wpad so that we get network information
- [WPAD](https://en.wikipedia.org/wiki/Web_Proxy_Auto-Discovery_Protocol) information here
- DNS discovery, more or less
Options:
- `-6`
	- Use IPv6
- `-t`
	- Target machine
	- typically want this to be the DC
- `-wh`
	- fake WPAD
	- `name.domain.local`
- `-l`
	- loot
	- where do you want your information stored?
	- creates a folder named whatever you name it
