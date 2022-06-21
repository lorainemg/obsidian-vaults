# Falsehoods Programmers Believe About Plain Text
Creado: 2022-06-21 17:03
Tags: #every-programmer-should-know, #falsehoods, #internalization 
Topic: [[Falsehoods Programmers Believe About Internalization]]

----
### Non-technical

- The Latin alphabet has 26 letters. 
- Ignoring case, the Latin alphabet has 26 letters. 
- Ignoring case and accents, the Latin alphabet has 26 letters. 
- Yes, but ignoring variants, the Latin alphabet has 26 base letters. 
- Seriously, ignoring variants and combinations, the Latin alphabet has 26 **base** letters. 
- Modern English doesn't use any of those except case. 
- *Ignoring foreign names and borrowings,* Modern English doesn't use any of those except case. 
- There's no such thing as "the English/French/German/Spanish/etc. alphabet": they use the Latin alphabet. 
- There's no such thing as "the English alphabet": English uses the Latin alphabet. 
- Accented letters are never used as distinct letters in an alphabet. 
- Ligatures are never used as distinct letters in an alphabet. 
- Digraphs are never used as distinct letters in an alphabet. 
- Trigraphs are never used as distinct letters in an alphabet. 
- Letter variants used in an alphabet always immediately follow their base letter in the alphabetic order. 
- Every alphabet derived from the Latin alphabet puts the base letters in the same order. 
- The alphabet of each language is fixed and unchanging. 
- Latin alphabets are used to write every language. 
- All writing systems are alphabets. 
- All writing systems have at most a few dozen characters. 
- All writing systems have at most a few hundred characters. 
- All writing systems have a fixed inventory of characters. 
- One language won't be written using two or more writing systems.  
- Mutually unintelligible spoken languages can't use a mutually intelligible writing system. 
- Authors won't need to quote text using other writing systems. 
- One mono-lingual text won't contain multiple writing systems. 
- Characters go from left to right in horizontal lines and lines go from top to bottom on a page. 
- Quoted text is always written in the same direction as surrounding text. 

### Technical

- Characters are bytes (or ASCII + code page) 
- Characters are two bytes (or UTF-16 code units). 
- Characters are integers (or Unicode code points). 
- Characters are the basic parts of a writing system (or graphemes). 
- Characters in <*programming language*> are <*one of the above*>.  
- Text files can be opened and processed without an encoding. 
- The encoding of plain text can be guessed. 
- The encoding of plain text can be discovered by examining the text. 
- Text in a database doesn't have an encoding. 
- Text in a database has the same encoding as the rest of the system. 
- Unicode has an elegant and harmonious design, otherwise it wouldn't be the most widely used encoding. 
- All bytes are characters. 
- All sequences of bytes are strings.  
- A code point represents exactly one character. 
- A code point represents at most two or three characters. 
- A code point never represents a whole word, phrase, or sentence. 
- There's a limit to the amount of text which can be represented by one code point. 
- A code point represents at least one whole character. 
- There's a limit to the number of code points needed to represent a whole character.  
- A code point represents a character or part of a character. 
- A code point represents something. 
- Code points are unambiguous about which character they represent. 
- Different code points represent different characters. 
- A character can be represented in one and only one way. 
- Strings with different lengths can't be equal. 
- Text can be processed without normalization. 
- Canonical normalization of text isn't necessary. 
- Compatibility normalization of text isn't necessary. 
- Compatibility normalization fixes all problems with look-alike characters. 
- Concatenating normalized strings results in a normalized string. 
- Changing the case of a normalized string results in a normalized string. 
- Strings don't need to be normalized before changing their case. 
- Text can be processed without a locale. 
- Locale isn't necessary for changing case. 
- Locale isn't necessary for sorting and searching text. 
- Locale isn't necessary for splitting text into characters. 
- Locale isn't necessary for splitting text into words. 
- Locale isn't necessary for line-breaking. 
- Locale isn't necessary to quote text. 
- Locale isn't necessary for punctuation marks. 
- There are two cases: upper-case and lower-case. 
- There's a one-to-one correspondence between upper- and lower-case characters. 
- Only letters have case. 

### Bonus: Regular expressions

- **[a-zA-Z]** will match any letter. 
- **[0-9]** will match any numeral. 
- **[ \t\n\r]** or **\s** will match any whitespace character. 
- **\p{L}** or **\p{Letter}** will match any letter. 
- **\p{Lu}** or **\p{Uppercase_Letter}** will match any uppercase character. 
- **\p{Ll}** or **\p{Lowercase_Letter}** will match any lowercase character.   
- Matching the Unicode **General_Category** property is the right thing to do.   

## Referencias