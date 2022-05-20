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

--------------------------------------------------
Scope: scope of the variables

The scope is the scope that the variables have. It depends on where you declare or initialize a variable to know if you have access. Golden Rule:

a variable is only available within the region where it was created

Local Scope
It is the region that corresponds to the scope of a function, where we can have one or more variables, the variables will be accessible only in this region and will not be visible to other regions

Global Scope
By writing one or more variables in this region, they can be accessible from any part of the code.

------------------------------------------------------
closures


rules for finding a closure

 * we must have a nested function
 * the nested function must reference a value of a higher scope
 * the function that wraps the nested must return it too

when we have a class that has only one method
when we work with decorators

```python

	def main():
		a = 1
		def nested():
			print(a)
		return nested

	my_func = main()
	my_func()
```

It is a way to access variables from other scopes through a nested function. The nested function is returned and it remembers the value it prints, although when it is executed it is not within its scope.


Rules for finding a Closure
We must have a nested function
The nested function must reference a value of a higher scope
The function that wraps the nested function must also return it

-------------------------

Programming closures

image

-------------------------
decorators

A decorator is a function that receives another function as a parameter, adds things to it, and returns a different function. They have the same structure as Closures but instead of variables what is sent is a function. Example:

image

It can be done in a simpler way, with syntactic sugar (sugar syntax): When we have a code that is embellished so that we see it in a more static way, helping to understand the code more easily. In this way, we have the above code:

image

This allows you to save code by implementing features (decorators) common to different functions:

-------------------------
Programming decorators



-------------------------
Iterators

Advanced data structures
Iterators
Before understanding what iterators are, we must first understand iterables.

They are all those objects that we can go through in a cycle. They are those data structures divisible into single elements that I can go through in a loop.

But in Python things are not like that. Iterables become iterators.

Example:

```python
# Creando un iterador

my_list = [1,2,3,4,5]
my_iter = iter(my_list)

# Iterando un iterador

print(next(my_iter))

# Cuando no quedan datos, la excepción StopIteration es elevada

```

```python
# Creando un iterador

my_list = [1,2,3,4,5]
my_iter = iter(my_list)

# Iterando un iterador

while True: #ciclo infinito
  try:
    element = next(my_iter)
    print(element)
  except StopIteration:
    break

```

Shocking moment: The "for" loop within Python does not exist. It's a while with StopIteration. 🤯🤯🤯

```python
my_list = [1,2,3,4,5]

for element in my_list:
  print(element)

```
evenNumbers.py:

```python

class EvenNumbers:
  """Clase que implementa un iterador de todos los números pares,
  o los números pares hasta un máximo
  """

  #* Constructor de la clase
  def __init__(self, max = None): #self hace referencia al objeto futuro que voy a crear con esta clase
    self.max = max


  # Método para tener elementos o atributos que voy a necesitar para que el iterador funcione
  def __iter__(self):
    self.num = 0 #Primer número par
    #* Convertir un iterable en un iterador
    return self

  # Método para tener la función "next" de Python
  def __next__(self):
    if not self.max or self.num <= self.max:
      result = self.num
      self.num += 2
      return result
    else:
      raise StopIteration
```
-------------------------
The Fibonacci Sequence



```python
import time

class FiboIter():
    
    def __init__(self, max=None):
        self.max = max

    def __iter__(self):
        self.n1 = 0
        self.n2 = 1
        self.counter = 0
        return self
        
    def __next__(self):
        if self.counter == 0:
            self.counter += 1
            return self.n1
        elif self.counter ==1:
            self.counter += 1
            return self.n2
        else:
            self.aux = self.n1 + self.n2
            self.counter += 1
            self.n1, self.n2 = self.n2, self.aux
            if not self.max:
                return self.aux, self.counter

            if self.max:
                if self.aux > self.max:
                    raise StopIteration
                else:
                    return self.aux, self.counter

if __name__ == '__main__':
    for element in FiboIter():
        print(element)
        time.sleep(.05)

```
-------------------------
generators

Sugar syntax for iterators. Generators are functions that store a state. It is an iterator written in a simpler way.

```python

def my_gen():

  """un ejemplo de generadores"""

  print('Hello world!')
  n = 0
  yield n # es exactamente lo mismo que return pero detiene la función, cuando se vuelva a llamar a la función, seguirá desde donde se quedó

  print('Hello heaven!')
  n = 1
  yield n

  print('Hello hell!')
  n = 2
  yield n


a = my_gen()
print(next(a)) # Hello world!
print(next(a)) # Hello heaven!
print(next(a)) # Hello hell!
print(next(a)) StopIteration
```

Now we will see a generator expression (it is like list comprehension but much better, because we can handle a lot of
of information without having performance problems):


#Generator expression

```python
my_list = [0,1,4,7,9,10]

my_second_list = [x*2 for x in my_list] #List comprehension
my_second_gen = ()x*2 for x in my_list]) #Generator expression
```
-------------------------
Improving our Fibonacci sequence


```python
from time import sleep
def fibonacci_gen():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a+b

if __name__ == "__main__":
    fibonacci = fibonacci_gen()
    for element in fibonacci:
        print(element)
        sleep(1)
```

---------------------------
sets

Sets are a data structure very similar to lists in terms of their form, but they have certain particular characteristics:

Sets are immutable

Each element of the set is unique, that is, duplicates are not allowed, even if repeated elements are added during the definition of the set, pyhton only saves one element

the sets keep the elements in disorder

To declare them, {} are used, similar to dictionaries, only that they lack the set composition {a:b, c:d}

```python

# set de enteros
my_set = {1, 3, 5}
print(my_set)

# set de diferentes tipos de datos
my_set = {1.0, "Hi", (1, 4, 7)}
print(my_set)
```

Los sets no pueden ser leídos como las listas o recorridos a través de slices, esto debido a que no tienen un criterio de orden. Sin embargo si podemos agregar o eliminar items de los sets utilizando métodos:

add(): nos permite agregar elementos al set, si se intenta agregar un elemento existente simplemente python los ignorara
update(): nos permite agregar múltiples elementos al set
remove(): permite eliminar un elemento del set, en el caso en que no se encuentre presente dicho elemento, Python elevará un error
discard(): permite eliminar un elemento del set, en el caso en que no se encuentre presente dicho elemento, Python dejará el set intacto, sin elevar ningún error.
pop(): permite eliminar un elemento del set, pero lo hará de forma aleatoria.
clear(): Limpia completamente el set, dejándolo vació.

```python
#ejemplo de operaciones sobre sets 
my_set = {1, 2, 3} 
print(my_set) #Output {1, 2, 3} 

#añadiendo un elemento al set 
my_set.add(4) 
print(my_set) #Output {1, 2, 3, 4}

#añadiendo varios elementos al set, python ignorará elementos repetidos 
my_set.update([1, 5, 6]) 
print(my_set) #Output {1, 2, 3, 4, 5, 6}

# eliminado elementos del set 
my_set.discard(1) 
print(my_set) #Output {2, 3, 4, 5, 6}

# borrando un elemento aleatorio 
my_set.pop()
print(my_set) #Output el set menos un elemento aleatorio 

#limpiar el set 
my_set.clear()
print(my_set) # Output set() 

```

We can use existing data structures to transform them to sets using the set method:

```python

#usando listas para crear sets
my_list = [1, 2, 3, 3, 4, 5]
my_set = set(my_list)
print(my_set)  #output {1, 2, 3, 4, 5}

#usando tuplas para crear sets 
my_tuple: ('hola', 'hola', 1, 2)
my_set2: set(my_tuple)
print(my_set2) #Output {'hola', 1}
```

Sets are immutable

Sets are mutable; its elements are immutable.

---------------------------
Operations with sets

Union
Result of putting together all the elements that have both, combining both sets

```python
set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_3 = set_1 | set_2 #  -> {1, 2, 3, 4, 5}

# O de forma mas explicita
set_1.union(set_2) #  -> {1, 2, 3, 4, 5}
```
Intersection
Those that are repeated in both sets

```python

set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_3 = set_1 & set_2 #  -> {3}

# O de forma mas explicita
set_1.intersection(set_2) #  -> {3}
```

Difference
Take two sets and from one remove all the elements that the other has

```python

set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_3 = set_1 - set_2 #  -> {1, 2}

# O de forma mas explicita
set_1.difference(set_2) #  -> {1, 2}
```


Symmetric Difference
Take all elements except those that are repeated

```python

set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_3 = set_1 ^ set_2 #  -> {1, 2, 4, 5}

# O de forma mas explicita
set_1.symmetric_difference(set_2) #  -> {1, 2, 4, 5}
```
----------------------------
Removing duplicates from a list


-------------------------------
Date management


-----------------------------
Time zones



