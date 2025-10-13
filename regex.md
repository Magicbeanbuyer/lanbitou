# metacharacters
`[]`: used for specifying a character class, which is a set of characters that you wish to match. 
- characters can be listed individually, e.g. `[abc]` will match any of the characters `a`, `b`, or `c`.
- or characters can be listed a range of characters by a `'-'`. e.g., `[abc]` will match any of the characters `a`, `b`, or `c`.

Metacharacters (except `\`) are **not** active inside classes. For example, `[abc$]` will match any of the characters `'a'`, `'k'`, `'m'`, or `'$'`.

A leading `'^'` in a class means _complementing_ the set. E.g. `[^5]` will match any character except `'5'`. If the caret appears elsewhere in a character class, it does not have special meaning. For example: `[5^]` will match either a `'5'` or a `'^'`.
