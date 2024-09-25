## Lab 02

- Name:  Alec Porter
- porter.223@wright.edu


## Part 1 Answers

The answers for this section are to help you record what steps  
are needed to create a file locally (in your cloned repo)  
and push them (sync) with GitHub.  Only `git` commands are 
valid answers

1. View the status of the repository:  git status  
> This command details if the branch is up to date with origin/main and outlines which files are being tracked for commit/push

2. Add a file for tracking:  git add Labo2.md

3. Commit changes:  git commit
> This command commits any changes made to Lab02.md in the local repository.  If no changes have been made the output will display that your branch is up to date.  If you have made updates, you need to provide a comment and save.  After you provide a comment, save, and exit the editor you recieve details on the file changes such as number of insertions and deletions. 

5. Sync local commits with GitHub: git push
> Syncs the local repositor changes you identitifed when using the 'git commit' command.  The Lab02.md on Github matches the Lab02.md on your local repositiory.

6. Sync commits on GitHub to `clone`d repository:  git pull
> If you haven't made any changes to the reposity on Github then you get a message stating you are aready up to date.  If you made changes on Github then you get some details of the synch and file changes such as iinsertions and deletions.

## Part 2 Answers

1. `chmod u+r bubbles.txt`
> Means:  give the owner/user read permission to bubbles.txt but does not change any other existing permissions 
2. `chmod u=rw,g-w,o-x banana.cabana`
>  Means:  for banana.cabana, give the owner/user read and write permission but not execute, remove write permission from the group (leaves other permissions as is), remove execute permission from others (leaves the other permissions as is).
3. `chmod a=w snow.md`
> Means: for snow.md, give owner/user, group, and others, only wright permission (other permissions are removed).
4. `chmod 751 program`
> Means: for program, give owner/user read/write/execute, give group read/execute only, and give others execute only.
5. `chmod -R ug+w share`
> Means: for share, add write permissions recursively (i.e. apply to all files and folders inside share) to user/owner and group, no other permissions are changed.

## Part 3 Answers

For each, write the command used or answer the question posed.

1. sudo adduser aporter
2. /home/aporter
3. no, only aporter can read, write, and execute anything in /home/aporter
4. su aporter
5. cd /home/aporter (or: cd ~ )
7. yes, aporter has write permission for their home directory
8. su alecporter
9. cd /home/alecporter (or: cd ~ )

## Part 4 Answers

For each, write the command used or answer the question posed.

1. sudo addgroup crew
2. sudo usermod -a -G crew aporter | sudo  usermod -a -G crew alecporter
3. sudo chgrp -R crew share
4. su aporter
5. touch file.txt
6. yes, I was able to add the file becasue the permissions for share are rwx (read, write, execute) for the group which was set to crew in step 3.

## Part 5 Answers

For each, write the command used or answer the question posed.

1. sudo touch sudowho.txt
> This creats a file titled sudowho.txt as root
3. -rw-r--r-- = owner/user has read/wright permissions, group has read permission, and others have read permissions
4. sudo vim sudowho.txt
> when using sudo to creat a file the user/owner and group is set to root so you have to use sudo to edit the file otherwise you open it in read only mode.
4. sudo chown alecporter:crew sudowho.txt

## Part 6 Answers

1. `ssh` command before configuring `config` file: ssh -i labsuser.pem ubuntu@34.225.112.222
2. HostName: 34.225.112.222
3. User: ubuntu
4. IdentityFile: /home/alecporter/Documents/2024Spring/CS2350/labsuser.pem
5. `~/.ssh/config` contents:

```
Host AWS
HostName 34.225.112.222
User ubuntu
IdentityFile /home/alecporter/Documents/2024Spring/CS2350/labsuser.pem

```

6. `ssh` command after configuring an entry in the `config` file: ssh AWS
