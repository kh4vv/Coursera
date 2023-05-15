# Annotated follow-along guide: Data structures in Python

This notebook contains the code used in the instructional videos from Week 4: Data structures in Python.

As a reminder, an in-video message will appear to advise that the video you are viewing contains coding instruction and examples. This follow-along notebook has different sections for each video included in the week’s content. The in-video message will direct you to the relevant section in the notebook for the specific video you are viewing.

To skip directly to the code for a particular video, use the following links:



1.   **[Introduction to lists](#1)**
2.   **[Modify the contents of a list](#2)**
3.   **[Introduction to tuples](#3)**
4.   **[More with loops, lists, and tuples](#4)**
5.   **[Introduction to dictionaries](#5)**
6.   **[Dictionary methods](#6)**
7.   **[Introduction to sets](#7)**
8.   **[Introduction to NumPy](#8)**
9.   **[Basic array operations](#9)**
10.   **[Introduction to pandas](#10)**
11.   **[pandas basics](#11)**
12.   **[Boolean masking](#12)**
13.   **[Grouping and aggregation](#13)**
14.   **[Merging and joining data](#14)**


<a name="1"></a>
## 1. Introduction to lists


```python
# Assign a list using brackets, with elements separated by commas
x = ["Now", "we", "are", "cooking", "with", 7, "ingredients"]

# Print element at index 3
print(x[3])
```

    cooking



```python
# Trying to access an index not in list will result in IndexError
print(x[7])
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-5-0f1a2bb8a182> in <module>
          1 # Trying to access an index not in list will result in IndexError
    ----> 2 print(x[7])
    

    IndexError: list index out of range



```python
# Access part of a list by slicing
x[1:3]
```


```python
# Omitting the first value of the slice implies a value of 0
x[:2]
```


```python
# Omitting the last value of the slice implies a value of len(list)
x[2:]
```


```python
# Check the data type of an object using type() function
type(x)
```


```python
# The `in` keyword lets you check if a value is contained in the list
x = ["Now", "we", "are", "cooking", "with", 7, "ingredients"]
"This" in x
```




    False



<a name="2"></a>
## 2. Modify the contents of a list


```python
# The append() method adds an element to the end of a list
fruits = ['Pineapple', 'Banana', 'Apple', 'Melon']
fruits.append('Kiwi')
print(fruits)
```

    ['Pineapple', 'Banana', 'Apple', 'Melon', 'Kiwi']



```python
# The insert() method adds an element to a list at the specified index
fruits.insert(1, 'Orange')
print(fruits)
```

    ['Pineapple', 'Orange', 'Banana', 'Apple', 'Melon', 'Kiwi']



```python
# The insert() method adds an element to a list at the specified index
fruits.insert(0, 'Mango')
print(fruits)
```

    ['Mango', 'Pineapple', 'Orange', 'Banana', 'Apple', 'Melon', 'Kiwi']



```python
# The remove() method deletes the first occurrence of an element in a list
fruits.remove('Banana')
print(fruits)
```

    ['Mango', 'Pineapple', 'Orange', 'Apple', 'Melon', 'Kiwi']



```python
# Trying to remove an element that doesn't exist results in an error
fruits.remove('Strawberry')
print(fruits)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-33-50fbba439db1> in <module>
          1 # Trying to remove an element that doesn't exist results in an error
    ----> 2 fruits.remove('Strawberry')
          3 print(fruits)


    ValueError: list.remove(x): x not in list



```python
# The pop() method removes the element at a given index and returns it.
# If no index is given, it removes and returns the last element.
fruits.pop(2)
print(fruits)
```

    ['Mango', 'Pineapple', 'Apple', 'Melon', 'Kiwi']



```python
# Reassign the element at a given index with a new value
fruits[1] = 'Mango'
```


```python
print(fruits)
```

    ['Mango', 'Mango', 'Apple', 'Melon', 'Kiwi']



```python
# Strings are immutable because you need to reassign them to modify them
power = '1.21'
power = power + ' gigawatts'
print(power)
```

    1.21 gigawatts



```python
# You cannot reassign a specific character within a string
power[0] = '2'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-59-8817eab4e829> in <module>
          1 # You cannot reassign a specific character within a string
    ----> 2 power[0] = '2'
    

    TypeError: 'str' object does not support item assignment



```python
# Lists are mutable because you can overwrite their elements
power = [1.21, 'gigawatts']
power[0] = 2.21
print(power)
```

    [2.21, 'gigawatts']


<a name="3"></a>
## 3. Introduction to tuples


```python
# Tuples are instantiated with parentheses
fullname = ('Masha', 'Z', 'Hopper')

# Tuples are immutable, so their elements cannot be overwritten
fullname[2] = 'Copper'
print(fullname)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-61-9a0cd4c754f6> in <module>
          3 
          4 # Tuples are immutable, so their elements cannot be overwritten
    ----> 5 fullname[2] = 'Copper'
          6 print(fullname)


    TypeError: 'tuple' object does not support item assignment



```python
# You can combine tuples using addition
fullname = fullname + ('Jr',)
print(fullname)
```

    ('Masha', 'Z', 'Hopper', 'Jr')



```python
# The tuple() function converts an object's data type to tuple
fullname = ['Masha', 'Z', 'Hopper']
fullname = tuple(fullname)
print(fullname)
```

    ('Masha', 'Z', 'Hopper')



```python
# Functions that return multiple values return them in a tuple
def to_dollars_cents(price):
    '''
    Split price (float) into dollars and cents.
    '''
    dollars = int(price // 1)
    cents = round(price % 1 * 100)

    return dollars, cents
```


```python
# Functions that return multiple values return them in a tuple
to_dollars_cents(6.55)
```




    (6, 55)




```python
# "Unpacking" a tuple allows a tuple's elements to be assigned to variables
dollars, cents = to_dollars_cents(6.55)
print(dollars + 1)
print(cents + 1)
```

    7
    56



```python
# The data type of an element of an unpacked tuple is not necessarily a tuple
type(dollars)
```




    int




```python
# Create a list of tuples, each representing the name, age, and position of a
# player on a basketball team
team = [('Marta', 20, 'center'),
        ('Ana', 22, 'point guard'),
        ('Gabi', 22, 'shooting guard'),
        ('Luz', 21, 'power forward'),
        ('Lorena', 19, 'small forward'),
        ]
```


```python
# Use a for loop to loop over the list, unpack the tuple at each iteration, and
# print one of the values
for name, age, position in team:
    print(name)
```

    Marta
    Ana
    Gabi
    Luz
    Lorena



```python
# This code produces the same result as the code in the cell above
for player in team:
    print(player[0])
```

    Marta
    Ana
    Gabi
    Luz
    Lorena


<a name="4"></a>
## 4. More with loops, lists, and tuples


```python
# Create a list of tuples, each representing the name, age, and position of a
# player on a basketball team
team = [
    ('Marta', 20, 'center'),
    ('Ana', 22, 'point guard'),
    ('Gabi', 22, 'shooting guard'),
    ('Luz', 21, 'power forward'),
    ('Lorena', 19, 'small forward'),
    ]
```


```python
# Create a function to extract and names and positions from the team list and
# format them to be printed. Returns a list.
def player_position(players):
    result = []
    for name, age, position in players:
        result.append('Name: {:>19} \nPosition: {:>15}\n'.format(name, position))

    return result
```


```python
# Loop over the list of formatted names and positions produced by
# player_position() function and print them
for player in player_position(team):
    print(player)
```

    Name:               Marta 
    Position:          center
    
    Name:                 Ana 
    Position:     point guard
    
    Name:                Gabi 
    Position:  shooting guard
    
    Name:                 Luz 
    Position:   power forward
    
    Name:              Lorena 
    Position:   small forward
    



```python
# Nested loops can produce the different combinations of pips (dots) in
# a set of dominoes
for left in range(7):
    for right in range(left, 7):
        print(f"[{left}|{right}]", end=" ")
    print('\n')
```

    [0|0] [0|1] [0|2] [0|3] [0|4] [0|5] [0|6] 
    
    [1|1] [1|2] [1|3] [1|4] [1|5] [1|6] 
    
    [2|2] [2|3] [2|4] [2|5] [2|6] 
    
    [3|3] [3|4] [3|5] [3|6] 
    
    [4|4] [4|5] [4|6] 
    
    [5|5] [5|6] 
    
    [6|6] 
    



```python
# Create a list of dominoes, with each domino reprented as a tuple
dominoes = []
for left in range(7):
    for right in range(left, 7):
        dominoes.append((left, right))
dominoes
```




    [(0, 0),
     (0, 1),
     (0, 2),
     (0, 3),
     (0, 4),
     (0, 5),
     (0, 6),
     (1, 1),
     (1, 2),
     (1, 3),
     (1, 4),
     (1, 5),
     (1, 6),
     (2, 2),
     (2, 3),
     (2, 4),
     (2, 5),
     (2, 6),
     (3, 3),
     (3, 4),
     (3, 5),
     (3, 6),
     (4, 4),
     (4, 5),
     (4, 6),
     (5, 5),
     (5, 6),
     (6, 6)]




```python
# Select index 1 of the tuple at index 4 in the list of dominoes
dominoes[4][1]
```




    4



In the code cells below are two ways to add the total number of pips on each individual domino to a list, as indicated in this diagram:

![Screenshot 2023-03-23 1.13.21 PM.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAwgAAAFeCAYAAAAhTTjUAAABKGlDQ1BTa2lhAAAokX2QPUvDUBSGH0sXRVHQwcEhi+Cipq0WBRFsisW1VWgVhzT9QGxiSCO6OAlO/ggX0R/g4C7ugujkjxAHZ9+0SAISz+Xc89z3nvtxDmRmkWVNcL0wqFZKRr2xb5Aw2+n7pNsIfL9HM7wu/pOXZqOtdt9R/JSHgR7XlS3xTHfI5xE3h3wd8Vnoh+KbiIPdqiV+EC90E9xMsOMHUf6HeMPtnTrxvxlve3s1xbp8jgonGl16tFmmxjFH2KICJdYoklPMsUJZq1X5tkaBLan5Qcxpxxpk5LUqs64zFmbcz/4tFC8Fm7F26MLjG0xexdr8M0zdw9NFrMU99u3AHkhZeabTga87mGjA9AuMHfw2NqVW40+tBjt4OCyJ8piqoPgDPi9KBbIrzJ4AACAASURBVHic7N13mFNV3gfwb5JJphem0cvgUGQAcWhSpDgISFNRQLEXWHt/V5e1oOCqFMFVd11ZWEXpVYGhqHQF6dKlt6FM7y3lvH+EnElmkpkkk0wK38/z5HlmJveenHvn3NzzO+fccxRCCAEiIiIiIiIASk9ngIiIiIiIvAcDBCIiIiIikhggEBERERGRxACBiIiIiIgkBghERERERCQxQCAiIiIiIokBAhERERERSQwQiIiIiIhIYoBAREREREQSAwQiIiIiIpIYIBARERERkcQAgYiIiIiIJAYIREREREQkMUAgIiIiIiKJAQIREREREUkMEIiIiIiISGKAQEREREREEgMEIiIiIiKSGCAQEREREZHEAIGIiIiIiCQGCEREREREJDFAICIiIiIiiQECERERERFJDBCIiIiIiEhigEBERERERBIDBCIiIiIikhggEBERERGRxACBiIiIiIgkBghERERERCQxQCAiIiIiIokBAtEN5sSJExgyZAh+++03T2fFL/z4448YNWoULly44Oms1Lnc3Fy8/PLLmDJliqez4heys7PRrVu3G/La1Ov1+PLLL/HAAw94Oit+Y8iQIfj2228hhPB0VsgHMUAgukHodDr87W9/Q4cOHbB27Vr88MMPns6SX1i1ahWWLl2Ktm3b4qOPPrphbsbz589H69at8c9//hPLli3zdHb8wtq1a7F792706tULjzzyCPLz8z2dpTqxd+9eJCcn44UXXsDy5cuRl5fn6Sz5vEuXLmHt2rV4/PHH0bNnTxw7dszTWSIfE+DpDADAsWPHZGVl4MCBSE5O9nCOnGMwGJCZmYn4+HhPZ4V80MyZM7Fz584at2vcuDGmT5/uUNpFRUUYNWoU1q5dCwCIiopCx44dnconWerSpQsWLFiAoqIiTJgwAYcOHcI333wDjUbj6ay5zXvvvYcPPvgAAKBSqdCrVy8P58g/tGjRAi1atMC5c+fw/fff4+DBg0hNTUXjxo09nTW3Wb16NcaMGYPi4mIAQEpKCnQ6nYdz5fuUSiX69OmDrVu3YufOnejVqxdWrlyJPn36eDprfuv5559HVlZWjdv17dsXzz77bB3kqJaEF1iwYIEAIACII0eOeDo7TsnMzBRt2rQRAMSQIUOETqfzdJbIx9x3333yOqju1aZNG4fSzcjIEJ07d5b79+7dW1y5csXh/On1epGXlycMBoPD+/qC/Px8odVqndr33LlzIjk5WZ7jfv36ifz8fBfn0PMMBoN4/PHH5XE2atRI7Ny506m0anO+/VlhYaF49NFH5Tlu0qSJz94XazJr1iyhUqkEAKHRaMTs2bOdSqeoqEiUlJS4OHfeQa/XO/1dYjAYxMyZM+U5DgwMFEuWLHFxDsmkcePGdt3DH3vsMU9n1S5e0YNgLiIiwtNZcMqSJUvw559/AgBSU1OxZcsW3HHHHR7OFfmi1q1bY/jw4Tbfd6SHSq/XY8yYMdi7dy8A4IEHHsC3337rUOv2mjVrMHXqVPz222/QarUICgpCv379MGHCBNx+++12p+ONjhw5gkmTJmHt2rXIz8+HUqnErbfeihdeeAGPP/643ek0b94c27Ztw5gxY7B69Wps3rwZo0ePxurVq6FSqdx4BHVr4sSJ+OabbwAA7du3x7p16xxq3XbV+fZm+/btw9///nds2rQJ3bt3x5YtWxzaPzQ0FN9++y0SExPx7rvv4tKlSxg8eDB+//13NGzY0E25rnu//PILnnnmGej1ekRERGDNmjXo3bu33ftnZWXhH//4BxYtWoS0tDQAQEJCAh5++GG8+eabCA0NdVfW3e7ChQv4/PPPsWbNGpw4cQJ6vR7BwcHo0KEDHn30UYwbN86u73CFQoGXX34Zbdq0wciRI1FSUoKxY8ciJiYG/fv3r4MjubE888wzyM3Ntfn+smXLcO7cuTrMUS15OkIRwrIH4eLFi57OjlM2bNggj0GtVotTp055OkvkY0w9CPfdd5/L0vy///s/WS6HDx/ucIut+f6VX0qlUnz66acuy2tdW7p0qQgKCrJ5fKNGjXL4fJWWlop+/frJNN5++2035b7urV69WigUCgFAtGzZ0uFeKHecb29y7Ngxcf/998tzBEB07969Vmm+9dZbMq2+ffsKvV7votx61vnz50VsbKwAIIKCgsTmzZsd2v/48eOiSZMmNsvSzTff7FQvqTeYMWOG0Gg01bZAd+nSxeG60urVq0VAQIAAIOLi4nz2/PiyQYMG+VQPgtcFCBcuXPB0dpw2d+5c8fTTT4uffvrJ01khH+TqAGHr1q0Ww5KKiooc2v/LL7+U+ycmJop58+aJPXv2iFmzZon69evL93744QeX5Lcu7d+/X96Ew8PDxdSpU8Xu3bvFypUrRZcuXeSxvfrqqw6nnZOTI5o2bSqDqL1797rhCOpWbm6uiI6OlhW6w4cPO7S/O8+3p507d048/vjjchiH+au2AYIQQgwfPlymN3PmTBfk2PNSUlLkMTk6rKigoEC0bNlSABAKhUI899xzYvv27WLTpk3igQcekOl269bN5wJO84AwKChIPPvss2LdunViz549Yvny5eLJJ5+UAWi3bt1EWVmZQ+lPmzZNpn/PPfe46SjIFgYITvCXAIGoNlwdIPTu3VsAECqVSuzZs8ehfTMyMkRYWJgAIBo2bCjS09Mt3v/zzz9FSEiIHCNdWlrqkjzXldtuu01W4Lds2WLxXlFRkejYsaOsgBw8eNDh9Ddu3Ci/0/r06eOqbHvM3//+91pVUt19vj3J9OxZQECA6Nevn5g2bZq4+eabXRYgpKeni7i4OAFAREVFiezsbBfk2nN++umnWlVSzSvRkydPrvL+008/Ld//4osvXJHlOrFy5UqZ79tuu01cunTJ6nafffaZ3G7WrFkOfYbBYBD9+/eX+2/cuNEVWSc7MUBwgnmAcP78eU9nh8gjXBkgpKamymvqySefdHj/Dz74QO4/f/58q9t8/PHHcps5c+bUNst1xrxnZfz48Va32blzp9zm0Ucfdepz7r33XpnGtm3bapNlj0pPT5fBYuvWrR1ula2r8+0pK1euFAsXLhS5ubnyb927d3dZgCCEZaVw0qRJLknTU0znxpmhuEVFRSI8PFwAEElJSVbLYm5uruzhbNGihc9MqvDSSy8JACIhIcGiLFWm0+lEo0aNBADRs2dPhz9n//79shciJSWlNlkmBzFAqEZaWprYsWOHOHDggEXXmDMBwrVr18Thw4fF6dOnnZ4x6Pjx4+L48eNV/l5cXCwOHDjg8d6Mc+fOiQMHDoisrCyn9i8rKxMnT54UR44ccToNk7y8PHHkyBFx8OBBkZOT41QaBoNBXLhwQRw4cEAcOnRIXL161We+vOuCKwOEO++8U7bYnjt3zuH9Ta2i8fHxNq+vnJwced0OGDCgtlmuM3/5y19kvg8dOmRzO9M2oaGhTvWQHDx4UKbx0EMP1SbLHvXhhx/K4/juu+8c3r+uzrc3cXWAUFZWJho0aCB77Hz1e/PXX3+V/+ennnrK4f3N6wqff/65ze3uvvtuud327dtrk+U6NXXqVPHJJ5/UuJ2p8aFevXpOfc7IkSPl+Tlx4oRTaZDjfC1AcPssRkIIzJ07F9OmTcPhw4fl38PCwvDUU09h8uTJVba3paCgADNmzMA333yDs2fPyr+HhIRg6NChmDBhAjp16mR13xEjRuDChQt44IEHkJKSgqeffhoHDx4EAPTp0wfLli1DdHQ0PvvsM7z77rsoLCwEADz00EOYM2eO1RkD7r33Xot8mNSvXx/r16+v5qxUTaNXr1748ssvodfr8cUXX2DmzJnyaXeFQoEhQ4bgP//5j10zhmzbtg2ffPIJfv75Z5SVlcm/t23bFuPHj8dzzz2HwMDAGtMRQmDJkiX45z//iR07dsBgMMj8dO3aFW+88QZGjRpVYzonTpzA5MmTsWbNGmRnZ1u8FxMTgzvvvBNvvPEGOnfuXGNatfHRRx/h2rVrTu37zDPPoG3bti7OkXtkZGRg48aNAIABAwagefPmDu1/8eJFOSPXyJEjbc7CY77Q2vbt21FaWoqgoCAnc113fvrpJwBAmzZt0L59e6vbHDlyRP5cVFSEHTt2oF+/fg59TocOHZCcnIx9+/Zh5cqVPnN+Klu0aBEAIDIyEvfdd5/D+9fV+fZnGo0GY8eOxaeffopLly7h119/dWjGH29hKksA8NRTTzm8v6ksAcD9999vdZuioiKL76affvrJZ9bpeOONN+zaLjw8HACQk5MDrVYLtVrt0Oc8/vjjWL58OQDj/+Ttt992LKN0Y3Bn9FFSUmLRzQ5AREREWDzM1alTJ/H111/L38+ePWs1rVOnTslWTVuvgIAAm2PybrrpJgEY5yePiIgQcXFxspsOMM7wMnHiRNnFl5CQIN/78MMPraZpKz+NGze2+xyZ0hg0aJDIzc0Vffr0sXl8zZo1q7H1ftKkSRazaFh7de/eXVy9erXadPLz88XgwYPlPkFBQSIpKUk+HGZ6PfXUU9W2Zv38888iODhYbh8ZGSk6duwoOnXqJEJDQ+XfFQqFePnll906S0dN5ae619q1a92WLxNX9SAsXrxY5tvRMapCCLF8+XK5v60HCPfv32/xfwXg8HMOnmDe6/HII49Y3SY/P1+0bt3a4timTZvm1Od99NFHMo1NmzbVJusekZ6eXqtekLo+397C1T0IQgixY8cOeX7ee+89l6Vbl9q1a+fwPdKc6VmVpk2b2tzmwQcftChLw4YNcza7Xst0bw4LC3Nq//LycjlssG/fvi7OHdniaz0ISjtiCKc9++yzWLFiBQDg5ZdfxoULF5CXl4fi4mJs2LABSUlJOHDgAP7xj39Um05aWhp69Ohh0aq5bds2ZGZm4vjx4/jkk08QFRUFnU6HcePG4V//+pfNtDZv3oyePXviwoULSEtLw2OPPQbAuHbB5MmT8cQTT+DkyZM4deoUunXrBgCYO3eu1bS+/PJLrFixQr5uvvlmh8+RiV6vx4gRI7B161YMGjQIq1atwtmzZ7FlyxbZ+nHhwoUqPS7mJkyYgHfeeQdCCNSvXx9ffPEFTp06hfT0dPzyyy+48847AQC///47evXqhYKCAqvpGAwG3HPPPVi3bh00Gg2mTJmCrKwsHD58GKdPn8apU6cwcOBAAMDs2bMxZcoUq+nodDo89dRTKCkpQUxMDFauXInMzEz88ccf2L9/P3JycrBq1Sp06dIFQgh89tlnmDVrltPnsCYDBgzA3Xff7dSrfv36bsuXq+3bt0/+3KNHD4f3P3HihPzZWotvTk4O7rvvPmi1Wrz88svy78ePH3f4s+qa6TsEsH5sgLF17cSJE3j99dfl35w9NvPzb/5/8RW1LUt1fb79WXJysuz59cWyVFJSgmPHjgFwriwBFd9NtsrSZ599hgULFmDgwIHo0KEDAP8rS3q9Hjt37gRgXMXdGWq1Wu7ri2WJ6oi7Io/NmzfLCP6DDz6wuk1GRoZs2Te9zpw5U2U785ZsW2kdOnRIzqscEhJSZVyd6XMCAwPF5cuX5d/Xr18v027UqJHFaowTJkxwKErv1auX0z0ISqVSABAzZsyosk1RUZFcoa9hw4ZW0/n1119lGgkJCVbHnRsMBvHss8/K43366aetpjVjxgy5zeLFi61uU15eLlvJwsLCrM6scfToUZnO+++/b/Mc6HQ6MXz4cNG/f3+fm5bOlVzVg3D//ffLHjVnemRefvll+X9LS0uzeM9gMIihQ4cKAGL69Oli9+7dPtXqu2LFCpnfefPmVXn/k08+EQDEiBEjhMFgkL1czrZC5ubmys977rnnapv9OvfFF1/I/G/dutXh/ev6fHsLd/QgCCFEp06dBADRrl07l6ZbFw4fPlzjfbw65r1R48aNq/L+9u3bhVqtFi1atBCZmZnye8rZVnZvtWTJEnke/vnPfzqdziuvvCLTqTxLHbkHexCumzZtGgCgWbNmeOutt6xuExsbW22LOABs3boV69atAwD07dsX77zzjtXt2rdvj08//RQAUFxcjEmTJlndrmfPnharUZq3DD/yyCMWY4RjYmIAQD6P4E4GgwEvvvgiXnnllSrvhYSEyFVGr1y5IlthzL399tvyGYHZs2dbHXeuUCjw2WefoU2bNgCA//73vzhz5ozFNuXl5Zg6dSoA4O6777b5jIFarZY9P4WFhVi4cKHVzzO5cuWK1XQAQKVS4eOPP8aSJUsQEOB1i3v7nJycHABAvXr1oFQ6fombrwQZFhZm8d6kSZOwZs0ajBkzBq+99pocCwsAeXl5Tua47lR3bJs2bcKECRPQqlUrzJ07FwqFQh6fs8cWGRkpy7Tp/+JLzPNs+j50RF2fb39n+h+wLFmWpWvXrmH06NFQqVRYtmwZYmJiZFkqLCyU90Zfp9Vq8f777wMAoqOj8cQTTzidlvn/wBfLE7mfWwKE8vJy/PLLLwCMDxJV9wDN/fffb3Gxi0oPKS9YsED+/Pe//73az3344YdlxXjlypUoKSmpsk1CQoLF7+YP695yyy0W79mzlLmrBAQE4N1337X5vnlX4uXLly3eu3LlCrZs2QLAGABVt4S6Wq3Gm2++KX+fP3++xfvbtm2T6T/zzDPV5rlv377yf7d169Yq77dq1QqJiYkAgFmzZmHGjBk2v6jbtWvn1E2DqtLpdACMgaUzysvL5c+hoaHy5/Xr1+P9999HUlISZs+eDcDyRm3+QLy3snVsaWlpeOCBBxAUFIQVK1YgMjISQMXx1ebYTP8HrVbrdBqeYipLgHPlyRPn25+ZziHLUkVZ0ul0GD16NC5fvoyvvvoKycnJAHzvu8keH374oZzs5cMPP6wSKDnC/Bz6Ynki93NLgHD48GFZOa9pjFxAQIAc6w9UDRBMs7GEhYXVOKuFQqHAiBEjABhnPPr999+rbBMcHGxz/+rec7eOHTsiNjbW5vvR0dHy58ozAW3evFlWvIcNG1bjZw0fPly27v/8888W75kq+gqFAm3btkVmZqbNV05ODho0aAAAVXoiAGPPwJw5cxAaGgq9Xo/XXnsNbdu2lTNxkHuYbhrmLW6OMO/FMd2Uz58/j4ceegjh4eFYsWKFvLmUlpZa3c9bWTs2rVaLUaNGIT09HXPmzEFSUpLcxnR8zh6bXq+Xz/rU5mbuKeZ5dqY81fX59nemll6WpYpg4c0338TWrVvx3HPPyWcKAd/7bqrJ+vXr5ciIlJQUjB8/vlbpmfca+GJ5IvdzS4CQkZEhf46Pj69x++qm7kxLSwMAtGjRwq6pvFq3bl1lX19QXXAAWPZmVG4NMT9O8+Ov7rNMAUflc3Tx4kUAxkAtISEBcXFx1b5OnToFwHYX5e23347ffvtNBoEnT57E66+/jmbNmqF379748ssv2b3pYqbrKT8/H8XFxQ7vb966V1BQgLKyMtx3333Izs7G3Llz0apVK/m++fA7Z3ss6lLlYwOAV199FTt27MDrr7+O0aNHW2xvOj5nj+3q1auy0aNJkyZOpeFJ5t/N1Q0TtKWuz7e/M/0PWJaMZWnp0qX49NNP0aNHD8yYMcNie1NZCggIcHgaUG9z+PBhjBkzBgaDAc2aNcP8+fOdGj5qzvQ/UCqVFsOuiUzcEiCYVxoq9whYYz6O2Xz7kpISFBUVAbBsQa+O+XbmgYq3Mx+v7yjz43T0PFU+R+aVdZVKZferuuFYHTt2xM6dO5Gamophw4ZBo9FACIFff/0VL7zwApo1a4Y333zTqcqsI7p164aoqCinXqYhc76gXbt2AIzX0t69ex3ePy4uTv6cm5uL559/Hnv37sXbb78te+jM3zexpzHA0yof27x58/Dll1+iX79++OSTTyy21ev18rvM2WPbtWuX/Lk2s5x5iqksAcCePXsc3r+uz7c/y8nJwenTpwH4Zllq2LAh6tWrB8C5shQbGyvvk7m5uTh+/DiefPJJ1K9fH0uXLq1yDzJ9N/l6WTp//jzuuusu5OXloV69eli7dq1Ljsn03XTTTTfV6XBq8h1uCRAiIiLkz5WHw1iTmZlp9e/BwcHyoWF7uyTNK7j2VpZ9nelLF3D8PFU+R6ahIw0aNIBOp7P7Zb4InjUKhQJ33XUXVq1ahWvXruGbb76Rz0oUFhZiypQp6N69u1t7E/Lz85GXl+fUy5fGaJovoGR6NsURLVq0kD//9a9/xezZszF48GBMnDixyrbmD8w7uiCbJ5gf25IlSzB+/Hg0adIEixYtqrIg3MmTJ+W4aWePbfPmzfLn22+/3ak0PKlDhw7y+YDalqW6ON/+bPPmzbIBzRfLEgA5ZfeuXbusPiNYnYCAANkLsWfPHowcORIlJSVYvHgxGjVqVGV703eTL5elq1ev4s4778SlS5cQERGBdevWWQTtzsrMzJSLE/pqWSL3c8vAPPPo1nwebFvMuxsr9zg0atQIZ86cwfnz56HX622u6mpiamEx7XsjMO+6NT9+W3Jzc5GVlQWg6jkyzep07do1FBYWumVsYlRUFB577DE89thj2LdvH/7yl79gz549OHz4MN599118/vnnLv9MAPjqq6+cnpHK3as8u9Ktt96Kxo0bIy0tDd9//73Dq2SazzH+ww8/ICEhwWaX9qFDh6zu560SEhIQEhKC4uJi/Pzzz9BoNFi2bJnVFrnaHpter5crx3bo0AFNmzZ1PuMeolQqcdddd2HhwoXYtGkT0tLS7FrN3aQuz7e/mzdvHgBjRXnQoEEezo1zhg0bhtWrV6OwsBA//PADHnjgAYf2b9++PS5duoSTJ08CAGbOnIk+ffpU2S4jIwPXrl2T+/ii9PR0pKSk4OTJkwgLC0NqaqrF85q1sXDhQuj1egDA0KFDXZIm+R+39CAkJSXJlmjzFjRrDAYDjh49avN9U4tDXl4etm/fXuNnr169GoBxdqKuXbvam2WfZr6M/Jo1a2rcPjU11WZLVPfu3QEYAzVXDKsxfQnZkpycjM2bN8vAxDSlrTv069cPw4YNc+plPlTC2ymVSjz00EMAjAH6pk2bHNo/OTnZYoaL5cuXW/RSmTP9v1q2bOkTAblSqbS4Xj766CObN93U1FT5szOtbCtWrJCVlEceecTh/b3Fo48+CsD4Xf311187tG9dnm9/lpaWJu9tAwcO9NlhM6NGjZKjAv797387vL95uWjQoIHFQo3mfL0sZWZmYsCAATh69CiCg4OxevVqi+uoNoQQ8jqOjo5mgEA2uSVACAgIQEpKCgDjXNemrixrNm7cKFuzgao9CGPHjpU/21qx12TFihWyZWHYsGGya9zftWzZUlbst2zZYjHuuTKDwSDXqAAgK5ImKSkp8gu88kNfjtLpdBg6dGiNc1CHhoaiU6dOACxnpyDnvfDCC/LBPEd7ENRqNYYMGSJ/txUc/Prrr3L2qnvuucfJnNY987zaCvyKi4vlKvDJyckOt/7r9Xo5bXF4eDjGjRvnZG49b/DgwXLM+4wZM2wOCbWlLs63v3v//ffl5BTmK077mujoaDnT0NatW7FhwwaH9jcvS3379rW53ffffw/A+F121113OZFTz8nMzMQdd9yBQ4cOITg4GKtWrar2WB21YMEC2Vv3/PPPW0z1TmTBXSuwbdy4Ua7S16tXL4sVik3KyspE586dLVZSPn78uMU2Op1OrkoJQPz73/+2+nnnzp0TTZo0kSvI7tmzx+J900rKzz//vMXfjx07JtNesWKFxXuff/65fM8etVlJedCgQdVut2PHDpmX7777rsr7q1evlu8nJSWJzMxMq+m88847crt7773X6jbPP/+83Gbq1KnV5mvNmjXi6NGjVt/79NNPBQDx4osvVruib15enoiLixMAxPDhw6v9PH/mqpWUTV544QX5f/zf//7n0L7m1+8999xT5X2dTie6dOkiVwE/duyYXelqtVrxzjvviP79+4uPP/7YqZWeaysnJ0dEREQIAKJp06aioKCgyjbmq4x+/fXXDn/GlClT7FpF3Jbdu3eL4cOHi5EjR4rDhw87vL+rLV26VB6Po6uAuut8e0NZssWVKynv2LFDqFQqAUD079/f4f2vXr0qnnjiCTFw4MAq9zhPuHDhgggJCREARNu2bUVxcbFD+/fp00cAECqVSuzdu7fK+z/88IMsS2PHjrU73e+++06kpKSIZ555RuTk5DiUJ1fJzMwUHTt2FABEUFCQ2LBhg0vTz87OlvWkmJgYkZ2d7dD+nrzmdu7cKYYMGSJGjx4tzpw5I/+enZ0txo8fLwYMGCBWrlxpsc+cOXPEHXfcIV5//XWrddC65msrKbstQBBCiLFjx8oL9bbbbhObNm0SxcXFQqvVip07d8oL3VRJBmC1snn8+HH5haJQKMTLL78sLly4IIQQoqSkRCxcuFA0bdpUpvHee+9VScPVAYJerxcnT560eJmCnQYNGlj83ZRXa1wVIAghxFNPPSW3adOmjfjxxx9FWVmZEEKIU6dOiSeeeEK+Hx8fL65du2Y1ndzcXHm+AIgnn3xSnD171mKbtLQ08eabbwqVSiXi4+MtLlghhCgtLRXR0dEyjZ49e4oNGzaI8vJyuY1WqxUbN24UycnJcjtXfyH6ElcHCNnZ2aJBgwYCgAgPDxenTp1yaP8hQ4bI/8trr70mCgsLhRBCZGVlWVzb48ePtzvNmTNnWjQIOFN5dgXzCvyAAQPExYsXhRBClJeXi2nTpgmlUimDbfMya499+/YJjUYjAIjExESHK0Dl5eUiPj5e5i8mJkZkZWU5lIY7mG5uAMSiRYsc2tcd59tbypI1rgoQ8vLy5HdxYGCgU8HiPffcY3GeNm/eXKs8ucJHH30k8/Pss886tK95wNS8eXOxY8cO+V5qaqq874SEhNj9nbd//36hUChknpwJxGorOztb3HrrrTIPb731lti0aVO1r6+++kpcuXLF7s8YNWqUTH/WrFkOEORxvgAAIABJREFU59FT11xBQYFFfSI5OVm+Z34vCggIEH/++acQQogtW7ZY5HXChAl1ktfqMEAwU1BQIFJSUiz+SQqFQt4MTBH+l19+KX/fvXu31bR27dolKzumV1hYmEVaAMS7775rdX9XBwgZGRkWn1vdKykpyeY5cmWAoNVqxfjx4y0+W6VSidDQUIu/JSYmyovIllOnTombb77ZYr+EhATRrVs30bx5c/kFbaog6nS6Kmn89NNPonHjxhZpBAYGiiZNmogWLVqI4OBgi/cmTpxYbZ78nasDBCGEWL9+vbxGEhMTxdWrV+3e9+rVqyIxMVH+f4KDg0VCQoKs/AIQXbt2lYGDPcyDWMCx3jZX0uv1FhUnpVIpWrRoIcLDw+XfYmNjxZEjRxxK9+zZs6Jhw4YCgNBoNGLXrl0O5+3ixYtVvkOcuZm72uXLl0VsbKwsC9u2bbN7X3ecb28pS9a4IkAoLS0V/fr1k8c3c+ZMp9Ixb+wBIB566CGn8+QqOp1ONhACENOnT3do/+nTp1scU6NGjSyCaqVSKRYsWGB3et99912Va+7kyZOOHlatrFixwu46hfnL3t7bt956S+5jrVfYHp665k6cOFGlHmEwGIQQQva4mF4//vijEEKIf/3rXxZ/HzFiRJ3ktToMECopKysTH374oYiKirL4ZwUHB4sJEyYIrVZrEelV172clpYmnn766SoVXgCiR48eYu3atTb3vRECBJMFCxaIW265pUo+6tWrJ1599VW7uxULCwvF5MmTRaNGjaweV2Jiopg9e3a1aeTn54spU6ZUCTZML4VCIXr06CHWr19vV578mTsCBCGEmDZtmkVZrNzbU5309HQxZsyYKoG4Wq0W48ePF/n5+Q7lZf/+/SIyMtLie8BTysvLxdtvv231++SOO+5wuMflyJEjIiEhQabxzTffOJ23Rx991CI/H3/8sdNpudL27dtFYGCgACAiIyMd6vFz9fn2prJUWW0DhNzcXDFw4EB5bE888YTTeZk9e7ZF6/jgwYOdTsuV0tPTRcuWLeV94JNPPnFo/wULFsjhMuavVq1aOXw/yc3NFR06dLBIZ+fOnQ6lUVvuChAMBoNFcNCxY0eHv7dNPHXNGQwG0b9/f/m55vU483paYmKiPLa0tDQZNKpUqirDjzyBAYINZWVlYsuWLWL+/PkiNTVV5OXlOZ1WaWmp2Lt3r1i3bp3YsmWLzaEyN7pLly6JTZs2ifXr14s//vhDaLVap9M6evSoWLVqlfj+++/FihUrqjwrYo+0tDSxYcMGMX/+fLF48WKxadMmh1q0/Z27AgQhhJg6daqsJMTGxorVq1c7tH9aWppYunSp+O9//ytWrlwp0tPTnc7Lvn375JDBTp06OZ2Oq+Tn54u1a9eK2bNniwULFjjVcrhgwQLZGh4QEFBj4FwTvV4vHnroIXnj84abm8nGjRtlJUGlUomPP/7Yag+iLa443ybeVpZcYe/evRbDbseNG+fQ+bXmP//5j0zvlVdecVFOa+/ChQsiKSlJ5u3BBx90aFy8VqsV27dvF99884349ttvxa5du5weF5+VlSXzolAoPPYcgitdvXpVDBs2TJ7fbt261eq7WwjPXXPl5eVi2bJlVoO/nTt3igULFlSpV167dk3MmzdPHDx4sK6yWS0GCETkFFOAEBERIZKSkmy+Bg4c6FT6CxculK2/gGeHGrRq1UoAEB988IHH8uAKBoNBDB48WJ7TsLCwansyHTFv3jxZHqw92OtJhw4dsnju65Zbbql1xcNZ/lKWhBBi0qRJFsM3XXVMaWlpMs2tW7e6JE1XycnJsRhKFR8fL7Zv3+6RvIwbN072aPm61NRUi5Ebw4cPF0VFRS5J25+uOVfq3bt3tffusLAwBghE5DhTgFDTq3nz5k5/xr59+0SPHj0EADF06FAX5t5+u3fvlhUBR2fR8EbdunUTAERKSorNGb2cMXToUAFAfPjhhy5L05WuXr0qHnnkEaFQKERUVJTDD3O7gr+Vpb/+9a9yqMSaNWtclu7UqVMFAHHnnXe6LE1XKisrE5MmTZIt07aeRXSnwsJCER8fLxQKhUPP13ir1NRUORRw+vTpte6FMvG3a86VYmJi7LqH+0qAoBCi0sIDROQRBw4cwNWrV2vcLjg4uFbzYgsh8N133yE8PBz33nuv0+k4Q6vVolevXti9ezdWrlyJu+++u04/3x3mzp2L0NBQ3HfffS5Lc+XKlbj33nvRpUsX7NixAwEBbln03iV27NiBrVu34s0336zTz/XHsrRv3z6sX78er7/+OjQajUvSPH/+PG655RYIIXDo0CE0a9bMJem6w8WLFzFlyhR8/vnndf7Zr7zyCj777DO88sortV4DyBuUl5fjtddew7vvvuuyhfX88ZpzpY0bN9q1llPjxo3RoUOHOshRLXk2PiGiG4XBYJBT7b700kuezo7X2r9/v4iKihIxMTHixIkTns6OV2JZsk9OTo7o1KmTUCqVYunSpZ7OjteaM2eOUCgUonv37l4xX7434jV343HLSspERJVptVoUFBRg5MiRftFC5y65ubkICgrCqlWr0KpVK09nxyuxLNmnqKgI5eXlmD59ukt7uPxNTk4OWrVqhVWrViEoKMjT2fFKvOZuPBxiRER1xmAwQKvVIjAw0NNZ8WolJSUIDg72dDa8GsuSfViW7MPzVDNeczcWBghERERERCRxiBEREREREUkMEIiIiIiISGKAQEREREREEgMEIiIiIiKSGCAQEREREZHEAIGIiIiIiCQGCEREREREJDFAICIiIiIiiQECERERERFJAZ7OABERkTsZBKDXCwCAOkDh4dyQPzAIwGAwlqkAFcsU+R8GCETkVQ6fL8PXa3MAAJMfjUNEiMrDOSJf9/P+InydmgOlElg8oYmns0N+YMexEsxYngUA+O7/GiE4kAMyyL8wQCAir1JWLnA5UwcAMBg8nBkiIqIbEENeIiIiIiKSGCAQEREREZHEAIGIiIiIiCQGCEREREREJDFAICIiIiIiiQECERERERFJDBCIiIiIiEhigEBERERERBIDBCIiIiIikhggEBERERGRxACBiIiIiIgkBghERERERCQxQCAiIiIiIokBAhERERERSQwQiIiIiIhIYoBAREREREQSAwQiIiIiIpIYIBARERERkcQAgYiIiIiIJAYIREREREQkMUAgIiIiIiKJAQIREREREUkMEIiIiIiISGKAQEREREREEgMEIiIiIiKSGCAQEREREZHEAIGIiIiIiCQGCEREREREJDFAICIiIiIiiQECERERERFJDBCIiIiIiEhigEBERERERBIDBCIiIiIikhggEBERERGRxACBiIiIiIgkBghERERERCQxQCAiIiIiIokBAhERERERSQwQiIiIiIhIYoBAREREREQSAwQiIiIiIpIYIBARERERkcQAgYiIiIiIJAYIREREREQkMUAgIiIiIiKJAQIREREREUkMEIiIiIiISGKAQEREREREUoCnM0BEN7aMPJ3F73nFevlzVoEBWr2weD8ukl9bVL29J0stfj+frgUACCvvAUDnVkF1kS3yYXtOWZabM1fL5c/7z5RBo1ZYvN8lkWWKfJtCCCFq3oyIyD2+/SUPq3YW2LXtS3dHo0/7EDfniHzd1+tysGFvkV3bTn0qHgkNNG7OEfm67zflYeVv9n1PTXw4Du2bB7o5R0TuxSFGRORRvW62r8IfqFagV7tgN+eG/EGvdvaVqcRGGgYHZBd7v3saxgQwOCC/wACBiDwqsZHarkpar6QQqJSKGrcjSmoWiMax6hq3Y8BJ9kqor0Fi45q/p3ra2eBB5O0YIBCRx9lTUetpZ6swEQD0upllilyrtx3lpTeDTvITDBCIyONqChDqRwWgUwK77cl+PWsoU8mtghATrqqj3JA/qCnobNskEE3jau65IvIFDBCIyOPiIgPQ6SbbAUDPJLbKkWOaxKpxczPbZcre5xSITOqFq9ClmhmvevF7ivwIAwQi8gq92oXafs+O4SJEldnqmQpUK1imyCnVDUtj0En+hAECEXmFXu2CEaCq+hByq8YatKjPmWbIcbYqbD1tlDWimvRqF4xAddWy061tMCJCWKUi/8HSTEReQROgsNpFz1Y5clZ4sBLdrfQU9K6mt4qoOiolv6foxsAAgYi8hrU1EWp62JSoOpVnnomPDMAtLfnAOzmv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F8hkMh1W3fDcuHFD/EAUHR2tk+lHHz9+jMjISGRkZEAul2PAgAFaC6pVxZUrVzBo0CDk5eXhtddew5UrV2pcX32RlpaGIUOGICYmBjKZDGlpabCyspK6LJ1Qq9V49913ERAQAAD45Zdf8NZbb9XJz7516xYuXbqEYcOGac1wlpmZiSNHjsDZ2Rl9+vTRekx4eDiSk5Mxfvx4GBsb10md5Tl37hz69+8PAIiPj9daa4SooWFAICJqgEoGBBcXFxgZGZW77erVq+vsQ15J7du3F1fSXrFiRZ3//No0b948bNu2DSNGjKiziRPqSmBgINzd3WFpaYlHjx5xwbVngoKCsHr16nLbFQqFOOMXAwI1dFwHgYiogbt7926F7S+aXao2REVFITY2FnZ2dvj444/r/OfXptzcXBw8eBAymQy+vr5Sl6NzgYGBAIAlS5YwHJSQmppapzM7EUmJAYGIqAFydHTE0aNHK7VtXY/NVqlUWLBgAQBg69atDWJl6apYtmwZnj59ioULF2qt7dEY/PLLLwgJCUGvXr2wePFiqcupVyZMmAAXF5dKbcvF6qih4xAjIiLSGUEQMHv2bOzcuRN///vfsWHDBqlL0qmdO3di9uzZ6NOnD8LDwyUf965LV69exfDhw6Gvr4/IyMgaXTdERA0bZzEiIiKdUalUyM7OxuTJk7F+/Xqpy9G59PR0tGvXDocPH25U4QAAMjIyYGxsjMOHDzMcEDVxPINAREQ6pVaroVKpKrxwuiFTKBTi1LuNTWN+bkRUeQwIREREREQk4hAjIiIiIiISMSAQEREREZGIAYGIiIiIiEQMCEREREREJGJAICIiIiIiEQMCERERERGJGBCIiIiIiEjEgEBERERERCIGBCIiIiIiEjEgEBERERGRiAGBiIiIiIhEDAhERERERCRiQCAiIiIiIhEDAhERERERiRgQiIiIiIhIxIBAREREREQiBgQiIiIiIhIxIBARERERkYgBgYiIiIiIRAwIREREREQkYkAgIiIiIiIRAwIREREREYkYEIiIiIiISMSAQEREREREIgYEIiIiIiISMSAQEREREZGIAYGIiIiIiEQMCEREREREJGJAICIiIiIi0f8DA37YGswpIKMAAAAASUVORK5CYII=)

The first way uses a for loop. The second way uses a list comprehension.


```python
# You can use a for loop to sum the pips on each domino and append
# the sum to a new list
pips_from_loop = []
for domino in dominoes:
    pips_from_loop.append(domino[0] + domino[1])
print(pips_from_loop)
```

    [0, 1, 2, 3, 4, 5, 6, 2, 3, 4, 5, 6, 7, 4, 5, 6, 7, 8, 6, 7, 8, 9, 8, 9, 10, 10, 11, 12]



```python
# A list comprehension produces the same result with less code
pips_from_list_comp = [domino[0] + domino[1] for domino in dominoes]
pips_from_loop == pips_from_list_comp
```




    True



<a name="5"></a>
## 5. Introduction to dictionaries


```python
# Create a dictionary with pens as keys and the animals they contain as values.
# Dictionaries can be instantiated using braces.
zoo = {
    'pen_1': 'penguins',
    'pen_2': 'zebras',
    'pen_3': 'lions',
    }

# Selecting the `pen_2` key returns `zebras`--the value stored at that key
zoo['pen_2']
```




    'zebras'




```python
# You cannot access a dictionary's values by name using bracket indexing
# because the computer interprets this as a key, not a value
zoo['zebras']
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-80-037471d7b0ba> in <module>
          1 # You cannot access a dictionary's values by name using bracket indexing
          2 # because the computer interprets this as a key, not a value
    ----> 3 zoo['zebras']
    

    KeyError: 'zebras'



```python
# Dictionaries can also be instantiated using the dict() function
zoo = dict(
    pen_1='monkeys',
    pen_2='zebras',
    pen_3='lions',
    )

zoo['pen_2']
```




    'zebras'




```python
# Another way to create a dictionary using the dict() function
zoo = dict(
    [
     ['pen_1', 'monkeys'],
     ['pen_2', 'zebras'],
     ['pen_3', 'lions'],
    ]
)

zoo['pen_2']
```




    'zebras'




```python
# Assign a new key:value pair to an existing dictionary
zoo['pen_4'] = 'crocodiles'
zoo
```




    {'pen_1': 'monkeys',
     'pen_2': 'zebras',
     'pen_3': 'lions',
     'pen_4': 'crocodiles'}




```python
# Dictionaries are unordered and do not support numerical indexing
zoo[2]
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-84-5e45321afb99> in <module>
          1 # Dictionaries are unordered and do not support numerical indexing
    ----> 2 zoo[2]
    

    KeyError: 2



```python
# Use the `in` keyword to produce a Boolean of whether a given key exists in a dictionary
print('pen_1' in zoo)
print('pen_7' in zoo)
```

    True
    False


<a name="6"></a>
## 6. Dictionary methods



```python
# Create a list of tuples, each representing the name, age, and position of a
# player on a basketball team
team = [
    ('Marta', 20, 'center'),
    ('Ana', 22, 'point guard'),
    ('Gabi', 22, 'shooting guard'),
    ('Luz', 21, 'power forward'),
    ('Lorena', 19, 'small forward'),
    ]
```


```python
# Add new players to the list
team = [
    ('Marta', 20, 'center'),
    ('Ana', 22, 'point guard'),
    ('Gabi', 22, 'shooting guard'),
    ('Luz', 21, 'power forward'),
    ('Lorena', 19, 'small forward'),
    ('Sandra', 19, 'center'),
    ('Mari', 18, 'point guard'),
    ('Esme', 18, 'shooting guard'),
    ('Lin', 18, 'power forward'),
    ('Sol', 19, 'small forward'),
    ]
```


```python
# Instantiate an empty dictionary
new_team = {}

# Loop over the tuples in the list of players and unpack their values
for name, age, position in team:
    if position in new_team:                    # If position already a key in new_team,
        new_team[position].append((name, age))  # append (name, age) tup to list at that value
    else:
        new_team[position] = [(name, age)]      # If position not a key in new_team,
                                                # create a new key whose value is a list
                                                # containing (name, age) tup
new_team
```




    {'center': [('Marta', 20), ('Sandra', 19)],
     'point guard': [('Ana', 22), ('Mari', 18)],
     'shooting guard': [('Gabi', 22), ('Esme', 18)],
     'power forward': [('Luz', 21), ('Lin', 18)],
     'small forward': [('Lorena', 19), ('Sol', 19)]}




```python
# Examine the value at the 'point guard' key
new_team['point guard']
```




    [('Ana', 22), ('Mari', 18)]




```python
# You can access the a dictionary's keys by looping over them
for x in new_team:
    print(x)
```

    center
    point guard
    shooting guard
    power forward
    small forward



```python
# The keys() method returns the keys of a dictionary
new_team.keys()
```




    dict_keys(['center', 'point guard', 'shooting guard', 'power forward', 'small forward'])




```python
# The values() method returns all the values in a dictionary
new_team.values()
```




    dict_values([[('Marta', 20), ('Sandra', 19)], [('Ana', 22), ('Mari', 18)], [('Gabi', 22), ('Esme', 18)], [('Luz', 21), ('Lin', 18)], [('Lorena', 19), ('Sol', 19)]])




```python
# The items() method returns both the keys and the values
for a, b in new_team.items():
    print(a, b)
```

    center [('Marta', 20), ('Sandra', 19)]
    point guard [('Ana', 22), ('Mari', 18)]
    shooting guard [('Gabi', 22), ('Esme', 18)]
    power forward [('Luz', 21), ('Lin', 18)]
    small forward [('Lorena', 19), ('Sol', 19)]


<a name="7"></a>
## 7. Introduction to sets


```python
# The set() function converts a list to a set
x = set(['foo', 'bar', 'baz', 'foo'])
print(x)
```

    {'foo', 'baz', 'bar'}



```python
# The set() function converts a tuple to a set
x = set(('foo','bar','baz', 'foo'))
print(x)
```

    {'foo', 'baz', 'bar'}



```python
# The set() function converts a string to a set
x = set('foo')
print(x)
```

    {'f', 'o'}



```python
# You can use braces to instantiate a set
x = {'foo'}
print(type(x))

# But empty braces are reserved for dictionaries
y = {}
print(type(y))
```

    <class 'set'>
    <class 'dict'>



```python
# Instantiating a set with braces treats the contents as literals
x = {'foo'}
print(x)
```

    {'foo'}



```python
# The intersection() method (&) returns common elements between two sets
set1 = {1, 2, 3, 4, 5, 6}
set2 = {4, 5, 6, 7, 8, 9}
print(set1.intersection(set2))
print(set1 & set2)
```

    {4, 5, 6}
    {4, 5, 6}



```python
# The union() method (|) returns all the elements from two sets, each represented once
x1 = {'foo', 'bar', 'baz'}
x2 = {'baz', 'qux', 'quux'}
print(x1.union(x2))
print(x1 | x2)
```

    {'qux', 'baz', 'foo', 'quux', 'bar'}
    {'qux', 'baz', 'foo', 'quux', 'bar'}



```python
# The difference() method (-) returns the elements in set1 that aren't in set2
set1 = {1, 2, 3, 4, 5, 6}
set2 = {4, 5, 6, 7, 8, 9}
print(set1.difference(set2))
print(set1 - set2)
```

    {1, 2, 3}
    {1, 2, 3}



```python
# ... and the elements in set2 that aren't in set1
print(set2.difference(set1))
print(set2 - set1)
```

    {8, 9, 7}
    {8, 9, 7}



```python
# The symmetric_difference() method (^) returns all the values from each set that
# are not in both sets.
set1 = {1, 2, 3, 4, 5, 6}
set2 = {4, 5, 6, 7, 8, 9}
set2.symmetric_difference(set1)
set2 ^ set1
```




    {1, 2, 3, 7, 8, 9}



<a name="8"></a>
## 8. Introduction to NumPy


```python
# Lists cannot be multiplied together
list_a = [1, 2, 3]
list_b = [2, 4, 6]

list_a * list_b
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-104-f6837e8a9bfd> in <module>
          3 list_b = [2, 4, 6]
          4 
    ----> 5 list_a * list_b
    

    TypeError: can't multiply sequence by non-int of type 'list'



```python
# To perform element-wise multiplication between two lists, you could
# use a for loop
list_c = []
for i in range(len(list_a)):
    list_c.append(list_a[i] * list_b[i])

list_c
```




    [2, 8, 18]




```python
# NumPy arrays let you perform array operations

# Import numpy, aliased as np
import numpy as np

# Convert lists to arrays
array_a = np.array(list_a)
array_b = np.array(list_b)

# Perform element-wise multiplication between the arrays
array_a * array_b
```




    array([ 2,  8, 18])



<a name="9"></a>
## 9. Basic array operations


```python
import numpy as np

# The np.array() function converts an object to an ndarray
x = np.array([1, 2, 3, 4])
x
```




    array([1, 2, 3, 4])




```python
# Arrays can be indexed
x[-1] = 5
x
```




    array([1, 2, 3, 5])




```python
# Trying to access an index that doesn't exist will throw an error
x[4] = 10
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-109-43f18e2bca94> in <module>
          1 # Trying to access an index that doesn't exist will throw an error
    ----> 2 x[4] = 10
    

    IndexError: index 4 is out of bounds for axis 0 with size 4



```python
# Arrays cast every element they contain as the same data type
arr = np.array([1, 2, 'coconut'])
arr
```




    array(['1', '2', 'coconut'], dtype='<U21')




```python
# NumPy arrays are a class called `ndarray`
print(type(arr))
```

    <class 'numpy.ndarray'>



```python
# The dtype attribute returns the data type of an array's contents
arr = np.array([1, 2, 3])
arr.dtype
```




    dtype('int64')




```python
# The shape attribute returns the number of elements in each dimension
# of an array
arr.shape
```




    (3,)




```python
# The ndim attribute returns the number of dimensions in an array
arr.ndim
```




    1




```python
# Create a 2D array by passing a list of lists to np.array() function
arr_2d = np.array([[1, 2], [3, 4], [5, 6], [7, 8]])
print(arr_2d.shape)
print(arr_2d.ndim)
arr_2d
```

    (4, 2)
    2





    array([[1, 2],
           [3, 4],
           [5, 6],
           [7, 8]])




```python
# Create a 3D aray by passing a list of two lists of lists to np.array() function
arr_3d = np.array([[[1, 2, 3],
                   [3, 4, 5]],

                  [[5, 6, 7],
                   [7, 8, 9]]]
)

print(arr_3d.shape)
print(arr_3d.ndim)
arr_3d
```

    (2, 2, 3)
    3





    array([[[1, 2, 3],
            [3, 4, 5]],
    
           [[5, 6, 7],
            [7, 8, 9]]])




```python
# The reshape() method changes the shape of an array
arr_2d = arr_2d.reshape(2, 4)
arr_2d
```




    array([[1, 2, 3, 4],
           [5, 6, 7, 8]])




```python
# Create new array
arr = np.array([1, 2, 3, 4, 5])

# The mean() method returns the mean of the elements in an array
np.mean(arr)
```




    3.0




```python
# The log() method returns the natural logarithm of the elements in an array
np.log(arr)
```




    array([0.        , 0.69314718, 1.09861229, 1.38629436, 1.60943791])




```python
# The floor() method returns the value of a number rounded down
# to the nearest integer
np.floor(5.7)
```




    5.0




```python
# The floor() method returns the value of a number rounded up
# to the nearest integer
np.ceil(5.3)
```




    6.0



<a name="10"></a>
## 10. Introduction to pandas


```python
# NumPy and pandas are typically imported together.
# np and pd are conventional aliases.
import numpy as np
import pandas as pd
```


```python
# Read in data from a .csv file
dataframe = pd.read_csv('https://raw.githubusercontent.com/adacert/titanic/main/train.csv')

# Print the first 25 rows
dataframe.head(25)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>0</td>
      <td>3</td>
      <td>Moran, Mr. James</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>330877</td>
      <td>8.4583</td>
      <td>NaN</td>
      <td>Q</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>0</td>
      <td>1</td>
      <td>McCarthy, Mr. Timothy J</td>
      <td>male</td>
      <td>54.0</td>
      <td>0</td>
      <td>0</td>
      <td>17463</td>
      <td>51.8625</td>
      <td>E46</td>
      <td>S</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>0</td>
      <td>3</td>
      <td>Palsson, Master. Gosta Leonard</td>
      <td>male</td>
      <td>2.0</td>
      <td>3</td>
      <td>1</td>
      <td>349909</td>
      <td>21.0750</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>1</td>
      <td>3</td>
      <td>Johnson, Mrs. Oscar W (Elisabeth Vilhelmina Berg)</td>
      <td>female</td>
      <td>27.0</td>
      <td>0</td>
      <td>2</td>
      <td>347742</td>
      <td>11.1333</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>1</td>
      <td>2</td>
      <td>Nasser, Mrs. Nicholas (Adele Achem)</td>
      <td>female</td>
      <td>14.0</td>
      <td>1</td>
      <td>0</td>
      <td>237736</td>
      <td>30.0708</td>
      <td>NaN</td>
      <td>C</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>1</td>
      <td>3</td>
      <td>Sandstrom, Miss. Marguerite Rut</td>
      <td>female</td>
      <td>4.0</td>
      <td>1</td>
      <td>1</td>
      <td>PP 9549</td>
      <td>16.7000</td>
      <td>G6</td>
      <td>S</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>1</td>
      <td>1</td>
      <td>Bonnell, Miss. Elizabeth</td>
      <td>female</td>
      <td>58.0</td>
      <td>0</td>
      <td>0</td>
      <td>113783</td>
      <td>26.5500</td>
      <td>C103</td>
      <td>S</td>
    </tr>
    <tr>
      <th>12</th>
      <td>13</td>
      <td>0</td>
      <td>3</td>
      <td>Saundercock, Mr. William Henry</td>
      <td>male</td>
      <td>20.0</td>
      <td>0</td>
      <td>0</td>
      <td>A/5. 2151</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>13</th>
      <td>14</td>
      <td>0</td>
      <td>3</td>
      <td>Andersson, Mr. Anders Johan</td>
      <td>male</td>
      <td>39.0</td>
      <td>1</td>
      <td>5</td>
      <td>347082</td>
      <td>31.2750</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>14</th>
      <td>15</td>
      <td>0</td>
      <td>3</td>
      <td>Vestrom, Miss. Hulda Amanda Adolfina</td>
      <td>female</td>
      <td>14.0</td>
      <td>0</td>
      <td>0</td>
      <td>350406</td>
      <td>7.8542</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>15</th>
      <td>16</td>
      <td>1</td>
      <td>2</td>
      <td>Hewlett, Mrs. (Mary D Kingcome)</td>
      <td>female</td>
      <td>55.0</td>
      <td>0</td>
      <td>0</td>
      <td>248706</td>
      <td>16.0000</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>16</th>
      <td>17</td>
      <td>0</td>
      <td>3</td>
      <td>Rice, Master. Eugene</td>
      <td>male</td>
      <td>2.0</td>
      <td>4</td>
      <td>1</td>
      <td>382652</td>
      <td>29.1250</td>
      <td>NaN</td>
      <td>Q</td>
    </tr>
    <tr>
      <th>17</th>
      <td>18</td>
      <td>1</td>
      <td>2</td>
      <td>Williams, Mr. Charles Eugene</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>244373</td>
      <td>13.0000</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>18</th>
      <td>19</td>
      <td>0</td>
      <td>3</td>
      <td>Vander Planke, Mrs. Julius (Emelia Maria Vande...</td>
      <td>female</td>
      <td>31.0</td>
      <td>1</td>
      <td>0</td>
      <td>345763</td>
      <td>18.0000</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>19</th>
      <td>20</td>
      <td>1</td>
      <td>3</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>NaN</td>
      <td>C</td>
    </tr>
    <tr>
      <th>20</th>
      <td>21</td>
      <td>0</td>
      <td>2</td>
      <td>Fynney, Mr. Joseph J</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>239865</td>
      <td>26.0000</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>21</th>
      <td>22</td>
      <td>1</td>
      <td>2</td>
      <td>Beesley, Mr. Lawrence</td>
      <td>male</td>
      <td>34.0</td>
      <td>0</td>
      <td>0</td>
      <td>248698</td>
      <td>13.0000</td>
      <td>D56</td>
      <td>S</td>
    </tr>
    <tr>
      <th>22</th>
      <td>23</td>
      <td>1</td>
      <td>3</td>
      <td>McGowan, Miss. Anna "Annie"</td>
      <td>female</td>
      <td>15.0</td>
      <td>0</td>
      <td>0</td>
      <td>330923</td>
      <td>8.0292</td>
      <td>NaN</td>
      <td>Q</td>
    </tr>
    <tr>
      <th>23</th>
      <td>24</td>
      <td>1</td>
      <td>1</td>
      <td>Sloper, Mr. William Thompson</td>
      <td>male</td>
      <td>28.0</td>
      <td>0</td>
      <td>0</td>
      <td>113788</td>
      <td>35.5000</td>
      <td>A6</td>
      <td>S</td>
    </tr>
    <tr>
      <th>24</th>
      <td>25</td>
      <td>0</td>
      <td>3</td>
      <td>Palsson, Miss. Torborg Danira</td>
      <td>female</td>
      <td>8.0</td>
      <td>3</td>
      <td>1</td>
      <td>349909</td>
      <td>21.0750</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Calculate the mean of the Age column
dataframe['Age'].mean()
```




    29.69911764705882




```python
# Calculate the maximum value contained in the Age column
dataframe['Age'].max()
```




    80.0




```python
# Calculate the minimum value contained in the Age column
dataframe['Age'].min()
```




    0.42




```python
# Calculate the standard deviation of the values in the Age column
dataframe['Age'].std()
```




    14.526497332334044




```python
# Return the number of rows that share the same value in the Pclass column
dataframe['Pclass'].value_counts()
```




    3    491
    1    216
    2    184
    Name: Pclass, dtype: int64




```python
# The describe() method returns summary statistics of the dataframe
dataframe.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Fare</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>714.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>446.000000</td>
      <td>0.383838</td>
      <td>2.308642</td>
      <td>29.699118</td>
      <td>0.523008</td>
      <td>0.381594</td>
      <td>32.204208</td>
    </tr>
    <tr>
      <th>std</th>
      <td>257.353842</td>
      <td>0.486592</td>
      <td>0.836071</td>
      <td>14.526497</td>
      <td>1.102743</td>
      <td>0.806057</td>
      <td>49.693429</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.420000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>223.500000</td>
      <td>0.000000</td>
      <td>2.000000</td>
      <td>20.125000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>7.910400</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>446.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>28.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>14.454200</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>668.500000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>38.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>31.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>891.000000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>80.000000</td>
      <td>8.000000</td>
      <td>6.000000</td>
      <td>512.329200</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Filter the data to return only rows where value in Age column is greater than 60
# and value in Pclass column equals 3
dataframe[(dataframe['Age'] > 60) & (dataframe['Pclass'] == 3)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>116</th>
      <td>117</td>
      <td>0</td>
      <td>3</td>
      <td>Connors, Mr. Patrick</td>
      <td>male</td>
      <td>70.5</td>
      <td>0</td>
      <td>0</td>
      <td>370369</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
    </tr>
    <tr>
      <th>280</th>
      <td>281</td>
      <td>0</td>
      <td>3</td>
      <td>Duane, Mr. Frank</td>
      <td>male</td>
      <td>65.0</td>
      <td>0</td>
      <td>0</td>
      <td>336439</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
    </tr>
    <tr>
      <th>326</th>
      <td>327</td>
      <td>0</td>
      <td>3</td>
      <td>Nysveen, Mr. Johan Hansen</td>
      <td>male</td>
      <td>61.0</td>
      <td>0</td>
      <td>0</td>
      <td>345364</td>
      <td>6.2375</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>483</th>
      <td>484</td>
      <td>1</td>
      <td>3</td>
      <td>Turkula, Mrs. (Hedwig)</td>
      <td>female</td>
      <td>63.0</td>
      <td>0</td>
      <td>0</td>
      <td>4134</td>
      <td>9.5875</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>851</th>
      <td>852</td>
      <td>0</td>
      <td>3</td>
      <td>Svensson, Mr. Johan</td>
      <td>male</td>
      <td>74.0</td>
      <td>0</td>
      <td>0</td>
      <td>347060</td>
      <td>7.7750</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a new column called 2023_Fare that contains the inflation-adjusted
# fare of each ticket in 2023 pounds
dataframe['2023_Fare'] = dataframe['Fare'] * 146.14
dataframe
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>2023_Fare</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>1059.515000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>10417.341462</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>1158.159500</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>7760.034000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>1176.427000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>886</th>
      <td>887</td>
      <td>0</td>
      <td>2</td>
      <td>Montvila, Rev. Juozas</td>
      <td>male</td>
      <td>27.0</td>
      <td>0</td>
      <td>0</td>
      <td>211536</td>
      <td>13.0000</td>
      <td>NaN</td>
      <td>S</td>
      <td>1899.820000</td>
    </tr>
    <tr>
      <th>887</th>
      <td>888</td>
      <td>1</td>
      <td>1</td>
      <td>Graham, Miss. Margaret Edith</td>
      <td>female</td>
      <td>19.0</td>
      <td>0</td>
      <td>0</td>
      <td>112053</td>
      <td>30.0000</td>
      <td>B42</td>
      <td>S</td>
      <td>4384.200000</td>
    </tr>
    <tr>
      <th>888</th>
      <td>889</td>
      <td>0</td>
      <td>3</td>
      <td>Johnston, Miss. Catherine Helen "Carrie"</td>
      <td>female</td>
      <td>NaN</td>
      <td>1</td>
      <td>2</td>
      <td>W./C. 6607</td>
      <td>23.4500</td>
      <td>NaN</td>
      <td>S</td>
      <td>3426.983000</td>
    </tr>
    <tr>
      <th>889</th>
      <td>890</td>
      <td>1</td>
      <td>1</td>
      <td>Behr, Mr. Karl Howell</td>
      <td>male</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>111369</td>
      <td>30.0000</td>
      <td>C148</td>
      <td>C</td>
      <td>4384.200000</td>
    </tr>
    <tr>
      <th>890</th>
      <td>891</td>
      <td>0</td>
      <td>3</td>
      <td>Dooley, Mr. Patrick</td>
      <td>male</td>
      <td>32.0</td>
      <td>0</td>
      <td>0</td>
      <td>370376</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
      <td>1132.585000</td>
    </tr>
  </tbody>
</table>
<p>891 rows × 13 columns</p>
</div>




```python
# Use iloc to access data using index numbers.
# Select row 1, column 3.
dataframe.iloc[1][3]
```




    'Cumings, Mrs. John Bradley (Florence Briggs Thayer)'




```python
# Group customers by Sex and Pclass and calculate the total paid for each group
# and the mean price paid for each group
fare = dataframe.groupby(['Sex', 'Pclass']).agg({'Fare': ['count', 'sum']})
fare['fare_avg'] = fare['Fare']['sum'] / fare['Fare']['count']
fare
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th colspan="2" halign="left">Fare</th>
      <th>fare_avg</th>
    </tr>
    <tr>
      <th></th>
      <th></th>
      <th>count</th>
      <th>sum</th>
      <th></th>
    </tr>
    <tr>
      <th>Sex</th>
      <th>Pclass</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">female</th>
      <th>1</th>
      <td>94</td>
      <td>9975.8250</td>
      <td>106.125798</td>
    </tr>
    <tr>
      <th>2</th>
      <td>76</td>
      <td>1669.7292</td>
      <td>21.970121</td>
    </tr>
    <tr>
      <th>3</th>
      <td>144</td>
      <td>2321.1086</td>
      <td>16.118810</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">male</th>
      <th>1</th>
      <td>122</td>
      <td>8201.5875</td>
      <td>67.226127</td>
    </tr>
    <tr>
      <th>2</th>
      <td>108</td>
      <td>2132.1125</td>
      <td>19.741782</td>
    </tr>
    <tr>
      <th>3</th>
      <td>347</td>
      <td>4393.5865</td>
      <td>12.661633</td>
    </tr>
  </tbody>
</table>
</div>



<a name="11"></a>
## 11. pandas basics


```python
import pandas as pd

# Use pd.DataFrame() function to create a dataframe from a dictionary
data = {'col1': [1, 2], 'col2': [3, 4]}
df = pd.DataFrame(data=data)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>col1</th>
      <th>col2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use pd.DataFrame() function to create a dataframe from a numpy array
df2 = pd.DataFrame(np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]),
                   columns=['a', 'b', 'c'], index=['x', 'y', 'z'])
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>x</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>y</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>z</th>
      <td>7</td>
      <td>8</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use pd.read_csv() function to create a dataframe from a .csv file
# from a URL or filepath
df3 = pd.read_csv('https://raw.githubusercontent.com/adacert/titanic/main/train.csv')
df3.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Print class of first row
print(type(df3.iloc[0]))

# Print class of "Name" column
print(type(df3['Name']))
```

    <class 'pandas.core.series.Series'>
    <class 'pandas.core.series.Series'>



```python
# Create a copy of df3 named 'titanic'
titanic = df3

# The head() method outputs the first 5 rows of dataframe
titanic.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>




```python
# The columns attribute returns an Index object containing the dataframe's columns
titanic.columns
```




    Index(['PassengerId', 'Survived', 'Pclass', 'Name', 'Sex', 'Age', 'SibSp',
           'Parch', 'Ticket', 'Fare', 'Cabin', 'Embarked'],
          dtype='object')




```python
# The shape attribute returns the shape of the dataframe (rows, columns)
titanic.shape
```




    (891, 12)




```python
# The info() method returns summary information about the dataframe
titanic.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 12 columns):
     #   Column       Non-Null Count  Dtype  
    ---  ------       --------------  -----  
     0   PassengerId  891 non-null    int64  
     1   Survived     891 non-null    int64  
     2   Pclass       891 non-null    int64  
     3   Name         891 non-null    object 
     4   Sex          891 non-null    object 
     5   Age          714 non-null    float64
     6   SibSp        891 non-null    int64  
     7   Parch        891 non-null    int64  
     8   Ticket       891 non-null    object 
     9   Fare         891 non-null    float64
     10  Cabin        204 non-null    object 
     11  Embarked     889 non-null    object 
    dtypes: float64(2), int64(5), object(5)
    memory usage: 83.7+ KB



```python
# You can select a column by name using brackets
titanic['Age']
```




    0      22.0
    1      38.0
    2      26.0
    3      35.0
    4      35.0
           ... 
    886    27.0
    887    19.0
    888     NaN
    889    26.0
    890    32.0
    Name: Age, Length: 891, dtype: float64




```python
# You can select a column by name using dot notation
# only when its name contains no spaces or special characters
titanic.Age
```




    0      22.0
    1      38.0
    2      26.0
    3      35.0
    4      35.0
           ... 
    886    27.0
    887    19.0
    888     NaN
    889    26.0
    890    32.0
    Name: Age, Length: 891, dtype: float64




```python
# You can create a DataFrame object of specific columns using a list
# of column names inside brackets
titanic[['Name', 'Age']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Braund, Mr. Owen Harris</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>38.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Heikkinen, Miss. Laina</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Allen, Mr. William Henry</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>886</th>
      <td>Montvila, Rev. Juozas</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>887</th>
      <td>Graham, Miss. Margaret Edith</td>
      <td>19.0</td>
    </tr>
    <tr>
      <th>888</th>
      <td>Johnston, Miss. Catherine Helen "Carrie"</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>889</th>
      <td>Behr, Mr. Karl Howell</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>890</th>
      <td>Dooley, Mr. Patrick</td>
      <td>32.0</td>
    </tr>
  </tbody>
</table>
<p>891 rows × 2 columns</p>
</div>




```python
# Use iloc to return a Series object of the data in row 0
titanic.iloc[0]
```




    PassengerId                          1
    Survived                             0
    Pclass                               3
    Name           Braund, Mr. Owen Harris
    Sex                               male
    Age                               22.0
    SibSp                                1
    Parch                                0
    Ticket                       A/5 21171
    Fare                              7.25
    Cabin                              NaN
    Embarked                             S
    Name: 0, dtype: object




```python
# Use iloc to return a DataFrame view of the data in row 0
titanic.iloc[[0]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.25</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use iloc to return a DataFrame view of the data in rows 0, 1, 2
titanic.iloc[0:3]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use iloc to return a DataFrame view of rows 0-2 at columns 3 and 4
titanic.iloc[0:3, [3, 4]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use iloc to return a DataFrame view of all rows at column 3
titanic.iloc[:, [3]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Braund, Mr. Owen Harris</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Heikkinen, Miss. Laina</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Allen, Mr. William Henry</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>886</th>
      <td>Montvila, Rev. Juozas</td>
    </tr>
    <tr>
      <th>887</th>
      <td>Graham, Miss. Margaret Edith</td>
    </tr>
    <tr>
      <th>888</th>
      <td>Johnston, Miss. Catherine Helen "Carrie"</td>
    </tr>
    <tr>
      <th>889</th>
      <td>Behr, Mr. Karl Howell</td>
    </tr>
    <tr>
      <th>890</th>
      <td>Dooley, Mr. Patrick</td>
    </tr>
  </tbody>
</table>
<p>891 rows × 1 columns</p>
</div>




```python
# Use iloc to access value in row 0, column 3
titanic.iloc[0, 3]
```




    'Braund, Mr. Owen Harris'




```python
# Use loc to access values in rows 0-3 at just the Name column
titanic.loc[0:3, ['Name']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Braund, Mr. Owen Harris</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Heikkinen, Miss. Laina</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a new column in the dataframe containing the value in the Age column + 100
titanic['Age_plus_100'] = titanic['Age'] + 100
titanic.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>Age_plus_100</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>122.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>138.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>126.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>135.0</td>
    </tr>
  </tbody>
</table>
</div>



<a name="12"></a>
## 12. Boolean masking


```python
# Instantiate a dictionary of planetary data
data = {'planet': ['Mercury', 'Venus', 'Earth', 'Mars',
                   'Jupiter', 'Saturn', 'Uranus', 'Neptune'],
       'radius_km': [2440, 6052, 6371, 3390, 69911, 58232,
                     25362, 24622],
       'moons': [0, 0, 1, 2, 80, 83, 27, 14]
        }
# Use pd.DataFrame() function to convert dictionary to dataframe
planets = pd.DataFrame(data)
planets
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>25362</td>
      <td>27</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a Boolean mask of planets with fewer than 20 moons
mask = planets['moons'] < 20
mask
```




    0     True
    1     True
    2     True
    3     True
    4    False
    5    False
    6    False
    7     True
    Name: moons, dtype: bool




```python
# Apply the Boolean mask to the dataframe to filter it so it contains
# only the planets with fewer than 20 moons
planets[mask]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Define the Boolean mask and apply it in a single line
planets[planets['moons'] < 20]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Boolean masks don't change the data. They're just views.
planets
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>25362</td>
      <td>27</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
# You can assign a dataframe view to a named variable
moons_under_20 = planets[mask]
moons_under_20
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a Boolean mask of planets with fewer than 10 moons OR more than 50 moons
mask = (planets['moons'] < 10) | (planets['moons'] > 50)
mask
```




    0     True
    1     True
    2     True
    3     True
    4     True
    5     True
    6    False
    7    False
    Name: moons, dtype: bool




```python
# Apply the Boolean mask to filter the data
planets[mask]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a Boolean mask of planets with more than 20 moons, excluding them if they
# have 80 moons or if their radius is less than 50,000 km.
mask = (planets['moons'] > 20) & ~(planets['moons'] == 80) & ~(planets['radius_km'] < 50000)

# Apply the mask
planets[mask]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
    </tr>
  </tbody>
</table>
</div>



<a name="13"></a>
## 13. Grouping and aggregation


```python
import numpy as np
import pandas as pd

# Instantiate a dictionary of planetary data
data = {'planet': ['Mercury', 'Venus', 'Earth', 'Mars',
                   'Jupiter', 'Saturn', 'Uranus', 'Neptune'],
        'radius_km': [2440, 6052, 6371, 3390, 69911, 58232,
                     25362, 24622],
        'moons': [0, 0, 1, 2, 80, 83, 27, 14],
        'type': ['terrestrial', 'terrestrial', 'terrestrial', 'terrestrial',
                 'gas giant', 'gas giant', 'ice giant', 'ice giant'],
        'rings': ['no', 'no', 'no', 'no', 'yes', 'yes', 'yes','yes'],
        'mean_temp_c': [167, 464, 15, -65, -110, -140, -195, -200],
        'magnetic_field': ['yes', 'no', 'yes', 'no', 'yes', 'yes', 'yes', 'yes']
        }

# Use pd.DataFrame() function to convert dictionary to dataframe
planets = pd.DataFrame(data)
planets
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
      <th>type</th>
      <th>rings</th>
      <th>mean_temp_c</th>
      <th>magnetic_field</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>167</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>464</td>
      <td>no</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>15</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>-65</td>
      <td>no</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-110</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-140</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>25362</td>
      <td>27</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-195</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-200</td>
      <td>yes</td>
    </tr>
  </tbody>
</table>
</div>




```python
# The groupby() function returns a groupby object
planets.groupby(['type'])
```




    <pandas.core.groupby.generic.DataFrameGroupBy object at 0x7ff98cfd24d0>




```python
# Apply the sum() function to the groupby object to get the sum
# of the values in each numerical column for each group
planets.groupby(['type']).sum()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>radius_km</th>
      <th>moons</th>
      <th>mean_temp_c</th>
    </tr>
    <tr>
      <th>type</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>gas giant</th>
      <td>128143</td>
      <td>163</td>
      <td>-250</td>
    </tr>
    <tr>
      <th>ice giant</th>
      <td>49984</td>
      <td>41</td>
      <td>-395</td>
    </tr>
    <tr>
      <th>terrestrial</th>
      <td>18253</td>
      <td>3</td>
      <td>581</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Apply the sum function to the groupby object and select
# only the 'moons' column
planets.groupby(['type']).sum()[['moons']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>moons</th>
    </tr>
    <tr>
      <th>type</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>gas giant</th>
      <td>163</td>
    </tr>
    <tr>
      <th>ice giant</th>
      <td>41</td>
    </tr>
    <tr>
      <th>terrestrial</th>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Group by type and magnetic_field and get the mean of the values
# in the numeric columns for each group
planets.groupby(['type', 'magnetic_field']).mean()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>radius_km</th>
      <th>moons</th>
      <th>mean_temp_c</th>
    </tr>
    <tr>
      <th>type</th>
      <th>magnetic_field</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>gas giant</th>
      <th>yes</th>
      <td>64071.5</td>
      <td>81.5</td>
      <td>-125.0</td>
    </tr>
    <tr>
      <th>ice giant</th>
      <th>yes</th>
      <td>24992.0</td>
      <td>20.5</td>
      <td>-197.5</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">terrestrial</th>
      <th>no</th>
      <td>4721.0</td>
      <td>1.0</td>
      <td>199.5</td>
    </tr>
    <tr>
      <th>yes</th>
      <td>4405.5</td>
      <td>0.5</td>
      <td>91.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Group by type, then use the agg() function to get the mean and median
# of the values in the numeric columns for each group
planets.groupby(['type']).agg(['mean', 'median'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="2" halign="left">radius_km</th>
      <th colspan="2" halign="left">moons</th>
      <th colspan="2" halign="left">mean_temp_c</th>
    </tr>
    <tr>
      <th></th>
      <th>mean</th>
      <th>median</th>
      <th>mean</th>
      <th>median</th>
      <th>mean</th>
      <th>median</th>
    </tr>
    <tr>
      <th>type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>gas giant</th>
      <td>64071.50</td>
      <td>64071.5</td>
      <td>81.50</td>
      <td>81.5</td>
      <td>-125.00</td>
      <td>-125.0</td>
    </tr>
    <tr>
      <th>ice giant</th>
      <td>24992.00</td>
      <td>24992.0</td>
      <td>20.50</td>
      <td>20.5</td>
      <td>-197.50</td>
      <td>-197.5</td>
    </tr>
    <tr>
      <th>terrestrial</th>
      <td>4563.25</td>
      <td>4721.0</td>
      <td>0.75</td>
      <td>0.5</td>
      <td>145.25</td>
      <td>91.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Group by type and magnetic_field, then use the agg() function to get the
# mean and max of the values in the numeric columns for each group
planets.groupby(['type', 'magnetic_field']).agg(['mean', 'max'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th colspan="2" halign="left">radius_km</th>
      <th colspan="2" halign="left">moons</th>
      <th colspan="2" halign="left">mean_temp_c</th>
    </tr>
    <tr>
      <th></th>
      <th></th>
      <th>mean</th>
      <th>max</th>
      <th>mean</th>
      <th>max</th>
      <th>mean</th>
      <th>max</th>
    </tr>
    <tr>
      <th>type</th>
      <th>magnetic_field</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>gas giant</th>
      <th>yes</th>
      <td>64071.5</td>
      <td>69911</td>
      <td>81.5</td>
      <td>83</td>
      <td>-125.0</td>
      <td>-110</td>
    </tr>
    <tr>
      <th>ice giant</th>
      <th>yes</th>
      <td>24992.0</td>
      <td>25362</td>
      <td>20.5</td>
      <td>27</td>
      <td>-197.5</td>
      <td>-195</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">terrestrial</th>
      <th>no</th>
      <td>4721.0</td>
      <td>6052</td>
      <td>1.0</td>
      <td>2</td>
      <td>199.5</td>
      <td>464</td>
    </tr>
    <tr>
      <th>yes</th>
      <td>4405.5</td>
      <td>6371</td>
      <td>0.5</td>
      <td>1</td>
      <td>91.0</td>
      <td>167</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Define a function that returns the 90 percentile of an array
def percentile_90(x):
    return x.quantile(0.9)
```


```python
# Group by type and magnetic_field, then use the agg() function to apply the
# mean and the custom-defined `percentile_90()` function to the numeric
# columns for each group
planets.groupby(['type', 'magnetic_field']).agg(['mean', percentile_90])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th colspan="2" halign="left">radius_km</th>
      <th colspan="2" halign="left">moons</th>
      <th colspan="2" halign="left">mean_temp_c</th>
    </tr>
    <tr>
      <th></th>
      <th></th>
      <th>mean</th>
      <th>percentile_90</th>
      <th>mean</th>
      <th>percentile_90</th>
      <th>mean</th>
      <th>percentile_90</th>
    </tr>
    <tr>
      <th>type</th>
      <th>magnetic_field</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>gas giant</th>
      <th>yes</th>
      <td>64071.5</td>
      <td>68743.1</td>
      <td>81.5</td>
      <td>82.7</td>
      <td>-125.0</td>
      <td>-113.0</td>
    </tr>
    <tr>
      <th>ice giant</th>
      <th>yes</th>
      <td>24992.0</td>
      <td>25288.0</td>
      <td>20.5</td>
      <td>25.7</td>
      <td>-197.5</td>
      <td>-195.5</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">terrestrial</th>
      <th>no</th>
      <td>4721.0</td>
      <td>5785.8</td>
      <td>1.0</td>
      <td>1.8</td>
      <td>199.5</td>
      <td>411.1</td>
    </tr>
    <tr>
      <th>yes</th>
      <td>4405.5</td>
      <td>5977.9</td>
      <td>0.5</td>
      <td>0.9</td>
      <td>91.0</td>
      <td>151.8</td>
    </tr>
  </tbody>
</table>
</div>



<a name="14"></a>
## 14. Merging and joining data


```python
import numpy as np
import pandas as pd

# Instantiate a dictionary of planetary data
data = {'planet': ['Mercury', 'Venus', 'Earth', 'Mars'],
        'radius_km': [2440, 6052, 6371, 3390],
        'moons': [0, 0, 1, 2],
        }
# Use pd.DataFrame() function to convert dictionary to dataframe
df1 = pd.DataFrame(data)
df1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Instantiate a dictionary of planetary data
data = {'planet': ['Jupiter', 'Saturn', 'Uranus', 'Neptune'],
        'radius_km': [69911, 58232, 25362, 24622],
        'moons': [80, 83, 27, 14],
        }
# Use pd.DataFrame() function to convert dictionary to dataframe
df2 = pd.DataFrame(data)
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Uranus</td>
      <td>25362</td>
      <td>27</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
# The pd.concat() function can combine the two dataframes along axis 0,
# with the second dataframe being added as new rows to the first dataframe
df3 = pd.concat([df1, df2], axis=0)
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Uranus</td>
      <td>25362</td>
      <td>27</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Reset the row indices
df3 = df3.reset_index(drop=True)
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>25362</td>
      <td>27</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
# NOTE: THIS CELL WAS NOT SHOWN IN THE INSTRUCTIONAL VIDEO, BUT WAS RUN AS A
#       SETUP CELL
data = {'planet': ['Earth', 'Mars','Jupiter', 'Saturn', 'Uranus',
                   'Neptune', 'Janssen', 'Tadmor'],
        'type': ['terrestrial', 'terrestrial','gas giant', 'gas giant',
                 'ice giant', 'ice giant', 'super earth','gas giant'],
        'rings': ['no', 'no', 'yes', 'yes', 'yes','yes', 'no', None],
        'mean_temp_c': [15, -65, -110, -140, -195, -200, None, None],
        'magnetic_field': ['yes', 'no', 'yes', 'yes', 'yes', 'yes', None, None],
        'life': [1, 0, 0, 0, 0, 0, 1, 1]
        }
df4 = pd.DataFrame(data)
```


```python
df4
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>type</th>
      <th>rings</th>
      <th>mean_temp_c</th>
      <th>magnetic_field</th>
      <th>life</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Earth</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>15.0</td>
      <td>yes</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Mars</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>-65.0</td>
      <td>no</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jupiter</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-110.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Saturn</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-140.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Uranus</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-195.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Neptune</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-200.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Janssen</td>
      <td>super earth</td>
      <td>no</td>
      <td>NaN</td>
      <td>None</td>
      <td>1</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Tadmor</td>
      <td>gas giant</td>
      <td>None</td>
      <td>NaN</td>
      <td>None</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use pd.merge() to combine dataframes.
# Inner merge retains only keys that appear in both dataframes.
inner = pd.merge(df3, df4, on='planet', how='inner')
inner
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
      <th>type</th>
      <th>rings</th>
      <th>mean_temp_c</th>
      <th>magnetic_field</th>
      <th>life</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>15.0</td>
      <td>yes</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>-65.0</td>
      <td>no</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-110.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-140.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Uranus</td>
      <td>25362</td>
      <td>27</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-195.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-200.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use pd.merge() to combine dataframes.
# Outer merge retains all keys from both dataframes.
outer = pd.merge(df3, df4, on='planet', how='outer')
outer
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
      <th>type</th>
      <th>rings</th>
      <th>mean_temp_c</th>
      <th>magnetic_field</th>
      <th>life</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371.0</td>
      <td>1.0</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>15.0</td>
      <td>yes</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390.0</td>
      <td>2.0</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>-65.0</td>
      <td>no</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>69911.0</td>
      <td>80.0</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-110.0</td>
      <td>yes</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>58232.0</td>
      <td>83.0</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-140.0</td>
      <td>yes</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>25362.0</td>
      <td>27.0</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-195.0</td>
      <td>yes</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622.0</td>
      <td>14.0</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-200.0</td>
      <td>yes</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Janssen</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>super earth</td>
      <td>no</td>
      <td>NaN</td>
      <td>None</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Tadmor</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>gas giant</td>
      <td>None</td>
      <td>NaN</td>
      <td>None</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use pd.merge() to combine dataframes.
# Left merge retains only keys that appear in the left dataframe.
left = pd.merge(df3, df4, on='planet', how='left')
left
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
      <th>type</th>
      <th>rings</th>
      <th>mean_temp_c</th>
      <th>magnetic_field</th>
      <th>life</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mercury</td>
      <td>2440</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Venus</td>
      <td>6052</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Earth</td>
      <td>6371</td>
      <td>1</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>15.0</td>
      <td>yes</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mars</td>
      <td>3390</td>
      <td>2</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>-65.0</td>
      <td>no</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jupiter</td>
      <td>69911</td>
      <td>80</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-110.0</td>
      <td>yes</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Saturn</td>
      <td>58232</td>
      <td>83</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-140.0</td>
      <td>yes</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Uranus</td>
      <td>25362</td>
      <td>27</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-195.0</td>
      <td>yes</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Neptune</td>
      <td>24622</td>
      <td>14</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-200.0</td>
      <td>yes</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use pd.merge() to combine dataframes.
# Right merge retains only keys that appear in right dataframe.
right = pd.merge(df3, df4, on='planet', how='right')
right
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>planet</th>
      <th>radius_km</th>
      <th>moons</th>
      <th>type</th>
      <th>rings</th>
      <th>mean_temp_c</th>
      <th>magnetic_field</th>
      <th>life</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Earth</td>
      <td>6371.0</td>
      <td>1.0</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>15.0</td>
      <td>yes</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Mars</td>
      <td>3390.0</td>
      <td>2.0</td>
      <td>terrestrial</td>
      <td>no</td>
      <td>-65.0</td>
      <td>no</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jupiter</td>
      <td>69911.0</td>
      <td>80.0</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-110.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Saturn</td>
      <td>58232.0</td>
      <td>83.0</td>
      <td>gas giant</td>
      <td>yes</td>
      <td>-140.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Uranus</td>
      <td>25362.0</td>
      <td>27.0</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-195.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Neptune</td>
      <td>24622.0</td>
      <td>14.0</td>
      <td>ice giant</td>
      <td>yes</td>
      <td>-200.0</td>
      <td>yes</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Janssen</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>super earth</td>
      <td>no</td>
      <td>NaN</td>
      <td>None</td>
      <td>1</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Tadmor</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>gas giant</td>
      <td>None</td>
      <td>NaN</td>
      <td>None</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>


