#go 

[[ASCII]] (American Standard Code for Information Interchange). There, we used 7 bits to represent 128 characters, including upper and lowercase English letters, digits, and a variety of punctuations and device-control characters. 

Due to this character limitation, the majority of the population is not able to use their custom writing systems. To solve this problem, [[Unicode]] was invented. Unicode is a superset of ASCII that contains all the characters present in today’s world writing system. It includes accents, diacritical marks, control codes like tab and carriage return, and assigns each character a standard number called “Unicode Code Point”, or in Go language, a “Rune”. 

The Rune type is an alias of int32. 

**Important Points:**
-   Always remember, a string is a sequence of bytes and not of a Rune. A string may contain Unicode text encoded in UTF-8. But, the Go source code encodes as UTF-8, therefore, no need to encode the string in UTF-8.
-   UTF-8 encodes all the Unicode in the range of 1 to 4 bytes, where 1 byte is used for ASCII and the rest for the Rune.
-   ASCII contains a total of 256 elements and out of which, 128 are characters and 0-127 are identified as code points. Here, code point refers to the element which represents a single value.