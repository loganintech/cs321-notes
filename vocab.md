# Technical Vocabulary

| Symbols | Meaning |
|---------|---------|
|E|Epsilon|
|D|Delta|

| Term | Definition | Example | Writing |
|------|------------|---------|---------|
| Alphabet | Finite set of charaters (symbols) | `{0, 1} (binary set)` OR `{a, ..., z} (alpha set)` | {element, element, ...} |
| String | Ordered sequence of chars | `01110 -> String over alphabet {0, 1}` OR `abbac -> String over alphabet {a, ..., z}` | string contents, like `abcd` or `100101010` |
| Empty String | Unique string of length 0 | `''` | E |
| Length | Length of a string | `\|0110\| -> 4` OR `\|abcde\| -> 5` | \|foostring\| |
| Concatination | Appending a string to the end of another | foo.bar == foobar | the `.` is the concat operator -> `foo.bar`, `011.100`
| String Powers | Math operation foostring^foonum | `'01'^3 == '010101'` OR `'abc'^2 == 'abcabc'` | Power of (^) or superscript |
| Language | Any set of strings | `{0, 1}^foo` OR `{w 'E' {0, 1}^x | w is prime}` | Like an alphabet
| State Machine | A machine with a finite set of states based on its input and its previous state. Start on state 1, read input left to right (one at a time). For each input, follow arrow associated with input. After reading the entire input, get a yes or no answer. | ![](https://m.media-amazon.com/images/G/01/DeveloperBlogs/AppstoreBlogs/default/102117_StateMachine._CB513660882_.png?t=true) | Circles with numbers on the positions connected by arrows denoting each possible input in that state.
| DFA (Deterministic Finite Automaton) | Is a tuple, `M`, where M = (Q, E, D, S, F) where ```Q is a finite set, E is an alphabet of input chars, D is a _transition function_ of type S: Q x E -> Q. S(q, c) means 'What state do I go to if I read a 'c' in state 'q', S is a start state and 'S epsilon Q' (S is contained by Q), F is a set of _accept states_ where the state machine returns 'Yes'``` | As a tuple
| Let M is a DFA, L(M) | The language accepted by M | L(M) = {x e {a, b}^y \| W contains _aa_ as substring} | {x e E^x \| M `result yes` for input x} |
