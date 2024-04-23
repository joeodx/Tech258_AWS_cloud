# Linux processes 

************************************

Linux processes are the fundamental units of execution in the Linux operating system. They are essentially running instances of programs or tasks. Here's a breakdown of key points about Linux processes:



## How do we view our processes?

* To view processes use the 'ps' command 

```python
ps
```

* You can also use the 'top' command which will show the top processes in a real time view

```python
yop
```

* The 'jobs' command can also be sued for viewing background processes 

```python
jobs
```

# ps aux command

* This command will display all the information a user needs to current state of their systems running processes

```python
ps aux
```
![88.jpg](..%2Fpictures%2F88.jpg)

What do the columns mean?

* ```VSZ``` - This is the virtual memory being used by the process 
* ```RSS``` - Physical memory used by the process 
* ```TTY``` - Identifier for the current terminal session 


## Parent and Child processes?

arent and child processes are fundamental concepts in operating systems, including Linux. Here's what they entail:

Parent Process: A parent process is one that has created one or more child processes. Typically, when you start a program from the command line or through another process (like a shell), the process that initiates it becomes its parent. The parent process may also be responsible for managing the lifecycle of its child processes.
Child Process: A child process is a new process created by a parent process. The child inherits certain attributes from its parent, such as environment variables, file descriptors, and the working directory. Child processes are often created to perform specific tasks or to execute other programs.

* If you were to kill a child process, the parent process will try to restart the process once the child process has been wiped out
* It is always last resort to kill processes but if we need to there are the following commands...

## How to kill Processes 

There are quite a few kill processes commands but we will focus on the most common 

* TERMINATION (LEVEL 15)- this is to terminate gracefully. this is the default and stops zombie processes from starting. 

```python
kill (process_id)
```

* Brute force Kill - This is the harshest and can create a zombie processes if we kill the parent processes with this command.

```
kill - 9(process_id)
```

***********************************************************