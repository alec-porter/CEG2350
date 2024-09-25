## Lab 09

- Name: Alec Porter
- Email: porter.223@wright.edu

## Part 1 - Compiling

1. Method & command to get a copy of the source code files: use wget on the raw link in Github for each of the files I needed.
2. Windows C / C++ compiler
   - Download Windows installer from: https://www.msys2.org and follow instrucitons on freecodecamp.org/news/how-to-install-c-and-cpp-compiler-on-windows 
   - Confirm installed in Windows: in Powershell type gcc --version then g++ --version
3. Linux C / C++ compiler
   - Download Linux installer from: sudo apt install build-essential (my distro had it preinstalled :thumbsup:)
   - Confirm installed in Linux: gcc --version && g++ --version
4. Browser based compiler for C / C++: https://www.w3schools.com/cpp/cpp_compiler.asp and https://www.w3schools.com/c/c_compiler.php
5. Command(s) to compile the source code into an executable program: g++ main.cpp utility.cpp -o todolist
6. Command(s) to execute the program: ./todolist

## Part 2 - Document

### Program User Guide

#### Program Description
This program is a simple text based to-do list.  You can add tasks, marks tasts as complete, remove tasks, and view the status of your tasks.

#### How to Build and Run Program
Open a terminal.  Verify you have a C++ compiler installed on you Linux distribution by typing `g++ --version`.  If you need to install a C++ compiler type `sudo apt install build-essential` then verify the installation.  In the location you want to run the program, download the source code using wget:
```
wget https://raw.githubusercontent.com/pattonsgirl/CEG2350/main/Labs/Lab09/TODO-CPP/main.cpp
wget https://raw.githubusercontent.com/pattonsgirl/CEG2350/main/Labs/Lab09/TODO-CPP/utility.cpp
wget https://raw.githubusercontent.com/pattonsgirl/CEG2350/main/Labs/Lab09/TODO-CPP/utility.h
``` 
Compile the program with the following command: `g++ main.cpp utility.cpp -o todolist` where todolist is the title of the executable file.  You can change the title of the executable file.

You can now run the to-do list program by typing `./todolist` or ./ followed by what you titled your program.

#### How to Use Program
Menu Options:

1 - Add a task to the list by giving it a unique name.

2 - Mark a task complete by entering its unique name.

3 - Remove a task from the list by entering its unique name.

4 - View all of the tasks you entered and their status (Not Completed / Completed).

5 - Exit the program.

Notes:  The program will allow you to enter the same task name multiple times but managing multiple tasks with the same name is not ideal.  Using unique task names allows for easier updates/removal of tasks.


### `git` `branch` Guide

Create a branch: git branch lab09-branch

Change to branch: git switch lab09-branch

Add branch to remote if created locally (GitHub): git push --set-upstream origin lab09-branch

Steps to `merge` changes to another branch (`main`): git switch main; git merge -m 'merged branch to main, branch updated comments in utillity.cpp' lab09-branch; git push origin

Steps to resolve a `merge` conflict: open the file with the merge conflict in a text editor, search for the conflict marker (<<<<<<<<<).  That signifies the start of the merge conflict where the conflict from main is seperated from the branch by (==========).  Decide what I want to keep/remove then delete the conflict markers.  Use git commands to add the changed file, commit, then merge the changes.  Github Docs has a good article on the procedures: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line

## Part 3 - makey makey

Using `Makefile` to build executable: make build

Using `Makefile` to run program: make run

Using `Makefile` to remove compilation files, such as the executable: make clean

## Extra Credit - Ignore That

Remove this statement and the exclamation point from the line below so TAs can click to check for a working `.gitignore` file.  Test that the link works - if it doesn't, fix the pathing.

![`.gitignore` file in root of repository](../.gitignore)
