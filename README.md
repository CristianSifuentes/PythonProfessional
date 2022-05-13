# PythonProfessional

How does Python work?

Garbage collection ??
Pycache ??


How to organize your project folders?

module??


A module is any Python file. Generally, it contains code that you can reuse.

🗄 A package is a set of modules. It always owns the __init__.py file.

An example of organizing 🐍Python files is as follows.


----

What are types?

Typed is a classification of programming languages, we have four types:

* Static
* Dynamic
* Weak
* Strong

Language typing depends on how it treats data types.

Static typing is the one that raises an error at compile time, example in JAVA:


Static →→ Detect errors at compile time. Does not run until correct. For example, Java

Dynamic →→ Detect the error at runtime. It tells us the error when it reaches the line of code. For example, Python

Strong →→ More stringency with data types. Adding a number + a letter will throw an error.

Weak →→ Less strict with data types. If I want to add number and letter, I would concatenate them as strings. Cast data types automatically. For example, PHP

--------

Static typing in Python


To make Python statically typed, it is necessary to add some additional syntax to what has been learned, and this feature can only be applied from version 3.6 onwards.

```python
# De esta manera se declara una variable, se colocan los dos puntos (:), el tipo de dato y para finalizar se usa el signo igual para asignar el valor a la variable.

<variable> : <tipo_de_dato> = <valor_asignado>

a: int = 5
print(a)

b: str = "Hola"
print(b)

c: bool = True
print(c)

```

In the same way, this typing methodology in Python can be used for functions by adding the minus sign after the greater than sign to determine the data type. Example:



```python
def <nombre_func> ( <parametro1> : <tipo_de_dato>, <parametro2> : <tipo_de_dato> ) ->  <tipo_de_dato> :
	pass

def suma(a: int, b: int) -> int :
	return a + b

print(suma(1,2))

# 3

```

There is a factory library that comes pre-installed with Python called typing, which is very useful for working with typing with data structures between version 3.6 and 3.9, so:



```python
from typing import Dict, List

positives: List [int] = [1,2,3,4,5]

users: Dict [str, int] = {
	"argentina": 1.
	"mexico": 34,
	"colombia": 45,
}

countries: List[Dict[str, str]] = [
	{
		"name" : "Argentina",
		"people" : "45000",
	},
	{
		"name" : "México",
		"people" : "9000000",
	},
	{
		"name" : "Colombia",
		"people" : "99999999999",
	}
]

```

```python
from typing import Tuple, Dict, List

CoordinatesType = List[Dict[str, Tuple[int, int]]]

coordinates: CoordinatesType = [
	{
		"coord1": (1,2),
		"coord2": (3,5)
	},
	{
		"coord1": (0,1),
		"coord2": (2,5)
	}
]

```

mypy module
.
The mypy module is complemented by the typing module as it will allow you to display weak typing errors in Python.



--------------
Practicing static typing

Following the tips of intermediate python course, from terminal:
mkdir new_folder
git init
py -m venv venv
touch .gitignore
type in .gitignore file

```python

# Ignore the enviroment files when you push to github.
venv
```

avenv (alias to activate venv: .\venv\Scripts\activate)
pip install mypy
pip list (to check mypy)
touch palindrome-py
code palindrome-py
Make your code!!!
mypy palindrome-py --check-untyped-defs