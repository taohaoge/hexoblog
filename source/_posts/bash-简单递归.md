title: bash-简单递归
date: 2014-12-25 20:55:36
tags: [bash,递归]
categories: bash

---
#### 思路
1. 取随机数,最大数
2. 判断随机数是否小于最大数
3. 如果小于,则调用当前文件,否则结束

<!-- more -->

#### 代码
```shell
#!/bin/bash
#脚本递归
RANGE=10
MAXVAL=9
i=$RANDOM #取随机数
let "i%=$RANGE" #求余运算

if [ $i -lt $MAXVAL ] #判断大小
then
    echo "i= $i"
    ./$0 
fi
exit 0
```

#### 遇到的问题
- `unexpected operator`,不存在`let`方法
> 解决方法:sudo dpkg-reconfigure dash   选NO
- 无法进行调用
> 解决方法: chmod a+x XX.sh
