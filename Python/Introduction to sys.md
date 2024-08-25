- provides a bunch of variables and functions related to the python runtime environment
	- gives access to data sent as part of the command line arguments when executing a script
		- useful when entering variable data in the command line when executing the script
	- comes standard with python
		- don't need to download and install it with `pip`
		- just need to import it
			- `import sys`
- can be used to interact with different file handles
	- standard in
		- the file handle that the process reads from
	- standard out
		- the file handle that the process writes to
	- standard error
		- the file handle that the process writes errors to
```
for line in sys.stdin:
	if line.string() == "exit":
		break
	sys.stdout.write(">> {}".format(line))
```
- Let's break it down
	- for everything put in to the command line
		- if it's "exit", stop (`if line.string() == "exit":)
	- write on the screen (`sys.stdout.write`) the same line with the `>> ` in front of it (`(">> {}".format(line))`)
- can also use sys to do some low level functions
	- like flush your buffer
		- writes everything in the buffer to the terminal without waiting for a trigger.
- we can make progress bars
	- there are other modules out there to help, but we can do it ourselves
```
import time

for i in range(0, 51):
	time.sleep(0.1)
	sys.stdout.write("{} [{}{}]\r".format(i, '#'*i, "."*(50*i)))
	sys.stdout.flush()
sys.stdout.write("\n")
```
- this is using carriage return `\r` to write a new line with an extra piece `i, '#'*i, "."*(50*i)` with every write
	- the first `{}` defines the step in iteration `i` 
	- carriage return:
		- return to the start of a line of text
		- `\r` in regex
- we can use sys to pass command line arguments
	- again, more modules out there to do this, but we're jerry rigging
- `print(sys.argv)`
	- this will print all arguments put into the command line when entering the script
	- this could pass a username and password to a script
- can also make sure that people put in the correct number of arguments
```
if len(sys.argv) != 3:
	print("[X] To run {} enter a username and password".format(sys.argv[0]))
```
- every argument will start with the script
- we can find the the path that the module exists in
	- `print(sys.path)`
- we can also see all the modules installed right now
	- `print(sys.module)`
- we can also exit with a specific code
	- can tell if the script worked or not
	- `sys.exit(5)` this will assign the error code `5` to the "you didn't put in a username and password" error
	- if nothing went wrong , we can put `sys.exit(0)` 
- full docs at docs.python.org
- 