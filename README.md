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
| `???` | Rotate stack right (Top of stack moved to bottom) | `1 2 3` | `3 1 2` |
| `???` | Rotate stack left (Bottom of stack moved to top) | `1 2 3` | `3 1 2` |
| `^` | Reverse stack | `1 2 3` | `3 2 1` |
| `???` | Sum of stack | `1 2 3` | `6` |
| `??` | Push Second item from top of stack | `1 2 3` | `1 2 3 2` |
| `!` | Push Length/Number of items on stack | `1 2 3` | `1 2 3 3` |
| `+` | Add/Concatenate top two values on stack | `1 2 3` | `1 5` |
| `-` | Subtract top two values on stack | `1 2 3` | `1 -1` |
| `*` | Multiply top two values on stack | `1 2 3` | `1 6` |
| `/` | Divide top two values on stack | `1 2 3` | `1 0.6666666666666666` |
| `%` | Modulo top two values on stack | `1 2 3` | `1 2` |

Don't forget these commands! But you may wonder how to remember those fancy unicode chars. Don't worry, you aren't alone. The official [online Vyxal interpreter](https://lyxal.pythonanywhere.com/) will fix your problem. Open it, you'll see a Keyboard section. Expand it, a long list of commands will appear. In search box, just enter few words from the description of the command, it will return matches. And you just hover on the matches to get extended info. So simple, right!

But you may also wondering, how to conveniently access a value located in bad position on stack. You might want some alternative storage system. To solve that problem we present you: variables and registers

**1.1 Variables**

`???` command is used to set a variable. It is followed by alphabetic character(s), which is set to a variable having value of the top of stack (top of stack is popped then set). Assuming stack is `1 2 3`, `???a` will pop `3` and set the value of varaible `a` to 3.

To get a variable `???` is used. It gets the value of variable (without emptying it) and pushes the value of the variable to stack.

**1.2 Register**

Variables are often expensive, they cost a lot of bytes. You may need to store only one value, so to solve even that problem we have register.

Register is just like variable, it can hold any value of any data type. To pop and store a value in register, just use `??` command. To push the value of register to stack without emptying the register use `??`.

**2. Data types**

Vyxal aims simplicity, so we have as less as data types as possible. 

- Number
- String
- List
- Generator
- Function

**2.1 Number**

Numbers can be any integer, negative or floating point number.

We have already seen how to push and operate a postive integer. Now lets see how to push a negative integer. Suppose we want to push -12.

If you write `-12` then Vyxal will try to `-` as a builtin and subtract top two items on stack and then push 12. But that's not what we want. We want to push -12 exactly. So we have to push 12 first then write `N`. `N` is actually a builtin which inverts the sign of a number. I mean:

- If gets a positive number, changes its sign to negative.
- If gets a negative number, changes its sign to positive.
- If got 0 then return 0.

So by using `N` we have pushed a negative number.

To push a floating point number, use `.` as a decimal seperator. Writing `1.56` will push what are you expecting.

Vyxal partially supports complex numbers. We know imaginary unit is equal to ???-1. There is a builtin `u` which pushes `-1` to the stack. And `???` builtin pops a value from top of stack and pushes its square root. So `u???` should push the `1j`. Remember operations on complex numbers don't work as expected now but it is coming soon.

**2.2 String**

Instead of using `"` or `'`, `\`` is used instead for string.
