# WordLang
 A weird esoteric programming language based on words or meaning-like grammar that produces output.
 
 ![GitHub](https://img.shields.io/github/license/WilliamRagstad/WordLang)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/WilliamRagstad/WordLang) 
![GitHub All Releases](https://img.shields.io/github/downloads/WilliamRagstad/WordLang/total)

>[Download Interpreter](https://github.com/WilliamRagstad/WordLang/releases/latest) (latest).

Here's a good [ASCII table](https://www.asciitabell.se/).

## [Read the Wiki](https://esolangs.org/wiki/WordLang)

## Background

WordLang is an [esoteric programming language](https://en.wikipedia.org/wiki/Esoteric_programming_language), which means it's ... totally useless, kind of.
BUT! It's a challenge for highly intelligent geeky/bored [hackers](https://en.wikipedia.org/wiki/Hacker_culture), if don't feel like one, WordLang will most likely make you one.

The idea originated from [Brainfuck](https://sv.wikipedia.org/wiki/Brainfuck), with the twist that each character increases the data's value by its corresponding [ASCII](https://en.wikipedia.org/wiki/ASCII) value instead of the "+", "-" characters in Brainfuck for instance.

You can find similar languages on [https://esolangs.org/](https://esolangs.org/wiki/Language_list)!

## The Challenge

To create an understandable sentence that compiles to a valid output.

Would it even be possible to create a [Quine](https://esolangs.org/wiki/Quine) or Polyquine compatible with WordLang? How to [Write a Polyquine](https://codegolf.stackexchange.com/questions/37464/write-a-polyquine).

* [The Ideas of Quine (1977)](https://www.youtube.com/watch?v=B2fLyvsHHaQ)
* [Five Quines by Andy Balaam](https://www.youtube.com/watch?v=JQ_Fylah0Cg)

## Grammar

| Character     | Meaning                                                      |
| :-----------: | :----------------------------------------------------------- |
| Any character | Increment or decrement the data value by the character's corresponding [ASCII](https://en.wikipedia.org/wiki/ASCII) value. |
| **,**         | Toggle from increment to decrement mode, or vice versa. |
| **.**         | Print the corresponding data value's ASCII character to screen and **reset the data value** to 0. |
| **'**[variable]**'** | **Add** or **subtract** the data value depending on the value of *variable* and the current **mode**. |
| **>**[variable] | **Increase** the value of *variable* to the current data value and reset the data value to 0.<br />If the variable is undefined, it becomes a copy of the data value. |
| **<**         | Read a one character input and **add** it to the data value. |
| **-**[name]  | Create a named point that is possible to jump to.       |
| [name]**!**   | Jump to named point.                   |
|     [name]**!!**      | Jump to the named point **if data value is less than 0**.              |
|     [name]**!!!**     | Jump to the named point **if data value is larger than 0**.          |
| **(**[code]**)** | Convert and **print** the result of the parentheses to a number instead of a character and **reset the data value** to 0. |
| **"**[comment]**"** | Comment.                                                     |
| *[space/tab/newline]* | Ignored.                                                     |
| **\\**[escaped] | Any special character is escaped using `\`.                  |
| **?**         | Print information about the current data value at a given location and pause execution if the interpreter is running in debug mode. |

### Variables
When assigning variables, use a blank space to mark the end of a variable name. Ex: `>Var is a`... Now the current data value will be stored in `Var`.

Variables are stored as doubles, just as the data value. Read more about the double type below... 

### Data Value
The data value is of type [double](https://docs.microsoft.com/en-us/dotnet/api/system.double) (±5.0×10<sup>−324</sup> to ±1.7×10<sup>308</sup>,	8 bytes). Read more about [floating-point numeric types](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/floating-point-numeric-types).

Every time the ASCII character of the data value is printed *(using `.`)*, the value is first modulated by 255 (The byte size of an ASCII character) which means that `abc` becomes `'` (97 + 98 + 99 = 294 → **294** mod(255) = 39 = `'` ) even though **the data value is still 294**.

## Other

| Subject         | Description |
| --------------- | ----------- |
| File extensions | .w, .wl     |

## Example

### 1. Helloo, world.

This does not print hello world, just the result of the phrase if it's interpreted using WordLang.

```
Helloo, world.
```

Output: `;`

1. H = 72 → Increment the data value to 72
2. e = 101 → Increment the data value to 173
3. ...
4. , → Switch to decrement mode.
5. Space is ignored
6. W = 87 → Decrease the data value with 87
7. ...
8. . → Print the character of the data value to screen

### 2. [Cat program](https://esolangs.org/wiki/Cat_program) (Single-Input)

```
I.=.<>I		"Read and store input in I"
:,0.,		"Newline"
I.=.'I'.	"Read and write value of I"
```

Output:
```
I=[CHAR]
I=[CHAR]
```
Where `[CHAR]` is an arbitrary character of choice.

> **Disclaimer**
> This example defeats the purpose of WordLang in a way, the point is that every *sentence* should be readable text. But now it's just for the sake of understanding.

1. Print the text "I="
2. Read the input value
3. Store it in the variable I
4. Write a newline character
5. Print the text "I="
6. Print the value of I

### 3. Listing characters

```
1,0, > 1	"Store 1 into 1"
d > C		"C(ounter) is declared to 100 (d)"

'C'.		"Load and print C"
'C'		"Load C"

-loop		"declare loop"
,		"Set to decrease mode"
'1'		"Load and subtract 1"
,		"Set to increse mode"
> C		"Store to C"
'C'		"Load C"
.		"Print"
'C'		"Load C"
loop!!!		"Repeat while data isn't 0"
```

Output:

```
dcba`_^]\[ZYXWVUTSRQPONMLKJIHGFEDCBA@?>=<;:9876543210/.-,+*)('&%$#"! ▼▲↔∟←→↓↑↨▬§¶‼↕◄►☼♫
       ♠♣♦♥☻☺
```

> **Disclaimer**
> This example is just as the previous example... It defeats the purpose of WordLang, but now it's just for the sake of understanding.

### 4. CTF Flag

```
Hello there, mister, A,T. Would you like to dance with all of us, it would be, varry appreciated. A mean great deal young man g,l so would say.
But no one ever answered him on that, so that made him feel sorrow, but in the end, what does m,%.
Therefore the man leaved without D, z,.

This is a large flat > buffer - John
Agreed the space ('buffer'), is not small.
But, 'buffer' > buffer was cleared again and again, just until the 'buffer' was, empty?,.
Nothing was never the same again pas the normal, the difference was so small and unsignificant 'buffer'
"Run" John!!! Shouted Sherlock (Holmes)

But in the end 8, everything was fine.
```
Output:

```
flag{3100µ¢4173µÎ3575µú2977µ'2379µS1781µ⌂2052}
```

## Poems

> ### Let's live
> With death being the only certainty of life, life is just a bit too short for regrets.
> Let's live, while we're alive.
> Let's love, while we're alive.
> Let's live, and not just survive.
> 
> Output:
> `LÄ;Ù`

> ### Camouflaged
> In all chaotic beauty lies a wounded work of art.
> Beautiful but torn, wreaking havoc on my heart.
> Camouflaged by insecurities, blinded by it all.
> I love the way you sit there and barely notice me at all.
> 
> Output:
> `Hlt|`

> ### Someday
> Someday you will cry for me
> Like I cried for you.
> Someday you'll miss me
> Like I missed you.
> 
> Output:
> `Ö3`
