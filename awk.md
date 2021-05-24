# Definitions

Record
: is by default everything till a newline character. i.e. the entire line.\

Field
: by default, is any group of characters separated by spaces.\

## Record and field example:
```
This entire line would be a record.
```
- The word `This` in the last line would be field one.
- The word `entire` would be the second field.

# Some preset variables:

- `$0` stores the current record
- `$1` the first field in the current record
- `$2` the second, `$3` third, and so on


# Basic usage

## search for a pattern and then do sth.
```awk 'pattern{action}' file```\

For Example:
```awk '/[Ll]etter/{printf $1}' paper```\

## Print the line if the 4th field > 7500.
```df | awk '$4 > 7500'```\
*df* displays the free diskspace in a strange format.

## Prints the line if the 4th field equals 100.
```awk '$4 == 100'```\

## A `date` Examples with fields
```date | awk '{print "Month: " $2 "\nYear: " $6}```\

## Format a string. Prints: |           UNIX|
```echo "UNIX" | nawk '{printf "|%15s|\n", $1}'```\

## Print something that matches the first field
```awk '$1 ~ /SomethingInField1/' file```\

## Print something that doesn't match the first field
```awk '$1 !~ /SomethingInField1/' file```\

## Change the field separator with an arg to awk
```awk -F: '/semicolonIsNowTheFieldSeparator/' file```\
The new field separator is now *:*

## Use a semicolor *;* to separate lines of awk code
```awk '{max=($1 > $2) ? $1 : $2 ; print max}' file```\

## Create a variable by just mentioning it
```awk 'BEGIN{var=0; print var}' file```\
BEGIN block is executed before the file is processed by awk line by line.

## Count occurrences of the word *Fernando*
```awk '/[Ff]er(nando)?|[Nn]ando/ {mentions++; print mentions}' file```\

## format of the print command with OFMT
```awk 'BEGIN{OFMT="%.2f"; print 3.141516}' filename``` 

## Use OFS, the output field separator and ORS as the output record separator.
```awk 'BEGIN{FS=":";OFS="\t";ORS="\n\n"}{print $1, $2, $3}' file```\

## Use END block to run code that is executed after the file is processed.
```awk 'END{print "The number of records is" NR}' file```\
```awk '/[Ff]er.* /{count++}END{print "I was mentioned" count "times."}' file```\

## Send output to a different file.
```awk '$4 >= 60 {print $1, $2 > "another_file"}' file```\

## Use getline to get lines.
```awk 'BEGIN{"date" | getline d; print d}' file```\

## Use *split* to split a line, putting the fields in an array. 
```awk 'BEGIN{"date" | getline d; split(d, mon); print mon[2]}' file```\
In this case the array is called mon. Lazy_typist for month.

## Get the results of ls to print using getline.
```awk 'BEGIN{while("ls" | getline) print}' file```\

## get a line from another file. Store in name.
```
awk 'BEGIN{printf"What is your name?"; getline name <"/dev/tty"};\
     $1 ~ name {print "Found" name "on line", NR "."}\
     END{print "See you, " name "."} file 
```

## reverse sort using $1 and $2 as tiebreaker 
```awk '{print $1, $2 | "sort -r "}' file```\

# Flow Control 

## If, else if, and else statements

### use an if 
```awk '{if ($1 > 5) print NR}' file```\

### use an if and increase a counter
```awk '{if ($1 > 5) {print NR; count++}}' file```\

### use else 
```awk '{if ($1 > 5) print NR; else print "No good"}' file```\

### use if, a counter, and use an else 
```awk '{if ($1 > 5) {print NR; count++} else {print "No good" o_count++}}' file```\

### use if, counters, else if, and else 
```
awk '{if ($3 > 89) A++;\
      else if ($3 > 79) B++;\
      else if ($3 > 69) C++;\
      else F++}' file
```

### use if, counters, else if, and else is also valid without semicolons
```
awk '{if ($3 > 89) {A++}\
      else if ($3 > 79) {B++}\
      else if ($3 > 69) {C++}\
      else {F++} }' file
```

## Loops

### loop *while* the number of records is greater or equal to i
```awk '{i = 1; while (i <= NR) {print NF, i ; i++}}```\

### for loop while the number of records is greater or equal to i
```awk '{for (i = 1; i <= NR; i++) {print NF, i}}```\

### *Break* out of a loop 
```awk '{for (i = 1; i <= NR; i++) {if ($i == 10) break }```\

### skip the rest of a loop using *continue* 
```awk '{for (i = 1; i <= NR; i++) {if ($i == 5) continue }```\

### Print the third field of every record using a loop after processing the file 
```
awk '{id[NR]=$3};END{for(x = 1; x <= NR; x++)\
      print id[x]}' file
```

### Print my name a bunch of times? using for in syntax
```awk '/^[Ff]er/ {Name[NR]=$1};END{for(i in name){print name[i]}' file```\

### Loop through associative array to show number of ocurrances of the second field
```awk '{count[$2]++} END{for(name in count){print name, count[name]}' file```\

# How to create a script 

Name your script *something*.sc and put your commands there like follows:
```
/tom/ { count["tom"]++}
/mary/ { count["mary"]++ }
END{print "There are" count["tom"] "Tom's in the file and
" count["mary"]"Mary's in the file."}
```

# How to run a script:
```
% nawk -f awk.sc datafile
```

# user defined functions

## in a script:
```
function name (param, param, ...} {
   statments
   return expression #return is optional
}
{name(1,2,3,4,5)}
```

# Built-in string functions

| Function | Description |
| ----------- | ----------- |
| `delete(array[elem])` | deletes an array element |
| `split("line", array, "delimeter")` | takes a line and puts fields in an array. |
| `length("string")` | gets the length of the string |
| `sub(/regex/, "substitute")` | Substitutes the 1st intance of regex with the string. |
| `gsub(/regex/, "substitute")` | Subs all instances of regex with substitute |
| `index("string", "substring")` | Returns the index of the 1st instance of substring in string. |
| `substr("string", start, length)` | Returns the substring starting at start and up to length. |
| `match("string", /regex/)` | Returns the index where a regex is found |


# Built-in Variables 

| Variable | Description |
| ----------- | ----------- |
| ARGC | number of command line args |
| ARGV | array of command line args |
| FILENAME | name of the current input file |
| FNR | record number in current file |
| FS | The input field separator (space by default) |
| NF | number of fields in the current record |
| NR | number of records so far |
| OFMT | output format for numbers |
| OFS | output field separator |
| ORS | output record separator |
| RLENGTH | length of string matched by match function |
| RS | input record separator |
| RSTART | offset of string matched by match function |
| SUBSEP | subscript separator |


# Regular expressions 

| Symbol | Matches |
| ----------- | ----------- |
| `^` | Beginning of a line (record) |
| `$` | End of a line (record) |
| `.` | Anything except the newline character |
| `*` | zero or more of what came B4 |
| `+` | One of more of what came B4 |
| `?` | One or none of what came before |
| `[ABZ]` | Matches anything within the brackets |
| `[^ABZ]` | Matches anything no within the brackets |
| `[A-Z]` | Anything in the range (ascii range may not be what you are thinking) |
| `A|B` | A or B |
| `(AB)` | The set e.g. (AB)+ matches ABABAB |
| `\*` | Literal string |
| `&` | Used as the replacement string. Stores the match. |

# Conversion characters for the printf command 

| Symbol | Matches |
| ----------- | ----------- |
| c | character |
| s | string |
| d | decimal number |
| ld | long decimal |
| u | unsigned number |
| lu | long unsigned |
| x | hexadecimal number |
| lx | long hexadecimal  |
| o | octal |
| lo | long octal |
| e | scientific notation |
| f | floating point number |
| g | float using something weird. |


# Modifiers for the prinft command 

| Symbol | Description |
| ----------- | ----------- |
| - | Left justification  |
| # | leading 0 for decimal/ocatl or 0x for hex |
| + | For conversion? |
| 0 | pad with zeros. |


# Escape sequences for the print command

| Symbol | Description |
| ----------- | ----------- |
| `\n` | newline character |
| `\t` | tab character |
| `\f` | form feed |
| `\b` | backspace (kinda useless?) |
| `\r` | carriege return |
| `\047` | Octal value (don't know how that works) |
| `\c` | Represents any other char? |


# Built-in arithmetic functions

| Symbol | Description |
| ----------- | ----------- |
| atan2(x, y) | arctangent of y/x i the range |
| cos(x) | cosine of x, x in radians |
| exp(x) | exponential function of x,e |
| int(x) | integer part of x truncated down |
| log(x) | natural (base e) log of x |
| rand() | random number 0<r<1 |
| sin(x) | sine of x input in radians |
| sqrt(x) | square root of x |
| srand(x) | x is a new seed for rand() |

