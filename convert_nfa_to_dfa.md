## Converting NFAs to DFAs

![](https://i.imgur.com/st9MSzb.png)

| state | a | b |
|-----|---|---|
| S{1} | {1, 2} | {1} |
| {1, 2} | {1, 2} | {1, 3} |
| {1, 3} | {1, 2} | {1, 4} |
| {1, 4} | {1, 2, 5} | {1} |
| {1, 2, 5} | {1, 2, 5} | {1, 3, 5} |
| {1, 3, 5} | {1, 2, 5} | {1, 4, 5} |
| {1, 4, 5} | {1, 2, 5} | {1, 5} |
| {1, 5} | {1, 2, 5} | {1, 5}

```
Claim:

For any NFA, there is a corrisponding DFA that accepts the same language.

Proof:

Given M = (Q1, E1, sigma1, s1, F1)
Q1 = P(Q)
S1 = {s}
F1 = {A in Q1 | A intersect F != NULL}
S1(A, c) = {q | backE p in A, q in S(p, c)}

if A {1, 2} then (p = 1 S(1, c) == 3 and p = 2 S(2, c) == 4)
= {3, 4}
S(1, c) = {3, 4} and 5 is {3, 4, 5}

```

## Closure Properties

NFA(M) then L(M) is also regular

Is there an NFA for the complement of this language?

M: ![](https://i.imgur.com/CK52uX6.png)

Convert M to DFA

| state | a | b |
|-----|---|---|
| SF{1} | {1, 2} | |
| F{1, 2} | {1, 2, 3} | {1} |
| NULL | NULL | NULL |
| F{1, 2, 3} | {1, 2, 3} | {1, 2, 3} |

Compliment:

| state | a | b |
|-----|---|---|
| S{1} | {1, 2} | |
| {1, 2} | {1, 2, 3} | {1} |
| F-NULL | NULL | NULL |
| {1, 2, 3} | {1, 2, 3} | {1, 2, 3} |
