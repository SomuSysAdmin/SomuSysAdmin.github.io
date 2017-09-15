---
type : post
title : 'Understanding Regular Expressions'
tags : [RHCSA, RHCSA mod1, RHCSA chapter2, working with text files, understanding regular expressions, RegEx]
---

Below is a tiny table (which also comes in extremely handy as a cheat-sheet) showing the use of each symbol in a regular expression:

| Character | Definition                               | Example  | Result               |
|-----------|------------------------------------------|----------|----------------------|
| ^         | Start of a string                        | ^abc     | abc, abcdef, abc123  |
| $         | End of a string                          | abc$     | abc, blahabc, 456abc |
| .         | Any character except a newline           | a.c      | abc, aac, a2c        |
| |         | Alteration                               | 1|8      | 1,8                  |
| {...}     | Explicit quantity of preceding character | ab{2}c   | abbc                 |
| [...]     | Explicit set of characters to match      | a[bB]c   | abc, aBc             |
| (...)     | Group of characters                      | (abc){3} | abcabcabc            |
| *         | Null or more of the preceding character  | ab*c     | ac, abc, abbbbbc     |
| +         | One or more of the preceding character   | ab+c     | abc, abbbbc          |
| ?         | Null or one of the preceding character   | ab?c     | ac, abc              |{:.scroll-table}

