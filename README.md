# Regex-Tutorial

## Regular Expression - Matching an Email
Regular expressions are extremely useful in extracting information from text such as code, log files, spreadsheets, or even documents. <br>

While there is a lot of theory behind formal languages, the following lessons and examples will explore the more practical uses of regular expressions so that you can use them as quickly as possible. <br>

The first thing to recognize when using regular expressions is that everything is essentially a character, and we are writing patterns to match a specific sequence of characters (also known as a string). <br>

Most patterns use normal ASCII, which includes letters, digits, punctuation and other symbols on your keyboard like %#$@!, but unicode characters can also be used to match any type of international text. <br>

## Summary
A **regex**, which is short for **regular expression**, is a sequence of characters that defines a specific search pattern. <br>

When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. <br>

They are also frequently used to validate input. 

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` <br>
This is the expression in question. <br>
This line of regex look like a line of code in the matrix movie.<br>
However, we will break down this this string, and we will understand the meanning of this string. <br>

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
The characters `^` and `$` are both considered to be anchors. <br> 

The `^` anchor signifies a string that begins with the characters that follow it. <br>

The `$` anchor signifies a string that ends with the characters that precede it. <br>

In this case: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` <br>

The `^` means the string begin and follow `([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})` <br>

The `$` means the string end after `)`. <br>

--> The entire string is put in the middle of `^` and `$`.

### Quantifiers
Quantifiers set the limits of the string that your regex matches (or an individual section of the string). <br>

They frequently include the minimum and maximum number of characters that your regex is looking for. <br>

Quantifiers are inherently greedy, meaning they match as many occurrences of particular patterns as possible. They include the following: <br>
`*` Matches the pattern zero or more times

`+` Matches the pattern one or more times

`?` Matches the pattern zero or one time

`{}` Curly brackets can provide three different ways to set limits for a match:

- `{ n }` Matches the pattern exactly n number of times

- `{ n, }` Matches the pattern at least n number of times

- `{ n, x }` Matches the pattern from a minimum of n number of times to a maximum of x number of times

In this case: <br>

`([a-z0-9_\.-]+)`: Because our bracket expression will match one or more any string that includes any combination of lowercase letters between a and z, any number between 0 and 9, and the special characters of an underscore or a hyphen. <br>

`([a-z\.]{2,6})`: Because our bracket expression will match one or more any string that includes any combination of lowercase letters between a and z, any number between 0 and 9, and the special characters of an underscore or a hyphen and this quantifier means that this string has to be between 2 and 6 characters. <br>

### Grouping Constructs
Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. You can use grouping constructs to do the following: <br>

- Match a subexpression that is repeated in the input string.

- Apply a quantifier to a subexpression that has multiple regular expression language elements. For more information about quantifiers, see Quantifiers.

- Include a subexpression in the string that is returned by the Regex.Replace and Match.Result methods.

- Retrieve individual subexpressions from the Match.Groups property and process them separately from the matched text as a whole.

The following grouping construct captures a matched subexpression:<br>

`( subexpression )` <br>

Where subexpression is any valid regular expression pattern. <br>

Captures that use parentheses are numbered automatically from left to right based on the order of the opening parentheses in the regular expression, starting from one. <br>

The capture that is numbered zero is the text matched by the entire regular expression pattern. <br>

In this case: <br>

`([\da-z\.-]+)`: Creates a non-capturing group. <br>

### Bracket Expressions
A bracket expression (an expression enclosed in square brackets, "[]" ) is an RE that shall match a specific set of single characters, and may match a specific set of multi-character collating elements, based on the non-empty set of list expressions contained in the bracket expression. <br>

For example: <br>

- `[abc]`: will look for a, or b, or c.

- `[a-z]`: will look for any lowercase characters between a and z.

In this case: <br>

`[a-z0-9_\.-]+`

### Character Classes
A character class in a regex defines a set of characters, any one of which can occur in an input string to fulfill a match. 
We've actually already discussed some character classes. 
The bracket expressions outlined previously, including positive and negative character groups, are considered character classes. <br>

Here are some of the other common character classes: <br>
- `.` Matches any character except the newline character `(\n)`

- `\d` Matches any Arabic numeral digit. This class is equivalent to the bracket expression [0-9].

- `\w` Matches any alphanumeric character from the basic Latin alphabet, including the underscore `(_)`. This class is equivalent to the bracket expression `[A-Za-z0-9_]`.

- `\s` Matches a single whitespace character, including tabs and line breaks

In this case: <br>

`_\.-`: will looking to match any character except new line. 

### The OR Operator
Remember that a bracket expression does not require the string to meet all of the requirements in the pattern. <br>

Using the OR operator `(|)`, the expression `[abc]` could be written as `(a|b|c)`. <br>

However we don't have an OR operator in our string so I will take example from other. <br>

For example: <br>

`<\/\1>|\s+\/>`: which looks for 1 backslash OR whitespace between at the closing arrow `>`

### Flags
Flags are placed at the end of a regex, after the second slash, and they define additional functionality or limits for the regex. <br> 

There are six optional flags that can be used, either separately or together and in any order, but these are the three you're most likely to encounter:
- `g` Global search: the regex should be tested against all possible matches in a string.

- `i` Case-insensitive search: case should be ignored while attempting a match in a string

- `m` Multi-line search: a multi-line input string should be treated as multiple lines

However we don't have flags in our string. 

### Character Escapes
The backslash `(\)` in a regex escapes a character that otherwise would be interpreted literally. <br>

For example: <br>

The open curly brace `({)` is used to begin a quantifier, but adding a backslash before the open curly brace `(\{)` means that the regex should look for the open curly brace character instead of beginning to define a quantifier. <br>

This is common when looking for strings with special characters that are the same as a particular component of a regex.<br>

In this case: <br>
`[a-z0-9_\` 

## Author
My name is Truong Duong, and you can get in touch with me through:
* Email: truong.duong1908@gmail.com
* LinkedIn: https://www.linkedin.com/in/truongduong/
* Personal website: https://txd.com/
* Github: https://github.com/Truong-Duong/