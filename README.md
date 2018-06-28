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

### Truthy indexOf
In JavaScript, there is a function for arrays, `indexOf(element)` which returns the index of the element in the array if it exists, otherwise it returns -1. We can use the bitwise NOT operator to make the value returned by this function truthy.

```js
~-1 == 0 // 0 is false
~n != 0 // where n != -1; any number not equal to 0 is true
```

### negative, 0, positive values to 0,1, or 2
Suppose you have an array of 3 colours `[red, white, green]` and given a value n, you want the colour:

* red if n is negative (index 0)
* white if n is 0 (index 1)
* green if n is positive (index 2)

To get the correct index we can use this formula `1 + (n >> 31) - (-n >> 31)`. This assumes n is a 32-bit integer, otherwise this trick may not work. `n >> 31` will evaluate to -1 if n is negative otherwise it will evaluate to 0.
