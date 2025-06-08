# Python Basics

### Math Operators

- These are from highest to lowest precedence:

|Operator|Operation|Example|
|---|---|---|
|`**`|Exponent|`2 ** 3 = 8`|
|`%`|Modulus|`22 % 8 = 6`|
|`//`|Integer division|`22 // 8 = 2`|
|`/`|Division|`22 / 8 = 2.75`|
|`*`|Multiplication|`3 * 3 = 9`|
|`-`|Subtraction|`5 - 2 = 3`|
|`+`|Addition|`2 + 2 = 4`|

- Each of these operators can precede an equal sign to make an _augmented assignment operator_
    - For example, `var %= 1` is equivalent to `var = var % 1`
    - This works for string concatenation with `+=`
    - This also works for lists:
        ```Python
        my_list = ['item']
        my_list *= 3
        my_list # prints ['item', 'item', 'item']
        ```

### Walrus Operator

- The walrus operator `:=` allows for the assignment of a variable within an expression while still returning its value

```Python
print(my_var:="Hello World!") # assigns my_var the value of "Hello World!" & prints
```

### Data Types

- Integers (duh)
- Floats (double duh)
- Strings (triple duh)

### Concatenation & Replication

```Python
# Concatenation
>>> 'Alice' 'Bob'
# 'AliceBob'

# Replication
>>> 'Alice' * 5
# 'AliceAliceAliceAliceAlice'
```

### Variables

- Names must be one word (obviously) and can only use letters, numbers, and underscores
    - Cannot begin with a number
    - Underscore shouldn’t be the first character

### Comments

```Python
# comment

a = 1  # comment after code

# multi-line
# comment

'''
other kind of multi-line comment
'''
```

### The `print()` Function

- Writes the value of the arguments it is given, including multiple arguments, floats, and strings
- Printed without quotes & automatically adds a space between items

```Python
>>> a = 1
>>> print("Hello World!", a)
# Hello World! 1
```

### The `end` Keyword

- The keyword argument `end` can be used to avoid the newline after the output or end the output with a different string

```Python
>>> phrase = ['printed', 'with', 'a', 'dash', 'in', 'between']
>>> for word in phrase: 
				print(word, end='-')
# printed-with-a-dash-in-between
```

### The `sep` Keyword

- The keyword `sep` specifies how to separate the objects, if there is more than one

```Python
>>> print('cats', 'dogs', 'mice', sep=',')
# cats,dogs,mice
```

### The `input()` Function

- Takes input & converts it into a string

```Python
>>> my_name = input('What is your name? ') # default message (i.e. print within input)
>>> print('Hi, {}'.format(my_name))
# What is your name? Ryan
# Hi, Ryan
```

### The `len()` Function

- Evaluates to the integer value of the number of characters in a string, list, dictionary, etc.

```Python
>>> len('hello'
# 5
>>> len(['cat', 3, 'dog'])
# 3
```

- This should not be used to test if lists are empty, as we can simply use Boolean evaluation for emptiness testing
    - For example, `a = true` if the list `a` is not empty

### The `str()`, `int()`, and `float()` Functions

- These functions allow you to convert the type of variable

# Control Flow

### Comparison Operators

|Operator|Meaning|
|---|---|
|`==`|Equal to|
|`!=`|Not equal to|
|`<`|Less than|
|`>`|Greater than|
|`<=`|Less than or equal to|
|`>=`|Greater than or equal to|

### Boolean Operators

- The three Boolean operators in order of precedence are:
    - `not`
    - `and`
    - `or`
- These can be mixed with the comparison operators above

```Python
>>> (4 < 5) and (5 < 6)
# True

>>> (4 < 5) and (9 < 6)
# False

>>> (1 == 2) or (2 == 2)
# True
```

### `if` Statements

- These work the same as other programming language conditional statements:

```Python
>>> name = 'Ryan'
>>> if name == 'Ryan':
				print('Hi, Ryan')
# Hi, Ryan

>>> name = 'Collin'
>>> if name == 'Ryan':
				print('Hi Ryan')
		elif name == 'Ryan 2.0':
				print('Hi 2.0')
		else:
				print('Who are you?')
# Who are you?
```

- These can also be done with a _ternary operator_:

```Python
>>> print('kid' if age < 18 else 'adult')
```

- Ternary operators can also be chained together:

```Python
>>> print('kid' if age < 13 else 'teen' if age < 18 else 'adult')
```

### Switch-Case Statements

- In Python, the syntax is as follows:

```Python
>>> temp = 201
>>> match temp:
			case 200:
					print('OK')
			case 201:
					print('The world is ending!')
			case 202:
					print('OK')
# The world is ending!
```

- We can also use the pipe character `|` or `or` to allow Python to return the same response for multiple cases:

```Python
>>> temp = 502
>>> match temp:
			case 200 | 201:
					print('OK')
			case 300 | 307:
					print('OK')
			case 400 | 401:
					print('OK')
			case 500 | 502:
					print("Holy moly we're all doomed!")
# Holy moly we're all doomed!
```

- You can also match by length of iterable:

```Python
>>> responses = [200, 300, 404, 500]
>>> match responses:
			case [a]:
					print('One response')
			case [a, b]: 
					print('Two reponses')
			case [a, b, *rest]:
					print('More than two responses')
			case _:
					print('No responses') # Default value '_' is used for a default case
# More than two responses
```

- You can also use these statements for class matching:

```Python
>>> response = 'ryan'
>>> match response:
			case int():
					print('Arg, you have an integer matey!')
			case str():
					print('String')
			case _:
					print('How did we get here')
# String
```

- Last but not least, you can use these statements for input/variable validation:

```Python
>>> response = 300
>>> match response:
			case int():
					if response > 99 and response < 500:
							print('Valid')
			case _:
					print('Invalid')
```

### `while` Loop Statements

- Continues to repeat execution as long as an expression is True

```Python
>>> spam = 0
>>> while spam < 5:
			print('Hello World!')
			spam += 1
# Hello World!
# Hello World!
# Hello World!
# Hello World!
# Hello World!
```

### `break` Statements

- If execution reaches a `break` statement, it immediately exits the `while` loop’s clause:

```Python
>>> while True:
			name = input('Please type your name: ')
			if name == 'your name':
					print('You are my least favorite person on this forsaken Earth')
					break
			else:
					print('Thank youuuu :)')
# Please type your name: your name
# You are my least favorite person on this forsaken Earth
```

### `continue` Statements

- When the program execution reaches a `continue` statement, the program execution immediately jumps back to the start of the loop:

```Python
>>> while True:
			name = input('Who are you? '):
			if name != 'Ryan':
					continue
			password = input('Password? (It is a fish.): ')
			if password == 'swordfish':
					break
# Who are you? Collin
# Who are you? Ryan
# Password? (It is a fish.): swordfish
# Access granted.
```

### `for` Loop Statement

- The `for` loop iterates over a list, tuple, dictionary, set, or string:

```Python
>>> pets = ['Coco', 'Loki', 'Coop']
>>> for pet in pets:
				print(pet)
# Coco
# Loki
# Coop
```

### The `range()` Function

- The `range()` function returns a sequence of numbers

```Python
>>> for i in range(5):
				print(i)
# 0
# 1
# 2
# 3
# 4

# range(start, stop, step)
>>> for i in range(0, 10, 2):
				print(i)
# 0
# 2
# 4
# 6
# 8
```

- You can also use negative numbers for the step argument

### `for else` Statement

- The `for else` statement allows us to specify a statement to execute in case the full loop has been executed
    - This is only useful when a `break` condition can occur in the loop

```Python
>>> for i in [1, 2, 3, 4, 5]:
				if i == 3:
						break
		else:
				print('This is only executed when no items are equal to 3')
```

### Ending a Program with `sys.exit()`

- The `exit()` function allows us to exit in Python

```Python
>>> import sys
>>> while True:
				feedback = input('Type exit to exit: ')
				if feedback == 'exit':
						print(f'You typed {feedback}.')
						sys.exit()
# Type exit to exit: open
# Type exit to exit: exit
# You typed exit
```

# Functions

### Function Syntax

```Python
>>> def say_hello(name, greeting): # arguments
				print(f"{greeting} {name}")	# keyword arguments
				return 1 # return value
>>> result = say_hello("Ryan", "Hello")
# Hello Ryan
>>> print(result)
# 1
```

### The `global` Statement

- If you need to modify a global variable within a function, you must use the `global` statement:

```Python
>>> def spam():
				global eggs
				eggs = 'spam'
>>> eggs = 'global'
>>> spam()
>>> print(eggs)
# spam
```

### Lambda Functions

- If you need a single-line, single-expression, and anonymous function, you can create a `lambda` function:

```Python
>>> def add(x, y):
				return x + y
# is equivalent to
>>> add = lambda x, y: x + y
```

- You can also nest lambda functions, as seen here:

```Python
>>> def make_adder(n):
				return lambda x: x + n
>>> plus_3 = make_adder(3)
>>> plus_5 = make_adder(5)

>>> plus_3(4)
# 7
>>> plus_5(4)
# 9
```

# Lists & Tuples

### Lists

- Lists are Python’s implementation of arrays
    - Unlike in Java, this implementation can house multiple data types concurrently
- Index at $0$, negative indices function as expected
- You can subset a list with slicing:

```Python
>>> furniture = ['table', 'chair', 'rack', 'shelf']
>>> furniture[1:3] # [1:3)
# ['chair', 'rack'] 
>>> furniture[:2]
# ['table', 'chair']
```

- Get the length using `len()`
- Value assignment via index works as expected

### List Concatenation & Replication

```Python
>>> [1, 2, 3] + ['A', 'B', 'C']
# [1, 2, 3, 'A', 'B', 'C']

>>> [1, 2, 3] * 2
# [1, 2, 3, 1, 2, 3]
```

### Loops & Lists

```Python
>>> furniture = ['table', 'chair', 'rack', 'shelf']
>>> for item in furniture:
				print(item)
# prints each item 

>>> for index, item in enumerate(furniture):
				print(f'index: {index} - item: {item}')
# index: 0 - item: table
# index: 1 - item: chair
# etc. 

>>> price = [100, 50, 80, 40]
>>> for item, amount in zip(furniture, price):
				print(f'The {item} costs ${amount}')
# The table costs $100
# The chair costs $50
# etc.
```

### The `in` and `not in` Operators

```Python
>>> furniture = ['table', 'chair', 'rack', 'shelf']
>>> 'rack' in furniture
# True
>>> 'bed' in furniture
# False
```

### Multiple Assignment

```Python
>>> furniture = ['table', 'chair', 'rack', 'shelf']
>>> temp1, temp2, temp3, temp4 = furniture

>>> temp1
# 'table'
>>> temp2
# 'chair'
# etc.

>>> a, b = 'table', 'chair'
>>> a, b = b, a
>>> print(a)
# 'chair'
```

### The `index` Method

```Python
>>> furniture = ['table', 'chair', 'rack', 'shelf']
>>> furniture.index('chair')
# 1
```

### Adding Values to Lists

```Python
>>> furniture = ['table', 'chair', 'rack', 'shelf']
>>> furniture.append('bed')
>>> furniture
# ['table', 'chair', 'rack', 'shelf', 'bed']

>>> furniture.insert(1, 'dresser')
>>> furniture 
# ['table', 'dresser', 'chair', 'rack', 'shelf', 'bed']
```

### Removing Values from Lists

```Python
# continuing code above...
>>> del furniture[2]
>>> furniture
# ['table', 'dresser', 'rack', 'shelf', 'bed']

>>> furniture.remove('shelf')
>>> furniture
# ['table', 'dresser', 'rack', 'bed']
```

- If a value is repeated in a list, only the first one will be removed using the `remove()` function

### The `pop()` Function

- `pop()` removes & returns the last element of a list:

```Python
>>> animals = ['cat', 'bat', 'rat', 'elephant']
>>> animals.pop()
# elephant
>>> animals
# ['cat', 'bat', 'rat']
```

- You can also pop a specific element by specifying the index

### Sorting with `sort()`

```Python
>>> numbers = [2, 5, 3.14, 1, -7]
>>> numbers.sort()
>>> numbers
# [-7, 1, 2, 3.14, 5]
```

- By default, `sort()` sorts lowest to highest, but this can be reversed by passing `reverse=True` to the `sort()` calls
- `sort()` cannot handle mixed-type lists
- To sort in regular alphabetical order, you must set `key=str.lower` in the `sort()` call:

```Python
>>> letters = ['a', 'z', 'A', 'Z']
>>> letters.sort(key=str.lower)
>>> letters
# ['a', 'A', 'z', 'Z']
```

- Additionally, you can use the `sorted()` function to return a new list instead of modifying the original list

### Tuples

- Tuples are immutable lists that are shown with parentheses instead of square brackets
- To convert between the two data types:

```Python
>>> tuple(['cat', 'dog', 5])
# ('cat', 'dog', 5)
>>> list(('cat', 'dog', 5))
# ['cat', 'dog', 5]

# we can also use list() for breaking up strings
>>> list('hello')
# ['h', 'e', 'l', 'l', 'o']
```

# Dictionaries

- Example dictionary:

```Python
>>> my_cat = {
				'size': 'fat'
				'color': 'grey'
				'disposition': 'loud'
		}
```

### Setting/Getting Keys/Value Pairs Using the Subscript Operator `[]`

```Python
# continuing the code above... 
>>> my_cat['age_years'] = 2
>>> print(my_cat)
# {'size': 'fat', 'color': 'grey', 'disposition': 'loud', 'age_years': 2}

>>> print(my_cat['size'])
# 'fat'
>>> print(my_cat['eye_color'])
# error
```

### The `values()` and `keys()` Functions

```Python
>>> pet = {'color': 'red', 'age': 42}
>>> for value in pet.values():
				print(value)
# 'red'
# 42

>>> for key in pet.keys(): # you can omit .keys() here as this is default behavior
				print(key)
# 'color'
# 'age'
```

### The `items()` Function

```Python
# using the same dict from above...
>>> for item in pet.items():
				print(item)
# ('color', 'red')
# ('age', 42)
# these are tuples
```

### The `get()` Function

- The `get()` function returns the value of an item with the given key
    - If the key doesn’t exist, it returns `None`
        - You can also change the default `None` value to one of your choice

```Python
>>> wife = {'name': 'Reilly', 'eyes': 'brown'}
>>> f"My wife's name is {wife.get('name')}"
# 'My wife's name is Reilly'
>>> f"Her  eyes are {wife.get('eyes')}"
# 'Her eyes are brown'

>>> f"She is deeply in love with {wife.get('husband')}"
# 'She is deeply in love with None'
>>> f"She is deeply in love with {wife.get('husband', 'meeeee :)')}"
# 'She is deeply in love with meeeee :)'
```

### Adding Items with `setdefault()`

```Python
>>> wife = {'name': 'Reilly', 'eyes': 'brown'}
>>> wife.setdefault('has_hair', True)
>>> wife
# {'name': 'Reilly', 'eyes': 'brown', 'has_hair': True)
```

### Removing Items

- The `pop()` method removes & returns an item based on the given key:

```Python
# using the same wife dict from above...
>>> wife.pop('eyes')
# 'brown'
>>> wife
# {'name': 'Reilly'}
```

- The `popitem()` method removes the last item in a dictionary & returns it:

```Python
# using the same wife dict from earlier...
>>> wife.popitem()
# ('eyes', 'brown') (RETURNED AS TUPLE)
>>> wife
# {'name': 'Reilly'}
```

- The `del()` method removes an item based on a given key (i.e. `pop()` with no return)
- The `clear()` method removes all items in a dictionary

### Checking Keys/Values in a Dictionary

```Python
>>> person = {'name': 'Ryan', "L's": 'None'}
>>> 'name' in person.keys()
# True
>>> 'height' in person.keys()
# False but he's really tall I bet
>>> 'skin' in person # you can omit .keys()
# False

>>> 'Ryan' in person.values()
# True
>>> "Many L's" in person.values()
# False/Not a chance
```

### Merging Dictionaries

```Python
>>> dict_a = {'a': 1, 'b': 2}
>>> dict_b = {'b': 3, 'c': 4}
>>> dict_c = {**dict_a, **dict_b}
>>> dict_c
# {'a': 1, 'b': 3, 'c': 4}
```

# Sets

- A set is an unordered collection with no duplicate elements

### Initializing a Set

- You can either create a set using curly braces `{}` or using the function `set()`

```Python
>>> s = {1, 2, 3}
>>> s = set([1, 2, 3])

>>> s = {} # this will create a dictionary instead of a set, so be cautious
```

### Unordered Collections of Unique Elements

- A set automatically removes all duplicate values

```Python
>>> s = {1, 2, 3, 2, 3, 4}
>>> s
# {1, 2, 3, 4}
```

- As this data type is unordered, you cannot index sets

### Adding to & Updating Sets

```Python
>>> s = {1, 2, 3}
>>> s.add(4)
>>> s
# {1, 2, 3, 4}

>>> s.update([2, 3, 4, 5, 6])
>>> s 
# {1, 2, 3, 4, 5, 6}
```

### Removing & Discarding from Sets

```Python
# using the original s set from above...
>>> s.remove(3)
>>> s
# {1, 2}

>>> s.remove(3)
# error
```

- To avoid this error, replace `remove()` with `discard()`

### Set Union, Intersection, & Difference

- Union:

```Python
>>> s1 = {1, 2, 3}
>>> s2 = {3, 4, 5}
>>> s1 | s2
# {1, 2, 3, 4, 5}
```

- Intersection:

```Python
>>> s1 = {1, 2, 3}
>>> s2 = {2, 3, 4}
>>> s3 = {3, 4, 5}
>>> s1 & s2 & s3
# {3}
```

- Difference:

```Python
>>> s1 = {1, 2, 3}
>>> s2 = {2, 3, 4}
>>> s1 - s2
# {1}
>>> s2 - s1
# {4}
```

- For symmetric difference, use `^` :

```Python
>>> s1 = {1, 2, 3}
>>> s2 = {2, 3, 4}
>>> s1 ^ s2
# {1, 4}
```

# String Manipulation

### Escape Characters

|**Escape character**|**Prints as**|
|---|---|
|`**\'**`|Single quote|
|`**\"**`|Double quote|
|`**\t**`|Tab|
|`**\n**`|Newline (line break)|
|`**\\**`|Backslash|
|`**\b**`|Backspace|
|`**\ooo**`|Octal value|
|`**\r**`|Carriage Return|

### Raw Strings

- To print a raw string (i.e. printing the actual escape character sequences), you can insert the letter ‘r’ before the string

### Multi-Line Strings

```Python
>>> print(
		"""
		this
		is
		a
		multi-line
		string
		"""
		)
# this
# is
# a
# multi-line
# string
```

### Indexing & Slicing Strings

```Plain
H   e   l   l   o       w   o   r   l   d    !
0   1   2   3   4   5   6   7   8   9   10   11
```

```Python
>>> spam = 'Hello World!' 

>>> spam[0] # indexing
# 'H'
>>> spam[-1]
# '!'

>>> spam[0:5] # slicing
# 'Hello'
>>> spam[::-1]
# '!dlrow olleH'
>>> spam[6:-1]
# 'World'
```

### The `in` and `not in` Operators

```Python
>>> 'Hello' in 'Hello World'
# True
>>> 'HELLO' in 'Hello World'
# False
>>> '' in 'spam'
# True

>>> 'cats' not in 'cats and dogs'
# False
```

### Letter Case Functions

```Python
>>> greet = 'Hello world!'

>>> greet.upper()
# 'HELLO WORLD!'

>>> greet.lower()
# 'hello world!'

>>> greet.title()
# 'Hello World!'
```

```Python
>>> spam = 'Hello world!'

>>> spam.islower()
# False

>>> 'HELLO'.isupper()
# True

>>> 'abc12345'.islower()
# True

>>> '12345'.islower()
# False
>>> '12345'.isupper()
# False
```

### The `isX` String Methods

|**Method**|**Description**|
|---|---|
|isalpha()|returns `True` if the string consists only of letters.|
|isalnum()|returns `True` if the string consists only of letters and numbers.|
|isdecimal()|returns `True` if the string consists only of numbers.|
|isspace()|returns `True` if the string consists only of spaces, tabs, and new-lines.|
|istitle()|returns `True` if the string consists only of words that begin with an uppercase letter followed by only lowercase characters.|

### The `startswith()` and `endswith()` Functions

```Python
>>> 'Hello world!'.startswith('Hello')
# True

>>> 'Hello world!'.endswith('world!')
# True

>>> 'Hello'.startswith('Hello')
# True
>>> 'Hello'.endswith('Hello')
# True
```

### The `join()` and `split()` Functions

```Python
>>> ''.join(['My', 'name', 'is', 'Ryan'])
# MynameisRyan

>>> ' '.join(['My', 'name', 'is', 'Ryan'])
# My name is Ryan

>>> 'My name is Ryan'.split()
# ['My', 'name', 'is', 'Ryan']

>>> 'My name is Ryan'.split('n')
# ['My', 'name is Rya', 'n']
```

### Removing Whitespace

```Python
>>> spam = '     Hello World     '
>>> spam.strip()
# 'Hello World'

>>> spam.lstrip()
# 'Hello World     '

>>> spam.rstrip()
# '     Hello World'

>>> strip = 'SpamSpamBaconSpamEggSpamSpam'
>>> spam.strip('Spam')
# BaconSpamEgg
```

### The `count()` Method

```Python
>>> sentence = 'one sheep two sheep three sheep four'
>>> sentence.count('sheep')
# 3

>>> sentence.count('e')
# 9

>>> sentence.count('e', 6)
# 8
# returns count of e after 'one sh' i.e 6 chars since beginning of string

>>> sentence.count('e', 7)
# 7
```

### The `replace()` Method

```Python
>>> text = "Hello, world!"
>>> text.replace("world", "planet")
# 'Hello, planet!'

>>> fruits = "apple, banana, cherry, apple"
>>> fruits.replace("apple", "orange", 1)
# 'orange, banana, cherry, apple'

>>> sentence = "I like apples, Apples are my favorite fruit"
>>> sentence.replace("apples", "oranges")
# 'I like oranges, Apples are my favorite fruit'
```

# Object-Oriented Python

- OOP is fundamentally the same in Python as it is in other languages, so below is just an example of a class & its children

```Python
# The Shape class is defined with an abstract area method, 
# which is intended to be overridden by subclasses.
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    # The Rectangle class is defined with an __init__ method that initializes
    # width and height instance variables.
    # It also defines an area method that calculates and returns
    # the area of a rectangle using the width and height instance variables.
    def __init__(self, width, height):
        self.width = width  # Initialize width instance variable
        self.height = height  # Initialize height instance variable

    def area(self):
        return self.width * self.height  # Return area of rectangle


 # The Circle class is defined with an __init__ method
 # that initializes a radius instance variable.
 # It also defines an area method that calculates and
 # returns the area of a circle using the radius instance variable.
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius  # Initialize radius instance variable

    def area(self):
        return 3.14 * self.radius ** 2  # Return area of circle using pi * r^2

# The shapes list is created with one Rectangle object and one Circle object. The for
# loop iterates over each object in the list and calls the area method of each object
# The output will be the area of the rectangle (20) and the area of the circle (153.86).
shapes = [Rectangle(4, 5), Circle(7)]  # Create a list of Shape objects
for shape in shapes:
    print(shape.area())  # Output the area of each Shape object
```