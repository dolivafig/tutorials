# Title (replace with your title)

This tutorial is going to explain the use of regex to match emails using the expression /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/. This can be useful when validating emails using applications/technologies such as Node (Inqurier) or MongoDB.

## Summary

A regular expression is a sequence of characters that defines a search pattern. This is commonly used to find patterns within a string, find/replace characters within a string or validate input. This tutortial will go walk through the components of a regex and how it applies to matching an email.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
<!-- - [OR Operator](#or-operator) -->
- [Character Classes](#character-classes)
<!-- - [Flags](#flags) -->
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
<!-- - [Boundaries](#boundaries) -->
<!-- - [Back-references](#back-references) -->
<!-- - [Look-ahead and Look-behind](#look-ahead-and-look-behind) -->

## Regex Components
Before we dive into anchors, it is important to note that a regex is considered a literal, so the regex pattern must be wrapped in slash characters (/) as seen in our regex example.

Anchors do not match any characters within the regex. Instead, they are used to match a position before, after, or between characters. They can be used to "anchor" the regex at certain positions.

There are two main anchors we need to be concerned about in our regex. The caret (^) and the dollar sign ($). The caret ^ signifies a string that begins with the characters that follow it. There are two formats this string can come in:

    -An exact string match, such as ^Orange, where the strings "Orange" or "Orange cat" match, but "orange" and "orange cat" do not. This is because a regex is case-sensitive.
    -The second format is a range of possible matches, displayed using bracket expressions, as seen in our regex below. Make sure to read the "Bracket Expressions" and "Quantifiers" sections for more on this!

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Similarly, the dollar sign $ matches right after the last character in the string, as seen above.

### Anchors
The anchors used in this regex expression for matching an email are ^ , which indicates the beginning of the string and $ to indicate the ending of the string. (m), or multiline is not enabled, so the regex will end at $.

### Quantifiers
Quantifiers in this regex includes the + operator, which will connect the users email name + email service + .com. Another quantifier for this regex includes {2,6}, which will allow a match range of 2-6 characters for the character set of [a-z\.].

Quantifiers are also defined as greedy, meaning the regex will match as many occurrences of particular patterns as possible. This includes:

*: Matches the pattern zero or more times
+: Matches the pattern one or more times
?: Matches the pattern zero or one time
{}: Curly brackets provides a way to set limits to a match, where {x,y} defines the minimum and maximum amount of characters allowed in the preceding string.

If we look back at our regex, this tells us that the first and second bracket expressions matches a pattern one or more times, and the final bracket expression of our regex is looking for any string between 2 and 6 characters that contains a combination of lowercase letters.

<!-- ### OR Operator -->

### Character Classes
The character class in this expression is \d, which matches a single characters that is a digit from 0-9. It will only match a single digit such as "4", but not "44".

<!-- ### Flags -->

### Grouping and Capturing
While many regular expressions are straightforward, others have multiple bracket expressions that need to be checked to determine different requirements. Looking at our regex, you can see that our bracket expressions have been separated into three groups, and divided by the "@", "\", and "." symbols.

The backslash \ is actually a type of character escape - in other words, it escapes a character that otherwise would be interpreted literally. For example, the open curly brace ({) is used to begin a quantifier, but adding a backslash before the open curly brace ({) means that the regex should look for the open curly brace character instead of beginning to define a quantifier - in other words, it must have an open curly brace, and any strings without the open curly brace will not be accepted as a match.

Using this logic, we now know one more key piece of information about our regex:

there must be a period (.) before the beginning of the third group to define the third group
But what about the at (@) symbol? Knowing that we are using a regex to match an email value, we can infer that the @ symbol and the period are being used to break up an email search into three groups, like so:

/^([user email]+)@([email service or site]+)\.([domain name(.ca, .com, .org, .gov, etc)]{2,6})$/ Ex: claudiacdavis + @gmail + .com

Note: the backslash loses its special significance inside bracket expressions.

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Capturing group #1 in this expression is ([a-z0-9_\.-]+) that matches the user email name. The second capturing group is ([\da-z\.-]+) which will match the email service. Then lastly, capture group #3 is ([a-z\.]{2,6}) to capture the .com.

### Bracket Expressions
Bracked expressios for email validation includes the character sets of [a-z0-9_\.-], which is matching any letter a-z and is case senstive. It also matches a character 0-9 and matches the characters "_" , "-" , and "."; [\da-z\.-], which is matching a single digit from 0-9, any character a-z (case senstive), and the characters "." and "-".; [a-z\.] matches any character a-z(case senstive) and the character ".".

### Greedy and Lazy Match
This regrex includes greedy matches. Since it includes the + Quantifier, it will match as many times as possible giving back as needed. Another greedy Quantifier used in this regex is {} when matching `{2,6} for the last capture group.

<!-- ### Boundaries

### Back-references

### Look-ahead and Look-behind -->

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
