
## Syntax

A bash script must always start with the shebang line which indicate the path to the interpreter:<br>
`#!/bin/bash`

## Conditional statements

### if-else-fi

```
if [ condition 1 ]
then
	specific action...
elif [ condidition 2]
then
	other specific action...
else
	default action...
fi
```


### Case

Case statement always compares the variable with the exact value and so comparison like greater or less are not compatible with case.<br>
```
case <expression> in
	pattern1 ) expression;;
	pattern2 ) expression;;
esac
```

## Variables

### Special variables

Bash automatically store the nine first arguments in the first 1 to 9 variable (0 being the script name).<br>
We can access them using the '$' sign.<br>
The '#' variable is the number of arguments.<br>
The '@' variable is the list of given arguments.<br>
The '$' variable is the process ID of the currently executing process.<br>
The '?' variable is the exit code of the previously executed script or program.<br>
### Variables

To assign a value to a variable we do not use the '$' sign and there must be no spaces between the '=' sign and the value:<br>
`var=3`

There is no type specification in bash all variables are strings and will be treated as number if asked or if it only contains numbers.<br>
### Arrays

To create and assign values to an array we use '()':<br>
`array=(value1 value2 value3)`

We can retrieve a value using its index:<br>
`echo ${array[1]}`

## Operators

### Strings

For strings we can use theses operators:<br>

| op  | meaning                |
| --- | ---------------------- |
| ==  | equal to               |
| !=  | different from         |
| >   | greater in ASCII order |
| <   | less in ASCII order    |
| -z  | string is empty        |
| -n  | string is not empty    |

We need to put the variable in double quotes to indicate that it is a string.<br>
The '>' and '<' operators only works inside double brackets:<br>
`if [[ "$1" > "test" ]]`

### Integers

When working with integers we can use these operators:<br>

| op  | meaning          |
| --- | ---------------- |
| -eq | equal            |
| -ne | non equal        |
| -lt | less             |
| -le | less or equal    |
| -gt | greater          |
| -ge | greater or equal |

With theses operators we also indicate to bash that we are dealing with integers.<br>
### Files

With files we can use theses operators:<br>

| op  | meaning                                                 |
| --- | ------------------------------------------------------- |
| -e  | if the file exist                                       |
| -f  | test if it is a file                                    |
| -d  | test if it is a directory                               |
| -L  | test if it is a symbolic link                           |
| -N  | check if the file was modified after it was read        |
| -O  | check if the current user owns the file                 |
| -G  | check if the file's group id matches the current user's |
| -s  | test if the file has a size greater than 0              |
| -r  | test if the file has read permissions                   |
| -w  | test if the file has write permissions                  |
| -x  | test if the file has execute permissions                |

### Logical operators

We can use these three logical operators:<br>

| op   | meaning  |
| ---- | -------- |
| !    | negation |
| \|\| | or       |
| &&   | and      |

### Arithmetic operators

In bash we can use all basics arithmetic operators like '\*' '/' or '++' and '--'.<br>
We can also get the length of a variable using this syntax:<br>
`len=${#var}`

We use double parenthesis for arithmetic operation and also to use C style syntax.<br>
## Loops

### For loops

```
for var in list
do
	actions...
done
```

### While loops

```
while [ condition ]
do
	actions...
done
```

We can use the keyword `break` to get out of a loop or the `continue` keyword to go straight to the next iteration><br>
### Until loops

```
until [ condition ]
do
	actions...
done
```

## Functions

Functions are declared like this:<br>
```
funtion name {
	commands
}
```

or:<br>
```
name() {
	commands
}
```


