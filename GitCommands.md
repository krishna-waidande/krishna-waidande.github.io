# GIT COMMANDS


firstly getting started with git let me explain you about git.

+ Who invented Git ?


``` Linus Torvalds creator of the Linux operating system kernel, created a git to control versions of his work.```


+ What is git?


```Git is a version control system. that means``` 


Now we will learn how to use basic git commands.


first install git on your machine .
to install git [Click-here](https://git-scm.com/download/linux).


After installation of git on local machine.

Create a account on [Github](https://github.com)

After creating account on Github you will see a window on that window look on on right upper corner on navigation bar.

> You will see + sign click on that sign choose new repository option.


> Now give a repository name same as your project name (not mendatory same as project).


> After that just click on create repository button.



Once done now Open terminal.



Go to a folder in which you will create your all projeect files.
suppose I want to create my project in DemoProject folder which is located on my desktop just get in that project


For example : 

```
user@user-Lenovo-ideapad-320-15ISK:~$ cd Desktop/
user@user-Lenovo-ideapad-320-15ISK:~/Desktop$ ls
CRM  DemoProject PYTHON  reports.sql  StoreDB.sql
user@user-Lenovo-ideapad-320-15ISK:~/Desktop$ cd DemoProject/
user@user-Lenovo-ideapad-320-15ISK:~/Desktop/DemoProject$ 
```

now you are in a project where you want to clone a github repository.

> Clonning directory means sinking our local repository(folder) with remote repository(your git repository).

now on teminal just before typing a command just go on your github page and copy the url.

for exmmple :- https://github.com/krishna-waidande/DemoProject.git


and now on terminal type following command and hit enter.

```
git clone https://github.com/krishna-waidande/DemoProject.git
```
After typing this command just type ```ls``` you will see a folder is created in your local machine name will be same as your remote repository name. 

```
user@user-Lenovo-ideapad-320-15ISK:~/Desktop/DemoProject$ git clone https://github.com/krishna-waidande/DemoProject.git
Cloning into 'DemoProject'...
warning: You appear to have cloned an empty repository.
user@user-Lenovo-ideapad-320-15ISK:~/Desktop/DemoProject$ ls
DemoProject
user@user-Lenovo-ideapad-320-15ISK:~/Desktop/DemoProject$ cd DemoProject/
user@user-Lenovo-ideapad-320-15ISK:~/Desktop/DemoProject/DemoProject$ 

```

In above example DemoProject is name of my remote repository (Github repository) . 

Get into that folder by typing cd <repository name as show above.
