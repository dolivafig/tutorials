# REGEX TUTORIAL- MATCHING AN E-MAIL

This tutorial is going to explain the use of regex to match emails using the expression /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/. This can be useful when validating emails using applications/technologies such as Node (Inqurier) or MongoDB.

## Summary

A regular expression or REGEX is a sequence of characters that defines a search pattern. These are commonly used to find patterns within a string, find/replace characters within a string or validate input. This tutortial will break each component down and walk through the components of this regex and how it works when matching an email.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components
It is important to note that a regex is considered a literal, so the regex pattern must be wrapped in slash characters (/) as seen in our regex example.

Anchors do not match any characters within the regex. Instead, they are used to match a position before, after, or between characters. They can be used to "anchor" the regex at certain positions.

There are two main anchors we need to be concerned about in our regex. The caret (^) and the dollar sign ($). The caret (^) signifies a string that begins with the characters that follow it. There are two formats this string can come in:

-An exact string match, such as ^Apple, where the strings "Apple" or "Apple red" match, but "apple" and "apple red" do not. This is because a regex is case-sensitive.
-The second format is a range of possible matches, displayed using bracket expressions, as seen in our regex below. Make sure to read the "Bracket Expressions" and "Quantifiers" sections for more on this!

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Similarly, the dollar sign $ matches right after the last character in the string, as seen above.

### Anchors
A regex is considered a literal, so the regex pattern must be wrapped in slash characters (/) as seen in our regex example.

Anchors do not match any characters within the regex. Instead, they are used to match a position before, after, or between characters. They can be used to "anchor" the regex at certain positions.

There are two main anchors we need to be concerned about in our regex. The caret (^) and the dollar sign ($).

The caret (^) indicates the beginning of the string.
The dollar sign ($) indicates the ending of the string.

### Quantifiers
Quantifiers in this regex includes the + operator, which will connect the users email name + email service + .com. Another quantifier for this regex includes {2,6}, which will allow a match range of 2-6 characters for the character set of [a-z\.].

Quantifiers are also defined as greedy, meaning the regex will match as many occurrences of particular patterns as possible. This includes:

*: Matches the pattern zero or more times
+: Matches the pattern one or more times
?: Matches the pattern zero or one time
{}: Curly brackets provides a way to set limits to a match, where {2,6} define the minimum and maximum amount of characters allowed in the preceding string

If we look back at our regex, this tells us that the first and second bracket expressions matches a pattern one or more times, and the final bracket expression of our regex is looking for any string between 2 and 6 characters that contains a combination of lowercase letters.

### Character Classes
Character classes allow us to write more compact regular expressions. Two common character classes are:

\d: matches any digit between 0-9
\w: matches any letter, digit and underscore character

The character class in this expression is \d, which matches a single characters that is a digit between 0-9. It will only match a single digit such as "4", but not "44".

### Grouping and Capturing
While many regular expressions are straightforward, others have multiple bracket expressions that need to be checked to determine different requirements. Looking at our regex, you can see that our bracket expressions have been separated into three groups, and divided by the (@), (\), and (.) symbols.

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

The backslash \ is actually a type of character escape - in other words, it escapes a character that otherwise would be interpreted literally. For example, the open curly brace ({) is used to begin a quantifier, but adding a backslash before the open curly brace ({) means that the regex should look for the open curly brace character instead of beginning to define a quantifier - in other words, it must have an open curly brace, and any strings without the open curly brace will not be accepted as a match.

There must be a period (.) before the beginning of the third group to define the third group.

Since this regex is being used to match an email format, we can infer that the @ symbol and the period are being used to break up an email search into three groups:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

    Group 1                 Group 2                         Group 3
/^([user email]+)@([email service or site]+)\.([domain name(.ca, .com, .org, .gov, etc)]{2,6})$/ 

Example: johndoe + @gmail + .com

The backslash loses its special significance inside bracket expressions.

Capturing group #1 in this expression is ([a-z0-9_\.-]+) that matches the user email name. The second capturing group is ([\da-z\.-]+) which will match the email service. Then lastly, capture group #3 is ([a-z\.]{2,6}) to capture the .com.

### Bracket Expressions
Bracked expressios for email validation includes the character sets of:

 [a-z0-9_\.-] -> matches the user email name
    which is matching any character from "a" to "z" and is case senstive,
    which is matching a character 0-9, 
    which is matching the characters "_" , "-" , and "."

[\da-z\.-] -> matches the email service
    which is matching any character from "a" to "z" (case senstive), 
    which is matching the characters period (.) and (-)

[a-z\.] matches the .com/.org/.gov/ etc...
    which is matching any character from "a" to "z" (case senstive) 
    which is matching the character period (.).

### Greedy and Lazy Match
This regrex includes greedy matches. 
Since it includes the (+) quantifier, it will match as many times as possible giving back as needed.
Another greedy Quantifier used in this regex is {} when matching {2,6} for the last capture group, which sets the limits of the string that your regex matches and often includes the minimum and maximum number of characters that your regex is looking for.

## Author

Created for educational purposes by Daniel Oliva
## Click [here](https://github.com/dolivafig/tutorials) to see the gist on github.
