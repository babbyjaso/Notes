- python defers all checks until the line runs
- we can try-catch these using blocks
- Exception
	- error that occurs during execution that represents some runtime problem that results in a halt to normal execution
- types of blocks
	- try block
		- test a block of code
	- accept block
		- lets you handle any errors
	- finally block
		- executes regardless of anything thrown at you in the try and accept blocks
- types of errors
	- arithmetic error
		- calculation bad
	- syntax errors
	- indentation errors
- so, time to incorporate error answering into your stuff:
```
try:
	f = open("file")
except:
	print("the file does not exist")
```
- this attempts to load the file `file`
- if it can't find the file, it gives the error `the file does not exist`
- whatever you throw into the try, it will try, and if it doesn't work, it'll throw the except
- now incorporate the error into the message:
```
try:
	f = open("flsdkj")
except Exception as e:
	print(e)
```
- this will return the error `[Errno 2] No such file or directory: 'flsdkj'`
- we can also specify the catches that we're looking for
```
try:
	f = open("flsdkj")
except FileNotFoundError:
	print("the file does not exist")
```
- now this specifies which error message it's looking for
- if you want to always print out a message `finally:`
- we can also raise exceptions if we need to
```
n = 100
if n == 0:
	raise Exception("n can't be 0!")
if type(n) is not int:
	raise Exception("n must be an int!")

print(1/n)
```
- This will raise and exception if
	- `n` is 0
	- `n` is a not an integer
- we can also assert something
	- tell the code to test that condition and immediately trigger if it's false
```
n = 0
assert(n != 0)
print(1/n)
```
- this will throw an assert error because `n` is currently 0