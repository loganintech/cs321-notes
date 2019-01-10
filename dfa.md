## Ex: Design a DFA
{ w E {a, b}* | w contains `aa` substring }

![](https://i.imgur.com/GibeNuy.png)

L(M) = { w E {a, b}* | w contains `abba` as substring}

![](https://i.imgur.com/TfaiZBn.png)

{ w E {a, b}* |  w doesn't contain `aa`}

![](https://i.imgur.com/qfqr8v2.png)

L(M) = { w E {a, b}* | w ends with abba }

![](https://i.imgur.com/9Xp9zlu.png)

L(M) = { w E {0, 1}* | w is binary encoding of even numbers }

![](https://i.imgur.com/c1Ohlrr.png)

L(M) = { w E {0, 1}* | w is binary encoding of multiples of 3 }

![](https://i.imgur.com/CxpuY0l.png)

* Note: Concatenating 1 to a binary number is doubling and adding 1 to the number.

Def:
  * Bin: {0, 1}* --> |N
  * bin(x) is the number encoded in base 10 by string x
  * base case: bin(E) = 0
  * recessive case: {bin(x.0)} = 2\*bin(x) AND bin(x.1) = 2\*bin(x) + 1
  * bin(x.b) = 2\*bin(x)+b
```
Want: { w E {0, 1}* | bin(w) mod 3 = 0}
Have: S = Q x E -> Q
      S(q, c) is the state we reach when in state q and read single char c
```
```
Def:
  S*: Q       X(E*) -> Q
  S*(q, x) is state you reach when in state q and read string x

Ex:
  S*(q, `abc`)
  = S(S(S(q, a), b), c)
```

