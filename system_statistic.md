### [HOME](https://krishna-waidande.github.io/)

# How to debug performance issues of the server

`Hello Readers`,

Today we will see `how to monitor the performance of the system` also `How to check free available memory on Linux`. there are many utilities present on the Linux to do this task, but we will see inbuilt utility present on Linux i.e `top` command.


`Top`: It is a part of the procps package, a set of Linux utilities that provide system information. Besides top, procps also includes free, vmstat, ps, and many other tools. Top command provides statistics of all the running processes as well as memory usage, CPU usage. 

Let me explain you each and every field in top command :     

---

| top | 09:59:59 | up 55 min |  1 user | load average: 0.44, 0.52, 0.64 |


| Tasks | 301 total | 2 running | 251 sleeping | 0 stopped | 0 zombie |


| %Cpu(s) |  2.3 us |  1.4 sy | 0.0 ni | 96.2 id | 0.0 wa | 0.0 hi | 0.1 si | 0.0 st |


| KiB Mem | KiB Mem | 7946952 total | 2839680 free | 2611976 used | 2495296 buff/cache |


| KiB Swap |  2097148 total |  2097148 free | 0 used | 4942148 avail Mem |


| PID | USER | PR | NI | VIRT | RES |  SHR | S | %CPU | %MEM |  TIME+ | COMMAND |  
|---|---|---|---|---|---|---|---|---|---|---|---|
|1863 | user | 20 |  0 | 3475732 | 208536 | 80224 | S | 7.9 | 2.6 |  10:44.91 | gnome-shell |
| 1716 | user | 20 | 0 | 395152 | 81288 | 56844 | S | 6.9 | 1.0 | 7:59.85 | Xorg |
| 7651 | user | 20 | 0 | 719984 | 37016 | 27420 | S | 4.9 | 0.5 | 0:00.88 | gnome-terminal |


                                                                                                                         
### | top | 09:59:59 | up 55 min |  1 user | load average: 0.44, 0.52, 0.64 |

`Current time`: `9:59:59` is the current time of the system.

`System uptime`: `55 min` is uptime which tells us the time for which the system has been running.

`Active user sessions`: It tells how many users are logged in into the server. In this case, only `1 user` is logged in to the system.

`Load average`: Load average is the representation of the number of processes marked as runnable in the run queue. 
From left to right, they represent one-minute, five-minute, and 15-minute load averages.
Keep in mind that a process in a runnable state doesn't necessarily mean it's currently executed by the processor.
It's a mark stating that "`I (the task) am ready to be executed, but it's up to the scheduler to decide when to pick me up.`"
For more info on [Load Average](https://www.linuxjournal.com/article/9001)


### | Tasks | 301 total | 2 running | 251 sleeping | 0 stopped | 0 zombie |

`Total no of tasks`: Total 301 task are three they might be the system level or the user level.

`Running`: This represents the number of tasks in a runnable state.

`Sleeping`: Processes being blocked due to waiting for an event (e.g., timeout or I/O completion). 
It accounts for both interruptible (can be awakened earlier by SysV signal) or uninterruptible (completely ignoring SysV signal) processes.

`Stopped`: The exact meaning here is "paused," not "terminated." 
In a terminal, you can stop a program by sending it a SIGSTOP signal or pressing Ctrl-Z if it's a foreground task.

`Zombie`: `"A dead body without the soul"` might be a good analogy.
After a child task is terminated, it is cleaned up and the only thing left is a task descriptor that includes a very important value: exit status. 
So if the number of zombies is high, that is a sign that one or more programs have a bug properly terminating child tasks.


### | %Cpu(s) |  2.3 us |  1.4 sy | 0.0 ni | 96.2 id | 0.0 wa | 0.0 hi | 0.1 si | 0.0 st |


The two left-most fields, us and sy, represent the percentage of CPU time spent in user mode and kernel mode, respectively.

### What is user mode and kernel mode?


The amount of time CPU runs the code of any user program is called as user mode, but when our program needs to interact with hardware or I/O operation at that time our code calls the kernel functionality (System calls). when CPU is executing system calls it is in kernel mode.

`ni`: Linux uses a “nice” value to determine the priority of a process. A process with a high “nice” value is “nicer” to other processes and gets a low priority. Similarly, processes with a lower “nice” get higher priority.

`id`: It displays how much percentage of CPU is ideal, it means free to use.

`wa`: Which is the time the CPU spends waiting for I/O to complete.

`hi`: Hardware interrupts are typically used by peripherals to tell the system about events, such as a keypress on a keyboard


`si`: Software interrupts are generated due to specific instructions executed on the processor

`st`: In a virtualized environment, a part of the CPU resources are given to each virtual machine (VM). The OS detects when it has work to do, but it cannot perform them because the CPU is busy on some other VM. The amount of time lost in this way is the “steal” time.


### | KiB Mem | KiB Mem | 7946952 total | 2839680 free | 2611976 used | 2495296 buff/cache |


It shows us the information of memory like available, used, free memory.

| Total Memeory | 7.6 GB |
|---|---|
| Total Used | 2.5 GB |
| Free | 2.7 GB |
| Buffer / cache | 2.4 GB |
| Available | 4.3 |


### | KiB Swap |  2097148 total |  2097148 free | 0 used | 4942148 avail Mem |

This is the same as Memory usage. It tells you information about the swap device.

| Total Memeory | 2.0	 GB|
|---|---|
| Total Used | 0 GB |
| Free | 2.0 GB |


### | PID |	USER | PR | NI | VIRT | RES | SHR | S | %CPU | %MEM | TIME+ | COMMAND | 

`PID`: This is the process ID, a unique positive integer that identifies a process.

`USER`: The user that is the owner of the process it means who starts that process.

`PR`: The running instance of the program is called process, and each process needs space in RAM and CPU time to be executed, each process has its priority in which it is executed. The “PR” field shows the scheduling priority of the process from the perspective of the kernel.

`NI`: Nice value only controls CPU time assigned to process and not utilization of memory and I/O devices.
Its value ranges from -20 to 20(on most Unix like operating systems).

### These three fields are related with to memory consumption of the processes. 

`VIRT (Virtual Memory)`: “VIRT” is the total amount of memory consumed by a process. This includes the program’s code, the data stored by the process in memory, as well as any regions of memory that have been swapped to the disk.


The kernel will write the contents of a currently unused block of memory to the hard disk so that the memory can be used for another purpose. When the original contents are needed again, they are read back into memory. The part of the hard disk that is used as virtual memory is called the swap space.

`RES`: It is the memory consumed by the process in RAM.

`SHR (Shared Memory)`: This is a memory shared among the different processes. Access to shared memory areas is controlled via keys and access rights checking. Once the memory is being shared, there are no checks on how the processes are using it.

---

`S (State)`: This field shows the process state in the single-letter form. `S=sleep` `R=running` `Z=zombie`

`%CPU`: It tells how much CPU is utilized by individual processes.

`%MEM`: It expresses RES value as a percentage of the total RAM available. It tells us how much memory usage is done by that process.

`TIME+`: This is the total CPU time used by the process since it started, precise to the hundredths of a second.

`COMMAND`: This column shows the name of the processes.


### Tricks in top command (Press following characters from keyboard )

`Shift + R`: To sort processes with PID.

`Shift + u`: It will display the processes belongs to the specified user. Enter the username then you will see the processes only related to that user

`Shit + P`: It will sort the processes according to CPU usage. ( which mean a process which is consuming more CPU will come at the first place. )

`Shift + M`: It will sort the processes according to Memory usage ( which mean a process which is consuming more Memory will come at first place.. )

`r`: To renice the value of the process.

`c`: To get the location of COMMAND.

`k`: To kill the process. you need to enter PID of the process.

`d`: To change screen refresh interval time. by the default value of it is 3 secs


## How to check free available memory on Linux : 

There are 3 ways for it. You have seen one of the ways in the blog above. Below are 2 more ways given.

1. Run `free -mh` command, It will show you all memory related statistics. like below :

|     |         total |        used |       free |     shared | buff/cache |   available |
|---|---|---|---|---|---|---|
| Mem |           7.6G |        2.8G |        1.9G |        557M |        2.9G |        3.9G |
| Swap |          2.0G |         0B  |      2.0G |


2. Run ```cat /proc/meminfo``` command, this command will show you a lot many things. Better and easy to use the free or top command.


### Happy learning :)
