# SSH连接说明：
- cd openwrt && make menuconfig
#
- SSH连接说明：复制代码-->粘贴到putty开始连接-->等待跑码完成-->按Ctrl+c-->输入cd openwrt && make menuconfig然后回车-->等待跑码完成进入配置画面-->配置完成后-->一路Exit退出配置界面-->Ctrl+d结束SSH连接
#
- 已经连接了SSH后选择完插件，一路退出到yes or no那里按yes保存配置，然后必定要正确按键盘Ctrl+d结束SSH连接才会继续编译
#
- 打开了SSH连接功能，又没连接的话，30分钟后会跳过SSH继续运行编译的下一步
#
- [SSH工具下载](https://www.chiark.greenend.org.uk/~sgtatham/putty/releases/0.74.html)
#
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/ssh01.png" width="650" height="418" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/ssh02.png" width="650" height="418" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/ssh3.png" width="650" height="438" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/01.png" width="650" height="418" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/02.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/003.png" width="650" height="418" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/03.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/04.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/05.png" />
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/06.png" />
---
- ### 上图操作无非就是键盘上下键，确认的话有些按回车，有些按空格键，退出就选 EXIT 按回车，如果没这个选择就随便选一个项目按回车确认就退出了

- ### 选择插件的话，按 Y 就是对插件选择，按了后你就看到插件名字前面多了个 * 的，按 N 就是取消，按 M 就是编译出IPK但是不把这个插件编译进固件

- ### 都选择完毕后，就一路的选择 EXIT 按回车退出就可以了，看到 YES OR NO 的选择的时候默认YES保存配置即可
---
!<img src="https://github.com/danshui-git/shuoming/blob/master/doc/07.png" />
#
# - [SSH工具下载](https://www.chiark.greenend.org.uk/~sgtatham/putty/releases/0.74.html)
