## Python Lambda Functions #

We are all familiar with defining functions in Python, but on occasion we may decide to utilize lambda functions instead of our traditional named functions. A lambda is referred to as an **anonymous** function because it does not require a name. Let's look at some examples to get a better idea of what this all means:

```python
def add_ten(n):
    return n + 10

twenty = add_ten(10)
print(twenty)
>>> 20
```

So, we created a function that adds 10 to some input - a very basic example, but you get the idea. But, what if this function was only going to be used once - maybe as an argument to some different function? In those cases, it often isn't neccessary to define the function the traditional way.

Enter lambda functions:

```python
add_ten = lambda n: n + 10

twenty = add_ten(10)
print(twenty)
>>> 20
```

Above, we used the **lambda** keyword to define our function, and the assignment operator (=) to save it to the add_ten variable. It's not really anonymous when used this way, but it should demonstrate to you the syntactic differences.

Let's look at that syntax more closely.

A traditional function definition looks like this:

```python
def function_name(arguments):
  return expression
```

Lambdas are quite similar, just without the return statement:

```python
function_name = lambda arguments: expression
```

These syntax differences make lambdas idea for quick, single-expression functions. But, where would we most likely see these things in the wild?

Did you know that some functions actually take other functions as arguments? One example is the list's **sort** method. It includes a keyword argument called **key**. You can supply a function to the **key** argument that tells the method exactly which piece of each list element you want to sort on.

Here's an example where we have a list of tuples, but want to sort on the second item in each. Keep in mind that the sort method performs its operations *in place*, meaning it will not return a new list - rather, it will update the original.

```python
tlist = [('pepper', 13), ('banana', 2), ('sugar', 9), ('wheat', 15)]

tlist.sort(key=lambda item: item[1])

print(tlist)
>>> [('banana', 2), ('sugar', 9), ('pepper', 13), ('wheat', 15)]
```

Some other very common examples of functions that take functions as arguments:

- map(function, iterable) - Runs the function on each item in the iterable (i.e. list)

```python
# Square each item in the list
squared = map(lambda x: x**2, [1, 2, 3])
print(list(squared))
>>> [1, 4, 9]
```

- filter(function, iterable) - Runs the function on each item - if the expression evaluates to True, it is not returned.

```python
# Keep only values greater than 10
gt_ten = filter(lambda x: x>10, [13, 1, 4, 99, 10]
print(list(gt_ten))
>>> [13, 99]
```

## Challenge #

Use what you've learned to complete the following tasks:

1. Start with a list called **nums** that contains integers 1 through 10
2. Create a new list called **divided** that holds each value from **nums**, but divided by 42
3. Create another list that only holds values from **divided** which, when mutiplied by 10, are greater than 1

## Fin #

That should do for now - in your spare time, research other functions that accept lambdas and try them out.
