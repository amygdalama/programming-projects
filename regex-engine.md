# Construct a Simple Regular Expression Engine

By [David Branner](https://github.com/brannerchinese)

Without using tools that (transparently or not) already contain a regex implementation, build a tool to take an input string `s` and a regex pattern `p`, and tell whether the pattern matches the whole string or not. The two main models are "standard" regex, such as the flavor implemented in Perl and many other programming languages, and "globbing", a simpler system implemented on the Unix command line.

## 1. Standard Regex
#### 1a. Constructions to handle, at a minimum

*    any characters explicitly named
*    `.` any character
*    `*` the foregoing, zero or more times (Kleene star)

#### 1b. Other standard regex constructions to handle, optionally

*   `[abc]` any character from among a, b, and c
*   `[^abc]` any character excluding a, b, or c
*   `|`  disjunction: either everything before the pipe (back to the beginning  of the string or the nearest previous pipe) or else everything after the  pipe (up to the end of the string or the next successive pipe)
*   It would be simplest to avoid dealing with parenthesis-delimited groups at this time, but try it if you like.

## 2. Another Model: Unix Shell Globbing
#### 2a. Basic functionality: single characters

*   any characters explicitly named
*   `?` any character
*   `*` zero or more characters (not Kleene star)

#### 2b. More complicated character sets

*   `[abc]` any character from among a, b, and c
*   `[!abc]` or `[^abc]` any character excluding a, b, or c

## 3. Finally

Please be sure to include a good README, describing how to install and use your code.

## 4. Ideas for further tasks

There are a variety of ways to implement a regex engine -- if you have time, try more than one with the same functionality. Compare their time and space complexity in the write-up in your README.

## 5. Resources

*   Jan Goyvaerts, "[How a Regex Engine Works Internally](http://www.regular-expressions.info/engine.html)" and subsequent pages on the site. Goyvaerts documents the fine details of many regex implementations.
*   Russ Cox, "[Implementing Regular Expressions](http://swtch.com/%7Ersc/regexp/)".
*   Wayne O. Cochran, "[Roll Your Own Regular Expression Engine](http://ezekiel.vancouver.wsu.edu/%7Ecs317/archive/projects/grep/grep.pdf)".
*   Mendel Cooper, "[Advanced Bash-Scripting Guide: An in-depth exploration of the art of shell scripting. Chapter 19. Regular Expressions](http://www.faqs.org/docs/abs/HTML/globbingref.html)".