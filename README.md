<h1 align="center"> Shell-User-Interface-in-C 💻 </h1>
<p align="center"> This Repo was made for a lab project in Operating System - Second Semester 2019-2020 </p>


## Project 1 Description - Implementing a Shell
### Purpose 
The purpose of this project is to familiarize you with the mechanics of process control through the implementation of a shell user interface. This includes the relationship between child and parent processes, the steps needed to create a new process, shell variables, and an introduction to user-input parsing and verification. You may work in a group of two for this project.

### Problem Statement 
Design and implement a basic shell interface that supports the execution of other programs and a series of built-in functions, as specified below. 

### Part 1: General Shell Structure 
The shell is just a program that continually asks for user input, perhaps does something on the user’s behalf, resets itself, and again asks for user input. It should follow the following structure: \

*/ Get your Student ID */ \
If true, then while() { \
*/ Get user input */ \
*/ Exit? */ \
*/ Do something with input */ \
} \
If not true, then ask Again 
### Part 2: The Prompt 
At this point, the prompt should indicate that the shell is ready to accept input from the user. Often times, it also shows useful information, such as the name of the user running the shell, the Student ID you have logged in with, and the current directory. \
• The prompt should look like the following: \
o prompt$ \
• There should be a space after the dollar sign so that the user input does not visually run into the prompt. \
• Extra credit – make it different color(s)! \
• Extra credit – the prompt should display the current working directory: \
o /home/xkcd/$ 
### Part 3: Command Line Parsing 
Before the shell can begin executing commands, it needs to extract the command name and the arguments into “tokens”. It might be nice to store these tokens into an array so that you can then parse each one in order. In our shell, the first token will always be the name of the program we wish to execute, and all remaining tokens (perhaps including the first token) will be arguments to that program. Take note of the following assumptions: \
• No leading or trailing whitespaces \
• One space separates the command line tokens. \
• You can assume that each token is no longer than 80 characters. \
• You can assume that a command will have at most 10 space-separated tokens \
Make sure that you can successfully print out your array of tokens through different iterations of your shell loop before moving on. If you see garbage in any of your commands or arguments, try using the C library call memset() or bzero() to clear out your input string and token array before and/or after you are done using them. The C library call fgets() can gather user input from the screen and save it into a string (C character array). See the man pages for fgets for more information \
### Part 4: Command Execution
Once the shell understands what commands to execute it is time to implement the execution of simple commands. Since the execution of another program involves creating another process, you will have to use the fork() system call to create another process. Once you have created the new child process, that process must use the execvp() system call to execute the program. Finally, the parent (shell) process must wait for the child process to complete before releasing the child’s resources using the waitpid() system call. However, the execvp() system call may return if there is an error. If it does, your shell should print an error, reset, and prompt for new input. 
Here is an example: \
prompt$ hahaha \
-a Error: Command could not be executed \
prompt$ \
### Part 5: Built-ins
Not all commands are actually programs, and your shell must implement two “built-in” commands. In other words, if you encounter any of these two commands, do not execute them using fork(), exec(), and waitpid(). Instead, your shell should call a subroutine that implements the following functionality.: \
• exit – Description terminates your running shell process and prints 'exit'. \
prompt$ exit \
exit (shell exits) \
• cd [PATH] – Description : Changes the present working directory. You will need to use the chdir() system call and update the PWD environmental variable with setenv(). \
prompt$ pwd \
/user/diesburg/os/project1 \
prompt$ cd .. prompt$ pwd /user/diesburg/os \
prompt$ cd project1 \
prompt$ pwd \
/usr/diesburg/os/project1\
showpid – shows the last 5 child process IDs created by your shell. \
prompt$ showpid \
4987 \
4992 \
5001 \
5002 \
5004 \
•stat file or directory name Description: prints the size of the file or directory name, the attributes of the file or directory name, and the first cluster number of the file or directory name if it is in the present working directory. Return an error if FILE_NAME/DIR_NAME does not exist. (Note: The size of a directory will always be zero.) \
•ls DIR_NAME - Description: lists the contents of DIR_NAME, including the “.” (here) and “..” (up one directory) directories. It should not list deleted files or system volume names \
• read FILE_NAME POSITION NUM_BYTES Description: reads from a file named FILE_NAME, starting at POSITION, and prints NUM_BYTES. Return an error when trying to read a directory \

---

## Project 2 Description - Implementing a Concurrent Program
### Problem statement

Program
Design and implement a small concurrent program. Programming is done using C. You can select yourself the sub-project area from the following (Bank System, Airline Tickets, Library, Pharmacy. etc.) or use your own problem (specification approved in advance). The concurrent program must demonstrate semaphores and synchronizations best usages. Since its concurrent programing, I expect you to use multithreading to demonstrate how to manage critical sections. 
Accepted concurrent sub-program project contains at least the following:
1.	Problem description
2.	Explanation for selected solution method and granularity of used concurrency
3.	Algorithmic solution and explanations why it is correct
4.	Explanation on the advantages of the concurrent solution as compared to the serial solution (e.g., you can use linux command time).
5.	Solution source code
6.	Executable program as attachment, with enough user instructions. It must be very easy to execute it.
