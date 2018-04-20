# Shell Learning

Before I mostly read vbird to learn Shell of Linux. It's good for chinese to learn shell.
Shell commands is too many. So the collection of them continues in this post.

##### grep
```shell
1. ps -ef | grep -E 'a|b'
2. ps -ef | grep 'a\|b'
3. ps -ef | egrep 'a|b'
```

##### xargs
```shell
echo file | xargs -i cp {} <path>  用{}代替管道的输入
echo file | xargs -I {} cp {} <path> 定义{}符号，用来代替管道的输入。  
```
##### cp
```shell
--parents 连同目录结构一起复制
```

##### sed
```shell
sed -i s/old/new/g `grep -r old *`
替换所有包含old文件中的old 为 new
```
##### if
```shell
if …; then
…
elif …; then
…
else
…
fi

[ -f "$file" ] 判断$file是否是一个文件
[ $a -lt 3 ] 判断$a的值是否小于3，同样-gt和-le分别表示大于或小于等于
[ -x "$file" ] 判断$file是否存在且有可执行权限，同样-r测试文件可读性
[ -n "$a" ] 判断变量$a是否有值，测试空串用-z
[ "$a" = "$b" ] 判断$a和$b的取值是否相等
[ cond1 -a cond2 ] 判断cond1和cond2是否同时成立，-o表示cond1和cond2有一成立
要注意条件测试部分中的空格。在方括号的两侧都有空格，在-f、-lt、=等符号两侧同样也有空格。如果没有这些空格，Shell解释脚本的时候就会出错。
```
##### switch
```shell
#!/bin/bash
echo "Your choice?"
select var in "a" "b" "c"; do
break
done
echo $var

case $var in
1) 
   break;;
2)
   break;;
esac
```
Output
> Your choice?
1) a
2) b
3) c

##### Shell Script Argument
```shell
$#表示包括$0在内的命令行参数的个数。

在Shell中，脚本名称本身是$0，剩下的依次是$0、$1、$2…、${10}、${11}，等等。

$*表示整个参数列表，不包括$0，也就是说不包括文件名的参数列表。

$?：命令执行后返回的状态

$$：当前进程的进程号

$!：后台运行的最后一个进程号

$0：当前执行的进程名
```

## 系统信息命令
##### netstat
```
用来查看网络通信情况，端口通信情况

-a (all)

-n (numeric) 用ip地址表示，而不用变量名，比如localhost在此参数下就会被替代成127.0.0.1

-p (process id) 显示进程号
```
##### lsof
```shell
list opened file by system
就是列出系统打开的所有文件

-i (internet) 加入适当的参数可以列出网络相关的文件打开情况。一般可以用来查看端口
```
##### dmidecode
```shell
dmidecode
输出各种机器信息， 要什么就用grep吧。
```

> Refs: http://linux.vbird.org/linux_basic/0330regularex.php#sed
>       http://linux.vbird.org/linux_basic/0340bashshell-scripts.php
>       http://www.ibm.com/developerworks/cn/linux/l-cn-shell-debug/index.html (Shell 脚本调试技术)
>      	http://www.cnblogs.com/forward/archive/2012/01/10/2318483.html (Ubuntu 安装包相关命令)
>      	http://coolshell.cn/articles/9104.html （sed 简明教程）
>      	http://coolshell.cn/articles/9070.html （awk 简明教程）