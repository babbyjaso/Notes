- when we get the results of a boolean, we can set a condition to perform an action
	- fancy word for if statements???
- A thing that is true will be true
	- ```if True:
		print("True")```
		- This will print
	- ```if False:
		print("False")```
		- This will not print
	- ```if not False:
		print("not false")```
		- This will print
- You can have a second comparator
```
if 1 < 1:
	print("1 < 1")
elif 1 <= 1:
	print("1 <= 1")
```
- You can have a catchall
```
if 1 < 1:
	print("1 < 1")
elif 1 <= 0:
	print("1 <= 1")
else:
	print("else 1")
```
- You can not have an else statement if you don't want anything to happen if it's all false
- you can have multiple comparisons
```
if 1 < 1:
	print("1 < 1")
elif 1 <= 1:
	print("1 <= 1")
elif 2 <= 2:
	print("2 <= 2")
else:
	print("else reached")
```
or
```
if 1 > 0 and 0 < 1:
	print("1 > 0 and 0 < 1")
```
- remember that [[Booleans & Operators#^and|and]] requires both to be correct
- If you don't care if both are correct you can use [[Booleans & Operators#^or|or]] 
```
if (1 < 0 or 0 < 1) and 1 == 1:
	print("1 < 0 or 0 < 1")
```
- We can have this in shorthand as well
	- `if 0 < 1: print("0 < 1")`
		- prints `0 < 1` as expected
- Tearnary ^tearnary
	- operator used to return a value based on the result of a conditional expression
		- don't have to use an `elif`, can just use a tearnary
	- `print("1 >= 1") if 1 >= 1 else print ("1 < 1")`
		- This is the same as the block below:
```
if 1 >= 1:
	print("1 >= 1")
else:
	print("1 < 1")
```
- can create more complicated Tearnaries:
```
print ("1") if 0 <= 1 else print("2") if 0 < 1 else print ("3")
```
- always structure your conditionals in the way that you want it to be processed
	- everything in python is linear