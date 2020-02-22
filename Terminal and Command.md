## basic knowledge

Users access the bash shell through a terminal. A terminal provides a keyboard for user input and a display for output.

- physical console: 
- virtual console: 不是很懂，再议

## history command

```shell
history n             #list the last n command
history -w            #write the last command to command history file
                      #the default file is ~/.bash_history
                      # HISTSIZE env variable sets the limit of saved history command
                      # default HISTSIZE is set in file /etc/profile
```

```
!<number>:  expands to the command matching the number
!<command>: expands to the most recent command
```

- 关于单一用户多次登陆，导致history command无法被完整保存的问题？？？**
- 解决history command未登记执行时间的问题**

## shortcut of command operation

You can read bash(1) for detail information.

- **ESC+.** : Copy the last word of the previous command on the current command line where the cursor is.
- **Ctrl+a** : jump to the beginning of the command line.
- **Ctrl+e** : Jump to the end of the command line.
- **Ctrl+u** : Clear from the cursor to the beginning of the command line.
- **Ctrl+k** : Clear from the cursor to the end of the command line.
- **Ctrl+Left Arrow** : Jump to the beginning of the previous word on the command line.
- **Ctrl+Right Arrow** : Jump to the beginning of the next word on the command line.
- **Ctrl+r** : Search the history list of commands for a pattern.

## standard input/ouput/error

### **channels(file descriptior)**

| number | channel name | description     | default connection | usage      |
| ------ | ------------ | --------------- | ------------------ | ---------- |
| 0      | stdin        | standard input  | keyboarder         | read only  |
| 1      | stdout       | standard output | terminal           | write only |
| 2      | stderror     | standard error  | terminal           | write only |
| 3+     | *filename*   | other files     | none               | read/write |

### redirect file

| usage        | description                          |
| ------------ | ------------------------------------ |
| > file       | redirect stdout to a file            |
| >> file      | append stdout to a file              |
| 2> file      | redirect stderr to a file            |
| 2> /dev/null | discard stderr                       |
| &> file      | redirect stdout and stderr to a file |
| >> file 2>&1 | append stdout and stderr to a file   |

### construct pipline

Create a pipeline with character '|'.  The output of ***ls*** is the input of ***wc -l***

```shell
ls | wc -l 
```

Create a three way pipeline with character '|' and command ***tee***.  The output of ***ls*** is display on termial and file at the same time.

```shell
ls -l | tee /tmp/saved-output
```

### display current terminal device

```
tty
```



## path control

```shell
cd ./bin     #enter bin directory under the working dir
cd ../bin    #enter bin directory under the upper level dir of working dir
cd ~         #enter the main directory of the current user
cd ~usr1     #enter the main directory of the user usr1
cd -         #enter the previous working directory
```



## pattern matching (move to shell notes in the future)

### basic pattern


| pattern      | matches                                                      |
| ------------ | ------------------------------------------------------------ |
| *            | Any string of 0 or more characters.                          |
| ?            | Any single character                                         |
| [abc...]     | Any one character in the enclosed class.                     |
| [!abc...]    | Any one character not in the enclosed class.                 |
| [^abc...]    | Any one character not in the enclosed class.                 |
| [[:alpha:]]  | Any alphabetic character.                                    |
| [[:l ower:]] | Any lower-case character.                                    |
| [[:upper:]]  | Any upper-case character.                                    |
| [[:alnum:]]  | Any alphabetic character or digit.                           |
| [[:punct:]]  | Any printable character not a space or alpha numeric.        |
| [[:digit:]]  | Any digit, 0 - 9.                                            |
| [[:space:]]  | Any one whitespace character;  may include tabs, newline, or carriage returns. |

### tilde expansion

| pattern      | matches                                                      |
| ------------ | ------------------------------------------------------------ |
| ~            | The current user's home directory.                           |
| ~username    | User use rname's home directory.                             |
| ~+           | The current working directory                                |
| ~-           | The previous working directory.                              |

### brace expansion

 ```shell
echo file{1..3}.txt
echo file{a..c}.txt
echo file{a,c}.txt
echo file{a{1,2},b,c}.txt
 ```

### command substitutetion

```shell
$(command)        #recommand
`command`
```

### protecting arguments

```shell
\             # escape character for single character
""            # allow command and variable substitution.
''            # interpret all text literally.
```

