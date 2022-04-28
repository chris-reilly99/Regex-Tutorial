# Regex tutorial!

## Intro

Regular expressions (a.k.a. Regex) are sequences of characters that define search patterns in text. One way to imagine this is like the search tool we all know and love: ctrl + f. But we can do a little more with regex than just your basic 'ctrl + f' combo, we can search for patterns that match either specific text, or we can search for patterns that fit certain criteria as opposed to specific text. For example, if you want to search for a phone number in a document, you could use 'ctrl + f' to search for the exact number, but if you don't know the phone number you could use regex to search for any text that fits a standard phone number format. 

## Summary

In this tutorial, we'll build of understanding of regular expressions by examining an example regex is structured. The following regex is used to search for a hex color code:

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

For hex codes, there are two formats, a standard hex triplet and a shorthand version. Both start with a # symbol.
Standard hex triplet format is the # symbol followed by 6 alphanumeric characters. The short hand version is the # symbol followed by 3 alphanumeric characters.

Ex:
Standard: #000000
Shorthand: #000

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

For regular expressions, there are two anchors. Anchors signify the beginning and end of the pattern that is being search for. The two anchors are:

The beginning, carrot symbol: `/^`
The end, dollar sign: `$/`

They are highlighted in our hex-code regex below:

`/^`#?([a-f0-9]{6}|[a-f0-9]{3})`$/`

### Quantifiers

Quanitifiers are used to describe the number of characters that are expected. There are a few different quantifiers that each search for a different value types. Additionally there are greedy and lazy quanitifiers. Greedy quantifiers tries to match a specified element as many times as possible, a lazy one tries to match that element as few times as possible.

`?` looks to match 0 or 1 time
`*` looks to match 0 or more times
`+` looks to match 1 or more times
`{` n `}` looks to match exactly n times
`{` n `,}` looks to match at least n times
`{` n `,` m `}` looks to match from n to m times

Each of these is a greedy quantifier and can be turned into a lazy quanitfier by adding a `?` after the quantifier characters.
For example, turn the `*` greedy quantifier into a lazy one by making it `*?`.

As mentioned in the summary, there are 2 hex color code formats, we'll use the OR operator to distinguish which format we are using. In our Hex Value regular expression we have `{6}` (Hex Triplet Format) and `{3}` (Shorthand Hex Format), this indicates that the length of the component preceding these quantifiers should be 6 for `{6}` and 3 for `{3}`. The `?` indicates that we are looking to match the expression 0 or 1 times.

They are highlighted in our example hex format below:

/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/

### Grouping Constructs

Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. For grouping, we use parathesis `()` around the subexpression we are looking for. So if we but `(abc)` into our expression, every instance of the character `a` followed by `b` followed by `c` will be matched. 

The grouping contructs are highlighted below to help us under stand how they function in our expression. 

/^#?`(`[a-f0-9]{6}|[a-f0-9]{3}`)`$/

In our example, we are only looking for one sub expression. But, sometimes we want to search for multiple subexpressions, like in an email. In an email regex, there would a subexpression before the `@`, another subexpression immediately after, and a third after the `.`.

### Bracket Expressions

Brackets `[]` indicate a set of characters to match. Any individual character between the brackets will match. Bracket expressions in our regular expression signify the beginning of a character class or quantifier statement. In our example we use parenthesis to define our bracket expressions.

/^#?(`[`a-f0-9`]`{6}|`[`a-f0-9`]`{3})$/

In our example, we are using the brackets to search for the character class: `a-f0-9` for both the standard and shorthand format.

### Character Classes

Character classes are descriptions inside our regex that tells us what type of characters to look for. In our example, our character classes are contained within the brackets `[]`. Our character classes are `a-f0-9`, which will search for any characters that are either letters between `a` and `f` in the alphabet, or digits `0` through `9`. These are case sensitive, so the `a-f` part of our character class will only search for `a-f` if they are lowercase, if they are uppercase it will not be detected by the regex.

/^#?([`a-f0-9`]{6}|[`a-f0-9`]{3})$/

### The OR Operator

The "or" operator is pretty much exactly what it sounds like. If there are multiple components of an expression, it indicates that either component within the expression could be the one that the expression should look for. The OR operator is defined with the `|` character. In our example, it indicates that the regex should be looking for the standard hex code (left) OR the shorthand hex code (right).

/^#?([a-f0-9]{6}`|`[a-f0-9]{3})$/

### Flags

Regular expressions may have flags that affect the search. There are six different types of flags:
`i` - this flag makes the search non-case-sensitive
`g` - the search will look for all matches, without it, only the first result is returned
`m` - multiline mode - this only affects the behavior of `^` and `$`, it allows the search to cover multiple lines of text
`s` - Enables “dotall” mode, that allows a dot . to match newline character
`u` - Enables full Unicode support. The flag enables correct processing of surrogate pairs.
`y` - “Sticky” mode: searching at the exact position in the text

Unfortunately, there are no flags in our example.

### Character Escapes

Character escapes are used to indicate a literal character. You also escape certain letters that represent common character classes, such as `\w` for a word character or `\s` for a space.

Unfortunately, there are no character escapes in our example.

## Author

Chris Reilly

Chris Reilly is a finance and accounting professional looking to expand his coding skills. He is a student at the University of Denver's Full Stack Coding Boot Camp.

GitHub: [chris-reilly99](https://github.com/chris-reilly99)
