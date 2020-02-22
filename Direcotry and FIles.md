## dicrecotry

### information

```shell
pwd                       #show current directory
pwd -P                    #show current physical directory of symbolic/hard link
```

### create

```shell
mkdir test                #create directory test
mkdir -p test/test/test   #create directory test,test/test and test/test/test
mkdir -m 711 test         #create directory test with authority 711
```

### remove

```shell
rmdir test                #delete directory test, if it’s not empty, delete will fail
rmdir test/test           #delete directory test/test and test
```

## file management

### 

### copy

```shell
cp file1 file2 /tmp           #copy file1 and file2 to dir /tmp
cp -r /ect/ /tmp              #copy directory /etc to /tmp recursively.
cp -i ~/.bashrc /tmp/bashrc   #copy file .bashrc to dir /tmp/ and rename to bashrc. 
                              #-i means promotion before overwrite
cp -a ~/.bashrc /tmp/bashrc   #-a means copy the original info of the file.
cp -u ~/.bashrc /tmp/bashrc   #-u means update
```

### move

```shell
mv file1 file2                #change name of file1 to file2
mv file1 /dir1/               #move file1 to directory dir1
```

### remove

```shell
rm -i file1                   #delete file1 using promotion mode
rm -rf /dir1                  #force delete directory dir1 recursively
\rm -rf /test                 #ignore the parameters seated by alias
```



## view and edit file content



## list and find file



```shell
ls -al --color=always     #list files(include hidden files) with detail info and color
ls -l --full-time         #the format of last modified time is full.
ls -d                     #list directory
ls -l --time=mtime        #the type of time is last modification of file status(default).
ls -l --time=atime        #the type of time is last access of file.
ls -l --time=ctime        #the type of time is last modification of file content.
ls -i                     #list inode number of each files
ls -dl                    #list directories detail info 
ls -ls                    #list the allocated size of each file in blocks
ls -R                     #list contents of subdirectories
```



















```shell
find I - nouser -o - nogroup 2> /dev/null   # delete unowned files
```

