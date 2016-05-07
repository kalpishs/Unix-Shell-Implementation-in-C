============================================================================================================================================ 
                     UNIX SHELL IMPLEMENTATION IN C
============================================================================================================================================ 
This program simulates the working of command line interface in Unix-like environment. Implemented Functionalities are as under:
1. Execute all the External commands (ls, clear, vi etc.)
2. Implement Internal commands: cd, pwd
3. Initialize and use environment variables
4. Print environment variables using echo command
5. Redirection operators: STDIN, STDOUT, STDERR (>>,>,<<,<,2>) 
6. Support for history command and '!' operator (history, !!, !-1, !10,!-10 etc)
7. Pipes “|” (multiple) (Ex: ls | grep 'a' | wc)


============================================================================================================================================ 
                          Input/Output Format
============================================================================================================================================ 

Input from the 'stdin' in an infinite loop till an “exit” is entered.
The corresponding output should be printed to 'stdout'.

Ex:
assume that PWD==home/user
Shell name: My_Shell
bash prompt:~$ ./a.out

My_Shell:/home/user$ ls
shell.c history.txt a.out
My_Shell:/home/user$ gfhj
gfhj: command not found
My_Shell:/home/user$ exit
Bye...
bash prompt:~$


============================================================================================================================================ 
                         Implementation Details
============================================================================================================================================ 

The shell.c contains the main function which takes the input from user and checks it for pipeline. If pipeline exist it processes the data separately else it passes the data to the functions. 

int with_pipe_execute():
This function is the initial function which is called for checking the all the command after initial preprocessing . It passes the processed output to function split

int split(char *cmd_exec, int input, int first, int last):

This function is responsible for splitting of command and passing it to command function


static int command(int input, int first, int last, char *cmd_exec):

this does the major part of the program. It  checks for various possibilities of commands. The types of commands that are checked are as under:
1) Internal commands: pwd and cd
2) echo commands, setting and getting environment variables
3) redirection handler 
4) PIPE
5) External commands
it make use of various funtions like tokenise_redirect_input_output,tokenise_redirect_input,tokenise_redirect_output which internally calls tokenise_commands() for tokenization


Helper functions:
getcwd():
gets the current woring Directory
signal():
Handle Interrupt Signal
void prompt():
initiates new Promt 


