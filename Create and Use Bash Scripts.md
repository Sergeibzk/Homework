#How to Create and Use Bash Scripts

[Link to article and author](https://www.taniarascia.com/how-to-create-and-use-bash-scripts/)

###Create your first script


Create a file __hello-world__ with a string

```
echo "Hello, world!"
```

Now from the command line, run the script using the bash interpreter:

```
bash hello-world
```

The script run successfully!

```
Hello, world!
```

###Executable Scripts

If you want to run the script by name alone:

```
$ ./hello-world
```

Change the permissions to allow the script to be executable for the user

```
$ chmod +x hello-world
```

Find, where the bash interpreter is located

```
$ which bash
```

Make file executable by adding first string with __#!__

```
#!/usr/bin/bash

echo "Hello, world!"
```

Run hello-world file directly

```
$ ./hello-world
```

_response in terminal_

```
Hello, world!
```

###Strings

Wrapping quotes in string by wrappin string in opposite quotes

```
echo 'A single quoted "string"'
echo "A double quoted 'string'"
```

_response in terminal_

```
A single quoted "string" 
A double quoted 'string'
```

With the -e flag, bash will interpret strings with backslash-escaped characters, such as \n for newline

```
echo -e "This string has a \nnew line"
```

_response in terminal_

```
This string has a 
new line
```

###Variables

Example when a variable used for the entity being greeted, which is World

```
#!/bin/bash

who="World"

echo "Hello, $who!"
```

_response in terminal_

```
Hello, World!
```

Within a single quoted string, the dollar sign would be interpreted literally

Ver. 1

```
echo 'Hello, $who!'
```

Ver. 2

```
echo "Hello, ${who}!"
```

_response in terminal same for ver.1 and 2_

```
Hello, World!
```

###Shell Execution

Using the output of a shell execution within a string.
For example the __whoami__ command will print out your current user

```
$ echo "Hello, $(whoami)!"
```

_response in terminal_

```
Hello, sergeibzk!
```

###User Input

Making script that asks for the name of the person calling the script

```
#!/bin/bash

echo 'Who are you?'

read who

echo "Hello, $who!"
```

_response in terminal_

```
Who are you? > Sergei 
Hello, Sergei!
```

###Conditions

__if__ statements use the __if__, __then__, __else__, and __fi__ keywords. The condition goes in square brackets

```
#!/bin/bash

echo 'How old are you?'

read age

if [ $age -gt 20 ]
then
    echo 'You can drink.'
else
    echo 'You are too young to drink.'
fi
```

_response in terminal_

```
How old are you? > 30 
You can drink.
```

###Loops

Bash uses __for__, __while__, and __until__ loops. In this example, I'll use the __for...in__ loop to get all the files in a directory and list them

```
#!/bin/bash

files=/Users/you/dev/*

for file in $files
do
  echo $(basename $file)
done
```

_response in terminal_

```
Desktop Documents Downloads hello-world Music Pictures Public Templates Videos
```

###Arrays

An array in bash is defined inside parentheses. There are no commas between the items of the array. Arrays are 0-indexed in bash

```
beatles=('John' 'Paul' 'George' 'Ringo')

echo ${beatles[3]}
```

_response in terminal_

```
Ringo
```