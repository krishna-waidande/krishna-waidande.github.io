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

> Version 1.0

```C
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

## Second Approach

My second approach was using 2 file pointers. One file pointer at starting of file and another file pointer at end of the file and by swapping the first character with last . & again reading next character and reading second last character and swapping them with each other.in this way also we can solve the problem . for smaller size files program was running in no time. again for larger file size. this was taking hours to execute.

> Version 1.1


```C
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

## Third Approach


Then I started to think about another approach to solve this problem.


Then third approach came to my mind was reversing file order by using 2 files.for that I decide to read file chunk by chunk. reverse chunk data and store that data into another file. this approach was just reversing the file data line by lines. this was not my required output so tried to find  how I can prepend new data before old data.

> Version 1.3

```C

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


> For example :


my name is krishna.


my name is gautham.


> Output


anhsirk si eman ym


mahtuag si eman ym

**i am getting wrong output**

> Required Output is

mahtuag si eman ym


anhsirk si eman ym



so while inserting 2nd line I was looking for how can I place my new data at the beginning of my file. this was not possible to add data to starting of the output file. Because when I tried to do that old data was getting overwritten. so my this approach also failed.


## Fourth Approach


So another approach came to my mind was we can solve this problem by using Tower of Hanoi algorithm.by using that algorithm we were getting write output.but for larger files that algorithm was taking too much time to execute. this approach was also not correct to solve this problem.

**Version 1.4**



DISADVANTAGES
 

> More read-write operations.

> More execution time.

## Fifth Approach


We can create n temp files and store 1 chunk in one temp file. In this way, we will read the whole file and store that all data in temp files in reverse order so that while reading from temp files we can read the data from the last file into an output file. In this way, we can read k,k-1,k-2th & so on files into our output file.and after reading all temp files I deleted those files dynamically.
by using this approach I get required output.





