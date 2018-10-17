## List Comprehensions #

List comprehensions in Python provide a very easy and surprisingly readable way to create lists using Python. If you haven't been introduced to comprehension before, then you might go about creating a list in this way:

```python
old_list = ['i', 'am', 'a', 'list', 'of', 'strings']

new_list = []
for item in old_list:
    new_list.append(item.upper())

print(new_list)
>>> ['I', 'AM', 'A', 'LIST', 'OF', 'STRINGS']
```

Here, we iterate over a list of strings using a standard **for loop** - taking each item in the list, and adding its upper case version to a brand new list. Pretty straighforward. But, there is another way - it's called **list comprehension**. Check it out:

```python
old_list = ['i', 'am', 'a', 'list', 'of', 'strings']

new_list = [item.upper() for item in old_list]

print(new_list)
>>> ['I', 'AM', 'A', 'LIST', 'OF', STRINGS']
```

See what we did there? We actually perfomed our iteration and upper case operations on the same line that we declared our new list. This is comprehension - you might think of it as a modified **for loop**.

Pretty neat - but, what if I told you that you can even include conditional check *inside* the list comprehension? 

With a for loop:

```python
old_list = ['this', 'list', 'has', 'ints', 1, 2, 3, 4]

new_list = []

for item in old_list:
    if type(item) == str:
        new_list.append(item.upper())
    else:
        new_list.append(item)

print(new_list)
>>> ['THIS', 'LIST', 'HAS', 'INTS', 1, 2, 3, 4]
```

Now, with list comprehension:

```python
old_list = ['this', 'list', 'has', 'ints', 1, 2, 3, 4]

new_list = [item.upper() if type(item) == str else item for item in old_list]
print(new_list)
>>> ['THIS', 'LIST', 'HAS', 'INTS', 1, 2, 3, 4]
```

### Challenge! #

Now that you've seen some examples of list comprehension, take a look at the for loop below and try to rewrite it using list comprehension:

```python
evens_squared = []

for number in range(10):
    if number % 2 == 0:
        evens_squared.append(number ** 2)
```

Try this one too:

```python
replace_odds = []

for number in range(23):
    if number % 2 == 1:
        replace_odds.append('odd')
    else:
        replace_odds.append(number)
```

## Bonus #

As a bonus, lets try to write a nested list comprehension. What i mean, is a loop inside a loop. Take this example, where we build a deck of cards.

```python
suits = ['H', 'D', 'C', 'S']
values = ['A', 2, 3, 4, 5, 6, 7, 8, 9, 10, 'J', 'Q', 'K']

deck = []

for suit in suits:
    for value in values:
        card = (value, suit)
        deck.append(card)

print(deck)
>>> [('A', 'H'), (2, 'H'), (3, 'H'), ... ('J', 'S'), ('Q', 'S'), ('K', 'S')]
```

The equivalent loops using comprehension:

```python
deck = [(value, suit) for value in values for suit in suits]

print(deck)
>>> [('A', 'H'), (2, 'H'), (3, 'H'), ... ('J', 'S'), ('Q', 'S'), ('K', 'S')]
```

## Fin #

We'll leave off with that for now.


