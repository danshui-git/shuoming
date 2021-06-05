
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
