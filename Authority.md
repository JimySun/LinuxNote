## User

### basic

User information is stored in ***/etc/passwd*** file. The format(***man 5 passwd***) is as follow.

```
user_name:password:UID:GID:GECOS:<home_dir>:shell
```

- password : password is stored in ***/etc/shadow*** now.
- <home_dir> : user's personal file and configuration
- shell : program runs as the user log in.

#### UID ranges

- 0 : root
- 1-200 : assigned statically to system processes
- 201-999 : system processes that do not own files on the file system
- \> 1000 : regular users

### operation

- show information

  ```
  id           #current user
  id <user>    #identified user
  
  
  ```

- add/modify/delete

  ```shell
  useradd <username>              # defalut value is in file /etc/login.defs
  usermod
  userdel <username>
  ```

- change password

  ```shell
  passwd <username>              # change user's password
  ```

- verify password file

  ```shell
  pwck
  ```

  

### access control 

password is stored in the shadow file(***/etc/shadow***).  Fortmat of shadow file is 

```
name:password:lastchange:minage:maxage:warning:inactive:expire:blank
```

![image-20200219161623929](/Users/JimmySun/Library/Application Support/typora-user-images/image-20200219161623929.png)

```shell
chage -d 0 <username>   # force a password update on next login
chage -l <username>     # list a username's current settings
chage -E YYYY-MM-DD     # expire an account on a specific day
```

```shell
usermod -L <username>   # lock an account
usermod -U <username>   # unlock an account
```

```shell
authconfig --passalgo    # change user's password algorithm
```

### no logging user

set the user's login s h e l l to /sbin/nologin.

> Use of the nologin shell prevents interactive use of the system, but does not prevent all access. A user may still be able to authenticate and upload or retrieve files through applications such as web applications, file transfer programs, or mail readers.






## Group

### basic

Every user must belongs to a ***primary group***. One user can a member of zero or more ***supplementary group***.

Group information is stroed in ***/etc/group*** file. The format(***man 5 group***) is as follow.

```
group_name:password:GID:user_list
```

password : password is stored in ***/etc/gshadow*** now.

### operation

```shell
groupadd <group_name>      # defalut value is in file /etc/login.defs
groupadd -r <group_name>   # create a system group

groupmod -n <new_name> <old_name>
groupmod -g <group_name>   # specify a new GID

groupdel <group_name>
```

### user's group

```shell
usermod -g <group_name> <user_name>         # change user's primary group
usermod -aG <group_name> <user_name>        # add a supplementary group to a user
```



## file permission

| permission | effect on files                   | effect on directories                                        |
| ---------- | --------------------------------- | ------------------------------------------------------------ |
| r(read)    | File can be read.                 | Content of the directory(file names) can be list.            |
| w(write)   | File can be changed.              | Any file in the direcotry may be created or deleted          |
| x(exec)    | Files can be executed as commands | content of the directory can be accessed, depending on the permissions of the files in the direcotry |

### special permissions

| special permission | forth   perceding digit | show of ls          | effect on files                                              | effect on directories                                        |
| ------------------ | ----------------------- | ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| u+s(suid)          | 4                       | -rw**s**r-xr-x**.** | File executes as the user that owns the file, not the user that ran the file. | No effect                                                    |
| g+s(sgid)          | 2                       | -rw-rw**s**r-x**.** | File executes as the group that owns the file                | Files newly created in the directory have their group owner set to match the group owner of the directory. |
| o+t(sticky)        | 1                       | drwxrwxrw**t.**     | No effect                                                    | Users with write on the directory can only remove files that they own; they cannot remove or force saves to files owned by other users. |



### default file permission

Every process on the system has a umask, which is an octal bitmask that is used to clear the permissions of new files and directories that are created by the process. 

The system default umask values for Bash shell users are defined in the ***/etc/profile*** and ***/etc/bashrc*** files. 

If a bit is set in the umask, then the corresponding permission is cleared in new files. For example, the previous umask, 0002, clears the write bit for other users. The leading zeros indicate the special, user, and group permissions are not cleared. A umask of 077 clears all the group and other permissions of newly created files.

```shell
umask              # display current shell's umask
umask 0044         # set the umask of current shell
```



### change file permission

```shell
chmod <whowhatwhich> <file|directory>
chmod <nnn> <file|directory>
chmod <user>:<group> <file|directory>
chgrp <user>:<group> <file|directory>
```



## user switch operation

```shell
su - <user>        # start a login shell, a clean login as that user
su <user>          # start a non-login shell, start a shell with current env.

su - <user> -c "ls | grep file"  # execute command with user <user>
```

## 

## run command as *root*

### setting

file is ***/etc/sudoers***

command is ***visudo***

### execute

```
sudo <command>
```

### log

file is ***/var/log/secure***

## advance topic

### 

```shell

```

