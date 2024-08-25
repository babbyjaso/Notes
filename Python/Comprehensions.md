- shorter syntax to create a list based on some [[Loops#^iterator|iterators]]
- time for some examples:
```
list1 = ["a", "b", "c"]
print(list1)

list2 = [x for x in list1]
print(list2)
```
- so this is taking each element in `list1` and iterating it in `list2`
- we can even put [[Conditionals|conditionals]] in there
	- `list3 = [x for x in list1 if x == 'a']`
		- now this will only put `'a'` in the list
	- `list8 = [x for x in range(5) if x == 0 or x == 1]`
		- prints as `[0, 1]` because only 0 and 1 were the conditions
- can also put other [[Loops#^iterator|iterators]] in lists as well
	- `list4 = [x for x in range(5)]`
	- prints as `[0, 1, 2, 3, 4]`
- can also put [[Functions and code reuse|functions]] or [[Booleans & Operators#^operators|operators]] on there
	- `list5 = [hex(x) for x in range(5)]`
	- prints as `['0x0', '0x1', '0x2', '0x3', '0x4']`
- can also put [[Conditionals#^tearnary|ternary]] conditionals
	- `list6 = [hex(x) if x > 0 else "x" for x in range(5)]`
	- prints as `['x', '0x1', '0x2', '0x3', '0x4']`
- can put [[Booleans & Operators#^operators]] in there
	- `list7 = [x * x for x in range(5)]`
	- prints as `[0, 1, 4, 9, 16]`
- can also have [[Loops#^nested|nested]] lists
```
list9 = [[1,2,3],[4,5,6],[7,8,9]]
print(list9)

list10 = [y for x in list9 for y in x]
print(list10)
```
- prints as
	- `[[1, 2, 3], [4, 5, 6], [7, 8, 9]]`
	- `[1, 2, 3, 4, 5, 6, 7, 8, 9]`
	- take the list of elements `y` from nested lists `x` and create a new list of each `y` in list `x`
- can also be applied to [[Sets|sets]]
- Join ^join
	- used to combine iterables into a single string
```
list11 = [c for c in "string"]
print(list11)

print("".join(list11))
```
- prints as `['s', 't', 'r', 'i', 'n', 'g']` then `string`
- delineator is whatever you want it to be
	- also works backwards and can put whatever interable between the list
		-  `print("$".join(list11))`
		- prints as `$s$t$r$i$n$g$`
- if you're not sure what it's doing, you can always write it out in a longer format