---
title: Python
---

# Basics

## Ints in python

```
x = 1 # int
y = 2. # not an int, a float. Reapeat with me, flOat. 
```

ints are closed in python under subtraction, multiplication, and
addition, but not division like in regular math.

```
print(x + y)
$ 3.0
print(x + 1)
$2
```

## Division between ints always generates a float in python

```
x/2
$0.5
```

## Integer division is done with the // operator

```
print(7 // 3)
$2
print(7 % 3) # remainder operator.
$1
```

## Strings are created with **"** or **'**.

```
s = 'A string'
t = "It's nice weather outside."
print(t)
It's nice weather outside.
```

## Booleans values are uppercase True and False.

```
boolean = True
print(not boolean)
$False
```

## Relops. That is, relational operators.
```
print(4 < 8)
$True
print(4 == 8)
$False
```

## Special no value value, like nullptr, or NULL
```
c = None
print(c)
$None
```

## Testing if none:
```
if c is None:
   print("C is really None")

if c:
   print("Doesn't work, will fail if c is 0")
```

## shorthand for the +,-,\*,/,etc ops.
```
x = 2
x = x + 1
x += 1
print(x)
$4
x *= 3
print(x)
$12
```


# Lists and Tupples

```
l = ['a', 'b', 'c']
print(l)
$['a', 'b', 'c']
```

## A lot like a C array:

```
l2 = ['cat', 'dog', 'bird']
print(l2[0])
$cat
print(l2[1])
$dog
```

## Slice a list.
```
l = ['cat', 'dog', 'bird', fish', 'ant', 'fly']
l[:3] # till element 3 starting from 0, exludes that element.
$['cat', 'dog', 'bird']
```

## Slice a list from an index to another.
```
l[1:3] # till element 3 starting from 1, exludes the [3] element.
$['dog', 'bird']
```

## get the last element with the -1 shorthand.
```
l[-1] # prints the very last element; -2 the second to last and so on.
'fly'
```

## Address indices backwards
```
l[-2:] # From the penultimate, doesn't exlude anything.
$['ant', 'fly]
```

## slicing doesn't generate errors ?
```
l = ['a', 'b', 'c', 'd', 'e', 'f']
```
Well, this does produce errors:
```
print(l[-10])
```

## list operations

### Append.

```
l.append('spider')
l
$ ['a', 'b', 'c', 'd', 'e', 'f', 'spider']
```

### Concatenate.

```
l + [1, 2, 3]
$ ['a', 'b', 'c', 'd', 'e', 'f', 'spider', 1, 2, 3]
```

One is allowed to mix types, i.e. lists are heterogeneous. That's
Greek for you can mix types, said in a pretentious way.

### Remove a specific element from a list.
```
x = l.pop(3) # to retrieve and remove any element.
print(x)
$d
print(l)
$['a', 'b', 'c', 'e', 'f', 'spider']
```

### Reverse operator.
```
l.reverse()
l
$['spider', 'f', 'e', 'c', 'b', 'a']
```

### Sort operator
```
l = l + ['cat']
l.sort()
l
$ ['a', 'b', 'c', 'cat', 'e', 'f', 'spider']
```

### Everything to uppercase

```
"dog".upper()
$'DOG'
```

### Capitalize strings.

```
"dog".capitalize()
$'Dog'
```

### To capitalize each entry in the list. 

```
l_capitalized = [s.capitalize() for s in l]
l_capitalized 
$['A', 'B', 'C', 'Cat', 'E', 'F', Spider']
```

### applying a function to each entry if it satisfies a condition:

```
[s.capitalize() for s in l if startswith("C")]
$['C', 'Cat']
```

### Get the length of a string/list.
```
len(l) # gives you the lentgh of a list or a string.
$7
print([len(s) for s in l])
$[1, 1, 1, 3, 1, 1, 6]
```

There are even more functions that affect lists.

# Tuples

```
p1 = (1., 2.)
p2 = (3.1, 3.2)
```

## The advantage with tuples is that they're easy to take apart.
```
x, y = p1
print(x, y)
$1.0 2.0
```

## Triple tuple

```
import traceback
try:
   x, y, z = p2
except:
   print(traceback.format_exc())
```

## When you don't get enought values:

```
$Traceback (most recent call last):
$  File "<ipython-input-165-023e370181fb>", line 3, in <module>
$    x, y, z = p2
$ValueError: not enough values to unpack (expected 3, got 2)
```

## If you don't care about one of the values:

```
x, _ = 1
x
$1.0
```

# Strings

```
s = 'A string'
t = "B string'
```

## String concatenation
```
print(s + " " + t) # concatenation
$ A string B string
```

## Split a string into an array of strings
```
l = t.split() # split according to spaces by default.
print(l)
$['B', 'string']
```

## Join is the reverse of split and the delimiter is what gets dereferenced.
```
" ".join(l)
$"B string"
```

## Capitalize each word and rejoin it.
```
" ".join([x.capitalize() for x in t.split()])
$"B String"
```

## strings are just like lists.
```
t[1:]
$'string'
```

# Encodings

```
s = "Ouvrez la fenêtre, s'il vous plaît"
print(s)
$Ouvrez la fenêtre, s'il vous plaît
print(type(s))
$<class 'str'>
```

## Use utf8
```
bs = s.encode('utf8')
print(type(bs))
$<class 'bytes'>
```

## utf8 as the encoding
```
print(bs)
$b"Ouvrez la fen\xc3\xaatre, s'il vous pla\xc3\xaet"
```

## Go from utf8 (bytes) back to unicode or whatever strings are
```
ut = bs.decode('utf8')
print(ut)
$Ouvrez la fenêtre, s'il vous plaît
```

- encoding is important because like SI units they can ruin your
mission to mars.  decode()'s default is utf-8 btw.

- slicing bytes lists, unencoded strings works fine but addressing
a single byte returns the string value of the byte.

# Dictionaries

Dictionaries are hashtables with sweet, sweet syntatic sugar.

```
n_of_paws = {'cat': 4, 'fish':0, 'bird': 2, 'snake': 0}
n_of_paws['fish']
$0
```

## Dictionary constructor

```
d = dict(dog=4, cat=4, bird=2, fish=0) # another way to build dictionaries.
d
${'bird': 2, 'cat': 4, 'dog': 4, 'fish': 0}
```

## Get to get a value when the key might be missing.
```
print(n_of_paws.get('fish')) # the get member function is used when you don't know if the key is in the dictionary.
$0
```

## None is returned by get when the key is missing.
```
print(d.get("Elephant"))
$None
```

## to check whether something's in a dictionary you can use the in operator:

```
print("elephant" in n_of_paws)
$False
```

## Nicknames example of dictionaries

```
nicks = {'Robert': 'Rob', 'Alexander': 'Alex'}

def to_nick(n):
   nn = nicks.get(n)
   return n if nn is None else nn

print(to_nick('Robert'))
$Rob
print(to_nick('Helen'))
$Helen
```

## Alternative way of adding an element to the dictionary

```
d = {'luca': 4, 'anna': 5}
d['helen'] = 8
```

## Getting all the keys
```
s = d.keys() # returns the list of all the keys
for sname in s:
   print(sname)
$luca
$anna
$helen
```

## The stored value of the dictionary function keys() gets updated dynamically.

```
the_keys = d.keys()
print(the_keys)
$luca
$anna
$helen

d['fernando'] = 6 
print(the_keys)
$luca
$anna
$helen
$fernando
```

This dynamic behaviour is not very useful according to Luca. Better use:

```
the_keys = list(d.keys()) # doesn't get updated behind the scenes.
```

## Get dictionary values 
```
d.values()
$ dict_value([4, 5, 8, 6])
```

## It's also possible to get the items, that is the key, value pairs:
```
list(d.items())
[('luca', 4),
 ('anna', 5),
 ('helen, 8),
 ('fernando', 6),]
```

## Dictionary comprenhension:

```
people=['luca', 'anna', 'helen', 'fernando']
{a : d.get(a) for a in people}
```

# Sets

The defining quality of sets is that they're lists that don't allow repeated elements. 

## Create a dictionary

```
s = set() # {} would be a dictionary
print(s)
$set()
```

## Sets are just like dictionaries but **,** instead of **:**
```
set1 = {'cat', 'dog'}
set2 = {'bird', 'mouse', 'cat'}
set3 = {'dog', 'cat'}
```

## Set operators

### Union

```
print(set1 | set2) # union
$ {'cat', 'dog', 'bird', 'mouse', 'cat'}
```

### Intersection

```
print(set1 & set2) # intersection
{'cat'}
```

### Difference

```
print(set1 - set2) # difference
{'dog'}
```

### Set equality is defined element-wise. Order is unimportant.
```
set1 == set3
$True
```

## add adds elements to a set, in tests if something's in the set.
```
set1.add("The Brain")
print(set1)
${'cat', 'dog', 'The Brain'}

print('cat' in set1)
$True
```

## A trick to remove duplicates from a list is to turn it into a set.
```
my_list = [ 'lol', 'lmao', 'omw', 'omg', 'btw', 'lol' ]
uniq = list(set(my_list))
```

# Conditionals

## relops: < <= > >= == and !=
```
3 < 4
$True
```

## The *in* keyword tests membership in a data struct like lists, dictionaries, sets, or strings
```
print('a' in ['a', 'b', 'c'])
$True
```

## The *is* operator tests whether things are identical
```
[a for a in [1,2,3,4, None] if a is not None]
$ [ 1, 2, 3, 4,  None ]

if x % 2 == 0:
   print("even!")
elif x % 7 == 0:
   print("multiple of seven")
else:
   print("odd")
```

## Another way of doing if else inline:   

```
y = x + 1 if x % 2 == 0 else x + 2
print(y)
$5
```

## Conditionals Can be used in list comprehensions

```
[x if x % 2 == 0 else -x for x in range(10)]
$[0, -1, 2, -3, 4, -5, 6, -7, 8, -9]
```

## **for** for FLow CoNTroL

```
for i in range(10):
   print(i)
$0
$1
$2
$3
$4
$5
$6
$7
$8
$9
$10
```

## Iterate through a list
```
list_of_words = [ 'dog' 'duck' 'drill' 'very' ]

for w in list_of_words:
   print(w)
   if w.startswith('duck'):
      print("That's cochoe in Scz Spanish")
      break

$dog
$duck
$That's cochoe in Scz Spanish
```

## Do something while a condition is true.

```
x = 11.11
while x > 1.1:
  print(x)
  if x == 5.5:
     continue
  print("okay")
  x -= 1.1
```

## Get the index and iterate too
```
for i, w in enumerate(list_of_words):
    print("The word number", i, "is:", w)
$The word number 0 is dog
$The word number 1 is duck
$The word number 2 is drill 
$The word number 3 is very
```

## If you have a dictionary, you can iterate on it like this. 
On keys only (because .keys() returns a view over the keys):
```
for k in dictionary():
    print ("I have a", k)

for v in dictionary().itervalues:
    print ("I have a", v)

for k, v in dictionary.items():
    print("Word: ", k, " means", v)
```

# Functions

```
def addone(x):
    return x + 1

print(addone(3))
$4
```

## Functions with description comments

```
def add_one_to_prod(x, y):
    """This function adds one to the product of x and y,
    and this is how you are supposed to document what a 
    function does."""
    p = x * y
    return p + 1
print(add_one_to_prod(3,2))
$7
```

## Asserting inside a function
```
def factorial(n):
    # Assertions are useful to check that the values passed to a function make sense.
    # These assertions cause an error if not satisfied.  Try it! 
    assert type(n) is int, "n is not an integer!"
    assert n > 0, "n is not positive!"
    if n <= 1:
        return 1
    else:
        return n * factorial(n - 1)
    
factorial(4)
```


## Remember the Euclid's MCD algorithm? 

Well, I hope I do.
```
def mcd(n, k):
    assert type(n) is int and type(k) is int # I am being fussy
    assert n >= 0 and k >= 0
    if n < 2: # Case for 0, 1
        return k
    else:
        return mcd(k % n, n)
```

**Note that in the algorithm above, in the first call it might be the case that n > k, but in all other calls, n <= k (why?).**


```
mcd(342, 54)
$18
```

## optional arguments, which have a default value.
```
def incadd(x, d=1):
    return x + d

print(incadd(3, d=4))
$7
print(incadd(3))
$4
```

# Functions as arguments

```
def g(x):
    return x * x

def f(x, h=None):
    """Adds 1 to x, then applies modifier function h if any,
    and returns the result."""
    y = x + 1
    return y if h is None else h(y)

print(f(2))
print(f(2, h=g))
```

# I/O

## printing with format
```
print("I have {} chicken".format(3))
I have 3 chicken
```

## printing with format can take many arguments
```
print("{} is divisible by {}".format(10, 2))
10 is divisible by 2
```

## formatting the arguments to format
```
print("A gazillion is {:.2f}% less than a bazillion".format(15.67980))
$A gazillion is 15.68% less than a bazillion
```

## Openning a file for write 
```
with open('myfile', 'w') as f:
    f.write("hello")
```

## Openning a file for read 
```
with open('myfile') as f:
    s = f.read() # This reads the file in a single shot
print(s)
```

## Does this append?. The flag is probably a.
```
with open('mylongfile', 'w') as f:
   f.write('Hello,\n')
   f.write('World.\n')
```

## reads files line by line.

```
with open('mylongfile') as g:
   for s in g:
      print(s)
```

## importing modules

```
import math
math.sqrt(3.)

from math import sqrt as square_root
square_root(2.)
```

## Exceptions 

```
try:
    x = 34 / 'a'
except:
    x = None
print(x)
```

## The module 'traceback' is very useful to figure out where 
## exceptions happen, and what happened:

```
import traceback
try: 
    x = 34 / 'a'
except:
    print(traceback.format_exc())
```

## You can also define and raise your own exceptions, which are defined similarly to classes:

```
class Indigestion(Exception):
    pass

def eat(m, l):
    if len(l) > 2:
        raise Indigestion()
    return m + l

l = ['eggs', 'bacon', 'peanuts']

try:
    eat(['bananas'], l)
except Indigestion:
    print("Hey, that's too much.")
```


# Classes


```
class Product(object):
   def __init__(self, name, price=0., quantity=0):
      self.name = name        
      self.price = price
      self.quantity = quantity

   def __repr__(self):
      return "Hello, I am a {} and cost ${}; you have {} of me".format(
         self.name, self.price, self.quantity
      )
   
   def inflation(self, x):
      self.price *= x 

   def value(self):
      return self.price * self.quantity

cart = [
   Product('Pear', price=1.99, quantity=10),
   Product('Apple', price=0.99, quantity=15),
   Product('Onion', price=1.49, quantity=57)
]

for p in cart:
   print(p)
$Hello, I am a Pear and cost $1.99; you have 10 of me
$Hello, I am a Apple and cost $0.99; you have 15 of me
$Hello, I am a Onion and cost $1.49; you have 57 of me
```

# Decorators

## This is what we want to accomplish:
```
def fibo(n):
   return n if n < 2 else fibo(n - 1) + fibo(n - 2)

fibo(10)
$55
```

```
def stringize(func):
   def f(s):
      n = int(s)
      return str(func(n))
   return f

string_fibo = stringize(fibo)
string_fibo("10")
$'55'
```

## It is possible to define an immediately decorated function via:

```
@stringize
def plus2(n):
   return n + 2

plus2("1")   
$'3'
```

- \*args  is the list of all positional parameters.
- f(\*args) is equivalent to calling f(a, b, c) if args = ['a','b','c']

- \*\*kwargs  is the list of all named arguemnts.
- f(\*\*kwargs) is equivalent to f(a=x, b=y) if kwargs = {"a":x, "b":y}

```
import time

def timeit(func):
   def f(*args, **kwargs):
      t = time.time()
      r = func(*args, **kwargs)
      print("Time:", time.time() - t)
      return r
   return f 
```

## passing arguments to a decorator function:

```
def jso(indent = None):
   def jsonize(func):
      def f(s):
         args, kwargs = json.loads(s)
         return json.dumps(func(*args, **kwargs)
      return f
   return jsonize
```

## @jso by itself doesn't work bc jso is not a decorator.
```
@jso(indent = 2) # this does work.
```
