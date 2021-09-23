# Regex Tutorial -- Matching an HTML tag

As you know regular expressions or regex is a series of characters that define a search pattern. This is most helpful when needing to hide a users password and avoiding a breach to user info.
However, it is used to validate emails, usernames, HTML tag and etc. In this tutorial we will be going over matching an HTML tag and the breakdown of what it looks likes. For now, this is what it looks like and by the end of this tutorial you will know exactly what the pattern is looking for and how it can be helpful.

`/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

## Summary

As stated above, this tutorial will be going over matching an HTML tag. I will give a breakdown of the quantifiers, anchors, grouping constructs, bracket expressions, character classes and character escapes. In this specific pattern it does not use flags so, we will not be going over that. As far as everything else, I will give a brief description and what it looks like in the actual pattern itself.

Here is what we are going to be working with again:

`/^ <([a-z]+) ([^<]+) * (?:>(.*) <\/\1>|\s+\/>) $/`

`/^` -- before the first character `$/` -- after the last character

`[a-z]` -- lowercase a-z

`+` -- means one or more

`/s` -- matching whitespace or line breaks

`\` -- escapes a character

`()` -- capturing a group

`\1` -- uses results of group 1 contents

`*` -- means zero or more is greedy -- will match too much

`?` -- makes a quantifier non-greedy -- will match less

`:`, `|` -- is an OR operator

`^` -- beginining of a string

`>` -- matches `>` character

`([a-z]+)` -- group one
`([^>]+)` -- group two
`(?:>(.*) <\/\1>|\s+\/>)` -- group three

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

Since we are understanding matching an HTML Tag. This Regex pattern can be used to search for those exact HTML tags.
Regex patterns are considered literal and will be wrapped in slash characters `/` like so:

`/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

### Anchors

The character `^` is an anchor the signifies the start of the pattern and `$` is an anchor as well that is at the end of the string of characters.
So, in this case. After the anchor in this pattern we have `<` will only look for tags that start with `<` .

### Quantifiers

Quanitfiers can help narrow down your regex matches. For instance, in this regex pattern we have `*` and `+` inserted in our pattern.
Keep in mind quanitifers can match as many times as it wants.
`*` means matching 0 or more times and `+` means meatching one or more times.
In this case, `([a-z]+)` is looking for anything a-z more than one time and `([^>])` is looking for anything that is not specified in the pattern inside an HTML `<` more than one time as well.
I would like to point what greedy means in a regex as well. It is something along the lines of the regex characters wanting to match more than once. You can make a quantifier lazy meaning it will only match less so the opposite of a greedy quantifier.

### Grouping Constructs

Allows you to have a pattern looking for more than on specific set of requirements. In this pattern we have 3 groups.
Group constructs are like bracket expressions except they only match what is specified in the pattern.
`([a-z]+)` -- group one, matching a-z characters `[a-z]` `+` more than once.
`([^>]+)` -- group two, matching characters unspecified `[^>]` `+` more than once.
`(?:>(.*) <\/\1>|\s+\/>)` -- group three -- this specific group we have `?:>` inserted which means this pattern can not be re-used and `.*` is matching characters that do not include whitespace `\1` matching the results of group 1 and `|` is OR opertator `/s` means the pattern is looking for whitespace more than once and `/` is lookingg to match the `/` character inside an HTML tag.
Since HTML tags look something like this:
`<body>` `<header>` `</img>`

### Bracket Expressions

Now, bracket expressions are used to include the characters we want to match. In this specific regex we have two, `[a-z]` and `[^>]`.
Inside the square brackets `[a-z]` will only look for lowercase characters a-z. Also, keep in mind that regex is case sensitive.  
Indide the square brackets `[^>]` `^` will match a character that is not in the previous bracket expression and `>` will look for that specific element to match in the HMTL tag.

### Character Classes

A character class like bracket expressions can match input from strings. In our code we have `/s` and `.`
`/s` will match any whitespace like a line break and `.` is the opposite meaning it will match any character but not a whitespace.

### The OR Operator

OR operators allow two different group constructs to potentially match all the requirements in the pattern. When looking for OR operators they look like `:` or `|` in a pattern.
In the HTML code we have one here:

So, let's break this down. We have `<\/\1` which means the pattern is looking for the results we get from group 1 requirements OR because we use `|` we are looking for any whitespace more than once and a `/` character in this group 3 construct.
I understand it as this, say we have an HTML tag that looks like `<header> </header>`. With HTML regex it is looking to match the first tag with `([a-z]+)` and then looking to match the second tag with the group 3 pattern `<\/\1>|\s+\/>` since white space, closing `/` will be included and some of the same requirements from group 1.

### Character Escapes

The cool thing about character escapes is they can be used to in order for the pattern to look for a specific character.
In this particular pattern we have `\/` which means the pattern is specfifially going to look for a `/` to match.

## Author

K'trina Apodaca is a current student attending the DU coding bootcamp who currently lives in Colorful Colorado. Here is their github profile: https://github.com/kapodaca0403
