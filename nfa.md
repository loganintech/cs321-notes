# Nondeterministic Finite Automata

```
D from DFA means Deterministic

Deterministic Property:
For language {0, 1}, every state has exactly 1 outgoing path for each character
```

What happens remove the restriction of __exactly one__ next step.

Def: An NFA (Nondeterministic Finite Automata) is like a DFA but no restriction on output paths.

Ex:

![](https://i.imgur.com/nGQd6aC.png)

Runs:
```
1 --a-> 1 --b-> 1 --b-> 1
1 --a-> 2 --b-> 3 --b-> 4
```
Guess: So char 2nd to last is 'a'?

every time there is a choice, NFA "just guesses", NFA accepts if there is some set of guesses that leads to accept state

eg:

{a, ab, aab, abba}* designing the dfa: all strings we get by concatenating (any # of copies) of these 4 strings

![](https://i.imgur.com/eUselio.png)

Ex:

{ w (\0) | w is not multiple of 3 }

E - {0, 1, \0}

= { x | backwardsE w == x = w \0, and w is a M(3) }

![](https://i.imgur.com/j9mZfrc.png)

_Note: There's no one correct way to represent a DFA_

E = {0, 1}

A DFA:

![](https://i.imgur.com/tdzrsEs.png)

Without the dead state, this would be an NFA

An equivalent yet larger DFA:

![](https://i.imgur.com/PQKWx6t.png)

## automata --> automaton is singular
