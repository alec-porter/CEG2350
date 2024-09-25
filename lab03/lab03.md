## Lab 03

- Name: Alec Porter
- Email:  porter.223@wright.edu

## Part 1 Answers

1. `printenv $HOME > thishouse`
> printenv prints the values of specified environment variables to the file thishouse, but in this case the file is empty.  You don't use the $ with the printenv command.  To write the HOME environment variable to a file you use 'printenv HOME > thishouse'.
## Lab 03

- Name: Alec Porter
- Email:  porter.223@wright.edu

## Part 1 Answers

1. `printenv $HOME > thishouse`
> printenv prints the values of specified environment variables to the file thishouse, but in this case the file is empty.  You don't use the $ with the printenv command.  To write the HOME environment varibale to a file you use 'printenv HOME > thishouse'.
2. `cat doesnotexist 2>> hush.txt`
> cat will try to display the contents of a file; however, in this case there is no file titled doesnotexist to display.  2 redirects the stderr stream (there is an error because there is not file titled doesnotexist) to append the error message to a file titled hush.txt.  Because the stderr stream was redirected to append a file, the error is not displayed in the terminal.  
3. `cat nums.txt | sort >> all_nums.txt`
>  | allows you to string multiple commands together on a sinlge comamnd line.  The list of numbers in the nums.txt file will be sorted and appended to the all_nums.txt file.
4. `cat << "DONE" > here.txt`
> << redirects input to the command cat until the user types DONE.  All inputs the user types will be written to the file here.txt once the user types DONE.
5. `ls -lt ~ | head`
> ls list files and directories, the -l flag uses the long listing format, the -t flag sorts by time, and ~ is the list of files to display which will be the home directory of the user.  Head lists the first 10 lines in a file but when used with ls it lists the first 10 lines of the file list.  When head is used with ls -l it shows the cumulative disk space in blocks allocated for the files being displayed and the next 9 files. 
6. `history | grep ".md"`
history keeps a list of all other commands that have been run from the terminal.  If you want to see specific commands then use grep to identify specific commands to display.  Using ".md" displays any commands that contained the string ".md".

## Part 2

Verify that `roll` made it to your GitHub repository for this course and is in your `Lab03` folder.  No answers will be written here unless you would like to leave a note to the TAs

## Part 3 - Retrospective Answers

1. It went wrong everywhere.  A lot of reading through the manual for commands, seraching for examples, etc. online.  This is my first experience using bash and while it is similar to python (the only progrmaing language I've take) it was different enough in syntax that I need to do a lot of troubleshooting.
2. The overall structure is similar to python but the syntax is different in many areas and something as simple as not having a space before or after a character generated an error.
3. Making a lot of little changes and trying to capture commets via commits to github seemed overerly difficult for me.  I wanted to retain my code for the previous parts so I could more quickly reference back to is as I progressed through the lab.  I also want to keep a local record of my lab code and I don't want to rely on an offsite repository where I would need to look through the comments to see what I changed and why.  I was able to figure out how to script all of the different iterations of roll but my commit comments are somewhat messy.  In the future I'll have to figure out a different approach to commits and how I code.      

## Part 5 Answers

1. PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
2. -d "$HOME/bin" is false because there is no bin directory.  To make the argument true you need to mkdir bin in $HOME
3. Command: mkdir /home/alecporter/.local/bin
   - Full path: /home/alecporter/.local/bin
4. PATH = /home/alecporter/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
   - Difference: the folder /home/alecporter/bin has been added to PATH
5. cp /home/alecporter/Documents/2024Spring/ceg2350s24-alec-porter/Lab03/roll /home/alecporter/bin
6. using ls -l on roll the permissions were set to -rwx--x--x which means the user/owner, group, and others can execute the script.  This means I set the permissions earlier with chmod 711 roll.  In order to run the script the user/owner, group, and others must have execute permissions which at a minimum would be --x
7. All three can run the script given the file permission is set to rwx--x--x

## Extra Credit

1. I noticed that entering a float would crash the program.  Bash can't handle flaoting point arithmatic so you have to use another tool.  I updated the script so that it checks if a floating point number has been entered (it loops through the input looking for a decimal point) and will continute to loop until two valid integers have been entered.

