- CTF framework and exploit dev library
	- very useful for hackers and hacking scripts
	- does a lot of things
- `from pwn import *`
	- now we can just call functions directly from this
- so let's create a cyclic pattern for buffer overflow
	- `print(cyclic(50))`
- we can directly work with shellcode
	- `print(shellcraft.sh())`
- can send processes
```
	p = process("/bin/sh")
	p.sendline("echo hello;")
	p.interactive()
```
- this will get us an interactive shell using `sh` and will start off with the printed `hello;`
- can also interact with remote processes
```
	r = remote("127.0.0.1", 1234)
	r.sendline("hello!")
	r.interactive()
	r.close()
```
- be sure to set up NC to listen to 1234 lol
- we can pack and unpack numbers
	- `print(p32(0x13371337))`
- we can unpack numbers as well
	- `print(hex(u32(p32(0x13371337))))`
- we can load files
```
	l = ELF('/bin/bash')
	print(hex(l.address))
```
- we can search for addresses of processes
	- using the `l` variable above:
	- `print(hex(l.address))`
- we can find out the entry point of the program
	- `print(hex(l.entry))`
- we can find the location in the global offset table
	- `print(hex(l.go['write']))`
- we can find information about the procedure linkage table
	- `print(hex(l.plt['write']))`
- load files by searching the binary
	```
	for address in l.search('/bin/sh\x00'):
		print(hex(address))
	```
- if we need to search for one specific addres
	- `print(hex(next(l.search(asm('jmp esp')))))`
- we don't have to figure all this out ourselves, we just gotta do the [ROP function](https://docs.pwntools.com/en/stable/rop/rop.html)
```
r = ROP(l)
print(r.rbx)
```
- can use XOR
	- `print(xor("A","B"))`
- can encode in Base64
	- `print(b64e(b"test"))`
- can decode B64
	- `print(b64d(b"dGVzdA=="))`
- can make MD5 hashes
	- `print(md5sumhex(b"hello"))`
- can make SHA1 hashes
	- `print(sha1sumhex(b"hello"))`
- can make the bits out of anything
	- `print(bits(b'a'))`
- can unbit your bits
	- `print(unbits([o, 1, 1, 0, 0, 0, 0, 1]))`