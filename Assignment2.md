
### [Assigment 1](https://krishna-waidande.github.io//) | [Gradle Installation](https://krishna-waidande.github.io//gradle) | [Apache Tomcat Installation](https://krishna-waidande.github.io//tomcat) | [Java Indentation](https://krishna-waidande.github.io/JavaIndentation)


# Assignment 2  | [Things learned](https://krishna-waidande.github.io//things_learned2)

### So My second assignment was about count no of words from given text file.

> Again i have to test that code with larger file size.
 
### Count the occurrences of every word in an input file

For example, 

> “Apple is healthy food. Soda is junk food”. 


> Apple: 1 , is: 2 , healthy: 1 , junk: 1 , food: 2

+ ### First Approach


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

But if you know collection object wont exceed size limit. means it will take less memory you can go for this approach.

```java


import java.util.*;
import java.io.*;

public class word {

	public word() {
	}

	public static void main(String[] args) throws IOException{
		long startTime = System.nanoTime();
		
		File f= new File("1gb.txt");
		
		FileReader filereader = new FileReader("1gb.txt");
		FileWriter filewriter = new FileWriter("testout.txt");

		BufferedReader buffreader = new BufferedReader(filereader);
		BufferedWriter buffwriter = new BufferedWriter(filewriter);

		HashMap<String,Integer> hm= new HashMap();
		
		long filesize= f.length();
		char cbuf[] =new char[3999990];
		long n= filesize % 3999990;
		String temp_str;
		int i=0;
		do {
			br.read(cbuf, 0, (int)n);
			filesize = filesize - n;
			n = 3999990;
			temp_str = new String(cbuf);	

			String[] words = temp_str.split("[\\s@&.?$+-;=|\\<|\\>|\\[|\\]|\\/|@|\\'|\\(|\\)]+"); 
			while (i < words.length) {  
			    String s = words[i]; 
			    if(hm.containsKey(s)) {
			       hm.put(ab,hm.get(s)+1);
			    } else {
			 	hm.put(s,1);
			    }
			    i++;
			}//innerwhile
			i=0;
		}while(filesize>0);//while
				
		Set<String> keyset = hm.keySet();		//got all keys i.e words from collection object.
		int size = keyset.size();
		Iterator<String> it= keyset.iterator();
		while(it.hasNext()) {			//writing data to output file		
		    String key = it.next().toString();
		    String value = hm.get(key).toString();
		    buffwriter.write(key+" -> "+value+"\n");
		}
		br.close();
		buffer.close();
		fr.close();
		fw.close();
				
		long endTime   = System.nanoTime();
		long totalTime = (endTime - startTime)/1000000000;
		System.out.println("execution time for program="+totalTime+" secs");
		System.out.println("execution ends = "+ size);
	}
}
```

+ ### SECOND APPROACH


so then after i strted to think for another approach.

then afterwords. next approach come to my mind was we can serialise the collection object.

serialization means storing the current state of object into file . and vise varsa means retriving orignal object from file is called as deserialization.

but it was very complex to implement. and in this approach also my whole object was coming into memory . so this was a wrong approach to solve this problem.

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


+ ### THIRD APPROACH

So later after thinking we come up with solution that we will read the file in chunk by chunk and split that chunk into words and start storing each word into database.
and while inserting word only check whether that word is present there or not. if a word is present increment the count of word in database.

This was a correct and good approach to solve this type of problem.

```
MAIN()

WHILE 
	READ THE FILE BY FIXED CHUNK SIZE.
	SPLIT THE CHUNK WORD BY WORD.
	PUT THE WORDS IN THE ARRAY OF COLLECTION OBJECT.

	FUNCTION CALL TO UPDATE_DB()

LOOP UNTIL END OF FILE. 
READ THE NEXT CHUNK(REPEAT WHILE).




FUNCTION UPDATE_DB()
	
	WHILE
	READ THE ARRAY OF COLLECTION OBJECT 

	CHECK WHETHER THE WORD(COLLECTION OBJECT) IS PRESENT IN THE DATABASE TABLE.

	IF PRESENT
	  UPDATE THE COUNT IN DB.
	ELSE
	  INSERT THE WORD IN DB.

	END WHILE.	

	RETURN TO MAIN().

END UPDATE_DB.
 ```

#### NOTE:


#### COLLECTION OBJECT WILL BE STORED IN <KEY,VALUE> PAIR WHERE KEY = WORD AND VALUE = COUNT.


### above solution was correct for this problem but our mentor told us to come with some different solution.

+ ### Forth Approach

so i start to think on a different solution . but nothing come to my mind. because i was wondoring how I am going to store large data into memory without using database. 

so later my mentor gave me suggestion try to solve this problem using cacheing (EHCACHE).

so I started to read about how we can implement caching mechanism in our code.
In java there are many APIs available to implement caching mechanism in java.

I read documentation of ehcache available on their official site [EHCACHE](http://www.ehcache.org/)

## so read learn things section in my blog to get more information about ehcache.

> before running this code please read [learned things](https://krishna-waidande.github.io//things_learned2) to configure ehcache.
without configuration of ehcache code won't work.

```java

package Assisn;
import net.sf.ehcache.Cache;
import net.sf.ehcache.CacheManager;
import net.sf.ehcache.Element;
import java.util.*;
import java.io.*;

public class word {

	public word() {
	}
	
	public static void storeToCache(String str,Cache cache)
	{
		StringTokenizer string_token = new StringTokenizer(str," ");								//split chunk by space to get individual words.
		
		while (string_token.hasMoreTokens()) {  
         		String str_word = string_token.nextToken();
			if(cache.isKeyInCache(str_word)) {	//if word is in cache just increment word count.
				Element el = cache.get(str_word);
				cache.put(new Element(str_word ,Integer.parseInt(el.getObjectValue().toString())+1));
			} 
			else {
				cache.put(new Element(str_word,1));	//New word is inserted in cache and word count is 1
			}
		}//while
	}
	public static void main(String[] args) throws IOException{
		long startTime = System.nanoTime();
		
		File file= new File("demo1.txt");
		FileReader filereader = new FileReader("demo1.txt");
		FileWriter filewriter = new FileWriter("output.txt");
		BufferedReader buffreader = new BufferedReader(filereader);
		BufferedWriter buffwriter = new BufferedWriter(filewriter);
		
		CacheManager cachemanager = CacheManager.newInstance("src/ehcache.xml");
		//give path where you will keep ehcache.xml file I put this file in src folder.
		Cache cache = cachemanager.getCache("mycache1");
		cachemanager.clearAll();
				
		long filesize = file.length();
		char cbuf[] = new char[4999990];				//to store chunk
		String temp_str;
		long remainder= filesize % 4999990;		
		int index;
		do {
			buffreader.read(cbuf, 0, (int)remainder);		// reading by chunk size of n bytes
			filesize = filesize - remainder;
			remainder=4999990;
						
			temp_str=new String(cbuf);	
			temp_str=temp_str.replaceAll("[^a-zA-Z0-9]"," ");	//remove special characters.
			word.storeToCache(temp_str , cache);			//function call to storeTocache
		}while(filesize>0);
				
		List keylist = cache.getKeys();					//retrieving all keys present in  the cache
		int size = keylist.size();
		ListIterator iterator = keylist.listIterator();
		while(iterator.hasNext()) {
			String key= iterator.next().toString();
			Element el = cache.get(key);				//getting value according to key.
			String value = el.getObjectValue().toString();
			buffwriter.write(key+" -> "+value+"\n");	//storing key values in text file.
		}
		long memsize = cache.getMemoryStoreSize();
		System.out.println("Data On Memory = "+memsize);
		long disksize=cache.getDiskStoreSize();
		System.out.println("Data On Disk = "+disksize);
				
		cachemanager.clearAll();
		cachemanager.shutdown();
		buffreader.close();
		buffwriter.close();
		filereader.close();
		filewriter.close();
		
		long endTime = System.nanoTime();
		long totalTime = (endTime - startTime)/1000000000;
		System.out.println("execution time for program="+totalTime+" secs");
		System.out.println("getkeys size = "+ size);
	}
}
```



