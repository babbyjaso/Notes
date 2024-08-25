- we've done a lot of start to finish scripts
- now, let's do something that runs infinitely
	- don't wanna copy/paste the same code over and over until you get the desired results
- While loop ^while-loop
```
a = 1
while a < 5:
	a += 1
	print(a)
```
- always know your exit condition
	- in this case it's the `a += 1`
		- adds one until it reaches 5, then the loop stops
- For loop ^for-loop
```
for i in [0, 1, 2, 3, 4]:
	print(i+6)
```
- prints out each number in sequence and adds 1
	- This is an iterator ^iterator
```
for i in range(5):
	print(i+6)
```
- Does the same as the first For loop
- Now let's get nested ^nested
```
for i in range(3):
	for j in range(3):
		print(i,j)
```
Here's what happens:
```
0 0
0 1
0 2
1 0
1 1
1 2
2 0
2 1
2 2
```
- Column 1 is `i`, column 2 is `j`
	- goes through each value of `j` first, then each value `i`
- all of these loops execute until completed
	- we can terminate loops using `break` ^continue
```
for i in range(5):
	if i == 2:
		break
	print(i)
```
Returns
```
0
1
```
- Once `i == 2` the loop broke (stopped)
- And if we don't want to terminate the loop early: `continue` ^continue
```
0
1
3
4
```
- Once the loop hit 2, it goes back to the iteration instead of printing
- And if we want something to pass once it hits the requirement: `pass` ^pass
```
for i in range(5):
	if i == 2:
		pass
	print(i)
```
- just lets it through because nothing changes to the data
- we can loop over any iteral object an iterator from
```
for c in "string":
	print(c)
```
Returns
```
s
t
r
i
n
g
```
And
```
for key, value in {"a":1, "b":2, "c":3}.items():
	print (key, value)
```
Returns
```
a 1
b 2
c 3
```
