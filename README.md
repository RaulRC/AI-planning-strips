### STRIPS - Monkey PROBLEM

#### Description

https://en.wikipedia.org/wiki/Monkey_and_banana_problem

```
"""
Definition
===============================

 items = [monkey, banana, box]

 positions = [0, 1, 2]

OPERATORS
===============================

Move(subject, x1, x2)
PC: monkeyAt(x1), monkeyLevelDown
A: monkeyAt(x2)
D: monkeyAt(x1)

PushBox(x1,x2)
PC: monkeyAt(x1), boxAt(x1), monkeyLevelDown
A: monkeyAt(x2), boxAt(x2)
D: monkeyAt(x1), boxAt(x1)

ClimbBox(x, direction={Up, Down})
PC: monkeyAt(x), boxAt(x), monkeyLevelDown
A: monkeyLevelUp
E: monkeyLevelDown

HaveBanana(x)
PC: monkeyAt(x), bananaAt(x), boxAt(x), monkeyLevelUp
A: GetBananaAt(x)


INITIAL STATE - Properties
===========================

monkeyAt0, monkeyLevelDown, bananaAt1, boxAt2


GOAL STATE - Properties
===========================

GetBanana(at 1)

"""
```



#### Usage

The following code will execute the default example: 

```python3 strips.py```

Having the following (possible) output:

```
Initial state:
---------
{'monkeyAt0', 'bananaAt1', 'monkeyLevelDown', 'boxAt2'}

Goal state:
---------
{'haveBanana'}

STRIPS START
==============
Apply Movemonkey(0,2) to state
Apply PushBox(2,1) to state
Apply ClimbBoxUp(at 1) to state
Apply GetBanana(at 1) to state

Done! Final plan:
[Movemonkey(0,2), PushBox(2,1), ClimbBoxUp(at 1), GetBanana(at 1)]
```

This is an iterative version of STRIPS with heuristic based on the usage of a stack in which either Properties or Operations are pushed defining this way the sub-goals needed to reach, in a regressive approach of the search.


User is able to change the configuration of the states directly on the ```src/strips.py``` file:

```{python}
initial = State()
#Simple state
initial.setProperties({"monkeyAt0", "bananaAt1", "boxAt1", "monkeyLevelDown"})

#Lab state
initial.setProperties({"monkeyAt0", "bananaAt1", "boxAt2", "monkeyLevelDown"})

goal = State()
goal.setProperties({'haveBanana'})
```

Code is commented for a better comprenhension.
