title: bash交互式与非交互式
date: 2014-12-25 09:24:22
tags: [bash,交互式]
categories: bash

---
### 运行方式
```shell
while:
do
	read line
    eval "$line"
done
```
通过循环,使用read来实现i交互操作
<!-- more -->
### 检测方式
- 通过提示符 `$PS1`
```shell
if [ -z $PS1 ] #没有提示符
then
	# 非交互
    ...
else
	# 交互式
    ...
```
- 通过判断`$-`变量中是否出现选项`i`
```shell
case $i in
"i") #交互式
;;
*) #非交互式
;;
```
> 脚本可以使用-i 选项强制在交互式模式下运行或脚本头用#!/bin/bash -i
> 注意这样可能会引起脚本古怪的行为或当没有错误出现时也会显示错误信息