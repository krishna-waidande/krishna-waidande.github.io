# Assignment 2

So My second assignment was about count no of words from given text file.

Again i have to test that code with larger file size.
 
 Count the occurrences of every word in an input file

For example, 

> “Apple is healthy food. Soda is junk food”. 


> Apple: 1 , is: 2 , healthy: 1 , junk: 1 , food: 2


By Looking at this problem, First approach come to my mind was we can use collection of java.In map interface there is facility to store objects in key value pair.

so I thought, I can put a word as a key and count as a value.

But the problem in my approach was, what if size of collection object increase periodically. then that object may aquire full space of RAM . 

```where can I store object ?``` I cant handle that object into memory.

but later one thought come to my mind. i.e I googled english dictionry word count. so i got that

``` Oxford English Dictionary contains full entries for 171,476 words in current use, and 47,156 obsolete words. To this may be added around 9,500 derivative words included as subentries.```

So after reading this  I feel that all those words can fit into collection object. because that was a finite number . So at most our ```collection object will go upto 10-15 MB.```

but the problem with that solution was what if my text file will contain words other than english words. for exmple 
I can write a marathi word in english so there is possibility of my object can exceed the 10-15 MB size.

My mentor suggested us that a think a appraoch for that file which will contain 4-5gb of words. so our object will occupy the space of all RAM. so in this condition our code wont be able to run .

So this was ```disadvantage of our approach that we cant restrict size of collection object.```
