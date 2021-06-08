
## 如何在本地使用此项目编译自己需要的 OpenWrt 固件

### 注意：
- 不要用 root 用户！！！
- 国内用户编译前请准备好梯子,使用大陆白名单或全局模式
- 请使用Ubuntu 64bit，推荐 Ubuntu 18 或 Ubuntu 20

### 一键脚本:

- 使用非root用户登录您的ubuntu系统,执行以下代码即可:

- 首次编译:
```
wget -O compile.sh https://raw.githubusercontent.com/281677160/common/main/compile.sh && chmod -R +x compile.sh && bash compile.sh
```

- 二次编译:
```
bash openwrt/recompile.sh
```

---
- 问：进入一键本地编译系统后叫我选择编译源码，我该任何选择？<br />
###### 答：我[这里](https://github.com/danshui-git/shuoming/blob/master/%E7%AE%80%E5%8D%95%E4%BB%8B%E7%BB%8D%E6%96%B0%E8%84%9A%E6%9C%AC.md)作了简单介绍，当然本地编译是不支持自建文件夹来增加机型的，云编译你们拉取了我仓库后可以随便自建。
- 问：设置openwrt的IP地址是什么意思？<br />
- 答：这个地址就是用来登录你openwrt用的，需要什么IP是根据你个人需要，固件编译完成，你安装好固件后，在浏览器输入此IP就可以登录openwrt了，默认帐号是root，默认秘密为空
