# Assignment 2

### So My second assignment was about count no of words from given text file.

> Again i have to test that code with larger file size.
 
### Count the occurrences of every word in an input file

For example, 

> “Apple is healthy food. Soda is junk food”. 


> Apple: 1 , is: 2 , healthy: 1 , junk: 1 , food: 2

### First Approach


By Looking at this problem, First approach come to my mind was we can use ```collection of java.``` Map interface there is facility to store objects in key value pair.

so I thought, I can put a word as a key and count as a value.

But the problem in my approach was, what if size of collection object increase periodically. then that object may aquire full space of RAM . 

```where can I store object ?``` I cant handle that object into memory.

but later one thought come to my mind. i.e I googled english dictionry word count. so i got that

``` Oxford English Dictionary contains full entries for 171,476 words in current use, and 47,156 obsolete words. To this may be added around 9,500 derivative words included as subentries.```

So after reading this  I feel that all those words can fit into collection object. because that was a finite number . So at most our ```collection object will go upto 10-15 MB.```

but the ``problem with that solution was what if my text file will contain words other than english words. for exmple 
I can write a marathi word in english so there is possibility of my object can exceed the 10-15 MB size.``

My mentor suggested us that a think a appraoch for that file which will contain 4-5gb of words. so our object will occupy the space of all RAM. so in this condition our code wont be able to run .

So this was ```disadvantage of our approach that we cant restrict size of collection object.```


# SECOND APPROACH


so then after i strted to think for another approach.

then afterwords. next approach come to my mind was we can serialise the collection object.

serialization means storing the current state of object into file . and vise varsa means retriving orignal object from file is called as deserialization.

but it was very difficult to implement. so these approach also failed .

PSUDO CODE 

> Approach 2 using SERIALIZATION CONCEPT

```
MAIN()

CREATE OUTPUT FILE.
WHILE 
	READ THE INPUT FILE BY FIXED CHUNK SIZE.
	SPLIT THE CHUNK WORD BY WORD.
	PUT THE WORDS IN THE ARRAY OF COLLECTION OBJECT TEMP_COLL.
	
	FUNCTION CALL TO MAKE_SERIALIZE()

LOOP UNTIL END OF FILE. 
READ THE NEXT CHUNK(REPEAT WHILE).


FUNCTION MAKE_SERIALIZE()

WHILE

	DECLARE  COLLECTION OBJECT MASTER_COLL.
	READ THE ARRAY OF COLLECTION OBJECT TEMP_COLL.

	RETRIVE THE CONTENTS OF MASTER_COLL FROM THE OUTPUT FILE.

	CHECK WHETHER THE WORD(COLLECTION OBJECT TEMP_COLL) IS PRESENT IN THE MASTER_COLL.

	IF PRESENT
	  UPDATE THE COUNT IN MASTER_COLL.
	ELSE
	  INSERT THE WORD IN MASTER_COLL.

	WRITE THE MASTER_COLL OBJECT INTO THE OUTPUT FILE.(SERIALIZTION OF OBJECTS)
	CLEAR MASTER_COLL DATA.

	END WHILE.	

	RETURN TO MAIN().

END MAKE_SERIALIZE().
```
