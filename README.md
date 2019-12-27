# WordLang
 A weird programming language based on words.

## Background

WordLang is an [esoteric programming language](https://en.wikipedia.org/wiki/Esoteric_programming_language), which means it's ... totally useless, kind of. BUT! It's a challenge for geeky or bored developers.

The idea originated from BrainFuck, with the twist that each character increases the data's value by its corresponding [ASCII](https://en.wikipedia.org/wiki/ASCII) value instead of the "+", "-" characters in BrainFuck for instance.

You can find similar languages on [https://esolangs.org/](https://esolangs.org/wiki/Language_list)!

## The Challenge

To create an understandable sentence that compiles to a valid output.

Would it even be possible to create a Polyquine compatible with WordLang? How to [Write a Polyquine](https://codegolf.stackexchange.com/questions/37464/write-a-polyquine).

* [The Ideas of Quine (1977)](https://www.youtube.com/watch?v=B2fLyvsHHaQ)
* [Five Quines by Andy Balaam](https://www.youtube.com/watch?v=JQ_Fylah0Cg)

## Grammar

| Character     | Meaning                                                      |
| ------------- | ------------------------------------------------------------ |
| Any character | Increment or decrement the data value by it's corresponding [ASCII](https://en.wikipedia.org/wiki/ASCII) value. |
| ,             | Toggle from increment to decrement mode, or wise versa.      |
| .             | Print the corresponding data value's ASCII character to screen. And reset the value to 0. |
| '[variable]'  | Add the value of *variable* to the data value.               |
| \>[variable]  | Set the value of *variable* to the current data value.       |
| <             | Read a one character input and add it to the data value.     |
| - [name]      | Create a named point that is possible to jump back to.       |
| [name]!       | Jump back to a named point.                                  |
| "[comment]"   | Comment.                                                     |
| [space/tab/newline]   | Ignored.                                                     |
| \\[escaped]   | Any special character is escaped using `\`.                  |

When assigning variables, use a blank space to mark the end of a variable name. Ex: `>Var is a`... Now the current data value will be stored in `Var`.

## Other

| Subject         | Description |
| --------------- | ----------- |
| File extensions | .w, .wl     |

## Example

### 1. Hello world

```
Helloo, world. :3
```

1. H = 72 → Increment the data value to 72
2. e = 101 → Increment the data value to 173
3. ...
4. , → Switch to decrement mode.
5. Space is ignored
6. W = 87 → Decrease the data value with 87
7. ...
8. . → Print the character of the data value to screen

Result is: `;`

### 2. Input

```
I.=.<>I
I.=.'I'.
```

This example defeats the purpose of WordLang, the point is that every sentence should be readable. But is for the sake of understanding.

1. Print the text "I="
2. Read the input value
3. Store it in the variable I
4. Print the text "I="
5. Print the value of I
