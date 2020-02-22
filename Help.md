### man

```shell
man <topic>               # display popluar section
man -f <topic>            # display the sections of command
man <section> topic       # display specific section of topic
```

**section of the Linux manual**

| section | content type                                                 |
| ------- | ------------------------------------------------------------ |
| 1       | User commands(both executable and shell programs)            |
| 2       | System calls(kernel routines invoked from user space)        |
| 3       | Library functions(provided by program libraries)             |
| 4       | Special files(such as device files)                          |
| 5       | File formats (for many configuration files and structures)   |
| 6       | Games (historical section for amusing programs)              |
| 7       | Conventions. standards, and miscel laneous (protocols, file systems) |
| 8       | System administration and privileged commands (maintenance tasks) |
| 9       | Linux kernel API(internal kernel calls)                      |



```shell
man -k <key>         # search for topic by key, rely on the index created by mandb(8)
man -K <key>          # full text search for text
```



### info

The info documenttation will be more in-depth than man.

```shell
pinfo info
pinfo pinfo
pinfo <topic>
```



### /usr/share/doc



