# 补丁制作方法
- 用[WinSCP](https://winscp.net/eng/download.php)(文件协议F选择SCP)进入乌班图系统，按一下那个房子进入根目录
- 新建目录（文件夹），名字叫diff，然后在diff文件夹里面建立test1.txt和test2.txt两个文件
- test1.txt放入源码文件内容
- test2.txt也放入源码文件内容，并且修改好
- 要记住test1.txt是原内容，你在源码文件复制内容过来粘贴保存，- test2.txt是修改好的，你复制内容过来粘贴后，修改好，保存，然后使用命令
#
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x001.png" />

#
- 用[putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/releases/0.74.html)连接乌班图系统，输入 cd diff  回车进入diff文件夹
然后输入 diff -Naur test1.txt test2.txt > test.patch 命令，回车就完成了，输入命令后也没啥提示跟改变的，刷新WinSCP查看
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x004.png" />
#
- 刷新WinSCP，能看到 test.patch 文件，这个就是补丁了
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x002.png" />

#
- 修改路径

!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x003.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/x005.png" />

#
- 补丁文件叫什么名字好像都没关系的，我懒的取名字，就默认名字前面加001-这样的，不过记得格式一定是（.patch）的
#
- test1.txt跟test2.txt还有test.patch都不用管他了，你以后要做补丁就继续的原内容test1.txt，修改test2.txt，执行命令，test.patch就自动是最新补丁了
