# Title -The regex for Matching and Patterns

## Summary

Patterns used to match character combinations in strings are called regular expressions. Regular expressions are also objects in JavaScript.

These patterns are used with the exec() and test() methods of RegExp, and with the match(), matchAll(), replace(), replaceAll(), search(), and split() methods of String."  

A regular expression's purpose is to make it easier for users to sort and locate important sets of strings that they might need for some reason.They might be sorting web URLs or collecting telephone numbers for a database.Regex is a common name for regular expressions.

This regex /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/ matches a URL.

The URL matching regex ```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/ ``` is used.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Character Classes and Bracket Expressions](#character-classesbracket-expressions)
- [Grouping and Capturing](#grouping-and-capturing)
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

(Remember the / are to denote the start and end of the regular expression itself. )

After the first ```/``` we can see the ```^``` which translates into "start searching from the start of the string"

Before the final ```/``` we can see the ```$``` which translates into "... and stop searching at the end of the string"

When used together, these two effectively inform the expression as a whole that we must evaluate the entire string rather than merely matching specific portions.If we were to evaluate a string like this, let's say we did not have it in our email illustration:

```Youareawesome@gmail.com test ahhhh``` 

**```Youareawesome@gmail.com```** ```test ahhh``` 

The email part of the string would be returned as a match, but the rest of the string would not.We don't want this to happen; if the string we get isn't just an email, we don't want it to pass at all. However, including the anchors once more:

```Youareawesome@gmail.com test ahhh``` no longer has any matches, while:

**```Youareawesome@gmail.com```** is now a perfect match!

They are used to instruct the expression to search/query only a very narrow range of characters.


### Quantifiers

Quantifiers determine how many instances of a character, group, or character class must be present for a match to be found. 

In our email example:

```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```

The quantifiers are the ```+``` symbols and the ```{2,6}``` near the end

In this instance the ```+``` is saying "Match a char in this character class one or more times". It shows up twice in the expression to make sure we are typing in something before and after the '@' symbol in the email

The ```{2,6}``` is saying "Match a char in this character class from 2 to 6 times" 

Some other quantifiers include:

```?``` "Match zero or one time"

```*``` "Match zero or more times" (you can think of this kinda like a wildcard quantifier)

These quantifiers can either be greedy or lazy...

### Greedy and Lazy Match
  The default quantifiers try to match as many instances of a particular pattern as possible because they are greedy.However, they may also be lazi, matching as few instances of a particular pattern as they can.```?``` is a quantifier on its own, but if it is added after another quantifier (or even itself), the matching mode changes from greedy to lazy.

For example, if I have the follow regex:

```/a+/```

And the following string:

aaaaaaa

It will match the whole string as its in greedy mode; its gonna try to match as MANY occurrences of the 'a' as possible.

**```aaaaaaa```**

However if I add a ```?``` to the end of the regex expression:

```/a+?/```

It will only match the first instance of 'a':
 
**```a```**```aaaaaa```

As its now in lazy mode, aka its gonna try to match as FEW occurrences of the 'a' as possible.

### Character Classes and Bracket Expressions
They are used to specify a range or set of acceptable characters, also known as character sets.The argument/acceptable characters are indicated by being enclosed within square brackets [].The term "bracket expression" refers to anything within these brackets. For instance, if I wanted to check for all lowercase letters, I could do something like:

```/[a-z]/``` or alternatively use a character class ```/[[:lower:]]/```

For a more practical example, lets say I want to match all instances of the word 'grey' from something.

Depending on where you're from in the world you might spell it grey with an 'e'

```/grey/``` will only check for instances of 'grey'

or gray with an 'a '

```/gray/``` will only check for instances of 'gray'

Using character classes, we can account for this difference and check to see if a specific character matches from a set of acceptable characters:

```/gr[ae]y/``` will check for instances of 'grey' and 'gray', as both the 'e' and 'a' character are valid here

In our email example:

```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```

We have a couple of character sets, however lets take a look at:

```[a-z0-9_\.-]+```

(the + is a quantifier applied to the set)

This translates into:

Match any of the following at least once, up to as many times as possible:

* Any lowercase letter     ```a-z```
* Any digit                ```0-9```
* A underscore             ```_```
* A period                 ```\.```
* A hyphen                 ```-```

The reason we would want to have this at the start of the expression, is because its the first part of the email we are checking for!

**```Youareawesome```**```@gmail.com```


### Grouping and Capturing
Treating multiple characters as a single unit can be accomplished by grouping them together, or "capturing" groups.By using parentheses around the characters you want to group together, you can make them.You can use quantifiers on any member of the group and check the entire group for a match thanks to this.In our example email:

```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```

We have three groups

**```([a-z0-9_\.-]+)```** **```([\da-z\.-]+)```** **```([a-z\.]{2,6})```**

We have a character set with a quantifier for each group.The first two sets look for at least one match, while the final set in the last group looks for characters that match between 2 and 6.

The three sections of an email, with the exception of the @ and, are represented by these three groups.for the site itself)

**```Youareawesome```**@**```gmail```**.**```com```**

Because we are verifying that there is the appropriate quantity of data as well as valid data all over the place, grouping is particularly useful in this situation.Similar to grouping in mathematics, everything within a parenthesis will be evaluated on its own before being tested in the expression as a whole.

### Look-ahead and Look-behind

Given our email expression, here's a translation. 
I will put the regex and section of string that corresponds to the translation in code snippets:

Regex: ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```

String: ```Youareawesome@gmail.com```

```/^``` 
The beginning of the regex expression, searching from the start of the string

```([a-z0-9_\.-]+)``` Match at least one character that's either a lowercase letter, digit, an underscore, period, or a hyphen 
```Youareawesome``` This would be the first part of the email

```@``` Match an at symbol '@'

```([\da-z\.-]+)``` Match at least one character that's either a digit (\d is shorthand for 0-9), lowercase letter, period, or a hyphen 
```gmail``` This would be the websites name

```\.``` Match a period '.'

```([a-z\.]{2,6})``` Match between 2 and 6 characters that are either a lowercase letter, or a period                    
```com``` This would be the domain part of the website, hence why we only want to check for 2-6 chars

```$/``` The end of the regex expression, ending the search at the end of the string

Hopefully after this tutorial that expression and this translation should make a lot more sense!

The main expressions are compelled to be what you have defined them to be when you use lookaheads and lookbehinds. It will not be accepted as a valid input if it is not exactly what it is.

## Author

LaTavya Collins: UT bootcamp coding student

### Sources and References
    * [regexr](https://regexr.com/)
    * [BackRef](https://www.regular-expressions.info/backref.html)
    * [RegExpression](https://www.regular-expressions.info/wordboundaries.html)

My Github [github] https://github.com/Collins418

