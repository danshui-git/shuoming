- 《[Telegram聊天吹水群](https://t.me/heiheiheio)》- 《[Telegram中文设置方法](https://github.com/danshui-git/shuoming/blob/master/tele.md)》


- # 介绍

- 编译amlogic系列，《[自动打包您所需的固件说明](https://github.com/danshui-git/shuoming/blob/master/Amlogic.md)》

- 源码已直接加入【[常用插件列表](https://github.com/danshui-git/shuoming/blob/master/%E5%90%8D%E7%A7%B0.md)】

- 《[如何在本地Ubuntu一键无脑编译](https://github.com/281677160/bendi)》
 
- 《[把定时自动在线更新插件编译进固件的说明](https://github.com/danshui-git/shuoming/blob/master/%E5%AE%9A%E6%97%B6%E6%9B%B4%E6%96%B0%E6%8F%92%E4%BB%B6.md)》

---
#
- # 编译教程：
- ### 以下的说明教程都是在我另外的仓库的，查看说明时候就跳转到另外仓库了，浏览器回退就会回来，别拉取到我说明的仓库，注意了！
#
- 编译openwrt两个常用的工具下载地址《[PuTTY(SSH)工具](https://github.com/danshui-git/shuoming/blob/master/Putty%E5%B7%A5%E5%85%B7%E4%B8%8B%E8%BD%BD.md)》《[WinSCP文件管理](https://github.com/danshui-git/shuoming/blob/master/WinSCP.md)》
#
- > 1、注册及登录github账号，github个别地区或网络已筑墙,请自备梯子《[注册链接](https://github.com)》
#
- > 2、拉取我的仓库到你的github帐号《[拉取仓库教程](https://github.com/danshui-git/shuoming/blob/master/1%E6%8B%89%E5%8F%96%E4%BB%93%E5%BA%93.md)》
#
- > 3、必须了解的脚本简单介绍，起码也知道我仓库有什么源码，出处那里，然后您才好选择《[脚本简单介绍](https://github.com/danshui-git/shuoming/blob/master/%E7%AE%80%E5%8D%95%E4%BB%8B%E7%BB%8D%E6%96%B0%E8%84%9A%E6%9C%AC.md)》
#
- > 4、必须获取密匙然后在你拉取我的仓库里使用，要不然我的仓库您使用不了《[仓库密匙获取跟使用](https://github.com/danshui-git/shuoming/blob/master/jm.md)》
#
- > 6、修改后台登录IP，在build文件夹-->对应您在第 5 步修改的源码文件夹里点开[diy-part.sh]，然后修改后台登录IP《[修改ip教程](https://github.com/danshui-git/shuoming/blob/master/ip.md)》
#
- > 7、开启或者关闭某功能，在build文件夹-->对应您在第 5 步修改的源码文件夹里点开[settings.ini]，然后按需控制各项目开关《[各开关控制教程](https://github.com/danshui-git/shuoming/blob/master/kaiguan.md)》
#
- > 8、启动编译《[启动编译程序和SSH连接修改插件机型等教程](https://github.com/danshui-git/shuoming/blob/master/config.md)》
#
- > 9、完成编译，下载固件《[固件下载教程](https://github.com/danshui-git/shuoming/blob/master/4%E5%9B%BA%E4%BB%B6%E4%B8%8B%E8%BD%BD.md)》
#
- > 10、安装固件，安装固件时出现“Please press Enter to activate this console”就表示安装好了，出现这个就不会跑码的，稍等2-3分钟就可以在浏览器输入IP进入openwrt后台了
- > 如果会跑码，就耐心等待跑码完成，大概2-3分钟就能跑完的
#
- > 11、下次编译，在不改变.config配置文件的情况下，就不需要再次获取了，直接启动编译就可以了，不改变配置的话，手机都可以启动编译
#
- > 12、
- 《[仓库密匙获取跟使用](https://github.com/danshui-git/shuoming/blob/master/jm.md)》
- 《[Telegram和pushplus的密匙获取方式](https://github.com/danshui-git/shuoming/blob/master/bot.md)》
- 《[在build文件夹里面，多开或删除文件夹教程](https://github.com/danshui-git/shuoming/blob/master/jlck.md)》
- 《[定时触发开启编译说明](https://github.com/danshui-git/shuoming/blob/master/%E5%AE%9A%E6%97%B6%E7%BC%96%E8%AF%91%E8%AF%B4%E6%98%8E.md)》
- 《[一键同步上游仓库说明](https://github.com/danshui-git/shuoming/blob/master/chongxinfork.md)》
- 《[X86编译时选固件格式和设置overlay空间容量](https://github.com/danshui-git/shuoming/blob/master/overlay.md)》
- 《[删除固件包中不想要的文件或固件](https://github.com/danshui-git/shuoming/blob/master/%E5%9B%BA%E4%BB%B6%E6%96%87%E4%BB%B6%E5%A4%B9%E6%95%B4%E7%90%86.md)》
- 《[IPV4/IPV6选择，和去除网络共享](https://github.com/danshui-git/shuoming/blob/master/%E5%85%B6%E4%BB%96%E8%AF%B4%E6%98%8E.md)》
- 《[banner的说明](https://github.com/danshui-git/shuoming/blob/master/banner%E8%AF%B4%E6%98%8E.md)》
- 《[本地提取.config](https://github.com/danshui-git/shuoming/blob/master/yijianconfig.md)》
- 《[patch补丁制作](https://github.com/danshui-git/shuoming/blob/master/buding.md)》
- 《[编译时增加NTFS格式盘挂载](https://github.com/danshui-git/shuoming/blob/master/NTFS%E6%A0%BC%E5%BC%8F%E7%9B%98%E6%8C%82%E8%BD%BD.md)》
- 《[拉取插件命令和各种命令的简单介绍](https://github.com/danshui-git/shuoming/blob/master/ming.md)》
- 《[编译出错时查看日志方法](https://github.com/danshui-git/shuoming/blob/master/errors.md)》
- 《[修改文件跟删除仓库](https://github.com/danshui-git/shuoming/blob/master/%E5%88%A0%E9%99%A4%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%87%E4%BB%B6.md)》

#
#
- ## 鸣谢
- [coolsnowwolf](https://github.com/coolsnowwolf/lede.git)
- [Lienol](https://github.com/Lienol/openwrt.git)
- [ctcgfw](https://github.com/project-openwrt/openwrt.git)
- [P3TERX](https://github.com/P3TERX/Actions-OpenWrt)
- [tuanqing](https://github.com/tuanqing/mknop)
- [Hyy2001X](https://github.com/Hyy2001X/AutoBuild-Actions)
- [ophub](https://github.com/ophub/amlogic-s9xxx-openwrt)
- [nicholas-opensource](https://github.com/nicholas-opensource/OpenWrt-Autobuild)
- [hx210](https://github.com/hx210/build-actions)
- <a href="#/README.md">hyird</a>
- <a href="#/README.md">World Peace</a>
- [github平台](https://github.com/)
- <a href="#/README.md">感谢各位大佬提供的各种各样的插件</a>
- <a href="#/README.md">感谢各位帮助过我的人，祝福各位好人一生平安</a>

#
- # 捐赠
- 如果你觉得此项目对你有帮助，请请我喝一杯82年的凉白开，感谢！

-微信-
# <img src="https://github.com/danshui-git/shuoming/blob/master/doc/weixin4.png" />
