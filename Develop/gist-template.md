# Regex Email Match Tutorial

The following tutorial will detail how to use regex (regular expressions) to match an email(s).

## Summary

The regex to match an email address will look something like this example: `(/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/)`. Below, I will detail the various components of a regex email and how to manipulate the regex to find what you are looking for based on the needs of your match. 


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
The two anchor components that can go into a regex are `^` and `$`. The `^` means match any character after. You can use this component to identify an exact string match such as `/^The/`. Or you can use it along with a bracket expression to identify a range of charaters that should be accepted such as `/^[a-z]/`. Its important to note that with the former component `^` when used without a bracket expression, that this is a case sensitive search. The second component `$` means match characters that end with the preceding characters. So when we look at our above example, the ending `{2,6}$` signifies to match an email address where this portion of the address is between 2 and 6 characters. 

### Quantifiers
At the very end of our example regex above, we have `{2,6})$` at the end. This component is called a quanitifer and what it does is puts limits upon the matched regex string. Typically, quanitifiers will include a minimum and maximum number of characters that your regex is trying to match. These values will be wrapped in curly brackets. So in our example we have `2` and `6`. Meaning, we want to try to match a string with a minimum of 2 characters and a maximum of 6 characters. So the quanitifer `{}` sets limits upon a match, we do also havbe a few more options besides this. The `*` quantifier matches the pattern zero or more times. The `+` matches the pattern one or more times. And the `?` quantifier matches the pattern zero or one time. So as relating to the above example, a string like `.com` as it contains a period, contains lowercase letters a-z, and is between 2 and 6 characters as set by the quanitifer. A string like `.asdfasdfasdf` would not work as it is more than 6 characters. 

### Grouping Constructs
With our above example, you can see a few `()` throughout the expression. We use these to break up a long and complicated expression into mini subexpressions so that we can check multiple different parts of a string to fulfill different requirements. So for example, if we had `/^([a-c0-9])@([a-c]).com/` we are allowing our requirements to match two separate requirements. The first being within the first set of `()`, `([a-z0-9])`. And the second withing the second set of `()`, `([a-z])`. So something like `abc123@aaa.com` would work as the characters `abc123` are within the first subexpression requirements and `aaa` are within the second subexpression. However something like `ght99@aaa.com` would not work as the `ght` does not fit the requirements of our first subexpression. Breaking a large and complicated expression into smaller and more manageable pieces can thus be accomplished by the use of `()` as subexpressions.

### Bracket Expressions
If you notice in our above example,there are numerous `[]` throughout. These portions of the regex are called bracket expression and they allow us to search through a range of characters. So in something like this `/[a-z]/` we are saying to match any string that contains any lowercase letter between a and z. Now within these brackets we can also match capitals letters with `/[A-Z]/` as well as underscores and hyphens with `/[_-]/` and even digits with `/[0-9]/`. So if we put all this together: `/[a-cA-C0-9_-]/`, example matches would include `a`, `aa`, `abc`, `bba-cca`, `a1_2`, `c2133`... Examples that wouldnt match include `gfd`, `nji`, `OPY`, `TER`, `qwERT`... Bascially any lower case or uppercase letter that is not a,b, or c would not match.

### Character Classes
The bracket expressions that we have used throughout our above example regex, is actually under this same component of character class. A character class defines what set of characters can fulfill a match. Along with our regex example having the bracket expressions, it also contains a `\d` which is another character class. What this does is matches any numerical digit 0-9. This is similar to `[0-9]`. There are also a few other character classes including `.` which matches any character, `\w` which matches any alphanumeric character, and `\s` which matches a single white space. So inour example above we have `\da-z` indicating that we want to match any numerical digit as well as letters a - z. 

### Character Escapes
So how would we be able to differentiate between characters with two functions. For example, `.` can either be a literal period or refer to the character class that calls to match any character. You can see how this could ruin a whole regex, but not to worry because with whats known as a chracter escape `\`, we can state that we want the literal character that follows this component. So in regards to our example regex above, there exists withtin the first subexpression `\.` which we are using to indicate that we want to match the actual period and not any character. Another example of this is with `{`. If we have just `{` then we are telling our regex that we are about to define a quantifier. However if we add `\` so it looks like `\{`, now we are saying that we want the literal curly brace to match.
  
## Author

Hi! My name is Ali Aldawoodi and have a passion for programming. I love problem solving and figuring out solutions to challenges. To be able to take an idea in your head and put it out into the world through code is a very motivating fact that I will continue to try to pursue. Thanks for reading my Gist and if you would like to view some of my other projects feel free to at: https://github.com/Ali-Aldawoodi.
