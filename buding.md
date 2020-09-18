# 补丁制作方法
- 用WinSCP进入乌班图系统，按一下那个房子进入根目录
- 新建目录（文件夹），名字叫diff，然后在diff文件夹里面建立test1.txt和test2.txt两个文件
- test1.txt放入源码文件内容
- test2.txt也放入源码文件内容，并且修改好
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x001.png" />

#
- 用putty连接乌班图系统，输入 cd diff  进入diff文件夹
然后输入 diff -Naur test1.txt test2.txt > test.patch 命令，就完成了
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x004.png" />
#
- 刷新WinSCP，能看到test.patch 文件，这个就是补丁了
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x002.png" />
#
- 修改路径

!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x003.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x005.png" />

#
- 补丁文件叫什么名字好像都没关系的，我懒的取名字，就默认名字前面加001-这样的，不过记得格式一定是（.patch）的
