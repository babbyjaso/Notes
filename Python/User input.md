- I _need_ to be able to change the script without changing the script!
	- well too bad, but we can make the user put something in.
	- `input()`
		- assign this to a variable and it will just echo our input
	- put in some text to make it more clear
		- `test = input("enter the IP:")`
- Let's do a loop:
```
while True:
	test = input("Enter the IP: ")
	print(">>> {}".format(test))
	if test == "exit":
		break
	else:
		print("exploiting...")
```
- The loop is `while True` because true will always be true
	- put in your IP
	- prints out your input using `">>> {}".format(test)`
		- curly braces returns what the input is
	- if the user puts in "exit", it will stop
	- otherwise, it's going to print "exploiting..."
	- this will keep asking for IPs until you put in "exit"