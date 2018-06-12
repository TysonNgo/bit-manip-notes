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

