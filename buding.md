# 补丁制作方法
- 用WinSCP进入乌班图系统，按一下那个房子进入根目录
- 新建目录（文件夹），名字叫diff，然后在diff文件夹建立test1.txt和test2.txt两个文件
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x001.png" />
- test1.txt放入源码文件内容
- test2.txt也放入源码文件内容，并且修改好
- 用putty连接乌班图系统，输入 cd diff  进入diff文件夹
然后输入 diff -Naur test1.txt test2.txt > test.patch 命令，就完成了，按WinSCP绿色环形箭头刷新，能看到test.patch 文件，这个就上补丁了
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x002.png" />
- 修改路径
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x003.png" />
