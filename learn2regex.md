# ***learn2regEx Email Edition***<br>
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
<br>
>&emsp;This tutorial will show you how to use the matching email regex to ensure the proper format is used when a user makes an input into an email address field for submission.
<br>

## **Summary**<br>

>&emsp;A matching email regex, also known as a regular expression or pattern, is used to validate whether an email address entered by a user matches a certain set of rules or criteria. The purpose of using a matching email regex is to ensure that the email address is in the correct format and contains the necessary elements such as a username, an @ symbol, a domain name, and a top-level domain (TLD). This is important for preventing errors or invalid email addresses from being submitted, which could reult in lost or misdirected messages, security vulnerabilities, or other issues. Matching email regexes can be used in programming lanuages, web forms, or other applications to verify email addresses and provide feedback to users if the input is incorrect.
<br>

## **Table of Contents**<br>
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
<br>

## **Regex Components**<br>
<br>

>&emsp;In regular expressions, the `^` and `$` symbols are used as anchors to match the start and end of a string, respectively. The `^` anchor specifies that the pattern being matched must appear at the beginning of the string, while the `$` anchor specifies that the pattern must appear at the end of the string.

>&emsp;For example, the regex pattern `^git` would match any string that starts with the word `git`, such as `git hub` or `git repository`, but would not match a string like `hub git`. Similarly, the regex pattern `hub$` would match any string that ends with the word `hub`, such as `git hub` or `the hub`, but would not match a string like `hub is updated`.
<br>

### &emsp;&emsp;<u>***Anchors***</u><br>

>&emsp;In regular expressions, the `^` and `$` symbols are used as anchors to match the start and end of a string, respectively. The `^` anchor specifies that the pattern being matched must appear at the beginning of the string, while the `$` anchor specifies that the pattern must appear at the end of the string.

>&emsp;For example, the regex pattern `^git` would match any string that starts with the word `git`, such as `git hub` or `git repository`, but would not match a string like `hub git`. Similarly, the regex pattern `hub$` would match any string that ends with the word `hub`, such as `git hub` or `the hub`, but would not match a string like `hub is updated`.

>&emsp;Using the `^` and `$` anchors can be useful for ensuring that a regex pattern only matches strings that exactly match the desired format or pattern, without matching partial or overlapping strings.

>&emsp;Using `^` and `$` together in a regular expression creates a pattern that matches an entire string that exactly matches the specified pattern. This is sometimes referred to as an "exact match" pattern.

>&emsp;For example, the regex pattern `^git$` would only match a string that contains only the word `git` and nothing else. This means that the string `git` would match, but `git hub` or `git repo` would not match.

>&emsp;Using `^` and `$` together can be useful in cases where you need to ensure that the entire string matches a specific pattern, and not just a portion of it. This can be particularly important in situations where you need to validate user input or ensure that data conforms to a certain format.
<br>

>&emsp;Here is an example of a Jest Test that would use Anchor matching:
```javascript
// regex checks whether the pattern matches a string that contains a valid email address at the beginning of the string
test('matches a valid email address at the beginning of a string', () => {
  const regex = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
  const string1 = 'jane.doe@example.com';
  const string2 = 'john_smith123@mydomain.co.uk';
  const string3 = 'notanemail.com';
  expect(regex.test(string1)).toBe(true);
  expect(regex.test(string2)).toBe(true);
  expect(regex.test(string3)).toBe(false);
});
```

### &emsp;&emsp;<u>***Quantifiers***</u><br>

>&emsp;In regular expressions, quantifiers are used to specify how many times a certain pattern should be matched in a string. There are several quantifiers available, including:

>&emsp;- The `+` quantifier matches one or more occurrences of the preceding pattern.<br>
>&emsp;- The `*` quantifier matches zero or more occurrences of the preceding pattern.<br>
>&emsp;- The `?` quantifier matches zero or one occurrence of the preceding pattern.<br>
>&emsp;- The `{n}` quantifier matches exactly n occurrences of the preceding pattern.<br>
>&emsp;- The `{a,b}` quantifier matches between a and b occurrences of the preceding pattern.<br>

>&emsp;For example, the regex pattern `colou?r` would match both `color` and `colour`, as the `?` quantifier specifies that the letter `u` is optional. The regex pattern `a{3}` would match any string that contains exactly three consecutive occurrences of the letter `a`, such as `baaaad`. The regex pattern `a{1,3}` would match any string that contains between one and three consecutive occurrences of the letter `a`, such as `baaad` or `baaaad`.

>&emsp;Using quantifiers can be helpful in cases where you need to match a pattern that occurs multiple times in a string, without having to specify each occurrence individually.

>&emsp;Here is an example of a Jest Test that would use Quantifier matching:
```javascript
// regex is matching any string that starts with 1 to 64 characters that are either letters (upper or lowercase), digits, or any of the characters ._%+-, followed by the @ symbol, then one or more letters, digits, or hyphens, followed by a period and two or more letters 
test('matches a valid email address with a range of characters for the local part', () => {
  const regex = /^[a-zA-Z0-9._%+-]{1,64}@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
  const string1 = 'jane.doe@example.com';
  const string2 = 'john_smith123@mydomain.co.uk';
  const string3 = 'notanemail@mydomain.com';
  expect(regex.test(string1)).toBe(true);
  expect(regex.test(string2)).toBe(true);
  expect(regex.test(string3)).toBe(false);
});
```

### &emsp;&emsp;<u>***OR Operator***</u><br>

>&emsp;In regular expressions, the OR operator is represented by the vertical bar `|` and allows you to specify multiple possible patterns to match. It functions by matching either the pattern to its left or the pattern to its right. For example, the regular expression pattern `cat|dog` would match either the string `cat` or the string `dog`.

>&emsp;The OR operator can be used in a variety of situations, such as when you want to match alternative spellings or variations of a word, or when you want to match multiple possible patterns. For instance, the pattern `gr(a|e)y` would match either `gray` or `grey`, because the OR operator is used to allow for either spelling.

>&emsp;In addition to the | symbol, some regex engines may support other ways of expressing the OR operator, such as using square brackets to specify a set of possible characters to match. Regardless of the syntax used, the OR operator is a powerful tool for creating flexible and versatile regular expressions.

>&emsp;Here is an example of a Jest Test that would use OR Operator matching:
```javascript
// regex is testing to see if there are matches to any string that contains a valid email address with the domain names "gmail.com", "yahoo.com", or "hotmail.com"
test('matches a valid email address with multiple valid domains', () => {
  const regex = /^[a-zA-Z0-9._%+-]+@(gmail|yahoo|hotmail)\.com$/;
  const string1 = 'jane.doe@gmail.com';
  const string2 = 'john_smith123@yahoo.com';
  const string3 = 'notanemail@hotmail.co.uk';
  expect(regex.test(string1)).toBe(true);
  expect(regex.test(string2)).toBe(true);
  expect(regex.test(string3)).toBe(false);
});
```

### &emsp;&emsp;<u>***Character Classes***</u><br>

>&emsp;In regular expressions for email matching, character classes are used to specify a group of characters that can be matched. There are several character classes that are commonly used in email matching, including:<br><br>
>&emsp;&emsp;EXAMPLE:&emsp;`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`<br>
>- `[a-z]` matches any lowercase letter from a to z.<br>
>- `[A-Z]` matches any uppercase letter from A to Z.<br>
>- `[0-9]` matches any digit from 0 to 9.<br>
>- `.` matches any character, including letters, digits, and symbols.<br>
>- `\w` matches any word character, which includes letters, digits, and underscore.<br>
>- `\d` matches any digit from 0 to 9.<br>
>- `\s` matches any whitespace character, including spaces, tabs, and line breaks.<br>

>&emsp;These character classes can be combined to create more complex patterns for matching email addresses. For example, the pattern `[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}` matches most valid email addresses by allowing one or more occurrences of letters, digits, and symbols before the "@" symbol, followed by a domain name that includes letters, digits, and hyphens, and ending with a top-level domain of two or more letters.

>&emsp;Using character classes can be helpful for matching specific patterns of characters in an email address, such as the username, domain name, or top-level domain.

>&emsp;Here is an example of a Jest Test that would use Character Class matching:
```javascript
// regex is matching any string that contains a valid email address with the limited set of characters
test('matches a valid email address with a limited set of characters for the local part', () => {
  const regex = /^[a-zA-Z0-9!#$%&'*+\/=?^_`{|}~-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
  const string1 = 'jane-doe@example.com';
  const string2 = 'john_smith123@example.com';
  const string3 = 'notanemail@mydomain.com';
  expect(regex.test(string1)).toBe(true);
  expect(regex.test(string2)).toBe(true);
  expect(regex.test(string3)).toBe(true);
});
```

### &emsp;&emsp;<u>***Flags***</u><br>

>&emsp;Flags are a way to modify the behavior of regular expressions when matching emails. They allow the matching to be more flexible and adaptable to different situations. There are several flags that can be useful for email matching, such as `i` to make the matching case-insensitive or `m` for multi-line matching. For example, the pattern `/^[A-Z]+$/i` would match uppercase letters regardless of their capitalization, and the pattern `/^From: .+$/m` would match any line starting with `"From:"`, even if it is on a different line than the start of the string.

>&emsp;The `s` flag enables `"dot all"` mode, which means that the `.` character matches all characters, including line breaks. This is useful when matching email bodies that contain multi-line text. For example, the pattern `/^Dear .+?$/s` would match any text starting with `"Dear"` and ending with the first occurrence of a line break.

>&emsp;Lastly, the `u` flag enables Unicode support, which allows matching of characters from a wide range of languages and scripts. For example, the pattern `/^[\p{L}\p{M}]+$/u` would match any string containing only Unicode letters and combining marks. Overall, flags in regular expressions provide a powerful tool for matching emails with greater accuracy and flexibility.

>&emsp;Here is an example of a Jest Test that would use Flag matching:
```javascript
// regex checks to see if it matches any string that contains a valid email address with case-insensitive matching
test('matches a valid email address with case-insensitive matching', () => {
  const regex = /^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$/i;
  const string1 = 'jane.doe@example.com';
  const string2 = 'JOHN_SMITH123@MYDOMAIN.CO.UK';
  const string3 = 'notanemail@mydomain.com';
  expect(regex.test(string1)).toBe(true);
  expect(regex.test(string2)).toBe(true);
  expect(regex.test(string3)).toBe(true);
});
```

### &emsp;&emsp;<u>***Grouping and Capturing***</u><br>

>&emsp;Using grouping in regular expressions for email matching can help to organize patterns and capture specific portions of an email address. Grouping allows you to specify a sub-pattern within the overall pattern and apply quantifiers and other modifiers to that sub-pattern.

>&emsp;For example, to match email addresses from either `Gmail` or `Yahoo`, you could use grouping to create a sub-pattern for the domain name:&emsp;`/(.*@(gmail|yahoo)\.com)/`<br>

>&emsp;In this pattern, the sub-pattern `(gmail|yahoo)` matches either `"gmail"` or `"yahoo"`, and the overall pattern matches any string that contains the sub-pattern followed by `".com"`. The parentheses around the sub-pattern also capture the entire email address as a matching group, which can be useful for further processing.

>&emsp;Grouping can also be used to extract specific portions of an email address, such as the username or domain name:&emsp;`/^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+\.[a-zA-Z]{2,})$/`<br>

>&emsp;In this pattern, the parentheses around the sub-patterns for the username and domain name capture those portions of the email address as matching groups. This can be helpful for validating or processing the email address in a program or script.

>&emsp;Overall, grouping in regular expressions is a powerful tool for matching emails and other complex patterns, and can help to make the matching more organized and precise.

>&emsp;Here is an example of a Jest Test that would use Grouping and Capturing matching:
```javascript
// regex checks if the first 2 items are numbers / second 2 items are numbers / last 4 items are numbers
test('matches a valid email address with grouping and capturing', () => {
  const regex = /^([a-z0-9._%+-]+)@([a-z0-9.-]+\.[a-z]{2,63})$/i;
  const string1 = 'jane.doe@example.com';
  const string2 = 'JOHN_SMITH123@MYDOMAIN.CO.UK';
  const string3 = 'notanemail@mydomain.com';
  const match1 = string1.match(regex);
  const match2 = string2.match(regex);
  const match3 = string3.match(regex);
  expect(match1[1]).toBe('jane.doe');
  expect(match1[2]).toBe('example.com');
  expect(match2[1]).toBe('JOHN_SMITH123');
  expect(match2[2]).toBe('MYDOMAIN.CO.UK');
  expect(match3[1]).toBe('notanemail');
  expect(match3[2]).toBe('mydomain.com');
});
```

### &emsp;&emsp;<u>***Bracket Expressions***</u><br>

>&emsp;Bracket expressions in regular expressions for email matching can help to match specific sets of characters within a string. These expressions are enclosed in square brackets and can contain a combination of individual characters and character ranges.

>&emsp;For example, to match email addresses that contain only letters, digits, and underscores in the username portion, you could use a bracket expression like this:&emsp;`/^[a-zA-Z0-9_]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/`

>&emsp;In this pattern, the bracket expression `[a-zA-Z0-9_]` matches any individual letter, digit, or underscore character. The `+` quantifier after the bracket expression specifies that one or more of these characters must be present in the username portion of the email address.<br>

>&emsp;Bracket expressions can also be used to match specific ranges of characters. For example, to match email addresses that contain only lowercase letters and digits in the domain name, you could use a bracket expression like this:&emsp;`/^[a-zA-Z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$/`<br>

>&emsp;In this pattern, the bracket expression `[a-z0-9]` matches any lowercase letter or digit, and the `.` character matches a period.<br>

>&emsp;Overall, bracket expressions in regular expressions are a useful tool for matching specific sets of characters within a string, and can help to make the matching more precise and accurate.

>&emsp;Here is an example of a Jest Test that would use Bracket Expression matching:
```javascript
// regex checks to see if ONLY lowercase letters and numbers are in the domain name
test('matches a valid email address with only lowercase letters and digits in the domain name', () => {
  const regex = /^[a-z0-9._%+-]+@[a-z0-9.-]*[a-z0-9]+\.[a-z]{2,}$/i;
  const string1 = 'jane.doe@example.com';
  const string2 = 'john_smith123@mydomain.co.uk';
  const string3 = 'notanemail@ButUppercase.com';
  expect(regex.test(string1)).toBe(true);
  expect(regex.test(string2)).toBe(true);
  expect(regex.test(string3)).toBe(false);
});
```

### &emsp;&emsp;<u>***Greedy and Lazy Match***</u><br>

>&emsp;In regular expressions for email matching, greedy and lazy matching can be used to control how the regex engine matches a pattern within a string. Greedy matching is the default behavior, in which the regex engine matches as many characters as possible that satisfy the pattern. In contrast, lazy matching matches as few characters as possible that satisfy the pattern.

>&emsp;For example, in the regex pattern `/.+/`, the `+` quantifier is `greedy`, which means it matches one or more of any character. This can result in the entire string being matched, which may not be the desired behavior for email matching.

>&emsp;To make the matching lazy, you can add a question mark `?` after the quantifier. For example, the regex pattern `/.+?@/` matches one or more of any character, but stops matching as soon as it encounters the `@` symbol. This is useful for matching the username portion of an email address before the domain name.

>&emsp;Lazy matching can also be used with specific character classes or sub-patterns. For example, the regex pattern `/[0-9]+?/` matches one or more digits, but stops matching as soon as it encounters a non-digit character.

>&emsp;Overall, greedy and lazy matching are important concepts to understand when working with regular expressions for email matching, as they can affect the precision and accuracy of the pattern matching.

>&emsp;Here is an example of a Jest Test that would use Greedy and Lazy matching:
```javascript
// regex checks to see the shortest possible match
test('matches the email address using the lazy quantifier', () => {
  const regex = /<.*?>/;
  const string = '<p>jane.doe@example.com</p><p>john_smith123@mydomain.co.uk</p>';
  const match = string.match(regex)[0];
  expect(match).toBe('<p>');
});
// regex checks to see the longest possible match
test('matches the email address using the greedy quantifier', () => {
  const regex = /<.*>/;
  const string = '<p>jane.doe@example.com</p><p>john_smith123@mydomain.co.uk</p>';
  const match = string.match(regex)[0];
  expect(match).toBe('<p>jane.doe@example.com</p><p>john_smith123@mydomain.co.uk</p>');
});
```

### &emsp;&emsp;<u>***Boundaries***</u><br>

>&emsp;In regular expressions for email matching, boundary matches are used to specify the exact beginning and end of a pattern within a string. This can be useful for matching email addresses within longer blocks of text or when ensuring that a pattern matches only the desired portion of a string.

>&emsp;Two common boundary matches are the caret `^` symbol and the dollar sign `$` symbol. The caret symbol matches the beginning of a line or string, while the dollar sign matches the end of a line or string.

>&emsp;For example, the regex pattern `/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/` matches a valid email address that starts with one or more letters, digits, periods, underscores, percent signs, plus signs, or hyphens, followed by an `@` symbol, then a domain name containing letters, digits, periods, and hyphens, and ending with a top-level domain of two or more letters. The caret symbol at the beginning and the dollar sign at the end ensure that the pattern matches only the entire email address, and not any additional characters before or after it in the string.

>&emsp;Another example is the regex pattern `/^Dear .+,$/m,` which matches any line that starts with the text `"Dear "` and ends with a comma, in a multi-line string. The m flag enables multi-line matching, and the caret and dollar sign symbols ensure that the pattern matches only lines that start with `"Dear "` and end with a `,` comma.

>&emsp;Overall, using boundary matches in regular expressions for email matching can help to ensure that the pattern matches only the desired portion of a string and can make the matching more precise and accurate.

>&emsp;Here is an example of a Jest Test that would use Boundary matching:
```javascript
// regex checks to see if the email starts at a word boundary at jane
test('matches email address that starts with "jane"', () => {
  const regex = /\bjane\S*@/;
  const string1 = 'jane.doe@example.com';
  const string2 = 'john.smith@example.com';
  expect(regex.test(string1)).toBe(true);
  expect(regex.test(string2)).toBe(false);
});
```

### &emsp;&emsp;<u>***Back-references***</u><br>

>&emsp;In regular expressions for email matching, back-references are used to capture and reuse a matched pattern within the same regular expression. This can be useful for matching email addresses that have repeated patterns or for validating that two portions of an email address match.

>&emsp;To create a back-reference, you can use parentheses to capture a sub-pattern and then reference that sub-pattern later in the regex using a backslash followed by the capturing group number. For example, the regex pattern `/(\w+)\.(\w+)\1@\2\.\w+/` matches an email address that has the same two words before and after the `@` symbol, separated by a period. The `\1` reference matches the same text as the first capturing group, which is the first word, and the `\2` reference matches the same text as the second capturing group, which is the domain name.

>&emsp;Back-references can also be used to validate that two portions of an email address match, such as the username and domain name. For example, the regex pattern `/^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+\.[a-zA-Z]{2,})$/` matches a valid email address with one or more letters, digits, periods, underscores, percent signs, plus signs, or hyphens in the username portion, and a domain name containing letters, digits, periods, and hyphens. The parentheses capture the username and domain name portions as separate groups, which can be referenced later in the pattern to ensure that the two portions match.

>&emsp;Overall, using back-references in regular expressions for email matching can help to make the matching more precise and can be useful for matching email addresses that have repeated patterns or for validating that two portions of an email address match.

>&emsp;Here is an example of a Jest Test that would use Back-Reference matching:
```javascript
// the first capturing group captures the local part of the email address, and the second capturing group captures the domain name, which is split into two parts by the dot separator. The back-references are used to refer to these capturing groups in the test, so that the test can verify that the correct parts of the email address have been captured
test('matches a valid email address with back-references', () => {
  const regex = /^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+)\.([a-zA-Z]{2,})$/;
  const string1 = 'jane.doe@example.com';
  const string2 = 'john.smith@example.co.uk';
  const string3 = 'notanemail.com';
  const match1 = string1.match(regex);
  const match2 = string2.match(regex);
  const match3 = string3.match(regex);
  expect(match1[1]).toBe('jane.doe');
  expect(match1[2]).toBe('example');
  expect(match1[3]).toBe('com');
  expect(match2[1]).toBe('john.smith');
  expect(match2[2]).toBe('example.co');
  expect(match2[3]).toBe('uk');
  expect(match3).toBe(null);
});
// regex checks to see if the string does not meet the requirements of a valid email address
test('does not match an invalid email address with back-references', () => {
  const regex = /^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+)\.([a-zA-Z]{2,})$/;
  const string = 'notanemail';
  const match = string.match(regex);
  expect(match).toBe(null);
});
```

### &emsp;&emsp;<u>***Look-ahead and Look-behind***</u><br>

>&emsp;In regular expressions for email matching, look-ahead and look-behind assertions are used to match patterns that are preceded or followed by a specific set of characters or patterns, without including those characters or patterns in the match itself. These assertions can be useful for matching email addresses that are surrounded by certain characters or that contain specific patterns before or after the address.

>&emsp;Look-ahead assertions are specified using the `(?=...)` syntax, and match patterns that are followed by a specific set of characters or patterns. For example, the regex pattern `/\b\w+(?=@example\.com)/` matches any word that is followed by the text `@example.com` and is surrounded by word boundaries. This can be useful for matching email addresses that end in a specific domain name.

>&emsp;Look-behind assertions are specified using the `(?<=...)` syntax, and match patterns that are preceded by a specific set of characters or patterns. For example, the regex pattern `/(?<=Dear )\w+/` matches any word that is preceded by the text `Dear` and is not included in the match. This can be useful for matching the username portion of an email address that is preceded by a specific text pattern.

>&emsp;Look-ahead and look-behind assertions can also be combined to match more complex patterns. For example, the regex pattern `/(?<=From: )\w+(?=.*@example\.com)/` matches any word that is preceded by the text `From:` and is followed by the text `@example.com`, but does not include either of those patterns in the match. This can be useful for matching email addresses in specific contexts, such as within a line that starts with `"From: "`.

>&emsp;Overall, using look-ahead and look-behind assertions in regular expressions for email matching can help to match more complex patterns and make the matching more precise and accurate.

>&emsp;Here is an example of a Jest Test that would use Look-Ahead And Look-Behind matching:
```javascript
// The regex pattern is looking ahead of the @ symbol and the looking behind the . for 2 or more letters to complete the email
test('matches a valid email address with look-ahead and look-behind', () => {
  const regex = /(?<=@)[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}(?=$)/;
  const string1 = 'jane.doe@example.com';
  const string2 = 'john_smith123@mydomain.co.uk';
  const string3 = 'notanemail@mydomain';
  expect(regex.test(string1)).toBe(true);
  expect(regex.test(string2)).toBe(true);
  expect(regex.test(string3)).toBe(false);
});
```

### &emsp;&emsp;<u>***Author***</u><br>

>&emsp;James Kelly<br>
>&emsp;Full Stack Web Developer / UTA BootCamp Student<br>
>&emsp;[![James Kelly GitHub](https://img.icons8.com/plasticine/100/null/github.png)](https://github.com/jk377y)<br>