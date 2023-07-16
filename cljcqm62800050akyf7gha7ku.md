---
title: "Shell scripting in Linux"
datePublished: Mon Jun 26 2023 10:50:08 GMT+0000 (Coordinated Universal Time)
cuid: cljcqm62800050akyf7gha7ku
slug: shell-scripting-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687776497928/1e80913e-9502-464a-a9ec-a7ca6c7df296.jpeg
tags: linux, devops, shubhamlondhe, trainwithshubham

---

![Your One and Only Linux Shell Scripting Tutorial](https://adamtheautomator.com/wp-content/uploads/2021/08/Your-One-and-Only-Linux-Shell-Scripting-Tutorial.jpg align="left")

1. Shebang: Specifies the interpreter to be used for executing the script.
    
    ```plaintext
    shellCopy code#!/bin/bash
    ```
    
2. Comments: Used for adding comments in the script to provide information or explanations.
    
    ```plaintext
    shellCopy code# This is a comment
    ```
    
3. Variables: Used to store values.
    
    ```plaintext
    shellCopy codevariable_name=value
    ```
    
4. Command substitution: Allows the output of a command to replace the command itself.
    
    ```plaintext
    shellCopy codevariable_name=$(command)
    ```
    
5. Conditionals: Used to perform actions based on certain conditions.
    
    ```plaintext
    shellCopy codeif condition
    then
        # commands
    elif condition
    then
        # commands
    else
        # commands
    fi
    ```
    
6. Loops: Used to iterate over a sequence of values or perform repetitive tasks.
    
    * For loop:
        
        ```plaintext
        shellCopy codefor variable in list
        do
            # commands
        done
        ```
        
    * While loop:
        
        ```plaintext
        shellCopy codewhile condition
        do
            # commands
        done
        ```
        
    * Until loop:
        
        ```plaintext
        shellCopy codeuntil condition
        do
            # commands
        done
        ```
        
7. Functions: Used to group a set of commands into a reusable block.
    
    ```plaintext
    shellCopy codefunction_name() {
        # commands
    }
    ```
    
8. Input/output redirection:
    
    * Redirecting standard output (stdout) to a file:
        
        ```plaintext
        shellCopy codecommand > file
        ```
        
    * Redirecting standard error (stderr) to a file:
        
        ```plaintext
        shellCopy codecommand 2> file
        ```
        
    * Appending stdout to a file:
        
        ```plaintext
        shellCopy codecommand >> file
        ```
        
    * Redirecting stderr and stdout to different files:
        
        ```plaintext
        shellCopy codecommand > stdout_file 2> stderr_file
        ```
        
9. Command-line arguments: Allowing passing arguments to a script.
    
    ```plaintext
    shellCopy codescript_name arg1 arg2 arg3
    ```
    
10. Conditional execution:
    
    * Execute a command only if the previous command succeeds (return code 0):
        
        ```plaintext
        shellCopy codecommand1 && command2
        ```
        
    * Execute a command only if the previous command fails (return code non-zero):
        
        ```plaintext
        shellCopy codecommand1 || command2
        ```
        
11. Exit status: Checking the exit status of a command.
    
    ```plaintext
    shellCopy code$?
    ```
    
12. String manipulation:
    
    * Concatenating strings:
        
        ```plaintext
        shellCopy codenew_string="$string1$string2"
        ```
        
    * Extracting substrings:
        
        ```plaintext
        shellCopy codesub_string="${string: start: length}"
        ```
        
    * String length:
        
        ```plaintext
        shellCopy codelength=${#string}
        ```
        

These are just a few essential commands and concepts in shell scripting. The possibilities and complexities of shell scripting are vast, and there are many more commands and features available.