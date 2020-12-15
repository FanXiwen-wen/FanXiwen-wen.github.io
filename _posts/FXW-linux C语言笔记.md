title: Linux C exercise
author: FanXiwen
date: 2020-12-15 00:34:00 +0800
categories: [Blogging, Tutorial]
tags: [favicon]
toc: false



# 常用指令

**进入vim编辑器：**

    * i:表示在光标前面插入字符
    * a:表示在光标后面插入字符
    * shift+i:在这一行的行首插入字符
    * shift+a:在这一行的行尾插入字符
    * x:删除字符
    * dd:删除一整行
    * int main函数中的内容标准缩进Tab键



**比如编译一个程序a.c**

   编译之后生成a.out

   用ls -l查看

​     -rw-rw-r--   1 f f 72        12月 15 16：45  a.c

​    -rwxrwxr-x 1  f f 16696  12月 15 16:45  a.out

​    rxw:表示当前用户所在的目录组权限   rxw:表示当前用户所在的用户组的用户权限   r-x：表示不是当前用户也不是当前用户组的用户的权限



**多个元文件分而治之**

#include<stdio.h>:从系统目录里面查找stdio.h

#include "max.c":从当前目录查找max.c,相当于直接就把max.c里面的代码粘贴进来了

gcc -c max.c -o max.o:编译成为max.o只是将max.c.变成二进制文件，并不能够执行

gcc max.o hello.c 

把不会再修改的函数放在一个公共框架公共类中，形成静态库

Makefile写好之后，以前编译过的文件不需要再重新编译了



**main函数当中的参合和return **

echo $?  可以查看程序执行是否成功，如果成功输出0

int main(int argv,char* argc[])

   ./a.out :输出argv is 1

  ./a.out -l:输出argv is 2

 ./a.out -l -a:输出 argv is 3



**Linux的标准输入流、标准输出流、标准错误流**

./a.out  1>> a.txt   重定向输出流到a.txt （不会覆盖之前的a.txt中的内容）

./a.out > a.txt   重定向到输出流a.txt (会覆盖之前的a.txt中的内容)

./a.out < input.txt  重定向到输入流input.txt

./a.out 1>t.txt 2>f.txt  :把标准输出流重定向到t.txt,把标准输入流重定向到f.txt

printf():

   fpintf(stdout,"Please input the value:");

scanf("%d",&a);

   fscanf(stdin,"%d",&a);





**管道**

ls  /etc/ | grep  ab   在etc下面包含ab的文件

ps -e查看进程

ps -e | grep ssh  查看进程中是否有ssh

结合两个程序：./input.out | ./avg.out  把两个具有独立功能的程序拼接到一起使用



# gdb工具的使用

gcc -g main.c -o main.out  这样生成的main.out是支持调试的

gdb main.out  进入调试

进入之后l显示代码  再按空格表示继续显示代码

start显示程序入口所在的行

p a  打印a的值

n 进入下一行

如果在调用一个函数change(a,b)想进入这个函数，那应该要按下s

bt:查看函数堆栈

