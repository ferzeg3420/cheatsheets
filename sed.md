# sed regex table

| Symbol | Matches |
| ----------- | ----------- |
| `^` | beginning of a line. |
| `$` | end of a line. |
| `[A-Za-z\-#]` | matches one in the set. |
| `[^slkfdj]` | matches one not in the set. |
| `.` | matches anything except a new line. |
| `*` | zero or more of the previous thing |
| `\(...\)` | capture group. |
| `&` | the character that invokes the entire match in a replacement. |
| `\<` | beginning of a word. |
| `\>` | end of a word. |
| `x\{n\}` | repeats x n times. |
| `x\{n,\}` | repeats x at least n times. |
| `x\{n,m\}` | repeats x at least n times but no more than m times. |
| `[[:space:]]` | matches space in this macos in 2020. |

# Deleting stuff

```
sed '1,3d' file
```
delete lines 1 through 3. 

```
sed '3,$d' file
```
delete lines 3 to the end. 

```
sed '/[Pp]attern/d' file
```
delete lines that contain the pattern.

```
sed '/[Pp]attern/!d' file
```
delete lines that contain the pattern. 

```
sed '$d' file
```
delete the last line in file. 

# Replacing (chaging) stuff

```
sed 'c/string/completely new line/' file
```
finds the lines that match string and complately replaces them with\
a new line that says completely new line.


# Printing stuff

```
sed '/[Pp]attern/p' file 
```
print lines that match, like grep. Prints all the other lines as\
well so it only repeats the matches.

```
sed -n '/[Pp]attern/p' file
```
only prints the matches, exactly like grep.

```
sed '/fer/,/miguel/'
```
print a range of lines from the first line that contains the string\
fer to the next first line that contains miguel.


# Replacing stuff

```
sed 's/string/replacement/' file
```
substitute only one occurrence of string.

```
sed 's/string/replacement/g' file
```
substitutions are global across the line, substitutes all instances\
of string with replacement.

```
sed 's/sugar/&cane/' file
```
the & takes what was matched and repeats in in the replacement\
string.

```
sed 's/\([Ff]er\)nando/\1dinand/' 
```
Replaces my name with ferdinand. \1 stores what was matched in the
parenthesis \(this is stored\).

```
sed -n 's/string/replacement/'
```
only prints the lines where the substitution happened.

# File I/O

```
sed '/string/r file2' file
```
reads the contents of file2 after a line in file where string is\
matched.

```
sed '/string/w file2' file
```
writes the lines matching string in file to file2

# inserting and appending

```
sed '/string/i\\
---------------\\
  Header\\
---------------' file
```
Inserts a the header before the line matching string.

```
sed '/string/a\\
---------------\\
  Footer\\
---------------' file
```
Inserts a footer after the line matching string.

# The next and quit commands

```
sed '/string/{n; s/otherString/replacement/;}' file
```
finds the line matching string and then goes to the next line and\
replaces otherString for replacement.

```
sed '/string/q' 
```
stops printing when it finds string.

```
sed '123q' 
```
stops printing at line 123.


# MISC

```
sed 's#pattern#sub#'
```
You can use other characters as a delimiter besides /.

```
sed '/[Vv]inci/,/[Bb]uonarroti/s/enemy/friend/'
```
You can chain commands.

```
sed -e 's/red/green/' -e 's/blue/cyan/'
```
a way to do multiple edits.

```
sed '1,10y/abcd/ABCD/' file
```
for lines 1 through 10 a becomes A, b -> B, and so on up to d.

```
sed '/fernando/h' -e '$G'
```
stores the line that contains fernando and then when the very last\
line is reached it is printed afterwards.

```
sed '/fernando/h' -e '$g'
```
stores the line that contains fernando and then the very last line\
is replaced by the stored line.
