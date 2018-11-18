Top : It is a part of the procps package, a set of Linux utilities that provide system information. Besides top, procps also includes free, vmstat, ps, and many other tools.
Top command provides statistics of all the running processes as well as memory usage, CPU usage. 


```
top - 09:59:59 up 55 min,  1 user,  load average: 0.44, 0.52, 0.64
Tasks: 301 total,   2 running, 251 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.3 us,  1.4 sy,  0.0 ni, 96.2 id,  0.0 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem :  7946952 total,  3848760 free,  2286788 used,  1811404 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  4942148 avail Mem
```

Row 1: 

Cureent time : 9:59:59 is the current time of the system.

System uptime : 55 min is uptime which tells us the time for which the system has been running.

Active user sessions : It tells how many users are logged in into the server. In this case only single user is logged in to the system.

Load average : Load average is the representation of the number of processes marked as runnable in the run queue. 
From left to right, they represent one-minute, five-minute, and 15-minute load averages.
Keep in mind that a process in a runnable state doesn't neccessarily mean it's currently executed by the processor.
It's a mark stating that "I (the task) am ready to be executed, but it's up to the scheduler to decide when to pick me up."
For more info on Load average (https://www.linuxjournal.com/article/9001)


Row 2 :

Total no of tasks : Total 301 task are three they might be the system level or the user level.

Running: this represents the number of tasks in a runnable state.

Sleeping: processes being blocked due to waiting for an event (e.g., time out or I/O completion). 
It accounts for both interruptible (can be awaken earlier by SysV signal) or uninterruptible (completely ignoring SysV signal) processes.

Stopped: the exact meaning here is "paused," not "terminated." 
In a terminal, you can stop a program by sending it a SIGSTOP signal or pressing Ctrl-Z if it's a foreground task.

Zombie: "A dead body without soul" might be a good analogy.
After a child task is terminated, it is cleaned up and the only thing left is a task descriptor that includes a very important value: exit status. 
So if the number of zombies is high, that is a sign that one or more programs have a bug properly terminating child tasks.



Row 3 : %Cpu(s):  2.3 us,  1.4 sy,  0.0 ni, 96.2 id,  0.0 wa,  0.0 hi,  0.1 si,  0.0 st

The two left-most fields, us and sy, represent percentage of CPU time spent in user mode and kernel mode, respectively.

What is user mode and kernal mode ?

```
To explain this let's take a example.
Write a program to sort given 10 numbers.

Here wrote a program, compiled it and created executable file. Now you run your program. that program might became the process.
Now when CPU is runninng the code written by you then process is running in user mode but lets say your program is taking input from user so here to take input and store that input onto disk.
your program will take the help of kernal, so here kernal will run it's own programs (System calls ) to perform I/O operations.
So when CPU is running the kernal program that means process is in kernal mode.
```

Row 4 : KiB Mem :  KiB Mem :  7946952 total,  2839680 free,  2611976 used,  2495296 buff/cache

This gives us the information of Memory it means Available, used, free memory. In above line
Total Memeory : 7.6 GB 
Total Used : 2.5 GB
Free : 2.7 GB
Buffer / cache : 2.4 GB
Available : 4.3



Row 5 : KiB Swap:  2097148 total,  2097148 free, 0 used.  4942148 avail Mem

This is same as Memory usage. It tells you information about swap device.
Total Memeory : 2.0	 GB 
Total Used : 0 GB
Free : 2.0 GB


Row 6 : PID		USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND 

PID : This is the process ID, an unique positive integer that identifies a process.

PR : The running instance of program is process, and each process needs space in RAM and CPU time to be executed, each process has its priority in which it is executed. The “PR” field shows the scheduling priority of the process from the perspective of the kernel.

NI : Nice value only controls CPU time assigned to process and not utilisation of memory and I/O devices.
It’s value ranges from -20 to 20(on most unix like operating systems).

VIRT : The kernel will write the contents of a currently unused block of memory to the hard disk so that the memory can be used for another purpose. When the original contents are needed again, they are read back into memory. The part of the hard disk that is used as virtual memory is called the swap space.

RES : 


SHR : 


S :

%CPU :

%MEM :

TIME+

COMMAND :


### Tricks in top command 

Press SHift + R : To sort processes with pid

Press r : to renice the value of process.

Press Shift + u : It will display the processes belongs to specified user. Enter the user name then you will see the processes only related to that user

Press Shit + P : It will sort the processes according to CPU usage. ( which mean process which is consuming more CPU will be come at first place. )

Press Shift + M : It will sort the processes according to Memory usage ( which mean process which is consuming more Memory will be come at first place.. )

Press c : to get location of COMMAND.

Press k : to kill the process. you need to enter PID of the process.

Press d : to change screen refresh interval time. by default value of it is 3 secs
