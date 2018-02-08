# ASSIGNMENT 1  [ASSIGNMENT2](https://krishna-waidande.github.io//Assignment2) [THINGS LEARNED](https://krishna-waidande.github.io//things_learned)     


# Reverse the contents of an input file
For example:

 “hello world


I am krishagni”

Should be :

 “ingahsirk ma i


dlrow olleh”.

**test your code with larger file size too. eg- 1GB , 5GB etc **

+ ## First Approach

My first approach for this problem  was reading file from ```backwards``` by using ```fseek()``` function in c.
put file pointer to end of input file and read one one character and print into output file.



I tried that logic on smaller file size . It works faster so I thought that my approach is coreect.and I got the solution very easyly but when I tested that code for larger file size (eg 500MB, 1GB) then  it took too much time to exeute. It was taking ```5 mins to execute 1gb file.``` than I realise that my code is correct but not efficient one. 





> Version 1.0

```c

#include<stdio.h>
#include<stdlib.h>
int main()
{

	int size,n;
   	FILE *fp,*fp1;
 	char c;
	
  	if ((fp = fopen("input.txt","r")) == NULL){
       printf("Error! opening file");
	}

	fp1= fopen("output.txt","w");

	fseek(fp, -2, SEEK_END);
	size=ftell(fp);

	while(n!=0)
	{
		c=fgetc(fp);
		fputc(c,fp1);
		fseek(fp,-2,SEEK_CUR);
		n=ftell(fp);
	}
	fclose(fp);
	fclose(fp1);
	return 0;	
}

```


### Advantage

> Faster for smaller file size.

> Memory requirement was less.
         
         

### Disadvantege

> Not efficient for larger file size.



+ ## Second Approach

My second approach was using 2 file pointers. **One file pointer at starting of file and another file pointer at end of the file and by swapping the first character with last. & again reading next character and reading second last character and swapping them with each other**.in this way also we can solve the problem . for smaller size files program was running in less time. but when i tested for larger file size. This was taking hours to execute.

> ### Logic : Swapping between starting and ending characters.

> Version 1.1


```c

#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
void main()
{

	int s,n,p;
  	 FILE *fp,*fp2;
 	char c,d,t;

	if ((fp = fopen("input.txt","r+")) == NULL)
	{
       		printf("Error! opening file");
	}
	fp2=fopen("output.txt","r+");
		
	struct stat st;
	stat("demo2.txt", &st);
  	n=st.st_size;

	fseek(fp2,-2,SEEK_END);

	p=n/2;
	s=0;
	while(s<p)
	{
		c=fgetc(fp);
		d=fgetc(fp2);
		t=c;
		c=d;
		d=t;
		fseek(fp,-1,SEEK_CUR);
		fseek(fp2,-1,SEEK_CUR);
		fputc(c,fp);
		fputc(d,fp2);
		fseek(fp2,-2,SEEK_CUR);
		s++;
	}
	
	fclose(fp);
	fclose(fp2);
	
}
```



### Advantage

> Faster for a smaller size.


> Memory requirement was less.

### Disadvantege


> Taking too much time for reversing large files.

+ ## Third Approach


Then I started to think about another approach to solve this problem.


Then third approach came to my mind was reversing file order by using 2 files.for that I decide to **read file chunk by chunk. reverse chunk data and store that data into another file. this approach was just reversing the file data line by lines. this was not my required output so tried to find  how I can prepend new data before old data.**


> Version 1.3

```c

#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>

void rev(char c[])
{
	int n,n1;
	int i=0,j;
	char t,k;
	FILE *f,*fp;
	
	n=strlen(c);
	n=n-1;
	n1=n;
	
	while(i<n)
	{
		t=c[i];
		c[i]=c[n];
		c[n]=t;
		i++;
		n--;
	}

	f=fopen("output.txt","a");
	fwrite(c,1,n1+1,f);
	fclose(f);
}
int main()
{

	int n,n1,k;
  	 FILE *fp,*fp1;
 	char c[1024];

  	if ((fp = fopen("input.txt","r")) == NULL)
	{
       		printf("Error! opening file");
     	}

	struct stat st;
	stat("input.txt", &st);
  	n=st.st_size;
	printf("%d",n);

	if(n<=1024)
	{
		fread(c, 1, n, fp);
		rev(c);
	}
	else
	{
		n1=1024;
		while(n>0)
		{
			fread(c, 1, n1, fp);
			rev(c);
			n1=n%1024;
			n=n/1024;
		}
	}
	
	fclose(fp);
	return 0;	
}

```


> **For example :**


my name is krishna.


my name is gautham.


> **Output**


anhsirk si eman ym


mahtuag si eman ym

**i am getting wrong output**

> **Required Output is**

mahtuag si eman ym


anhsirk si eman ym



so **while inserting 2nd line I was looking for how can I place my new data at the beginning of my file. this was not possible to add data to starting of the output file. Because when I tried to do that old data was getting overwritten. so my this approach also failed.**


+ ## Fourth Approach


So another approach came to my mind was we can solve this problem by using **Tower of Hanoi algorithm.** By using that algorithm we were getting right output,but for larger files that algorithm was taking too much time to execute. This approach was also not correct to solve this problem.


> Version 1.4


```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>

int flag=0;

void append()
{
	int n,n1;
  	 FILE *fp1,*fp2;
 	char c[1024];

  	if ((fp1 = fopen("demo11.txt","r")) == NULL)
	{
       		printf("Erro! opening file");

     	}
	
	fp2=fopen("demo7.txt","a");

	struct stat st;
	stat("demo11.txt", &st);
  	n=st.st_size;
	
	if(n<1024)
	{
		fread(c,1,n,fp1);
		fwrite(c,1,n,fp2);
	}
	else
	{
		n1=1024;
		while(n>0)
		{
			if(n/1024)
			fread(c,n1,1,fp1);
			else
			{
				n1=n%1024;
				fread(c,n1,1,fp1);

			}
			fwrite(c,n1,1,fp2);
			n=n-1024;
		}
	}
	fclose(fp1);
	fclose(fp2);

}

void moveto1()
{
	int n,n1;
  	 FILE *fp1,*fp2;
 	char c[1024];

  	if ((fp1 = fopen("demo7.txt","r")) == NULL)
	{
       		printf("Erro! opening file");

     	}
	fp2=fopen("demo11.txt","w");

	struct stat st;
	stat("demo7.txt", &st);
  	n=st.st_size;
	
	if(n<1024)
	{
		fread(c,1,n,fp1);
		fwrite(c,1,n,fp2);
	}
	else
	{
		n1=1024;
		while(n>0)
		{
			if(n/1024)
			fread(c,n1,1,fp1);
			else
			{
				n1=n%1024;
				fread(c,n1,1,fp1);

			}
			fwrite(c,n1,1,fp2);
			n=n-1024;
		}
	}
	fclose(fp1);
	fclose(fp2);

}
void rev(char c[])
{
	FILE *fp1,*fp2;	
	int n,n1;
	int i=0,j;
	char t;
	
	n=strlen(c);
	n=n-6;
	c[n]='\0';
	n=n-1;
	
	while(i<n)
	{
		t=c[i];
		c[i]=c[n];
		c[n]=t;

		i++;
		n--;
	}

	if(flag==0)
	{
		fp1=fopen("demo11.txt","w");
		fputs(c,fp1);
		fclose(fp1);
		flag=1;
	}
	if(flag==1)
	{
		fp2=fopen("demo7.txt","w");
		fputs(c,fp2);
		fclose(fp2);
		append();
		moveto1();
	}	
}
int main()
{

	int n,n1;
  	 FILE *fp;
 	char c[1024];

  	if ((fp = fopen("input.txt","r")) == NULL)
	{
       		printf("Erro! opening file");

     	}

	struct stat st;
	stat("input.txt", &st);
  	n=st.st_size;
	printf("%d",n);
	
	if(n<1024)
	{
		fread(c,1,n,fp);
		rev(c);

	}
	else
	{
		n1=1024;
		while(n>0)
		{
			if(n/1024)
			{
				fread(c,n1,1,fp);
				
			}
			else
			{
				n1=n%1024;
				fread(c,n1,1,fp);

			}
			rev(c);
			n=n-1024;
		}
	}
	
	fclose(fp);
	
	return 0;	
}


```



DISADVANTAGES
 

> More read-write operations.

> More execution time.

+ ## Fifth Approach


We can **create n temp files and store 1 chunk in one temp file. In this way, we will read the whole file chunk by chunk and store that all data in temp files in reverse order so that while reading from temp files we can read the data from the last file into an output file. In this way, we can read k,k-1,k-2th & so on files into our output file.and after reading all temp files I deleted those files dynamically.**
by using this approach I get required output.


so while coding for this approach my first thought was how can i create temp files in c . 2nd pronblem was how can I generate unique n no of file names. so after reading on blogs i found that using ``` sprintf() ``` in c we can generate n no of filenames so this function help me to to give filenames at runtime.

so in this way i started coding for this approach.


> Version 1.5

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include<errno.h>

int k=0;

void rev(char c[])
{
	FILE *fp=NULL;	
	int n=0,n1=0;
	int i=0,j=0;
	char t='\0';
	char f[15]={NULL};

	n=strlen(c);
	n=n-2;
	c[n]='\0';
	n=n-1;
	
	while(i<n)
	{
		t=c[i];
		c[i]=c[n];
		c[n]=t;
		i++;
		n--;
	}
	sprintf(f,"%d.txt",k++);
	fp=fopen(f,"w");
	fputs(c,fp);
	fclose(fp);
}
void append(int k)
{
	FILE *fp=NULL,*fp2=NULL;
	char f[11]={NULL};
	char c[2999990]={NULL};
	int size=0;
	
	sprintf(f,"file%d.txt",k);
	
	fp2=fopen("demo1.txt","a");
	
	struct stat st;

	stat(f, &st);
  	size=st.st_size;
	//printf("%d",size);	
	

	fp=fopen(f,"r");
	if(size<2999990)
	{
	fread(c,size,1,fp);
	c[size]='\0';
	fputs(c,fp2);
	}
	else
	{
		
		fread(c,2999990,1,fp);
		c[2999990]='\0';
		fputs(c,fp2);
	}
	
	fclose(fp);
	fclose(fp2);

}
void delete(int k)
{
	char f[11];
	sprintf(f,"file%d.txt",k);
	unlink(f);

}

int main()
{

	long n=0,n1=0,i=0,n2=0;
  	FILE *fp=NULL,*fp2=NULL;
	char c[2999990]={NULL};
	
	if ((fp = fopen("5gb.txt","r")) == NULL)
	{
       		printf("Erro! opening file");

     	}

	struct stat st;
	stat("5gb.txt", &st);
  	n=st.st_size;
	printf("%d",n);
	
	if(n<2999990)
	{
		fread(c,n,1,fp);
		rev(c);

	}
	else
	{
		n1=2999990;
		n2=n1-1;
		while(n>n2)
		{
			fread(c,n1,1,fp);
			rev(c);
			n=n-2999990;
			
			
		}
			c[n]='\0';
			fread(c,n,1,fp);
			rev(c);
	}
	
	fp2=fopen("demo1.txt","w");

	for(i=k-1;i>=0;i--)
	append(i);

	for(i=k-1;i>=0;i--)
	delete(i);

	fclose(fp);
	return 0;	
}

```

after i finished the code. i saw that ```my code is not readable.``` so again i tried to **give proper names to my variables. do commentting in code.** so that anyone can identify what each line is doing in my code.

Afterwards I tested this code for different file size. It was efficient upto some extent.but again i realise that , code can become more effecient if i reduce the no of variables used and if statments from  my code. **My mentor suggested me that less no of variables and condition statements makes code more clean and chances of any bugs reduces.**

so tried to modified my code in such a way that it won't contain more no of variables and if statements it took me some time to think logic in that way. but in some time I got the answer for my problem.
in this way i made a more effecient and much more readable code.



> Version 1.6


```c

#include<stdio.h>
#include<string.h>
#include <sys/stat.h>
#include<errno.h>

int temp_file_num = 0;

void reverse_buffer(char buffer[])
{
	FILE *write_file_pointer = NULL;	
	int i=0,j=0;
	char temp_file[15] = {NULL},rev_buffer[3999990]={NULL};
	
	for(i=0,j= strlen(buffer)-1 ; j >= 0 ; i++,j--)
	rev_buffer[i]=buffer[j];
	
	sprintf(temp_file,"%d.txt",temp_file_num++);		//generate temp file name.
	write_file_pointer = fopen(temp_file,"w");		//creating temp file.
	fputs(rev_buffer,write_file_pointer);			//writing buffer to temp file.
	fclose(write_file_pointer);				//close temp file.

	
}

void file_append(int temp_file_num)
{
	FILE *read_file_pointer = NULL,*write_file_pointer = NULL;
	char temp_file[11] = {NULL};
	char buffer[3999990] = {NULL};
	int file_size = 0;
	
	sprintf(temp_file,"%d.txt",temp_file_num);
	
	write_file_pointer = fopen("output1.txt","a");		//opening output file in append mode
	read_file_pointer = fopen(temp_file,"r");		//opening temp file to read data

	 fread(buffer, 3999990 , 1 , read_file_pointer);	//reading chunk 
	 buffer[3999990]='\0';
	   
	fputs(buffer,write_file_pointer);			//appending to ouput file.
		
	fclose(read_file_pointer);

	fclose(write_file_pointer);

}
void file_delete(int temp_file_num)			
{
	char temp_file[11]={NULL};
	
	sprintf(temp_file,"%d.txt",temp_file_num);
	
	unlink(temp_file);
}

int main()
{

	long file_size=0,index=0,n=0;
	
	FILE *file_pointer=NULL, *read_file_pointer=NULL;
	char buffer[3999990]={NULL};
	char temp_file[15]={NULL};
	
	file_pointer = fopen("1gb.txt","r");
	
	struct stat file_info;
	stat("1gb.txt", &file_info);
  	file_size=file_info.st_size;
	printf("Size of input file: %ld\n",file_size);		//retriving input file size.

	n= 3999990 % file_size;
	
	do							//reading input file chunk by chunk file.
	{
             fread(buffer,n,1,file_pointer);
	     reverse_buffer(buffer);
	     file_size=file_size-n;
	     n=3999990;

	 }while(file_size>0);

	fclose(file_pointer);
	
	file_pointer = NULL;

	file_pointer = fopen("output1.txt","w");

	sprintf(temp_file,"%d.txt",temp_file_num - 1);		//retriving filename.

	read_file_pointer = fopen(temp_file,"r");		//open that temp file in read mode.

	stat(temp_file, &file_info);
  	file_size = file_info.st_size;				//retriving file size.

	fread(buffer, file_size , 1 , read_file_pointer);	//read in buffer
  	buffer[file_size]='\0';
	
	fputs(buffer, file_pointer);				//write to ouput file.
	
	fclose(file_pointer);
	fclose(read_file_pointer);				//closing opened files.


	for(index = temp_file_num - 2 ; index >=0 ; index--)	//for appending
	file_append(index);

	for(index = temp_file_num - 1 ; index >=0 ; index--)	//for deleting files
	file_delete(index);

	return 0;	
}
```

### _so this was my final code for this assignment. I learned so many new things from this assignment._ :)


