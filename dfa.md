## Notes

* Requires O(1) memory regardless of input string size
* Has finite set of states and finite set of transitions
* Convention:
  * e (epsilon) is the `empty string`. Sometimes also `labda`




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

Define in terms of S
S*(q, E) = q
S*(q, xb) = S(S*(q, x), b) for (b in E)


```
Def:

given M = (Q, E, S, s, F)
L(M) = { w in E* | S*(s, w) in F}

"all strings that reach an accept state, when starting from start state"
```

Let's prove correctness of the DFA from earlier

![](https://i.imgur.com/CxpuY0l.png)

Note: S(qi, b) = q(2i+b) mod 3

State 0: S(q0, 1) == (q1 = q(2(0) + 1) mod 3 = q(1 mod 3) = q(1))

```
Claim: after reading input x, DFA is in state q(bin(x) mod 3)

Proof: Bg induction on (length of) x

Base case: x = E

S*(q0, e) = q0 = qbin(e) mod 3

Induction Step
Suppose 1H true for X
let `b e E`
S*(q0, xb)

extend transition function <-- S*(q0, xb) = S(S*(q0, x), b) = S(qbin(x) mod 3, b) (1H)

previous note: S(qi, b) = q2i+b mod 3
 =q(2(bin(x) mod 3 + b)) mod 3
 =q(2(bin(x) + b)) mod 3
 =q(bin(xb) mod 3) -> from the definition of binary

So, the claim is true somehow. Also, for longer strings xb
Concluding correctness of the dfa
L(M) = {x in {0, 1}* | X*(q, x) in F}
     = {x ... | q(bin(x)mod3) in F}
     = {x ... | q0}
     = {x ... | bin(x) mod 3 = 0}
```

```
Real Life Example:

Vending Machine!
```

## Closure Properties of a DFA

A language (set of strings) is regular if it is accepted by some DFA.

```
Ex:

{w{0, 1}* | w encodes multiples of 3}
{w{0, 1}* | w contains 111 as substring}
```


Nonregular:

{w e {0, 1}* | w has more 0s then 1s}

### Closure

If R is a regular language (over E), then E*/R is regular too

What is closure?

(x, y) is Integar, x + y is also integar (symbolized by the Z with two middle lines)

if X and Y is an Integar, x / y isn't necessarily an integar

"Integers are not closed under division"

E*/R -> set difference: all strings in E* but not in R

Ex:

{w E {0, 1}* | w is not a Multiple of 3}

Idea: take DFA to M(3) flip accept / reject states and you'll get the compliment

proof: R is a regular language, then there exists a DFA where L(M) = R, then L\`(M) = {w E E* | S* (s, w) E F\`} where F` is Q - F

= { w .. | S*(s, w) E Q-F}
= { w | M doesn't accept w}
= { E* | L(M)}
= { E* | R}

So, E*|R is regular

----
Claim: Regular languages are closed under intersection

If R1, R2 are regular languages (over E)
then R1 intersect R2 is also regular

Ex: Let R1 represent multiples of 3, and R2 be substrings with 111 in them
R1 = {w e {0, 1}* | w is M(3)}
R2 = {w e {0, 1}* | w contains 111}

R1 intersect R2

State machines for each:

![](https://i.imgur.com/WSCSgTx.pngv)

Idea: Run both DFAs in parallel, keeping track of current state in M1 and M2

Can keep track of states in a set of state pairs, like a tuple of (State1, State2)

![](https://i.imgur.com/vDGvLPu_d.jpg?maxwidth=1024)

Proof of claim

R1, R2 are regular, so let
```
L(M1)=R1 M1={Q1 E, S1, s1, F1}
L(M2)=R2 M2={Q2 E, S2, s2, F2}

Q` = Q1 x Q2
S` = (S1, S2)
F1 = F1 x F2
S` ((p, q), c) = S`(S1(p, c), S2(q, c))

So we claim
---

S`*((p, q), c) = (S1*(p, w), S2*(p, w)) - Can be proved with induction
```

Assuming the claim is true, we can represent our language
```
L(M`) = {w | S*(s1, w) E F`}
      = {w | S*(s1, w) E F1xF2}
      = {w | S*((s1, s2), w) E F1xF2}
      = {w | S1*(ps1, w) E F1 and S2*(S2, w) E F2}
      = {w | w E L(M1) and w E L(M2) }
      = Lp(M1) intersect L(M2) ==> L(M1) intersect L(M2) is regular
```
