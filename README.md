# vyxal-tutorial

Welcome to the amazing world of Vyxal and stack based languages! Are you a programmer who is sickened by general purpose languages who wants to get a taste of recreational programming? Vyxal is definitely the best choice for you to begin with.

**So, What is Vyxal?**

Vyxal is a concise golfing language which focuses upon readability and also has some aspects of traditional languages.

Its main memory model is Stack. Programs revolve around pushing, doing things, and popping from stack. It has variables too.

It uses its own [256-byte codepage](https://github.com/Vyxal/Vyxal/blob/master/docs/codepage.txt). When scoring the program, each character in the program which is in the codepage is counted as a single byte.

Then let's get started!

**1. Intro to the basic concepts**

As I said before our main memory model is stack. Pushing a value to stack means to add a value to stack, or append a value to stack. And popping means to take out a value from its top. Giving an example, suppose `1 2 3` is our stack, when we push two values `4` and `5` it becomes `1 2 3 4 5` and if we pop a value it becomes `1 2 3 4` (`5` gets popped). For `1 2 3`, 3 is on **top of stack** and 1 is on **bottom of stack**.

To push an integer to stack, simply write it
```
69
```
The number 69 will get pushed.

But How to push more than 1? Simple, just make sure they are seperated by any non-digit character.
```
69 420
```
Will push both 69 and 420. Most of the non-digits characters are commands in Vyxal, they do something based on the values on top of stack (or enitre stack). Space and Newline is regarded as NO-OP or NOP, because they don't do anything except of seperating values.

By now you have also noticed that the digit you pushed last (top of stack) is automatically getting outputted. You are wondering you have never given any command to print anything, then how come you are getting the output? Because Vyxal has implicit output. Top of stack gets automatically printed at the end of program. If you don't like it you can use the `O` flag to turn it off and manually print with `,` command (More on flags later).

It has implicit input too. You have seen a box named Input in the online interpreter. Write down some values in it, they get automatically pushed to stack before the program starts, and they just behave like input.

Now lets quickly get used to few important commands which modify stack:

| Command | Description | Stack before | Stack after |
| --- | --- | --- | --- |
| `_` | Pop/discard/remove top of stack | `1 2 3` | `1 2` |
| `:` | Duplicate top of stack | `1 2 3` | `1 2 3 3` |
| `$` | Swap top two values on stack | `1 2 3` | `1 3 2` |
| `D` | Triplicate (three copies) of top of stack | `1 2 3` | `1 2 3 3 3` |
| `‟` | Rotate stack right (Top of stack moved to bottom) | `1 2 3` | `3 1 2` |
| `„` | Rotate stack left (Bottom of stack moved to top) | `1 2 3` | `3 1 2` |
| `^` | Reverse stack | `1 2 3` | `3 2 1` |
| `Ṡ` | Sum of stack | `1 2 3` | `6` |
| `Ȯ` | Push Second item from top of stack | `1 2 3` | `1 2 3 2` |
| `!` | Push Length/Number of items on stack | `1 2 3` | `1 2 3 3` |
| `+` | Add/Concatenate top two values on stack | `1 2 3` | `1 5` |
| `-` | Subtract top two values on stack | `1 2 3` | `1 -1` |
| `*` | Multiply top two values on stack | `1 2 3` | `1 6` |
| `/` | Divide top two values on stack | `1 2 3` | `1 0.6666666666666666` |
| `%` | Modulo top two values on stack | `1 2 3` | `1 2` |

