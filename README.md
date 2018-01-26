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


