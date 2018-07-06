# Linux Shell Skill

### wget
```
wget -r -np -nH --cut-dirs=3 -R index.html http://hostname/aaa/bbb/ccc/ddd/
```
Explanation:

It will download all files and subfolders in ddd directory:
* recursively (-r),
* not going to upper directories, like ccc/… (-np),
* not saving files to hostname folder (-nH),
* but to ddd by omitting first 3 folders aaa, bbb, ccc (--cut-dirs=3)
* excluding index.html files (-R index.html)

```
Refs: https://stackoverflow.com/questions/23446635/how-to-download-http-directory-with-all-files-and-sub-directories-as-they-appear
```

### ldconfig
```
ldconfig -v 2>/dev/null | grep -v ^$'\t'
```
Show linked library search path. 
Please check /etc/ld.so.conf.d/.

### Grub
```
Refs: https://blog.csdn.net/zhu_liangwei/article/details/7847034
```
### cat /proc/PID/status

* VmPeak:表示进程所占用最大虚拟内存大小
* VmSize:表示进程当前虚拟内存大小
* VmLck:表示被锁定的内存大小
* VmHWM:表示进程所占用物理内存的峰值
* VmRSS:表示进程当前占用物理内存的大小(与procrank中的RSS)
* VmData:表示进程数据段的大小
* VmStk:表示进程堆栈段的大小
* VmExe:表示进程代码的大小
* VmLib:表示进程所使用共享库的大小
* VmPTE:表示进程页表项的大小
