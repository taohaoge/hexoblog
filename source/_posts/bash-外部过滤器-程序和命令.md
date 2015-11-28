title: "bash-外部过滤器,程序和命令"
date: 2014-12-26 09:08:11
tags: [bash,外部过滤器,程序,命令]
categories: bash

---
#### 基本命令

- ls
- cat,tac
- tr a-z A-Z
- rev
- cp
- mv
- rm
- rmdir
- mkdir
- chmod
- chattr
```shell
chattr +i filename #使文件被标记为永远不变
chattr +s filename #不能被删除,safe
chattr +c filename #自动压缩,读取时自动解压缩
```
<!-- more -->
- ln
-s软链接必须使用`绝对路径`
- man,info

#### 复杂命令
- find
```shell
-exec COMMAND \;
find ~/ -name "*.txt"
```
如果command中包含{},那么find命令会将匹配的结果替换掉{}
```shell
# 从用户的home目录中删除所有的corm dump 文件
find ~/ -name 'core*' -exec rm {} \;
```
**关于文件时间属性的操作**
mtime = last modificatiuon time of file
ctime = last status change time
atime = last access time
```shell
#列出最后一天修改的文件
find /home -mtime 1
```
- xargs
xargs 的默认命令是 echo. 这意味着通过管道传递给 xargs 的输入将会包含换行和空白, 不过通过 xargs 的处理, 换行和空白将被空格取代.
```shell
1.当你尝试用rm 删除太多的文件，你可能得到一个错误信息：/bin/rm Argument list too long. 用xargs 去避免这个问题
find ~ -name ‘*.log’ -print0 | xargs -0 rm -f
2.获得/etc/ 下所有*.conf 结尾的文件列表，有几种不同的方法能得到相同的结果，下面的例子仅仅是示范怎么实用xargs ，在这个例子中实用 xargs将find 命令的输出传递给ls -l
# find /etc -name "*.conf" | xargs ls –l
3.假如你有一个文件包含了很多你希望下载的URL, 你能够使用xargs 下载所有链接
# cat url-list.txt | xargs wget –c
4.查找所有的jpg 文件，并且压缩它
# find / -name *.jpg -type f -print | xargs tar -cvzf images.tar.gz
5.拷贝所有的图片文件到一个外部的硬盘驱动 
# ls *.jpg | xargs -n1 -i cp {} /external-hard-drive/directory
```
- expr

#### 时间日期
- date
- zdump 查看特定地区当前时间
- touch
- at
- batch
- cal
- sleep
- usleep
- hwclock,clock

#### 文本处理
- sort
- tsort 拓扑排序
- uniq
- expand,unexpand
- cut
- paste
- join
- head
- tail
- grep
- sed
- awk
- wc
- fold
- fmt
- col
- column
- colrm
- nl
- pr
- iconv
- recode

#### 文件与归档
- tar
- shar
- ar
- rpm
- gizp
- file
- whic
- whereis
- whatis
- vdir
- diff
- path
- diff3
- cmp
- comm 多功能的文件比较工具
- basename
- dirname
- split
- csplit
- sum,cksum,md5sum,sha1sum
- shared 用随机字符填充文件,使得文件无法被恢复
- crypt
- mktemp
- dos2unix
- ptx
- more,less

#### 通讯命令
- host
- lookup
- ipcalc
- nsloopup
- dig
- whois
- finger
- chfn
- vrfy
- sx,rx
- sz,rz
- ftp
- uucp,uux,cu
- telnet
- wget
- curl
- lynx
- rcp
- rsync
- scp
- write
- netconfig
- mail

#### 终端控制
- tput
- infocmp
- reset,clear
- script

#### 数学运算
- factor 将一个正数分解为多个素数
- bc 可以处理浮点数

#### 混杂命令
- jot,seq
- getopt
- run-parts
- yes
- banner
- printenv
- lp
- tee
- mkfifo
- pathchk
- dd
- od
- hexdump
- objdump
- mcookie
- units
- m4
- doexec
- dialog
- sox
