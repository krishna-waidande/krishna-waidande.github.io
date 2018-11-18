# Basics of computer science 

`Hello Readers`,

This blog is all about some basic concepts in the computer science world which all must be known about it.
you all are using computers right? do you know how computer stores our humaan readable information within it?

Let's start with bit and bytes first.

You may heard these terms in internet speed or storing device like HDD, memory card, pendrives etc..
example : Our internet speed is 1Mbps or 5 Mbps or I have 1TB of HDD.

### What is Bit? 
Bit is a smallest unit of data used to store information in computer. A bit has a single binary value, either 0 or 1.

|0|
---


### Why 0 and 1?


Computer is a electronic digital device madeup by combining different hardwares together.So hardware understands only electronic language that means low or high voltage/current.So to express it we use 0's and 1's.
0 means low voltage and 1 means high voltage.


### What is Bytes? 

The means collection of 8 bits.8 bits form a single byte.

|1|0|0|1|0|0|0|1|
-----------------


### What is the difference between Mbps and MBps?

Mbps means megabits per second. Mb is used in reference to download and upload speeds.

MBps stands for megabytes per second. MB is used in reference to file size, or the amount of data transferred.

So, the difference is between bits and bytes. Yes. 

`1 Byte` = **8 bits** 

This means, 

`1MBps` = **8Mbps** 

That is eight times the difference. This is true for all units mentioning bits and bytes like kbps, gbps, tbps etc.

`1KBps` = **8kbps**

`1GBps` = **8Gbps**

`1TBps` = **8Tbps** 


Now let's dicuss about how computer stores our textual language into machine.

### What is character ?

A character is any letter, number, space, punctuation mark, or symbol that can be typed on a computer.
It takes 1 byte to store a single character. It varies according to the different operating system.


### Why 1 byte?
There are 128 character present so to store 128 characters we need 7 bits to store it. `2^7 = 128`.

So here we need to store the characters on the hardware but machine does not understand character.So for this
we need to encode the characters into machine understandable code.


### What is Encoding ?

Encoding is the process of converting data from one form to another. 
There are several types of encoding, including image encoding, audio and video encoding, and character encoding.


### What's a character encoding?

Words and sentences in text are created from characters. 
Examples of characters include the Latin letter `á` or the Chinese ideograph `請` or the Devanagari character `ह`.


Characters that are needed for a specific purpose are grouped into a character set.
To refer to characters in an unambiguous way, each character is associated with a number, called a `code point.`


Basically, you can visualise this by assuming that all characters are stored in computers using a special code, 
like the ciphers used in [espionage](https://en.wikipedia.org/wiki/Espionage) . A character encoding provides a key to unlock (ie. crack) the code.


It is a set of mappings between the bytes in the computer and the characters in the character set. 
Without the key, the data looks like garbage.


So, when you input text using a keyboard or in some other way, 
the character encoding maps characters you choose to specific bytes in computer memory, 
and then to display the text it reads the bytes back into characters.


So that the text is saved using one of different types of character encoding.

Types of encoding : 

+ `ASCII` :
An encoding for English characters based on 7-bits that are mapped to 128 characters. 
ASCII is an American standard that dates back to the early 1960s. 
It has been changed numerous times throughout its history including an expansion to competing versions of 8-bit ASCII. 
It is extremely limited, even for English, and led to a number of character sets being developed for every language.


+ `Unicode` :

Unicode is an international standard first released in the early 1990s to unify 135 modern and historic languages 
under a common character set. It currently has 128,237 characters that are increased over time. 
Its current maximum is 1,114,112 characters that represents the hexadecimal numbers 0 to 10FFFF. 
Unicode is a standard for a character set and not a character set itself.

+ `UTF-8` :

UTF-8 is a character set that implements Unicode. Despite its name, UTF-8 isn't a static 8-bit encoding but instead is a variable length encoding that uses up to 32 bits. It encodes the most common characters, such as basic numbers and English with 8-bits. This makes it efficient for most data. Another advantage of UTF-8 is that for English, it is identical to ASCII.

+ `UTF-16` 

+ `UTF-32` 














