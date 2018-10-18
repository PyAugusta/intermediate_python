## Python Decorators #

In this section, we're going to look at a special kind of function which is referred to as a **decorator**. Simply put, **decorators** are just functions which receive a different function as input, *wrap* that function with some logic, then return that new logic as a new function. To understand this better, let's see an example of this so-called *function wrapping*:

```python
def register_user(user):
    print('Adding ' + user + ' to database')

def include_greeting(process_function):
    def wrapper(user):
        print('Hello ' + user)
        process_function(user)
        print('Enjoy!')
    return wrapper

greet_and_register = include_greeting(register_user)
```

Here, we created a function that takes a user and "registers" them into our database. When called alone, it performs nothing more than what it is coded to do.

```python
>>> register_user('cory')
Adding cory to the database
```

Next, we created out include_greeting function. The purpose is to create and return a function that *wraps* the processing_function we provide it. To do this, we define a wrapper function - it runs some extra commands before and after executing the processing_function we gave it. Now, since the wrapper function was defined inside of include_greeting, it will never exist until include_greeting is called. When include_greeting is executed, it returns the entire wrapper function, which we can then use anytime.

```python
>>> greet_and_register('cory')
Hello cory
Adding cory to the database
Enjoy!
```

This example should demonstrate that functions are **first-class objects**, which just means that they can be passed around as arguments and used in ways similar to how you might use other common types, like strings and integers.

So, you might be thinking of ways to use this wrapping technique already, but maybe you hate the syntax - well, you aren't alone! Thankfully, Python provides special syntax to make things a little cleaner.

```python
def include_greeting(func):
    def wrapper(user):
        print('Hello ' + user)
        func(user)
        print('Enjoy!')
    return wrapper

@include_greeting
def greet_and_register(user):
    print('Adding ' + user + ' to the database')
```

See that fancy **@include_greeting** bit - that's the syntactic sugar we use to make decorators more appealing to look at.

## Challenge #

Often, when you're working on your coding project, you may find yourself wondering how long individual functions take to run. Write a decorator that gets the time before and after a function runs, then prints out the difference in seconds.

Some hints:

- One way to get the current time is by importing the time module and calling ```time.time()```. This function returns a float that represents your computer's current time.

- The function that you wrap can be anything you want. time.sleep(n) will block code execution for n seconds.

- You can access a function's name (should you choose to print it out as well) by accessing func.__name__

## Bonus #

One of the great things about Python is that it provides simple, easy to use *introspection*. Introspection refers to your ability to inspect and probe objects to learn more about them. For example, you may have used the builtin **help** function while working in the Python shell.

When it comes to decorators though, introspection can sometimes fail to get you the information you really need. This is an issue that the builtin module **functools** solves thanks to its **.wraps** function.

Feel free to explore this more, but just know, that if you want to maintain some of that awesome introspection that Python provides, you'll have to use **functools.wraps()** like so:

```python
import functools

def include_greeting(func):
    @functools.wraps(func)
    def wrapper(user):
        print('Hello ' + user)
        func(user)
        print('Enjoy')
    return wrapper
```

## Fin #

Hope you enjoyed this section - now get out there and decorate!

