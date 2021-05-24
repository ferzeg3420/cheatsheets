# Tell the program that runs your script to use the bash interpreter for the file:

```#! /bin/bash```

# You should probably prefer to use sh
The posix shell is a good option to make those programs work across\
the board in unix systems\
```#! /bin/sh```

# Traps to avoid:

## Exit vim
if you open vim and can't exit: type the esc key (escape), then type\
':q!' and finally press enter.

## Remove a file that starts with - 
you can use the full path to the file or use -- as one of the arguments.\
-- tells the command to stop looking for options (flags like -f)

```reset``` to fix a broken terminal.

# Essentials:

``` man commandName```\
Looks up the manual pages for *commandName*.\
q is used to exit the man pages.

*pwd*\
prints the directory where commands will take effect (full paths\
can be used to make sure the commands affect the files you want)

``` ls directoryName```\
Print files in the current directory or inside a directory.

*file /etc/hosts*\
tells you what kind of file its argument is.

```wc -l theFile```\
counts the number of lines in a file.\

```cd somedirOrPath ```\
changes the current directory that the shell is working on.

```cd ..```\
Go back to parent directory.

```cd -```\
goes back to the previous directory.

*which*\
Tells you where in the filesystem a commands lives

*type*\
I use it to figure out if a command is actually an alias

*watch*\
repeat things and see the output.

```cat file | less```\
Less pages long output.

```echo "scale=2; 32 + 3 / 2"```\
Do some math.

*htop*\
See running processes.

*mkdir*\
Create a directory.

*rmdir*\
remove a directory.

*rm*\
remove a file.

*ln -s /path/to/src /path/to/link*\
Creates a symbolic link to a file.

*stat*\
Exhaustive details about a file.

*cat*\
Concatenate files or display them.

*tac*\
Reverse lines or combine files in reverse.

*rev*\
Reverse a line. line becomes enil.

*uniq file*\
Get rid of repeat lines in a file.

*sort file*\
Sort lines in a file.

*head*\
Show the first ten lines (or a set amount with -4 for example) of\
a file.

*tail*\
Show the last ten lines (or a set amount with -4 for example) of\
a file.

*echo some text that can be printed.*\
Print some text.

*printf "%s style printing" C*\
Print in the style of C programs

*tee*\
Pipe and also redirect

*xargs*\
Transforms lines into arguments.

*jq*\
Select from JSON input

*jy*\
Select from yaml input

# Search for strings

*find . -size 10k -print*\
Prints files over 10kb

*find ~/ -type -d*\
shows all directories under ~/.

*find ~/ -type -d -ls*\
does ls on  all directories under ~/.

*find ~/sompathToSearch -iname "*.svg"*\
find all the files or directories that end in .svg in the \
~/somePathToSearch the search ignores case because of the \
-iname option, so it also finds\
SVG, SvG, SVg, sVG, Svg, sVg, and svG. The other option is to\
use -name if case matters to your search

*find ~/somePathToSearch -iregex '.*[a-z][^trs].*' *\
regex find (regular expressions) the .* which matches everything\
except newline any number of times (this is actually redundant.\
It's the default. Putting it here because I tend to forget).

*find ./ -name "*.old" -exec sh -c 'mv $0 `basename "$0" .old`.new' '{}' \;*\
replacing an extension with another using find in all subdirs:

*find ./ -name "*.old" -exec sh -c 'mv $0 `basename "$0" .old`' '{}' \;*\
Getting rid of the extension entirely:

*find . -name "*.py" -type f -exec grep -H "something" {} \;*\
Find and grep. grep -r does the same thing?

*grep ".*" files anotherFile AndSoOn*\
look for a string inside a file.

*egrep "(foo|bar)" file* \
Extended grep to find foo or bar in the file. It uses a different\
regex engine.

# Search and or manipulate strings 

*awk '{print $5}' file* \
This prints the fifth word of each line in a file. awk is a fully\
fleshed programming language that's useful for manipulating strings.\
It does much more than just this. Pretty much anything.

*sed s/foo/bar/g file*\
Sed is a streamlined editor command. This command replaces foo with\
bar in the file (actually outputs the new file with the changes to\
the standard output).

*sed -E s/foo/bar/g file* \
Use extended regex

*sed -i s/foo/bar/g file* \
Actually updates the file, which may be dangerous.

*cut -d ' ' -f 1*\
Choose spaces as a delimiter and grab the first field.

# ffmpeg to convert multimedia file formats 

*ffmpeg -i file.format file.otherFormat*\
convert file.format (the original file) to another format specified\
by the extension.

## for splitting videos (cutting videos):

*ffmpeg -ss start -t duration -i source.ext -vcodec copy -acodec copy out.ext*\

### Examples of splitting videos:
```
ffmpeg -ss 0 -t 100 -i source.m4v -vcodec copy -acodec copy part1.m4v
ffmpeg -ss 100 -t 100 -i source.m4v -vcodec copy -acodec copy part2.m4v  
ffmpeg -ss 200 -t 100 -i source.m4v -vcodec copy -acodec copy part3.m4v  
ffmpeg -ss 300 -t 100 -i source.m4v -vcodec copy -acodec copy part4.m4v
```

## joining videos (same codec):

1. Write the file names to be concatenated in a file. For example\
by doing this:

```
cat > files.txt
file 'part1.m4v'
file 'part2.m4v'
file 'part3.m4v'
file 'part4.m4v'
ctrl-d
```

2. Finally use this command:

*ffmpeg -f concat -safe 0 -i files.txt -c copy output.m4v*\

# Remote server stuff

*ssh user@host*\
connects to host as user. ssh means Secure shell implying you get\
a shell in the machine you're connecting to.

*whoami*\
Tells you your username. 

*id -un*\
Alternative to whoami

*hostname*\
Gives you the hostname of your machine.

*echo "$(whoami)@$(hostname)"*\
Gives useful info for ssh  (depends on the machine you're on).

*scp path/to/local_file remote_host:path/to/remote_file*\
Copy a file to a remote host

*scp remote_host:path/to/remote_file path/to/local_directory*\
Copy a file from the remote host to your current machine

*sftp user@host*\
Like ssh but used specifically to transfer files, its manpage shows\
how to use it.

# Docker

```docker run -it --rm ubuntu```\
```docker run -it --rm kalilinux/kali-rolling```\
Run some containers (emulate another operating system) and then\
imediately remove them.\

```docker pull debian:jessie```\
Pulls a single image from the docker registry.\

```docker run containerName```\
Create a container and run it. -it are useful. The -i flag for\
interactive. -t I don't remember for what.

```docker start containerName```\
Start a stopped container.\

```docker attach containerName```\
Attach to a dettached container.\

```docker stop containerName```\
Stop a running container.\

```docker rm containerName```\
Remove an existing container.\

```docker ps -a```\
show all containers\

```docker image list```\
List existing images\

```docker rmi image/name```\
Remove a downloaded image\

# Misc

```cal 5 1996```\
calendar for May 1996\

```date +%Y%m%d```\
tells you the date in years, month, and day\

```date +%H%M```\
tells you the time in hours and minutes?

```time commandName```\ 
a stopwatch for the command given as an argument.

```strace -tfp PID```\
traces system calls for the process indicated by the PID.

# Stuff with files 

```ls -la```\
lists all the files including .dot_files

```du -h```\
disk usage in human-readable form. GB instead of just bytes if that\
makes sense for instance.

```df -h```\
shows disk mounts.\

```touch afile```\
creates afile if it didn't exist before or updates its timestamp\
if it already existed in the working directory.

```alias ll='ls -l'```\
Now, when you type ll, ls -l takes its place.\

```unalias ll```\
unsets an alias...\

```ln -s ~/full/path/to/source ~/full/path/2/destination```\
creates a symlink, a shortcut to the source file.\

```less file```\
displays file page by page.\

# Archives and compression 

```tar cvf archive.tar.gz file1 file2 file3```\
compresses files and puts them in a tar archive.\

```tar -zxvf archive.tar.gz```\
uncompresses and untars all the files.\

```gunzip archive.tar.gz```\
uncompresses the tar archive. Result is archive.tar\

```tar -xvf archive.tar```\
untars.\

```which commandName```\
Where bash finds that command (somewhere in your path).

```basename /bin/ls```\
returns the stuff between the first / and the last one.\

```dirname /bin/ls```\
returns the stuff after the last /\

# Networking stuff 

```ifcongig -a```\
shows all the network adapters. NICs?\

```netstat -r```\
shows you the routers\

```netstat -a```\
shows the open ports\

# File redirection 

## file streams (like buffers for data)
- **0** is the code number for stdin
Input from your keyboard in this context.

- **1** is the code number for stdout 
Output to your screen.

- **2** is the code number for stderr
Where errors go to be ignored. Usually some file in /var/ or\
somewhere.

- `>` explicitly tells the command to the left where should the\
output go.

- `>>` Sends the output to the end of the file on the right hand\
side (appends to that file).

- The `<` in a command tells the file to its left where is the\
output coming from (usually a file to its right)

- The pipe in a command `|` means output from what's to the left\
of the pipe goes to the input of what's to the right of the pipe\
character.

## examples 

```cat fileX fileY 2>output```\
The errors from this command go to a file named output.

```cat fileX fileY 1>output```\
normal output is sent to a file named output.

```cat fileX fileY >output```\
Shorthand way of sending the normal output to a file named output.

```someCommad >command.out 2>&1```\
Output of the errors and normal output goes to commands.out. Basically\
combine the two types of output.

```cat < file ```\
cat gets the input from a file named file. I'm fun at parties.

```cat```\ 
When you do this, cat will get the input from standard input (your\
keyboard). Remember to type control-D to exit cat if you do this.\
C-d as the cool kids like to call the key combination inputs the\
EOF character, a special sequence of bits that indicates the 'End\
Of File'.

```ls *.png | grep '^particularPictureSetName.*'```\
The output of ls goes to grep.

# time-savers

```rm super_long_name[tab]```\
Tab autocompletes stuff that you're typing, so you'll see something\
like: rm super_long_name_califragilisticspialidocious

## Manipulating history
`!` repeats the last command `!string` repeats the last command\
that started with string. `!string:$` gets replaced by the last\
argument to the last command starting with string. There are a bunch\
of other which I can never remember.\

## emacs mode to edit commands on the fly:

- In emacs mode, pressing control-r and typing 'string' will show\
you the last command that starts with string. repeat pressing\
control-r to scroll through the list.

- In emacs mode, typing control-u deletes everything before the\
cursor

- In emacs mode, typing control-k deletes everything after the\
cursor.

- alt-delete deletes words.

- control-d deletes letters after the cursor.

- alt-d deletes words after the cursor. (When I say words I mean\
anything delimited by space characters.)

# You can download a command called youtube-dl to save your videos from youtube:
```noglob youtube-dl 'https://www.youtube.com/watch?=some_valid_url'```

## Get only the sound:
```youtube-dl -x --audio-format mp3 'https://www.youtube.com/watch?=some_valid_url'```

# Sysadmin

```adduser userName userGroup```\
```useradd```\
to Create User. `useradd` is for doing it the hard way.

```su - <user>```\
to "Login" as User

```deluser```\
and userdel to Delete User

```usermod```\
to Modify User Settings

```addgroup```\
and groupadd to Create Group

```delgroup```\
and groupdel to Delete Group

```groupmod```\
to Modify User Settings

```passwd```\
to Change Passwords

```id```\
to Get the User and Group Information\

```login```\
to Login\

```sudo```\
su - to Get Root Shell\

```doas```\
-s to Do Something As Root\

```who,w,whoami,who```\
am i,last to See Users\

```ls```\
-l to See Permissions\

```chmod```\
to Change Permissions\

```chown```\
to Change Owner (and Group)\

```chgrp```\
to Change Group\

## Don't use Setuid, Setgid, and such according to rwxrob.
