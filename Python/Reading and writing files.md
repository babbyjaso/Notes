- There are standard functions for reading, writing and creating files
	- `f = open('top-100.txt')`
	- This returns what mode it is in
		- `<_io.TextIOWrapper name='top-100.txt' mode='r' encoding='cp1252'>`
	- we can specify what modes of operation
		- read
		- append
		- write
		- create
	- `f = open('top-100.txt', 'rt')`
	- will return
		- `<_io.TextIOWrapper name='top-100.txt' mode='rt' encoding='cp1252'>`
		- This just reads the text `rt` 
- what if we wanna read the file?
	- `print(f.read())`
		- will print out the file, line by line
	 `for line in f:`
		`print(line.strip())`
	- can use this to break it down line by line but using a loop
- what if we wanna do something specific?
	- `print(f.readlines())`
	- shows each line in the file
	- if you do `.readlines()` twice, you will end up reading a blank list because it's already been read.
	- we can get around it with `f.seek(0)`
		- this resets it (seeking 0)
- what if we're done with the file?
	- `f.close()`
- what if we wanna write a file?
```
f = open("test.txt", "w")
f.write("test line!")
f.close()
```
- this opens the file "test.txt" in write mode, writes "test line!" then closes the file
	- if we input something different to write like `f.write("test line two!")` because it's in write mode, it will overwrite it
	- to append, we put it in append mode `"a"`
- What if you wanna see where you're at with the file handler?
	- `print(f.name)`
		- names the file
	- `print(f.closed)`
		- tells you if it's closed or not
	- `print(f.mode)`
		- tells you the mode it's in
- Sometimes the file isn't in ufc-8
	- just specify when you open it
		- `open('rockyou.txt', encoding='latin-1')`