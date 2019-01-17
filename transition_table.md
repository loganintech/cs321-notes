Transition Table Example

![](https://i.imgur.com/6sg3F8R.png)

First state is starting state, can have multiple final states

| state | a | b |
|-----|---|---|
| S{1} | {1, 2} | {1} |
| {2} | {3} | {3} |
| F{3} | NULL | NULL |
| {1, 2} | {1, 2, 3} | {1, 3} |
| F{1, 3} | {1, 2} | |
| F{2, 3} | | |
| F{1, 2, 3} | | |
| NULL | NULL | NULL |

---

| state | a | b |
|-----|---|---|
| S{1} | {1, 2} | {1} |
| {1, 2} | {1, 2, 3} | {1, 3} |
| F{1, 3} | {1, 2} | {1} |
| F{1, 2, 3} | {1, 2, 3} | {1, 3}


