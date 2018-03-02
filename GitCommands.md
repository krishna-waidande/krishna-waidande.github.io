# Getting Started With Git


Firstly getting started with git let me explain you about git.

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

Get into that folder by typing cd <repository name> as show above.
  
  
  Now You can create your project Folder files/folder in this folder.
  
  Now we will see how to add a text file into remote repository.
  
  create a text file once created just type following commands
  
  # Basic Git Commands
  
  git add <filename / folder name> : To add files to remote repository.
  ```
  user@user-Lenovo-ideapad-320-15ISK:~/Desktop/DemoProject/DemoProject$ git add DemoFile.txt
  ```
  
  git commit -m "initial commit" := This is used to commit added files to server.
  
  
  -m is used for givimg messege for our commit and it ia compulaory to give proper commit messages.
  
  
   ```
  user@user-Lenovo-ideapad-320-15ISK:~/Desktop/DemoProject/DemoProject$ git commit -m "My initial Commit"
  [master (root-commit) efc3358] My initial Commit
  1 file changed, 1 insertion(+)
  create mode 100644 DemoFile.txt
  ```
  
  git status :- 
  
  git push : to push our local file / folder to remote repository.
  
  git branch :- telles us on which branch we are.
  ``` 
  user@user-Lenovo-ideapad-320-15ISK:~/Desktop/DemoProject/DemoProject$ git branch
  * master
  ```
