Some bit manipulation techniques/tricks seem useful to implement in my code, so I want to be more comfortable with bit manipulation. This repo will be a place for me to dump my notes.

# Basics

### operators

| operation                       ||
| :----------------------: | :---: |
| &         | Bitwise AND          | 
| \|        | Bitwise OR           | 
| ^         | Bitwise XOR          | 
| ~         | Bitwise NOT          | 
| <<        | left shift           | 
| >>        | right shift          |
| >>>       | unsigned right shift |

##### example usage

& Bitwise AND
```
1 0 1 0 \ multiply 
1 1 0 0 / these
-------
1 0 0 0 <-- result of multiplication
```

---

| Bitwise OR
```
1 0 1 0
1 1 0 0
-------
1 0 1 0 <-- 1 if any of the pair above is 1 else 0
```

---

^ Bitwise XOR
```
1 0 1 0
1 1 0 0
-------
0 1 1 0 <-- 1 if only one of the pair above is 1 else 0
```

---

~ Bitwise NOT
```
~ 1 1 1 1 0 0 1 0 1 0 0 1 1 1
------------------------------- 
  0 0 0 0 1 1 0 1 0 1 1 0 0 0   flip all the bits; 1's become 0's and vice versa
```

---

\<\< left shift
```
<<

110 << 3
move 3 positions left
---------------------
      1 1 0
    1 1 0 0 1st shift
  1 1 0 0 0 2nd shift
1 1 0 0 0 0 3rd shift
```

---

\>\> right shift
```
111001 >> 3
move 3 positions right
            | ignore these
------------|----------------
1 1 1 0 0 1 |
  1 1 1 0 0 | 1     1st shift
    1 1 1 0 | 0 1   2nd shift
      1 1 1 | 0 0 1 3rd shift
      1 1 1 | final value
            |
```

---













# Tricks

## &
### bitwise enum
| ... | 1   | 1   | 1   | 1   | 1   | 1   | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ... | 64  | 32  | 16  | 8   | 4   | 2   | 1   |

Suppose we wanted to store the characteristics of food such as sour, sweet, salty, and spicy.

We can store these characteristics in an unsigned integer where each bit value represents a different characteristic.

```
// Example
binary  | decimal | characteristic
--------o---------o----------------
      1 | 1       | sour
    1 0 | 2       | sweet
  1 0 0 | 4       | salty
1 0 0 0 | 8       | spicy
```

So if we wanted the characteristic sweet and sour, we can add the values of the characteristics. ie. 1 + 2 = 3 (0b11)

To figure out which characteristics that the food contains, we can make use of the bitwise AND operator. Comparing the food's characteristic value with the value of the characteristic. If the result is equal to the value of the characteristic then the food contains that characteristic, otherwise it does not contain that characteristic.

```
// Example
sweet and sour = 3 (0b11)
sweet = 2 (0b10)
sour = 1 (0b1)
salty = 4 (0b100)

3 & 2 == 2 (0b10) √ is sweet
3 & 1 == 1 (0b1)  √ is sour
3 & 4 == 0 (0b0)  x is not salty
```

## ~

### Truthy indexOf
In JavaScript, there is a function for arrays, `indexOf(element)` which returns the index of the element in the array if it exists, otherwise it returns -1. We can use the bitwise NOT operator to make the value returned by this function truthy.

```js
~-1 == 0 // 0 is false
~n != 0 // where n != -1; any number not equal to 0 is true
```

## >>

### negative, 0, positive values to 0,1, or 2
Suppose you have an array of 3 colours `[red, white, green]` and given a value n, you want the colour:

* red if n is negative (index 0)
* white if n is 0 (index 1)
* green if n is positive (index 2)

To get the correct index we can use this formula `1 + (n >> 31) - (-n >> 31)`. This assumes n is a 32-bit integer, otherwise this trick may not work. `n >> 31` will evaluate to -1 if n is negative otherwise it will evaluate to 0.
