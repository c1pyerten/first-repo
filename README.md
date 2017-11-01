# ResultSetExtractor 

```
jdbcTemplate.query(sql, new ResultSetExtractor() {
    Object extractData(ResultSet rs) {}
})
return Object
```

# RowCallbackHandler

```
jdbcTemplate.query(sql, new RowCallbackHandler() {
    void processRow(ResultSet rs) {}
})
return void
```

# RowMapper

```
jdbcTemplate.query(sql, new RowMapper() {
    Object mapRpw(ResultSet rs, int rowNum)
})
return List
```


> sp_month_new_big_customer


# todos

- autojump-zsh not working

# red

>  DECR, DECRBY, DEL, EXISTS, EXPIRE, GET, GETSET, HDEL, HEXISTS, HGET, HGETALL, HINCRBY, HKEYS, HLEN, HMGET, HMSET, HSET, HVALS, INCR, INCRBY, KEYS, LINDEX, LLEN, LPOP, LPUSH, LRANGE, LREM, LSET, LTRIM, MGET, MSET, MSETNX, MULTI, PEXPIRE, RENAME, RENAMENX, RPOP, RPOPLPUSH, RPUSH, SADD, SCARD, SDIFF, SDIFFSTORE, SET, SETEX, SETNX, SINTER, SINTERSTORE, SISMEMBER, SMEMBERS, SMOVE, SORT, SPOP, SRANDMEMBER, SREM, SUNION, SUNIONSTORE, TTL, TYPE, ZADD, ZCARD, ZCOUNT, ZINCRBY, ZRANGE, ZRANGEBYSCORE, ZRANK, ZREM, ZREMRANGEBYSCORE, ZREVRANGE, ZSCORE

## generic
- get
- set
- del
- expire
- ttl:  -2 for deleted, -1 for never expire

## list
RPUSH, LPUSH, LLEN, LRANGE, LPOP, ,RPOP 

lrange: lrange key st end, end -1 for retrieve all elements

## set
SADD, SREM, SISMEMBER, SMEMBERS SUNION

## Sorted Set
similar to set

- zadd zadd key score value

zadd hackers 1940 "alan kay"

- zrange

zrange hackers 0 -1

# Hash
> Hashes are maps between string fields and string values

- hset  => hset key field value [field, value...]
- hmset  => hmset key field value [field, value...]
- hgetall => hgetall key
- hincrby
- hdel



# The linux command line

## chapter2
- date, cal, df, free

## chapter3 file system
区分大小写
- cd -  => jump to last directory

## ch4 os 
> command -options arguments 

> -options  包含长选项(两个-), 短选项(一个-)

- ls 
- file => lookup file type
- less 

ls 
- -a --alll
- -d --directory
- -h --human-readable
- -l long 
- -t  time
- -r --reverse
- -F --classify 区分

-rw-r--r--    1                     root         root         47584         2007-04-03 11:05    logo-Edubuntu.png

(access auth) (hard link number)  (file owner)  (file group)  (file size)  (last modified time) (filename)
> access auth: 文件所有者，文件组所有者，和其他人的读，写，执行权限

> 对于文件的访问权限。第一个字符指明文件类型。在不同类型之间， 开头的“－”说明是一个普通文件，“d”表明是一个目录。其后三个字符是文件所有者的 访问权限，再其后的三个字符是文件所属组中成员的访问权限，最后三个字符是其他所 有人的访问权限

> first letter 'l' stands for symbolic


ascii pronounce "As-Key"
 

## ch5 os file and direcotry

- cp => cp items... dist-directory
- rm
- mkdir
- mv
- ln

wildchars
- \* match zero or whatever
- ? match one
- [chars]
- [!chars]


### ln

hard: ln item link,  hard link has no difference than regular file

soft(symlink, symbolic): ln -s file link, write to symbolic will also add content to correspond file 

#### hard link
> 当考虑到硬链接的时候，我们可以假设文件由两部分组成：包含文件内容的数据部分和持有文件名的名字部分. 创建文件硬链接的时候，实际上是为文件创建了额外的名字部分， 并且这些名字都关系到相同的数据部分

> blocks <= inode <= file-name


#### symbolic

> 建立符号链接的目的是为了克服硬链接的两个缺点：硬链接不能跨越物理设备， 硬链接不能关联目录，只能是文件。符号链接是文件的特殊类型，它包含一个指向 目标文件或目录的文本指针。


# ch6
all about commands
- type ==> 
- which
- man
- apropos
- whatis
- alias


# ch7 redirection   > for redirection and | for pipe line   

- cat － concatenate files and print on the standard output:  read one or more files, concat them and then copy to stdout ===> cat file1 file2 > concat_file.txt
- sort － sort line    ===>  ls /bin /usr/bin | sort | less
- uniq － 报道或省略重复行  ===> ls /bin /usr/bin | sort | uniq | less
- grep －  grep pattern [file...]
- wc － 打印文件中换行符，字，和字节个数  lines, words, bytes ===> wc file1
- head － print some first parts: 10 lines for default, -n to specify  ====> head -n 5 file.txt 
- tail -- print some last parts   ====> tail -n 5 file.txt.  tail -f file : Prints the appended lines on the terminal as the file grows. (like top command)
- **tee**:  read from stdin, write to both **file** and **stdout**   =====>  ls /usr/bin | tee txt | grep zip



> 与 Unix 主题“任何东西都是一个文件”保持一致，程序， ls，实际上把他们的运行结果 输送到一个叫做标准输出的特殊文件（经常用 stdout 表示），而它们的状态信息则送到另一个 叫做标准错误的文件（stderr）。默认情况下，标准输出和标准错误都连接到屏幕，而不是 保存到磁盘文件。除此之外，许多程序从一个叫做标准输入（stdin）的设备得到输入，默认情况下， 标准输入连接到键盘。

I/O 重定向允许我们可以更改输出走向和输入来向。一般地，输出送到屏幕，输入来自键盘， 但是通过 I/O 重定向，我们可以改变输入输出方向。


\> and >>  redirection

2> rediret stderr   ====>  ls /no/file 2> ls-output.txt

&> redirect both stdout and strerr

[stdin, stdout, sterr] => 0, 1, 2

ctrl-d : EOF



# ch8 see world through shell 

echo 

- \* spread as wildchar
- ~ spread to home
- $(()) suanshu expression
- {} multiple string spread  ===> echo Front-{A,B,C}-Back
- parameter spread:  echo $USER, echo $SHELL

rest remains.........


# ch9 keyboard advanced

- clear
- history

- C-a: to line start
- C-e: to line end
- C-f: forward a char
- C-b: backward a char
- Alt-f: forward a word
- Alt-b: backward a word
- C-w: cut to previous whitespace
- C-l: same as clear
- C-u: from cursor clip to line start
- C-k: from cursor clip to line end
- C-y: paste


## history
- C-r: reverse-search
- C-n: next histroy
- C-p: previous history
- Alt-p
- Alt-n
- !num: copy history command to shell
- !!: last history
- C-g: cancel searching history

meta key: usually alt


# ch10 authorization

- id
- chmod: change file mode bits, two ways for chmod, 1.octal and 2.char
- umask: set default auth
- su: in other user and group
- sudo: in admin
- chown : change file owner and group ==> chown [options]... [owner][:[group]] file...  ==> chown bob:users a.txt 
- chgrp : change group ownership
- passwd: passwd [user]
- adduser(useradd)
- groupadd    


## chmod way 1: octal way 
octal mode: bit-bit-bit => r-w-x

> chmod [user-oct][group-oct][other-oct] file  ===> chmod 600 file

some frequently used: 7 (rwx) 6 (rw-) 5 (r-x) 4 (r--) 0 (---)

## chmod way 2: char way
if not specify a char, default to -a, + means add , - means minus, = means add those and delete others(do not affect other two)

can be separated by ,: u+x, o-x
- u user
- g group
- o others
- a all: includes all ugo


command | desc
--- |-----
u+x	        | 为文件所有者添加可执行权限。
u-x         | 删除文件所有者的可执行权限。
+x          | 为文件所有者，用户组，和其他所有人添加可执行权限。 等价于 a+x。
o-rw        | 除了文件所有者和用户组，删除其他人的读权限和写权限。
go=rw       | 给群组的主人和任意文件拥有者的人读写权限。如果群组的主人或全局之前已经有了执行的权限，他们将被移除。
u+x,go=rw	| 给文件拥有者执行权限并给组和其他人读和执行的权限。多种设定可以用逗号分开。





# ch11 process

tty: teletype, a control terminal

- ps
  - ps x ==>  a "stat" column
  - ps aux 
- top : monitoring system's process updating information
- jobs: show current jobs(also show jobspec)
- fg  ==> fg %1
- bg
- kill ===> kill [-signal] PID
- killall:  killall [-u user] [-signal] name...   ==> killall -9 PID
- shutdown

> note: [1] and %1  is jobspec


C-c terminate process
C-z stop process

command &  : run and put process to background     =======>  node &

## signal

> kill [-signal] PID

signals: 
- HUP 1 ==> kill -1 13546
- INT 2  中断 C-c
- QUIT 3
- KILL 9
- TERM 15 
- CONT 18
- STOP 19
- TSTP 20 终端停止 C-z

more command about process
- pstree
- vmstat 系统资源使用快照，包括内存，交换分区和磁盘 I/O




# ch12 shell environment

two types in shell: 环境变量和 shell 变量

> $PS1(prompt string one), $SHELL, $HOME, $EDITOR are shell vars

> USER, TERM, PWD  are enviroment vars

- printenv:  enviroment variable  ==> printenv(show all), printenv USER
- set: shell variable  ==> set(show all) , echo $SHELL, echo $PS1
- export:  export path: shell's subprocess can use PATH 
- alias

command lines stored in $PATH, echo $PATH:  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin



# ch14 homemade shell prompt string one

all about $PS1 preference


# ch15 package manager

|dist|ground tool| app tool|
|----|----|----|
|debian-style|dpkg|apt-get, aptitude|
|redhat|rpm| yum|


# ch17 network system

- ping
- traceroute
- netstat
- wget
- ssh(Secure Shell)

...remains 


# ch18 find files

- find
- locate
- xargs
- stat
- touch


## find tests
some heavily used tests:

-type: b, c, d, l, f
block device
character device
directory
symbolic
file

- -name
- -iname: case-insensitive name
- -user
- -size 

> find /etc -type f -iname "nginx.*"  -user root -size +1M

## operators

- -and
- -or
- -not

## pre-defined operation

- -ls
- -print
- -quit 
- -delete

## -exec [command] '{}'

### examples: 
> find ~ -type f -name "\*.JPG" -size +1M | wc -l

> find ~ ( -type f -not -perm 0600 ) -or ( -type d -not -perm 0700 )

> find ~ -type f -name '*.BAK' -delete

> find ~ -type f -and -name '*.BAK' -and -print





------------------------------------------------------

# About inode (index node)

stat, ls -i:  lookup inode

inode marked by a series of number: 132536

inode标识文件, 文件名标识inode
filename => inode => blocks

### directory

**directory contents a series of dirent(目录项), a dirent contents two parts: 1.filename 2.filename's correspond inode**


> 创建目录时，默认会生成两个目录项："."和".."。前者的inode号码就是当前目录的inode号码，等同于当前目录的"硬链接"；后者的inode号码就是当前目录的父目录的inode号码，等同于父目录的"硬链接"




--------

# random notes

### find out distribution release:  lsb_release -a
- /etc/*-release file.
- lsb_release command.  lsb_release -a
- /proc/version file.


# vim

- %  =>    go to pair
- \#, *  =>  next(pevious) occurrance of the word
- v, C-v  =>  expand section, (C-w in jetbrains)
- gu[], gU[]   ===>  guw, gue, gUw, gUe, gU$, gU2w
- :bn, :bp  => buffer-next, buffer-previous
- C-v, then select lines, then [I, A] [words] [Esc]  ======> insert/append to multiple lines
- C-n, C-p ======> completion
- /\c case insensitive search   =====> /\cfoo


# Git

3 file status
- committed(unmodified)
- modified
- staged

3 areas
- working directory
- staging area: file infos to be submitted
- .git directory (repository)

git config level
- global 
- current user
- repository

----------------

# ch2 basic

git add *.c 

file status cycle:  untracked  unmodified  modified  staged

- git status -s  (git status --short)

### git diff: 
- unstaged modification  git diff
- staged modification:  git diff --cached  | git diff --staged 

### rm

untrack file: 
git rm --cached file

------------

## log

> git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit

------

## **cancel**

- git commit --amend: submit all staged files
- **cancel staging: git reset HEAD [file]**
- **restore to last commit: git checkout -- [file]**

--------------

## remote repository

- git remote: list remote repo
- git remote -v: list verbose
- git remote show [remote-branch-name]  => git remote show origin

### add remote 
git remote add [shortname] [url] : add remote repo

git remote add **pb** https://github.com/paulboone/ticgit,  after add remote repo, we can **fetch**: git fetch pb, then all pb's branchs will be located at remotes/pb/... , E.G: pb/master, pb/ticgit (listing command: git branch -r)

### fetch
if clone a repo, by default a **origin** remote will be added as remote repo

### rename and mv
git remote rename pb paul
git remote rm paul

-----
## Tag
two types of tag:
- lightweight 
- annotated ==> git tag -a v1.4 -m 'my version 1.4'


commands
- git tag: list tags
- git show [tag-name]
- git push origin [tagname]
- git push origin --tags: put all tags to remote if tag not in remote


--------

# ch3 branch
**Actually, git branch is just pointers pointing at commit object**

A pointer called HEAD pointing at branches

- git branch [new-branch]
- git checkout [branch]
- git checkout -b [new-branch]:  combine above two

## merge
two merging ways:
1. **fast-forward merge** , direct point master to [branch]
2. **diverged from common ancestor merge**, auto make a new commit 

- git merge [branch]: merge current-branch to [branch]
- git add conflict-file: mark file as conflict solved
- git mergetool: using gui to solve conflict  

## branch

- git branch
- git branch -v: every branch's last commit
- git branch -r: list remote branch
- git branch -d [branch]: delete branch
- git branch --merged, git branch --no-merged


## remote branch

remote branch name as: remote/[branch]

- git remote show [branch]: get remote branch infos
- git fetch [remote]: update remote-branch 

- git push origin serverfix:  git push origin serverfix: serverfix :  **serverfix spread to : refs/heads/serverfix:refs/heads/serverfix**
- - git push [remote-name] [local-branch]: [remote-branch]
