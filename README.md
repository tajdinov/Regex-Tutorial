# Regex-Tutorial
Computer Science for JavaScript Challenge Regex Tutorial

It is a tutorial that explains how a specific regular expression, or regex, functions by breaking down each part of the expression and describing what it does.

## Summary
The following snippets of code will be used throughout this tutorial to give specific examples on how the different components of regex can be used. A common use for this code is for validation, to make sure that an email follows the correct format.

Matching a Hex Value:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

Matching an Email: 
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Matching a URL: 
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Matching an HTML Tag: 
`/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`



## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

`/`^`#?([a-f0-9]{6}|[a-f0-9]{3})`$`/`

The anchor is a term which defines the start and end of the expression. They can be used to “anchor” the regex match at a certain position. The caret `^` matches the position before the first character in the string. Applying `^a` to `abc` matches `a`. `^b` does not match `abc` at all, because the `b` cannot be matched right after the start of the string, matched by `^`. See below for the inside view of the regex engine.
Similarly, `$` matches right after the last character in the string. `c$` matches `c` in `abc`, while `a$` does not match at all.

### Quantifiers

`/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/`

Quantifiers are used to communicate how many characters are expected. Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. By default, quantifiers are greedy, and will match as many characters as possible. If the "`,+,?,{}`" characters are found within regular expressions, they are considered quantifiers. The `?` indicates the expression to match `0` or `1`time. As mentioned in the summary above because there are 2 types of formats we'll use the or operator to distinguish which format we are using. In our Hex Value regular expression we have `{6}` (Hex Triplet Format) and `{3}` (Shorthand Hex Format), this indicates that the length of the component preceding these quantifiers should be `6` for `{6}` and `3` for `{3}`.

### OR Operator

The 'OR' Operator is not present in our example code for matching against an email, so for now, in order to talk about the OR Operator, we will take a look at the following code for matching against a hex code:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

What we see here, is an expression for matching a hex code that uses the OR Operator. What this operator does is look for a matching string where it starts with a # first followed by one of the following:

`[a-f0-9]{6}` this will match a 6 character long string which contains a combination of a-f letters and 0-9 numbers.

| this is the OR Operator

`[a-f0-9]{3}` this will match a 3 character long string that contains a combination of a-f letters and 0-9 numbers.

Notice both of the above examples are referencing the same character class `[a-f0-9]`. This is because the OR Operator is looking for a match that starts with a # and then either a 6 character long string or a 3 character long string. It does not matter which one it is, as long as it starts with a # and then either a 6 character long string or a 3 character long string.

### Character Classes

`/^#?(`[a-f0-9]`{6}|`[a-f0-9]{3}`)$/`

Character classes are components within our regular expression that tells us what type of characters to expect. In our example our character classes are confined within brackets `[]`. For our example we have 2 character classes: `[a-f0-9]` and `[a-f0-9]` which searches for the same values. We will be breaking down what the characters are searching within these character classes. `a-f` searches for letters `a-f` and `0-9` searches for digits `0-9`.

### Flags

A flag is not used in the matching email code in this tutorial. A regular expression typically looks like this:

`/pattern/flags`

Where the slashes denote where the regular expresssion starts and ends. A flag can be used after the slash to provide more guidelines for matching. The flags are:

- `g` which stands for "global" which will allow for matching all the instances within a string that follow the matching guidelines set in the regular expression.
- `m` which stands for "multiline" which will search line by line rather than searching through a string as a whole.
- `i` which stands for "insensitive" will make the regular expression case-insensitive, so capitals and lower-case letters will not deture the matching.

### Bracket Expressions

`/^#?`([a-f0-9]{6}|[a-f0-9]{3})`$/`

Matches any character in the square brackets. For example 	`[nN]` `[oO]` matches `no`, `nO`, `No`, and `NO`.
`gr[ae]y` matches both spellings of the word `'grey'`; that is, `gray` and `grey`.

### Greedy and Lazy Match

`/^#`?`([a-f0-9]{6}|[a-f0-9]{3})$/`

A greedy match tries to match an element as many times as possible. Whereas, a lazy match tries to match an element as few times as possible. In our example we have `?` which signifies lazy quantifier. This is referred to a lazy quantifier because it causes the regular expression engine to match as few occurances as possible. We can simply turn this lazy match into a greedy one by adding a `?`.

### Boundaries
If in a string, we are looking for for specific words. Boundaries are not used in the given matching an email code.

## Author

Roman Tazhdynov

[GitHub](https://github.com/tajdinov)