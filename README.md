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

> Version 1.4

```C
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

## Fifth Approach


We can create n temp files and store 1 chunk in one temp file. In this way, we will read the whole file and store that all data in temp files in reverse order so that while reading from temp files we can read the data from the last file into an output file. In this way, we can read k,k-1,k-2th & so on files into our output file.and after reading all temp files I deleted those files dynamically.
by using this approach I get required output.


so while coding for this approach my first thought was how can i create temp files in c . 2nd pronblem was how can i generate unique n no of file names. so after reading on blogs i found that using sprintf() in c we can generate n no of filenames so this function help me to to give filenames at runtime.

so in this way i started coding for this approach.

```C
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
	char f[11]={NULL};

	
	n=strlen(c);
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

	sprintf(f,"file%03d.txt",k++);
    	fp=fopen(f,"w");
	fputs(c,fp);
	fclose(fp);
}
void append(int k)
{
	FILE *fp=NULL,*fp2=NULL;
	char f[11]={NULL};
	char c[1999990]={NULL};
	int size=0;
	
	

	
	
	sprintf(f,"file%03d.txt",k);
	
	fp2=fopen("demo1.txt","a");
	
	struct stat st;

	stat(f, &st);
  	size=st.st_size;
	printf("%d",size);	
	

	fp=fopen(f,"r");
	if(size<1999990)
	{
	
	fread(c,size,1,fp);
	fputs(c,fp2);
	}
	else
	{
		fread(c,1999990,1,fp);
		fputs(c,fp2);
	}
	
	//unlink(f);
	fclose(fp);
	fclose(fp2);

}
void delete(int k)
{
	char f[11];
	//memset(f,'',sizeof(f));

	sprintf(f,"file%03d.txt",k);
	
	unlink(f);

}

int main()
{

	long n=0,n1=0,s=0,i=0;
  	 FILE *fp=NULL,*fp2=NULL;

 	char c[1999990]={NULL};
	
	if ((fp = fopen("input.txt","r")) == NULL)
	{
       		printf("Erro! opening file");

     	}

	struct stat st;
	stat("input.txt", &st);
  	n=st.st_size;
	printf("%d",n);
	
	if(n<1999990)
	{
		fread(c,n,1,fp);
		rev(c);

	}
	else
	{
		n1=1999990;
		while(n>0)
		{
			if(n/1999990)
			{
				fread(c,n1,1,fp);
				rev(c);
				
			}
			else
			{
				n1=n%1999990;
				fgets(c,n1,fp);
				rev(c);
				break;
			}
			
			printf("\n %d \n",s++);
			n=n-1999990;
			
		}
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


