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

| Bitwise OR
```
1 0 1 0
1 1 0 0
-------
1 0 1 0 <-- 1 if any of the pair above is 1 else 0
```

^ Bitwise XOR
```
1 0 1 0
1 1 0 0
-------
0 1 1 0 <-- 1 if only one of the pair above is 1 else 0
```

~ Bitwise NOT
```
~ 1 0

TODO
```

\<\< left shift
```
TODO
```

\>\> right shift
```
TODO
```

\>\>\> unsigned right shift
```
TODO
```
