- anonymous function that does not have a name
	- any number of arguments
	- can only have one expression
		- no multiple lines
- `add_4 = lambda x : x + 4`
	- So, this function is a variable that takes x and adds 4
	- print it out: `print(add_4(4))`
	- get: `8`
- `add = lambda x, y: x + y`
	- add `x` and `y`
	- print it out: `print(add(10,4))`
	- get: `14`
```
is_even = lambda x: x % 2 == 0
print(is_even(2))
print(is_even(3))
```
- lambda to tell us if something is even or not
- then try 2 and 3 to see if they're even
- breaking string into blocks
	- `blocks = lambda x, y: [x[i:i+y] for i in range(0, len(x), y)]`
	- this will break a string `x` into size `y`
	- this is a [[Dictionaries|Dictionary]] in a [[Lists|list]] that is saying for each 2 block chunk (what we input as `y`), take that many from how long x is and break it up into those bits
- if you don't get it or aren't comfortable with it, can always just define a function to do the same thing