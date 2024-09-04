# Get Next Line

## Overview
This is a project aimed at implementing a function that reads a line from a file descriptor.
This function is commonly used in various programming environments to help developers master file handling, dynamic memory allocation, and buffermanagement in C language
The goal of this project is to create a function, get_next_line, that reads the next line from a given file descriptor each time it is called.

## Project Objective

    char *get_next_line(int fd);
    
- Parameters: int fd — the file descriptor to read from.
- Return Value: Returns the next line read from the file descriptor, including the newline character (\n), or NULL if there is nothing more to read or an error occurs.
- Memory Management: The function must allocate memory dynamically to store each line it reads. Proper memory management is crucial to avoid memory leaks.

## Features

- Reads a single line from a file descriptor, including the newline character.
- Handles files with varying line lengths, including very long lines.
- Properly manages dynamic memory allocation to avoid memory leaks.

## How It Works
The function get_next_line uses a buffer to read chunks of data from the file descriptor. The function continues reading from the file until 
it encounters a newline character (\n) or reaches the end of the file (EOF).
Each time get_next_line is called, it returns the next line from the file. If the end of the file is reached or an error occurs, the function returns NULL.

## Example Usage

    #include <stdio.h>
    #include <fcntl.h>
    #include "get_next_line.h"

    int main(void)
    {
    int fd;
    char *line;

    fd = open("example.txt", O_RDONLY);
    if (fd == -1)
        return (1);

    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }

        close(fd);
        return (0);
    }

Assuming the example.txt file contains

      Hello, World!
      This is the second line.
      And this is the third line.

The output will be

    Hello, World!
    This is the second line.
    And this is the third line.

## Installation
To use or test this project, 
1. clone this repository

       git clone git@github.com:elpah/get_next_line.git gnl
2. Create an example.txt file and paste in some text to read
3. Compile the program with the command

        gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c -o your_program
4. Run the program

        ./your_program.out





      
  


