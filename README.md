# ASSIGNMENT 1


# Reverse the contents of an input file
For example: 

 “hello world 


I am krishagni”

Should be :

 “ingahsirk ma i 


dlrow olleh”.

## First Approach

My first approach for this problem  was reading file from backwards by using fseek function in c.
put file pointer to end of input file and read one one character and print into output file. 



I tried that logic on smaller file size . It works faster so I thought that my approach is coreect.and I got the solution very easyly but when I tested that code for larger file size (eg 500MB, 1GB)then  it took too much time to exeute. It was taking 5 mins to execute 1gb file . than I realise that my code is correct but not efficient one.  



### Advantage 

> Faster for smaller file size.

> Memory requirement was less. 
	      
	      

### Disadvantege 

> Not efficient for larger file size.

## Second Approach

My second appoach was using 2 file pointers . One file pointer at starting of file and another file pointer at end of the file and by swapping first character with last . & again reading next character and reading second last chracter and swapping them with each other.in this way also we can solve the problem . for smaller size files program was running in no time. again for larger file size . this was taking hours to execute. 



### Advantage 

> Faster for smaller size.


> Memory requirement was less.

### Disadvantege 


> Taking too much time for reversing large files.

## Third Approach


Then i started to think about another approach for this problem.


Then third approach come to my mind was reversing file order by using 2 files.for that I decide to read file chunk by chunk . reverse chunk data and store that data into another file. this approach was just reversing the file data line by lines. this was not my required output  so tried to find about how i can prepend new data before old data.


For example :


my name is krishna.


my name is gautham.


Output 


anhsirk si eman ym


mahtuag si eman ym


so while inserting 2nd line i was looking for how can i place my new data at the begining of my file. this was not possible to add data to starting of output file . Because when I tried to do that old data was getting overwritten. so my this approach also failed.




