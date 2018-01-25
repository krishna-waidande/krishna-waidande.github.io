#Reverse the contents of an input file
For example: 

“hello world 
I am krishagni”

Should be :

“ingahsirk ma i
dlrow olleh”.


our first approach for this was reading file from backwords by using fseek function in c.
we tried that logic on smaller files. it works faster so I thought that my approach is coreect. and i got the solution very easyly but when we tested that code for larger file size it took too much time to exeute. than I realise that my code is correct but not efficient. 

