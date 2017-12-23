---
layout: post
title: Functional Programming with python
comments: true
permalink: /:title
image: ''
date:   2017-12-23 00:03:56
tags:
- Python
- Functional Programming
- Lambda
description: Functional programming with python
categories:
- Functional Programming
serie: learn


---

Back when I started reading [SICP](https://mitpress.mit.edu/sicp/) (Structure and Interpretation of computer programs), I was quite fascinated by the power of a functional programming language like lisp which was invented in 1958. Quite old, Isn't it? So, I started digging into python for its functional programming features. Python supports the creation of anonymous functions (i.e. functions that are not bound to a name) at runtime, using a construct called "lambda".

 If you write a program in any programming language,which is ever been invented or ever will be invented, It can someway be coded in lambda calculus.  This is kind of Turing hypothesis by Alan Turing, which states you can code anything on his Turing machine. Turing machine and lambda calculus is kinda equivalent. Any Turing machine program can be translated in to lambda calculus program and vice versa.

Lambda calculus is present in most major programming language today and is the basis of all the functional programming language like Haskell or Lisp. This wasn't the case 10-15 years ago, but is the case today. So, today in this article , we will study some of the way to convert basic programs in python into one liner using functional paradigm.

The lambda calculus is basically got nothing with it. If you want to do these things in lambda calculus, you need to encode them.

Let's first start by how lambda function works:

Syntax: `lambda arguments: expression`

It can have any number of arguments but can contain only one expression.

Example:

```python
square = lambda x : x*x
```

is equivalent to 

```python
def square(x):
   return x * x
```



Lets look at some more examples.

 Convert this into a single line?

```python
x = 1
y = x + x
z = y + y
print z + z
```

Sol.

```python
print(lambda x: (lambda y:( lambda z: (z + z)) (y + y) ) (x + x) )(1)
```

## Functions

 Convert this into single line?

```python
def f(x):
    return x*10
print f(3)
```

Sol.

```python
print( (lambda x:(x*10))(3)) 
#or in a better way would be
print(lambda f:f(3)) (lambda x: x*10)
```

Lambda function also works with `*args` and `**kwargs`.



Till now, we did some work where we were assigning some variable. What if we don't want to assign any variable. How to do in the Lambda way?

Consider a situation like this:

```python
do_something()
print 42
```

We can do it in single line like this:

```python
print (lambda _: 42)( do_something() )  #Here the return value of do_something goes to _ which is a unused variable. It will print 42 always
```

or we can do it like this without using lambda.

```python
print (do_something(), 42)[1] #We made a tupple and printed the second element always which is 42
```

In python 3, `print()` is a function and as we know, in python, every function is a first class object. ie. it can be assigned and returned to some variable, we can assign the print() function to lambda. Whereas in python2, `print` is a statement, which can't be assigned to any variable and hence it cannot be passed to a lambda variable and cannot be used with lambda.

```python
(lambda _: 2)(print(1))
```



However we can use print as a function in python2  from builtins.(Note: We could import print function from `__futute__` but as it is a compiler directive rather than a module, we can't make it into one line. It has to be in `from __future__ import` form only. Later in this post, we will study how we can import modules in one line.)

```python
__print = __builtin__.__dict__['print']
#now you can use __print as a print function as in python3
```

## Classes

```python
class Person(object):
    def __init__(self):
        ...
```

```python
Person = type('Person', (object,),{'__init__':lambda self: ...})

```

eg.

```python
x = 2 + 2
def f(x):
    return x * 5
print x
y = f(x)
```

```python
(lambda x:
	(lambda f:
    	(lambda _:
        	(lambda y: None) f(x)
    	)(__print(x))
	)(lambda x : x * 5)
)(2 + 2)

```

## Control flow

```python
if boolean:
    x = 5
else:
    x = 10
print x*100
```

Just think for a while How can we reduced into a one liner?

We can use conditional expression(_ if_ else _) plus continuation passing.

To make it one liner, for simplicity, We can reduced the above expression like this:

```python
def continuation(x):
    return x * 100
if boolean:
    x = 5
    return continuation(x)
else:
    x = 10
    return continuation(x)
```

Transforming it into one liner using lambda we can have,

```python
(lambda continuation:
 	(lambda x:
     	continuation(x)
    )(5)
 if boolean else
 	(lambda x:
     	continuation(x)
    )(10)
)(lambda x: __print(x*100))
```

## While loop

To implement while loop using lambda, we would be using recursion. But as lambda are anonymous functions and we can't call it by name. To solve this, we have `Y combinator`(Not the HackerNews :p). Y-combinator can be used to implement recursion on these anonymous functions. In simple terms, it takes one function as input and creates a recursive version as an output. It was pretty difficult for me to fully understand Y combination in one go. [Here](http://mvanier.livejournal.com/2897.html) is a great article about Y combinator if you want to learn more. Below is the implementation of Y combinator using python.

```python
Y = (lambda f: lambda(x: x(x))
    (lambda y: f(lambda: y(y)())))
```

So, how to convert the below snippet into one liner?

```python
x = 5
while x < 20:
    x = x + 4
print x
```

Here is the answer.

```python

lambda x:
	(lambda while_loop:
    	while_loop(x)
    )
    
(Y(lambda while_loop:
 	(lambda x:
    	(lambda x:
    		while_loop(x)
        )(x+4)
    if x<20 else
    	__print(x)
    )
  )
)(5)
```



### More Resources

1. https://medium.com/@ayanonagon/the-y-combinator-no-not-that-one-7268d8d9c46
2. http://www.ics.uci.edu/~lopes/teaching/inf212W12/readings/lambda-calculus-handout.pdf
3. https://www.youtube.com/watch?v=DsUxuz_Rt8g
