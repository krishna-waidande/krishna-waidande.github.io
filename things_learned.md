# Things  Learned 


## FUNCTIONS :


> ## fgets() :-

          this function is used to read string from a file.
          
          if '\n' char is appeared while reading with fgets(). fgets() fails to read further data. so this is disadvatage of 
          
          
> ## fputs() :- 

          this function is used to write our passed string onto destination file.
        


> ## fgetc() :-

        this function reads one character from source file.


> ## fputc() :- 

        this function writes one character to destination file.
        
        

> ## fread() :-

          this function reads a chunk of data from source file.


> ## fwrite() :- 

          this function writes a chunk of data to destination file.

> ## fseek() :-

          this function moves the file pointer to desired  position.
          

> ## sprintf() :-

          sprintf stands for “String print”. Instead of printing on console, it store output on char buffer which are specified in sprintf. 
          eg :-
          
       
          #include<stdio.h>
          int main()
          {
                    char buffer[50];
                    int k=0
                    
                     while (k<5)
                    sprintf(buffer, "file%d.txt",k++);
 
                    printf("\n %s\n ", buffer);
 
                    return 0;
          }
          
         
         o/p of program :- 
          file0.txt
          file1.txt
          file2.txt
          file3.txt
          file4.txt
          
          
      
          
          this above function helped me to generate n no of temp file names dynamically.


+ ### In some versions of my code i was getting some garbage data into my output so one my collegue suggested me that. after declaration of every variable initialize that variable with some value. if i dont do so than there are much more chances of getting garbage in output. 


+ ### Give proper names to every variable. so that our code can be more readable.

+ ### How to debug . In the sense if we are getting some wrong output in that case try to put proper messages in our code & see what values we are getting.





