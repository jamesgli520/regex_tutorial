# regex_tutorial
This is a tutorial that explains how a specific regular expression, or regex work and what they are, and by breaking down each part of the expression and describing what it does
.
## Summary

Regular expression, or regex lets you perform pattern matching on strings of characters. Following is the regex components.
```
/^[a-z0-9_-]{3,16}$/
```
The pattern must be wrapped in slash characters (/). If we examine the “Matching a Username” regex.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
The characters ^ and $ are both considered to be anchors.

The ^ anchor signifies a string that begins with the characters that follow it. This could be in one of two formats:

* Regex is case-sensitive such as ^A, where the strings "A" match, but "a" do not.

* A range of possible matches, displayed using bracket expressions.

The $ anchor signifies a string that ends with the characters that precede it.

In “Matching a Username” regex, the string must start and end with something that matches the pattern [a-z0-9_-]

### Quantifiers
Set the limits of the string that your regex matches. In the “Matching a Username” regex example:
* Looking for any string between 3 and 16 characters that starts and ends with a combination of lowercase characters, the numbers 0–9, and the special characters of an underscore and a hyphen.

On the other hand, there are more Quanitifers:
* *—Matches the pattern zero or more times

* +—Matches the pattern one or more times

* ?—Matches the pattern zero or one time

* { }—Curly brackets can provide three different ways to set limits for a match:

    * Asterisk * : Matches the preceding item "x" 0 or more times. 
        *   For example, /username*/ matches "usernameeeeeee" 
    * Plus sign +: Matches the preceding item "x" 1 or more times. Equivalent to {1,}. 
        *   For example, /a+/ matches the "a" in "candy" and all the "a" in "caaaaaaandy". 
    * ? Matches the preceding item "x" 0 or 1 times. 
        *   For example, /e?le?/ matches the "el" in "angel" and the "le" in "angle."
### Grouping Constructs.
Grouping constructs have two primary categories: capturing and non-capturing. Following are the example:

**Capturing Group**: use the alternation | meta character

* The regular expression (c|g|p)ar means: a lowercase c, g or p, followed by a, followed by r.
```
"(c|g|p)ar" => The car is parked in the garage.

ar is in the group 0, and c, g, p are in group 1
```


**Non-Capturing Group**:
* A non-capturing group is denoted by a ? followed by a : within parentheses (...). For example, the regular expression (?:c|g|p)ar is similar to (c|g|p)ar in that it matches the same characters but will not create a capture group.
```
"(?:c|g|p)ar" => The car is parked in the garage.

c, g, p and ar are in same group
```

### Bracket Expressions
A set of square brackets ([ ]) represents a range of characters that we want to match. We outline the characters we want to inlcude inside the bracket expression also known as a positive character group. 
* For example, if we include abc123 in the breacker [abc], then we will look for a string that includes a or b or c, regardless of the length of the string. 
* Example of the strings that include abc123: aaa, apple, cat,  banana etc 

A hyphen (-) used between alphanumeric characters (letters and numbers only) to represent a range of those possible characters. This means that [a-c] and [abc] will look for the exact same thing.

In the “Matching a Username” regex example, we can break down the bracket expressions as follows:

* [a-z] The string can contain any lowercase letter between a–z.

* [a-zA-Z] The string can contain any lowercase and uppercase letter between a–z and A-Z

* [0-9]—The string can contain any number between 0–9

* [ _-]—The string can contain an underscore or hyphen. Both the underscore and the hyphen are called special characters. So, the string will only include special character underscore or hyphen
* Example of qualified username accoding to our parttern: 
```
a_regex-username01
```
* Example of not qualified username accoding to our parttern: 
```
a_Regex-username01
``` 
because it includes an uppercase character, R.
### Character Classes
Here are some of the other common character classes:

* . Matches any character except the newline character (\n)

* \d Matches any Arabic numeral digit. This class is equivalent to the bracket expression [0-9].

* \w Matches any alphanumeric character from the basic Latin alphabet, including the underscore (_). This class is equivalent to the bracket expression [A-Za-z0-9_].

* \s Matches a single whitespace character, including tabs and line breaks

### Flags
There are the three that we're most likely to encounter:

* g—Global search: the regex should be tested against all possible matches in a string (rather than stopping after the first match).
    *   This will stop after first match, it stops on fat
    ```
    "/.(at)/" => The fat cat sat on the mat.
    ```
    * This will continue seaching until the last one, it stop on mat
    ```
    "/.(at)/g" => The fat cat sat on the mat.
    ```
* i—Case-insensitive search: case should be ignored while attempting a match in a string
    * /The/i
    ```
    "The" => The fat cat sat on the mat.
    ```
    It will stop on "The"
* m—Multi-line search: a multi-line input string should be treated as multiple lines
```
"/.at(.)?$/gm" => The fat
                  cat sat
                  on the mat.
With g and m flag, it matches the fat, sat and mat
```

### Character Escapes
A backslash \ is used in regular expressions to escape the next character.
```
"(f|c|m)at\.?" => The fat cat sat on the mat.
This will match fat, cat and mat.
```
## Author
James G Li

A Georgia Tech Full Stack Bootcamp student 

Link to my profile: https://github.com/jamesgli520