# Python Identifiers

Cannot Start with numbers
a-z1-9\_
reserved words : 33
True , False , None -> First Word Capital
Except these 3 reserved words all contain smaller

bin() -> Number to binary Return the binary representation of an integer.
oct() -> Return the octal representation of an integer.
hex() -> Return the hex representation of an integer.

bool data type
True , False

string data type
string is just an arra

eg shubhang
string slicing 3: -> ang
string slicing :3 -> shu

eg durga 1:40 -> urga

len() -> Length of string

# Type Casting

s -> can be converted to int
sjhefueh -> can not be converted to int

# Check Data type

typeof()

# Id of Data type

id()

# Why Id of integer is same and complex differrent

python cache adress of from -5 to 256 numbers

# List

- Insertion
- Hetrogenous
- Growable

Char

- Ordered
- Mutable
- Hetrogenous
  Immutable data type in python -> Tuple

# Set

No indexing
No douplication

# Frozen Set

Same as set except Immutable

# \r

overwrite the length of character

print("hello\rupes") -> upeso

# \b

backslash

# ~ bitwise compilementame

-> answer always -1 \* number -1
eg -> 1 -> -2

# << Operator

eg) 10 << 2 -> 40
how to 10 _2 = 20 _ 2 = 40

# >> Operator

eg) 10 >> 2 -> 10 //2 = 5 // 2 -> 2

# Terneray operator

eg) x = 30 if x<10 else 40

- For greater in 3 numbers
  eg) x = a if (a > b and a>c) else b if (b > c and b > a) else c

# Eval in Python

```python3
x = "print(55)"
eval(x) -> Ouput: 55
```

# Hashing in Tuples

Dictionary does not have index like list or tuples instead it uses hash function to store data efficiently

Tuples are hashable because they are immutable

But same cannot be applied on the list because it is mutable

t = (10,20)
print(hash(t)) -> This will work
print(hash([1,2,3,4])) -> This will give you error as list is mutable and cannot be hashed

# Dictionary

.FromKeys

```python
a = ['1','2','3']
print(dict.fromkeys(a))
```

Used to quickly initialize the dictionary by providing a default value to all the keys.

.Update

# Get Function Source Code

from inspect get source
source(functioname)

from inspect getfile

getfile(functioname)

# Dunder Methods or Data Model Methods

```python3
__xyz__ methods
```

The Protocol View of python
The Inheritance View of python

How object orientation in python works

Closure order duality
