
# 🐚 Shellvetica: A SimpleShell in C

**Instructor:** Vivek Kumar

**Submitted by:**
- Saksham Singh - 2022434
- Sidhartha Garg - 2022499

## 📜 Table of Contents

- [Assignment 02 - Group 50 - Shellvetica: A SimpleShell in C](#assignment-02---group-50---shellvetica-a-simpleshell-in-c)
  - [📜 Table of Contents](#-table-of-contents)
  - [🚀 Introduction](#-introduction)
  - [🔧 Usage](#-usage)
  - [📁 Code Structure](#-code-structure)
  - [🛠️ Functions](#️-functions)
    - [init_shell()](#init_shell)
    - [launch()](#launch)
    - [cntrl_cHandler()](#cntrl_chandler)
    - [execute()](#execute)
    - [execute_pip()](#execute_pip)
    - [shInterpreter()](#shinterpreter)
  - [🚀 Main Function](#-main-function)
  - [👥 Contribution](#-contribution)

## 🚀 Introduction

This C code implements a basic shell with the following features:

- Command execution
- Handling Ctrl+C (SIGINT) to display information about executed commands
- Piping multiple commands
- Command history

## 🔧 Usage

1. **Compile and run the code:**

   shell
   make run_shell
   

2. **Welcome to the shell:**
   - The shell accepts externally defined commands from `/usr/bin` with appropriate flags and syntax.
   - It runs ELF executables and bash scripts compatible with the OS.
   - Supports pipes (`|`) and background processes (`&`).
   - Internal commands handled:
     - `exit`: exits the shell and provides data of executed processes.
     - `history`: prints the list of all entered commands.
   - Note: `cd` command not implemented.

3. **Compile `fib.c` to `./fib`:**

   ```shell
   make fib
   ```

4. **Cleanup:**

   ```shell
   make clean
   ```

## 📁 Code Structure

The code is structured as follows:

- It defines a `command_info` struct to store information about executed commands.
- The `init_shell()` function initializes the shell and displays a welcome message.
- The `launch()` function is responsible for creating child processes to execute commands. It handles command execution, including redirection for piped commands, and records information about the executed command in the `command_info` struct.
- The `cntrl_cHandler()` function is a signal handler for Ctrl+C (SIGINT). It displays information about previously executed commands, including their PIDs, arguments, start times, and execution times.
- The `execute()` function parses and executes single commands. It supports built-in commands such as "exit" and "history," as well as external commands. It also records executed commands in the command history.
- The `execute_pip()` function handles the execution of piped commands. It splits the input command into individual commands based on the "|" delimiter and executes them sequentially, passing the output from one command as input to the next.
- The `shInterpreter()` function reads and executes shell script files.

## 🛠️ Functions

### init_shell()

This function initializes the shell, displays a welcome message, and prints the username of the current user.

### launch()

The `launch()` function creates a child process to execute a command. It handles command execution, including redirection for piped commands. It records information about the executed command in the `command_info` struct.

### cntrl_cHandler()

This function is a signal handler for Ctrl+C (SIGINT). When Ctrl+C is pressed, it displays a list of previously executed commands, including their PIDs, arguments, start times, and execution times.

### execute()

The `execute()` function parses and executes single commands. It supports built-in commands such as "exit" and "history," as well as external commands. It records executed commands in the command history.

### execute_pip()

The `execute_pip()` function handles the execution of piped commands. It splits the input command into individual commands based on the "|" delimiter and executes them sequentially, passing the output from one command as input to the next.

### shInterpreter()

The `shInterpreter()` function reads and executes shell script files. It reads the contents of a shell script file line by line and executes each line as a command.

## 🚀 Main Function

The `main()` function is the entry point of the shell. It repeatedly prompts the user for input, reads commands, and executes them. It also maintains a history of commands.

## 👥 Contribution

This project was developed collaboratively by Saksham Singh and Sidhartha Garg for the course Operating Systems under the guidance of Instructor Vivek Kumar.

