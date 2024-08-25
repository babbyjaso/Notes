- Function ^function
	- a block of code only used when it's called
	- there's a number of them already built in
		- `print()`
		- `int()`
		- `range()`
	- we can also define our own functions:
```
def function1():
	print("hello from function!")

function1()
```
- if it were just the top two lines, it would do nothing
	- we have to call it using `function1()` to get it to do anything
- functions can also return a value
```
def function2():
	return "hello from function2!"
```
- to do anything with this, we have to assign it to a variable
	- all it does is return a string, not print it, so we gotta print it somehow
	- `return_from_function2 = function2()`
	- can also just `print(function2())`
- we can have a function require input
```
def function3(s):
	print("\t{}".format(s))

function3("parameter")
```
- breaking it down
	- input "parameter" into the function when you call it
		- this is not optional, and will throw an error if you don't have an input
	- input is assigned to `s`
	- `s` is then formatted to be tabbed over one and printed out
	- so you get: `        parameter`
- if you want multiple functions:
```
def function4(s1, s2):
	print("{} {}".format(s1,s2))

function4("s1","s2")
function4("Dude","Sweet")
```
- Prints as:
	- `s1 s2`
	- `Dude Sweet`
- You can also specify the keyword arguments
	- `function4(s2="Sweet",s1="Dude")`
		- Notice how the second argument is first in this.
	- prints as `Dude Sweet`
- can define arguments with a defined default argument
```
def function5(x = "default"):
	print("{}".format(x))

function5()
function5("not default")
```
- Prints as:
	- `default`
	- `not default`
- can handle unknown or variable number of arguments
```
def function6(s1, *more):
	print("{} {}".format(s1, " ".join([s for s in more])))

function6("function 6")
function6("function 6", "a")
function6("function6", "a", "b", "c")
```
- Prints as:
	- `function 6`
	- `function 6 a`
	- `function6 a b c`
- Let's break it down:
	- defines the function to take the arguments `s1` and `*more`
		- asterisk is for wildcards, so you can input anything
	- print out the arguments `s1` and an empty space for whatever iterable followed by the [[Comprehensions#^join|join comprehension]]
		- It will print out all of the wildcards inputed for the argument `*more` into a list
- can also print out a dictionary of arguments
```
def function7(**ks):
	for a in ks:
		print(a, ks[a])

function7(a="1", b="2", c="3")
```
- Prints as:
```
a 1
b 2
c 3
```
- Double asterisk is how you get your dictionary arguments
- We can use any data type:
```
def function8(s, f, i, l):
	print(type(s))
	print(type(f))
	print(type(i))
	print(type(l))

function8("string", 1.0, 1, ['l','i','s','t'])
```
- Prints out all the types of inputs
- the data types are anything we want them to be
- the variables used in functions are one of two (typically):
	- local
		- variables declared in a function have a local scope and can only be used in that function
	- global
		- variables declared outside of a function have a global scope and can be used by any function
```
v = 100
print(v)

def function9():
	print(v)

function9()
print(v)

def function10():
	v = 5
	print(v)

function10()
print(v)
```
- Here's the output
```
100
100
100
5
100
```
- Local variables do not affect the global variable
- you can change the local variable as much as you want
- if you want to change the global variable you have to specify that you're changing the global variable
	- `global v`
```
def function11():
	global v
	v += 1
	print(v)

function11()
print(v)
```
Prints out
```
100
101
101
```
- that's also with the additional `print(v)` above it.
- Can have functions call other functions
```
def function12():
	print("hello from function 12")

def function13():
	function12()
	print("hello from function 13")

function13()
```
Prints as:
```
hello from function 12
hello from function 13
```
- Xibit functions
- Recursion ^recursion
	- when a function calls itself
	- you need to be careful to make sure that they have a termination point
```
def function14(x):
	print(x)
	if x > 0:
		function14(x-1)

function14(5)
```
Prints as:
```
5
4
3
2
1
0
```
- Breaking it down:
	- `function14` takes `x` as an argument
	- we're gonna `print`that argument
	- if that argument is greater than 0, we're gonna take that number and subtract 1
	- repeat until x is no longer greater than 0
- recursion typically isn't necessary
- can just have other functions in an iterative manner:
```
def function15(x):
	while x>= 0:
		print(x)
		x -= 1

function15(5)
```
- This does the same as the recursive function above
- try not to copy and paste code
	- at least type it out so you can break it down.