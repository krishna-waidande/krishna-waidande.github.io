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

Total no of tasks : 301.

Running: this represents the number of tasks in a runnable state.

Sleeping: processes being blocked due to waiting for an event (e.g., time out or I/O completion). 
It accounts for both interruptible (can be awaken earlier by SysV signal) or uninterruptible (completely ignoring SysV signal) processes.

Stopped: the exact meaning here is "paused," not "terminated." 
In a terminal, you can stop a program by sending it a SIGSTOP signal or pressing Ctrl-Z if it's a foreground task.

Zombie: "A dead body without soul" might be a good analogy.
After a child task is terminated, it is cleaned up and the only thing left is a task descriptor that includes a very important value: exit status. 
So if the number of zombies is high, that is a sign that one or more programs have a bug properly terminating child tasks.
