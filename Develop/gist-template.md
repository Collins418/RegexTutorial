# Title (replace with your title)

The regex for a Matching

## Summary

Patterns used to match character combinations in strings are called regular expressions. Regular expressions are also objects in JavaScript.

These patterns are used with the exec() and test() methods of RegExp, and with the match(), matchAll(), replace(), replaceAll(), search(), and split() methods of String."  

A regular expression's purpose is to make it easier for users to sort and locate important sets of strings that they might need for some reason.They might be sorting web URLs or collecting telephone numbers for a database.Regex is a common name for regular expressions.

This regex /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/ matches a URL.

The URL matching regex ```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/ ``` is used



## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
Multiple parts of regular expressions can shape any search pattern you're working on.

The most typical components include:Anchors, quantifiers, character classes, bracket expressions, and other similar terms can become quite complicated when used in conjunction with regular expressions.Using particular components, you can basically find any string combination.Let's take a look, starting with the anchors, to get more information.

### Anchors
When using regex (regular expression), anchors are typically used to match a position in the string rather than a single character or set of characters.This means that you can match any character's position before, after, or between them.
The caret ```^``` matches the position before the first character in a string, while the ```$``` matches right after the last character in the string.

In our email regex example, we can see these as the ```^``` and ```$``` characters:

```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```

Extracting them out looks like:

```/^$/```

(remember the / are to denote the start and end of the regular expression itself )

After the first ```/``` we can see the ```^``` which translates into "start searching from the start of the string"

Before the final ```/``` we can see the ```$``` which translates into "... and stop searching at the end of the string"

These two used together effectively tell the whole expression that we need to evaluate the entire string, not just match certain sections of it. Let's say we didn't have it in our email example, if we were to evaluate a string like:

```timprimmer@gmail.com test test ahhh``` 

**```timprimmer@gmail.com```** ```test test ahhh``` 

The email section would come up as a match, while the rest of the string is not. This isn't the behavior we want, if the string given to us isn't purely an email we dont want it to pass AT ALL. However, adding back in the anchors:

```timprimmer@gmail.com test test ahhh``` no longer has any matches, while:

**```timprimmer@gmail.com```** is now a perfect match!

They are used as a way to tell the expression to only search/query a very specific section of characters.


### Quantifiers

Quantifiers communicate to the regex engine that it must match the quantity of the character or expression to its left. These are the quatifiers that are used in regex:
  ?, +, *, {n}, {n, }, {n,m}
  In the URL matching regex they are used in the following places:
    https?          Matches 'https', 'http'
    [\da-z\.-]+     Matches a single digit, group of letters (a-z), dot (.) or hyphen (-) 1 or more times
    [a-z\.]{2,6}    Matches 2 to 6 copies of the sequence [a-z\.]
    [\/\w \.-]*     Matches '/', '.', '-', 'www', '//'
  

### Character Classes
Character Classes ensure that a given sequence of characters matches a larger set of characters.

    [a-z]          Matches lowercase alphabetic characters between a and z
    \w             Matches a word
    \d             Matches a single character that is a digit
    .              Matches any character


### Grouping and Capturing
The use of grouping expressions is to allow for the extraction of the characters of a given group for validation. The text between paranthesis is a group.
    (https?:\/\/)       Matches: ' ', 'https://', 'http://'
    ([\da-z\.-]+)       Matches: 'ab.c-7', 'ab'
    ([a-z\.]{2,6})      Matches: 'ab.', '.ca'
    ([\/\w \.-]*)       Matches: '/', '/ab.'

### Bracket Expressions
Bracket expressions are used between brackets. In this example, we have the following Bracket Expressions.
    [\da-z\.-]
    [a-z\.]
    [\/\w \.-]

### Greedy and Lazy Match
These are my favorite named elements of a regular expression. Greedy and Lazy match. Are you kidding? What a country! These qualifiers allow you to find the "greedy" (longest) and "lazy" (shortest) match.
    ([\da-z\.-]+)       "+" operator is greedy as it allows character matching from one to an infinite amount of times.



## Author




## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

### Quantifiers

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
