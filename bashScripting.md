---
title: BASH
---

# Bash Scripting

###  CREATING A SCRIPT

To make a script executable type the following into the command prompt
Remember: that you have to be in the same directory as your script.

```
chmod +x hello_world.sh
```

In the command prompt (or inside a script)
type the following to run a script
Remember: that you have to be in the same directory as your script.
```
./hello_world.sh
```

if you're not in the same directory and know the path you can do:
```
path/hello_world.sh
```

- To get bash to interpret a script write the following as the first non-empty line in a script.
```
##!/bin/bash 
```
The pound sign, #, indicates comments in bash, but in the case of the first 
line in a file, this is a directive to run the bash interpreter.

## INCLUDING A SCRIPT

```
##!/bin/bash
source script.sh 
```
This includes script.sh if it's in the same directory as the
current script.

## VARIABLES

Bash variables are dynamic and weakly typed, meaning the types are 
determined at runtime and that the variables are allowed to vary.
That is, an int can become a string.

### create a variable.
```
NUM=1
```

### the dollar before the identifier dereferences the variable.
```
let "NUM=$NUM+1"
[ $NUM -eq 1 ] 

STRING="HELLO WORLD!!!"
echo $STRING
```

### to make a variable local to a function:
```
local VAR="something"
```

## LIST OF PRESET VARIABLES

```
$SHELL
```
tells you what shell you're running.

```
$RANDOM
```
generates random numbers.

```
$$
```
pid of the current process.

```
##$-
```
shell options currently set. Currently doesn't work in BASH? 

```
$?
```
exit status of the last command.

```
$!
```
pid of the background command.

## PASSING ARGUMENTS TO A SCRIPT

You can use predefined variables to access passed arguments.\
For example inside a script file you can do this:

```
echo echoing the arguments to the shell:
echo $1 $2 $3

echo echoing the name of this script.
echo $0
```

### You can also store arguments from bash command line in special array
```
args=("$@")
```

### echo arguments to the shell
```
echo ${args[0]} ${args[1]} ${args[2]}
```

### use $@ to print out all arguments at once

```
echo $@ 
```

### You can also use $\* to print out all arguments at once

```
echo $* 
```

```
echo "$*"
```
evaluates to "$1 $2 $3..."

```
echo "$@"
```
evaluates to "$1" "$2" "$3" ...

### print the number of arguments passed to a script
echo Number of arguments passed: $#

##  EXECUTING COMMANDS IN A SCRIPT

You can use backticks \` \` to use the output of a command as an argument for another command
```
echo `uname -o`
```

```
echo $(uname -o)
``` 
is another option to do the same.

##  READING USER INPUT

```
echo "Hi, please type a word:"
read  word
echo "The word you entered is: $word"
echo -e "Can you please enter two words? "
read word1 word2
echo "Here is your input: \"$word1\" \"$word2\""
echo -e "How do you feel about bash scripting? "
```

### The read command stores the user's reply iny the default build-in variable $REPLY

```
read
echo "You said $REPLY"
```

### The -a flag makes the read command, read inputs into an array
read -a colours
```
echo "My favorite colours are also ${colours[0]}, ${colours[1]} and\
    ${colours[2]}"
```

## TRAPS

```
trap aFunction INT
```

### The aFunction is executed when CTRL-C is pressed:
```
aFunction()
{
    echo "CTRL+C Detected"
}
```

### for loop from 1 to 10
```
for a in `seq 1 10`; do
    echo "$a/10 to Exit." 
    sleep 1;
done
```

### Signal numbers and signals

```
 1)HUP      12)SYS      23)POLL
 2)INT      13)PIPE     24)XCPU
 3)QUIT     14)ALRM     25)XFSZ
 4)ILL      15)TERM     26)VTALRM
 5)TRAP     16)URG      27)PROF
 6)IOT      17)STOP     28)WINCH
 7)EMT      18)TSTP     29)LOST
 8)FPE      19)CONT     30)USR1
 9)KILL     20)CHLD     31)USR2
 10)BUS     21)TTIN     
 11)SEGV    22)TTOU     
```

```
trap 2 resets the default action for SIGINT.
```

```
trap "" 1 2
```
The empty "" makes the SIGHUP and SIGINT be ignored.

## ARRAYS

### Declare array with 4 elements
```
ARRAY=( 'Debian Linux' 'Redhat Linux' Ubuntu Linux )
```

### get the number of elements in the array
```
ELEMENTS=${## ARRAY[@]}
```

### store the result of a command in an array.
```
ARRAY=($(du -h *.cpp))
```

### for loop through array
```
for (( i=0;i<$ELEMENTS;i++))
do
    echo ${ARRAY[${i}]}
done
```

## READ A FILE INTO BASH ARRAY

### Declare an array
```
declare -a ARRAY
```

### Link the file descriptor 10 with stdin
```
exec 10<&0
```

### stdin replaced with a file supplied as a first argument
```
exec < $1
let count=0

while read LINE
do
   ARRAY[$count]=$LINE
   ((count++))
done

echo Number of elements: ${## ARRAY[@]}
```


### echo array's content
```
echo ${ARRAY[@]}
```

### restore stdin from filedescriptor 10 and close filedescriptor 10
```
exec 0<&10 10<&-
```

### READ & PROCESS A FILE LINE BY LINE

```
while read -r line
do
   echo "$line"
done < /path/to/file.txt
```

## BASH IF / ELIF / ELSE / FI STATEMENTS


### bash check if directory exists

```
directory="./someDir"
dir2="./someOtherDir"

if [ -d $directory ]
then
   echo "Directory exists"
elif [ -d $dir2 ]
then
   echo "dir2 exists"
else
   echo "Directory does not exists"
fi
```

if you have nothing to do after a 'then' you have to use the nop operator which is a colon.

```
directory="./someDir"
if grep "$name" file > /dev/null 2>&1
then
   :   
else
   echo "$name not found in the database."
fi
```

## BASH FILE TESTS

```
boolExpr -a boolExpr # -a is the and operator.
boolExpr -o boolExpr # -a is the or operator.
! boolExpr ## is the negation operator. (formal logic's not)

-b filename	Block special file
-c filename	Special character file
-d directoryname	Check if directory exists
-e filename	True if a file exists
-f filename	True if a regular file exists
-G filename	True if file exists and is owned by the effective group ID.
-g filename	true if file exists and is set-group-id.
-k filename	Sticky bit?
-L filename	Symbolic link?
-O filename	True if file exists and is owned by the effective user id.
-r filename	True if file is a readable
-S filename	True if file is socket
-s filename	True if file is nonzero size
-u filename	True if file set-ser-id bit is set
-w filename	True if file is writable
-x filename	True if file is executable
```

### File test example:
```
file="./file"
if [ -e $file ]
then
   echo "File exists"
else 
   echo "File does not exist"
fi
```

### ARITHMETIC TESTS

```
-lt	less than
-gt	greater than
-le	less than or equal
-ge	greater than or equal
-eq	equal
-ne	not equal
```


### declaring integers
```
NUM1=2
NUM2=2
if [ $NUM1 -eq $NUM2 ]
then
    echo "Both Values are equal"
else 
    echo "Values are NOT equal"
fi
```

### STRING TESTS

```
=	equal
!=	not equal
=~      Equal that allows pattern matching requires [[ test  ]] format.
<	less than
>	greater than
-n s1	string s1 is not empty
-z s1	string s1 is empty
```
```
for VAR in *.[PpJj][NnPp][gG]
do
   imgcat "${VAR}"
   echo "Should ${VAR} be put in the trash? "
   read USER_ANSWER
   if [[ ${USER_ANSWER} =~ [Yy][Ee][Ss]|[Yy] ]]
   then 
      mv "${VAR}" ~/.Trash
   fi
done
```

## LOOPS: WHILE, UNTIL AND FOR

### bash for loop
```
for nickame in Fer Fernan Ferdy Nando NANDo NAND
do
   echo $nickname
done 
```

```
for counter in {1..10}
do
   echo $counter
done
```

### you can do metacharacter expansion
```
for file_in_pwd in *
do
    echo $file_in_pwd
done 
```

```
for line in `cat mylist`
do
    echo $line
done 
```

```
for file_name in "$( ls /var/ )"
do
    echo $file_name

    continue ## skips the rest of the do-done loop/block.
    break ## exits, breaks, out of the loop.
done 
```

### bash for loop through files ending in .pdf in the working directory.

```
for pdf_file in *.pdf 
do
    mv $pdf_file ~/.Trash
done
```

### bash for loop with ranges

```
for value in {1..5}
do
    echo $value
done 
```

### bash for loop with ranges and steps

```
for value in {10..0..2}
do
    echo $value
done 
```

### bash while loop

```
COUNT=6
while [ $COUNT -gt 0 ]
do
   echo Value of count is: $COUNT
   let COUNT=COUNT-1
done
```

```
while read line
do
   echo $line
done
```

### bash until loop

```
COUNT=0
until [ $COUNT -gt 5 ]
do
   echo Value of count is: $COUNT
   let COUNT=COUNT+1
done
```

##  BASH FUNCTIONS

### BASH FUNCTIONS should be declared at the top. (since scripts are
### interpreted line by line.)

```
foo() {
   echo foo
}
```

```
bar() {
   local var=$1
   echo ${var}
}
```

```
baz() {
   local var=42
   echo ${var}
}
```

```
qux() {
   all_args=("$@")
}
```

```
function deprecated_function_creation {
    echo not posix compliant but prevents alias collision
}
```

```
function parens_optional() {
    echo parenthesis after the function name are optional when using \
         the function keyword
}
```

### FUNCTION CALLS

#### calling a function
foo

#### Passing an argument to a function
bar "argument"

#### getting the return value from a function

```
VALUE=$(return_value)
```

#### You can store your functions on a separate file

Then use the `source` command to have them available on another file.

## BASH SELECT

```
OPERATING_SYS='Ubuntu Mint freeBSD UNIX Quit'
PS3='Select an operating system: ' 

select OS in $OPERATING_SYS 
do
  if [ $OS == 'Quit' ]
  then
      break
  fi
  echo "You selected ${OS} operating system."
done

exit 0 
```

## CASE

```
echo "What is your preferred programming / scripting language"
echo "1) bash"
echo "2) perl"
echo "3) phyton"
echo "4) c++"
echo "5) I do not know !"
read case;
case $option in
    1) echo "You selected bash";;
    2) echo "You selected perl";;
    3) echo "You selected phyton";;
    4) echo "You selected c++";;
    5) exit
esac
```

```
echo -n "What's your favorite color? "
read color;
case "$color" in
[Bb]l??)
   echo I feel $color
   echo The sky is $color
[Gg]ree*)
   echo $color is for trees
   echo $color is for seasick
red|orange)
   echo This color is warm
*) echo No such color
```

## USING QUOTES

### Single quotes

Single quotes in bash will suppress the special meaning of every meta
character. Therefore meta characters will be read literally. It is
not possible to use another single quote within two single quotes not
even if the single quote is escaped by a backslash.

### Double Quotes

Double quotes in bash will suppress the special meaning of every meta
character except "$", "\" and "`". Any other meta characters will be
read literally. It is also possible to use a single quote within double
quotes. If we need to use double quotes within double quotes bash can
read them literally if we scape them with the back slash "\".

### Back quotes

Everything inside back quotes is interpreted as a command: `date +%Y`

## ARITHMETIC

### bash addition
```
let ADDITION=3+5
echo "3 + 5 =" $ADDITION
```

### bash subtraction

```
let SUBTRACTION=7-8
echo "7 - 8 =" $SUBTRACTION 
```

### bash multiplication

```
let MULTIPLICATION=5*8
echo "5 * 8 =" $MULTIPLICATION
```

### bash division
```
let DIVISION=4/2
echo "4 / 2 =" $DIVISION
```

### bash modulus
```
let MODULUS=9%4
echo "9 % 4 =" $MODULUS
```

### bash power of two
```
let POWEROFTWO=2**2
echo "2 ^ 2 =" $POWEROFTWO
```


### There are two formats for arithmetic expansion:
- `$[ expression ]` 
-  `$(( expression #))`

```
echo 4 + 5 = $((4 + 5))
echo 7 - 7 = $[ 7 - 7 ]
echo 4 x 6 = $((3 * 2))
echo 6 / 3 = $((6 / 3))
echo 8 % 7 = $((8 % 7))
echo 2 ^ 8 = $[ 2 ** 8 ]
```

## Declare variables and read user input

```
echo -e "Please enter two numbers \c"
read num1 num2
declare -i result
result=$num1+$num2
echo "Result is:$result "
```

## Conversions in bash

### bash convert binary number 10001 to decimal 17?
```
result=2#10001
echo $result
```

### bash convert octal number 16 to decimal 22?
```
result=8#16
echo $result
```

### bash convert hex number 0xE6A to decimal ...?
```
result=16## E6A
echo $result 
```

### arithmetic with floating point numbers:
```
floatingPoint=$(echo "scale=2;3.4+43.1" | bc)
```

## FLAGS

```
a_flag=''
b_flag=''
files=''
verbose='false'

function print_usage() {
  printf "Usage: ..."
}

while getopts 'abf:v' flag
do
  case "${flag}" 
  in
    a) a_flag='true' ;;
    b) b_flag='true' ;;
    f) files="${OPTARG}" ;;
    v) verbose='true' ;;
    *) print_usage
       exit 1 ;;
  esac
done

if [ $OPTIND -eq 1 ]
then
   echo "NO_ARGS_PASSED <---"
fi
```

What is happening to the f, which has an arugment is the following:
```
"When the option requires an option-argument, the getopts utility
 shall place it in the shell variable OPTARG. If no option was found,
 or if the option that was found does not have an option-argument,
 OPTARG shall be unset." (getopts manpage)
```

## SHELL METACHARACTERS AND FILENAME SUBSTITUTION

Assume the following exist in your directory:
```
ls 
>abc abc122 abc2 file.bak file2.bak nonsense nothing one abc1 file1 file 2
>abc1 abc123 none noone nowhere file2
```

```
ls file?
>file1 file2
```

```
ls abc[123]
>abc1 abc2
```

```
ls abc[1-3]
>abc1 abc2
```

```
ls [a-z][a-z][a-z]
>abc one
```

```
ls [!f-z]???
>abc1 abc2
```

```
ls abc12[23]
>abc122 abc123
```

```
ls file*
>file file1 file2 file.bak file2.bak
```

### escaping metacharacters
Assume this file are in your current directory:

```
ls
>abc file1 file2 youx
```

```
echo How are you?
>How are youx
```

```
echo How are you\?
>How are you?
```

```
expr 23 \* 2
>46
```


### return the process number of a script.
```
echo $$  >1313
```

### return the exit value of the last command. 
```
echo $? >0
```

### The local keyword makes a variable local to a function 
```
local immutable='constant?' 
```

### Make a variable immutable. You can't change its value.
```
readonly immutable 
immutable='variable?'
>bash: immutable: readonly variable
```


### eval is used to do the variable substitution twice for a command.
```
echo "\$\?"
> $?
eval echo "\$\?"
> 0
```

#### eval only affects the one command that it is attached to:
```
eval echo "\$\?"; echo "\$\$"
>0
>$$
```

## VARIABLE EXPANSION MODIFIERS

### If 'variable' is set, substitute its value. Otherwise use word.
```
${variable:-word}
```

### Same as :- but word is substituted permanently, it becomes the new value of variable.     
```
${variable:=word}
```

### if variable is set and nonnull use 'word' instead. Otherwise do nothing.
```
${variable:+word}
```

### If 'variable' is set and nonnull substitute it. Otherwise use word and exit
```
${variable:?word}
```

## OVERVIEW OF A FEW PARAMETER EXPANSION MODES

### delete shortest match of pattern from the beginning
```
${MYVAR## pattern}     
```

### delete longest match of pattern from the beginning
```
${MYVAR### pattern}
```

### delete shortest match of pattern from the end
```
${MYVAR%pattern} 
```

### delete longest match of pattern from the end
```
${MYVAR%%pattern} 
```

So ## means match from the beginning (think of a comment line) and %
means from the end. One instance means shortest and two instances
means longest.

- You can get substrings based on position using numbers:

### Remove the first three chars (leaving 4..end)
```
${MYVAR:3}
```

### Return the first three characters
```
${MYVAR::3}
```

### The next five characters after removing the first 3 (chars 4-9)
```
${MYVAR:3:5} 
```

You can also replace particular strings or patterns using:

```
${MYVAR/search/replace}
```
## Parameter expansion examples:

### Given a variable like:
```
MYVAR="users/joebloggs/domain.com" 
```

### Remove the path leaving file name (all characters up to a slash):
```
echo ${MYVAR##*/}
domain.com
```

### Remove the file name, leaving the path
```
echo ${MYVAR%/*} 
users/joebloggs
```

### Get just the file extension (remove all before last period):
```
$echo ${MYVAR##*.}
.com
```

- NOTE: To do two operations, you can't combine them, but have to assign
to an intermediate variable. So to get the file name without path or
extension:

- NAME=${MYVAR##*/}      # remove part before last slash
echo ${NAME%.*} # from the new var remove the part after the last
period domain

## SOURCES

- SOURCE OF MOST OF THIS CHEATSHEET:
- https://linuxconfig.org/bash-scripting-tutorial
Kudos to the person who wrote it (it just says admin for the author).

- source of the getopts section:
Dennis on Stack Overflow

- source of the parameter expansion modes:
beroe on Stack Overflow

- Unix Shells by example by Ellie Quigley

- ryanstutorials.net
