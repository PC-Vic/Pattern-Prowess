# Pattern Prowess (a guide to help you understand regular expressions)

Email addresses can be quite diverse, and it's essential to validate them accurately. In this tutorial, we will explore a regular expression pattern for validating email addresses. This regex pattern is designed to match a wide range of valid email addresses and is a good starting point for email validation in your projects.

## Regex Pattern:

<span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

## Table of Contents

- [Pattern Prowess (a guide to help you understand regular expressions)](#pattern-prowess-a-guide-to-help-you-understand-regular-expressions)
  - [Regex Pattern:](#regex-pattern)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
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
  - [Author](#author)

## Regex Components

### Anchors

In regular expressions, anchors are special characters used to specify the position of a match within a string. They ensure that the pattern matches at specific positions in the string. For our email address validation regex pattern, the following anchors are utilized:

example: <span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

In this pattern, the <span style="color: green;">^</span> anchor asserts the start of the string. It indicates that the match must begin from the beginning of the input string. In the context of email validation, this ensures that the email address is matched from the very start, and no characters are allowed before it.

Also note, the <span style="color: green;">$ </span> anchor asserts the end of the string. Notice that the end of the regex above ends with the $ character. It signifies that the match must conclude at the end of the input string. In the case of email validation, this ensures that no characters are allowed after the email address, and it must be the last portion of the string.

### Quantifiers

In regular expressions, quantifiers are used to specify how many times a character or group of characters should be repeated in the input string. In our email address validation regex pattern, we use them as follows:

<span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

In this pattern, the + quantifier is used after character classes like <span style="color: green;">[A-Za-z0-9._%+-]</span> and <span style="color: green;">[A-Za-z0-9.-]</span>. It means that one or more of these characters can occur in the input string. This allows for flexibility in the local and domain parts of the email address, permitting different valid characters to be used.

* - The "Zero or More" Quantifier

<span style="color: green;">/^[A-Za-z0-9._%+-]*@[A-Za-z0-9.-]*\.[A-Za-z]{2,4}$/</span>

In some variations of email addresses, it's possible for parts of the email address to be empty, such as in "user@domain.com." The * quantifier allows for zero or more occurrences of the preceding character class, which means that these parts can be empty or have any number of valid characters.

### OR Operator

In regular expressions, the OR operator, represented by the pipe symbol <span style="color: green;">|</span>, allows you to specify alternative patterns. It means that the regex can match either the pattern on the left side of the <span style="color: green;">|</span> or the pattern on the right side. In the email address validation regex pattern, we don't typically use the OR operator to match different email address formats. Instead, we use character classes and quantifiers for flexibility.

<span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

In our pattern, we have a single, cohesive pattern that validates email addresses according to a set of rules and characters, without the need for OR operators. The absence of the OR operator makes the regex pattern straightforward and efficient for validating email addresses with specific rules. Let me show you an example of how to use this operator. Suppose you want to match either "apple" or "banana." You can use the OR operator like this:

<span style="color: green;">apple|banana</span>

This regex pattern will match either "apple" or "banana" in the input text.

For example, in JavaScript, you can use this pattern like so:

<span style="color: green;">const text = "I like apple and banana.";
const pattern = /apple|banana/g;
const matches = text.match(pattern);</span>


<span style="color: green;">console.log(matches); // Outputs: [ 'apple', 'banana' ]</span>


The pattern <span style="color: green;">/apple|banana/g</span> matches either <span style="color: green;">"apple"</span> or <span style="color: green;">"banana"</span> in the input text, and text.match(pattern) returns an array of matching words.

### Character Classes

Character classes are used to specify a set of characters that can be matched at a particular position in a regex. In our email address validation regex pattern, character classes are integral to matching valid characters in the local and domain parts of an email address.

<span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

In this pattern, we use character classes to define valid characters for the local and domain parts of the email address:

Specifying characters in regex can look like the following: <span style="color: green;">'[A-Za-z0-9._%+-]'</span> - The local part character class includes uppercase and lowercase letters, numbers, and special characters like dots (.), underscores (_), percent signs (%), plus signs (+), and hyphens (-). This allows for a wide range of valid characters in the local part of the email address.

<span style="color: green;">[A-Za-z0-9.-]</span> - The domain part character class includes uppercase and lowercase letters, numbers, dots (.), and hyphens (-). It ensures that the domain part consists of valid characters.

### Flags

Flags are optional settings that modify the behavior of the regex pattern. Common flags in JavaScript include i (case-insensitive) and g (global). However, for email address validation, we typically don't require flags as the pattern itself defines the validation rules.

Email Address Validation without Flags:
<span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

In our email address validation pattern, you'll notice that we haven't used any flags. The pattern itself is designed to match email addresses according to the rules and character classes we've defined. It validates email addresses case-insensitively because it includes both uppercase and lowercase letters in the character classes.

If your specific requirements necessitate flags, you can add them to the regex pattern. For example, if you want the pattern to be case-insensitive, you can add the i flag like this:

<span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/i</span>

The 'i' flag makes the pattern case-insensitive, allowing it to match both uppercase and lowercase letters. As I mentioned before, for most email address validation scenarios, flags are not needed, and the pattern itself defines the validation rules effectively.

### Grouping and Capturing

You can use parentheses <span style="color: green;">( )</span> to create groups. While in the provided email address validation regex pattern, the primary use of parentheses is for grouping character classes, they can also serve for capturing matched substrings or applying quantifiers to specific sub-patterns.

<span style="color: green;">(A-Za-z0-9._%+-)</span> - This group represents the valid characters for the local part of the email address. It includes uppercase and lowercase letters, numbers, and special characters like dots (.), underscores (_), percent signs (%), plus signs (+), and hyphens (-). While there is no explicit capturing or quantification applied to this group, it serves the purpose of grouping these characters for readability and future modification.

<span style="color: green;">(A-Za-z0-9.-)</span> - This group represents the valid characters for the domain part of the email address. It includes uppercase and lowercase letters, numbers, dots (.), and hyphens (-). Similarly, the primary role of this group is to group these characters for better pattern comprehension.

### Bracket Expressions

Bracket expressions, denoted by square brackets [ ], are used to define a set of characters that can be matched at a specific position in the regex. In the email address validation regex pattern, we primarily use character classes within bracket expressions to specify valid characters for different parts of the email address.

example:<span style="color: green;"> /^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

In our pattern, bracket expressions define character classes for the local and domain parts of the email address:

<span style="color: green;">[A-Za-z0-9._%+-]</span> - This bracket expression defines the character class for the local part of the email address, including uppercase and lowercase letters, numbers, and special characters like dots (.), underscores (_), percent signs (%), plus signs (+), and hyphens (-). These characters are valid for the local part of the email address.

<span style="color: green;">[A-Za-z0-9.-]</span> - This bracket expression specifies the character class for the domain part of the email address, including uppercase and lowercase letters, numbers, dots (.), and hyphens (-). These characters are valid for the domain part.

Bracket expressions help define the set of characters that can occur at specific positions in the email address, and they play a critical role in the structure of the regex pattern.

### Greedy and Lazy Match

quantifiers, such as * and +, are greedy by default. This means they match as much as they can while still allowing the entire regex to match successfully. However, you can make quantifiers lazy by adding a ? after them. Lazy quantifiers match as little as possible while still allowing the entire regex to match.

In the email address validation regex pattern:
<span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

+ and * are used in character classes like [A-Za-z0-9._%+-] and [A-Za-z0-9.-]. By default, they are greedy, matching as many characters as possible that satisfy the pattern. For example, [A-Za-z0-9._%+-]+ matches one or more characters in the local part of the email address.

In the context of email address validation, the use of greedy quantifiers makes sense. It ensures that all valid characters are matched, allowing for a wide range of email address formats.

However, you can make quantifiers lazy by adding a ? after them. For example, if you need to match as few characters as possible, you could use [A-Za-z0-9._%+-]+? to make the + quantifier for the local part of the email address lazy. In most email validation scenarios, greedy quantifiers are more appropriate.

### Boundaries

 Boundaries allow you to specify positions within the input string where the regex pattern should match. Two common boundary anchors are ^ (caret), which asserts the start of a line, and $ (dollar sign), which asserts the end of a line. These boundaries are not often used in email address validation because the entire email address needs to be validated, rather than just portions of it.

 example: <span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

<span style="color: green;">^</span> (caret) at the beginning of the pattern asserts the start of the string. This means that the match must start at the very beginning of the input string. In the context of email address validation, it ensures that the email address is matched from the start without allowing any characters before it.

<span style="color: green;">$</span> (dollar sign) at the end of the pattern asserts the end of the string. It signifies that the match must end at the very end of the input string. In the case of email validation, this ensures that no characters are allowed after the email address, and it must be the last part of the string.

In most email address validation scenarios, boundaries like <span style="color: green;">^</span> and <span style="color: green;">$</span> are crucial because the entire email address must be validated according to specific rules, and no extraneous characters are allowed before or after it.

### Back-references

Back-references allow you to refer back to captured groups within the regex pattern. This can be useful for matching repeated patterns or ensuring that a character matches the same character as a previously captured group.

<span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

The pattern that we are using above does not utilize back-references. This is because email address validation primarily focuses on matching the entire email address and does not require referring back to previously captured groups.

Back-references are more commonly used in scenarios where you need to match repeated patterns or enforce that a character must match a previously captured character. Suppose you want to match a word that repeats, such as "apple apple" or "banana banana." You can use a back-reference to ensure the word is repeated:

example: <span style="color: green;">\b(\w+) \1\b</span>

- <span style="color: green;">\b</span> asserts a word boundary.
- <span style="color: green;">(\w+)</span> captures one or more word characters (letters, digits, or underscores) in a group.
- <span style="color: green;">\1</span> is a back-reference to the first capturing group, ensuring that the same word appears again.
- <span style="color: green;">\b</span> asserts another word boundary.
  
With this regex, it will match instances where the same word is repeated, such as "apple apple" or "banana banana."

Here's how it works:

- <span style="color: green;">\b</span> ensures the match starts and ends at word boundaries.
- <span style="color: green;">(\w+)</span> captures a word.
- The space character matches the space between the two words.
- <span style="color: green;">\1</span> refers back to the captured word, ensuring that the same word follows.

### Look-ahead and Look-behind

 Look-ahead and look-behind assertions are used to check for patterns that are followed or preceded by another pattern, without including the latter in the match. They are useful for validating or matching patterns that have specific requirements around their surroundings.

 example: <span style="color: green;">/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/</span>

However, the pattern that we are using doesn't use look-ahead or look-behind assertions. This is because email address validation primarily focuses on matching the email address as a whole and doesn't require intricate checks on the surrounding text.

Here's a simple example to illustrate the concept of look-ahead and look-behind. Suppose you want to match "apple" only when it's followed by "pie," but you don't want to include "pie" in the match. You can use a look-ahead assertion like this:

<span style="color: green;">apple(?= pie)</span>

- apple matches the word "apple."
- <span style="color: green;">(?= pie)</span> is a positive look-ahead that ensures "pie" follows the word "apple" without including "pie" in the match.
With this regex, it will match "apple" only when it's followed by "pie."

## Author

I'm Victor Nieves, a passionate developer with a keen interest in regular expressions and web development. I created this tutorial to help others understand the intricacies of regex and how they can be applied in real-world scenarios. You can find more of my projects and connect with me on GitHub.

- GitHub: [PC-Vic](https:github.com/PC-Vic)
