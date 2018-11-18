# Basics of computer science 

Hello Readers,

What is a bit, what is a byte, what is the difference between bit and byte? How many bits make a byte?

This blog is all about some basic concepts in the computer science world which all must be known about it.

Lets start with bit and bytes first.

You may heard these terms in Internet speed or storing device like HDD, Memory card etc..

Bit : 
Bit is a smallest unit of data used to store information in computer. A bit has a single binary value, either 0 or 1.


Bytes : 


What is character ?

A character is any letter, number, space, punctuation mark, or symbol that can be typed on a computer.
It takes 1 byte to store a single character. It varies according to the different operating system.


Before moving onto char encoding let's see first what does encoding means.

Encoding : Encoding is the process of converting data from one form to another. 
There are several types of encoding, including image encoding, audio and video encoding, and character encoding.

So what's a character encoding?

Words and sentences in text are created from characters. 
Examples of characters include the Latin letter 'á' or the Chinese ideograph '請' or the Devanagari character 'ह'.

Characters that are needed for a specific purpose are grouped into a character set.
To refer to characters in an unambiguous way, each character is associated with a number, called a code point

Basically, you can visualise this by assuming that all characters are stored in computers using a special code, 
like the ciphers used in [espionage](https://en.wikipedia.org/wiki/Espionage) . A character encoding provides a key to unlock (ie. crack) the code.
It is a set of mappings between the bytes in the computer and the characters in the character set. 
Without the key, the data looks like garbage.

So, when you input text using a keyboard or in some other way, 
the character encoding maps characters you choose to specific bytes in computer memory, 
and then to display the text it reads the bytes back into characters.


So that the text is saved using one of different types of character encoding.


Types of encoding : 

1. ASCII :
An encoding for English characters based on 7-bits that are mapped to 128 characters. 
ASCII is an American standard that dates back to the early 1960s. 
It has been changed numerous times throughout its history including an expansion to competing versions of 8-bit ASCII. 
It is extremely limited, even for English, and led to a number of character sets being developed for every language.


2. Unicode :

Unicode is an international standard first released in the early 1990s to unify 135 modern and historic languages 
under a common character set. It currently has 128,237 characters that are increased over time. 
Its current maximum is 1,114,112 characters that represents the hexadecimal numbers 0 to 10FFFF. 
Unicode is a standard for a character set and not a character set itself.

3. UTF-8 :

UTF-8 is a character set that implements Unicode. Despite its name, UTF-8 isn't a static 8-bit encoding but instead is a variable length encoding that uses up to 32 bits. It encodes the most common characters, such as basic numbers and English with 8-bits. This makes it efficient for most data. Another advantage of UTF-8 is that for English, it is identical to ASCII.


4. UTF-16 :

UTF-8 is a character set that implements Unicode. Despite its name, UTF-8 isn't a static 8-bit encoding but instead is a variable length encoding that uses up to 32 bits. It encodes the most common characters, such as basic numbers and English with 8-bits. This makes it efficient for most data. Another advantage of UTF-8 is that for English, it is identical to ASCII.

5. UTF-32 :

UTF-32 is a character set that implements Unicode as a static 32-bit code. Unicode only requires 21-bits to encode its limit of 1,114,112 characters. As such, UTF-32 has a number of leading zeros that pad each code. This is inefficient and all data is smaller in UTF-8 and UTF-16. For English data, UTF-32 is typically about 4 times larger.
















