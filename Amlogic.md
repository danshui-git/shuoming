- ## CPU型号跟机型的对照表

| 型号  | 机顶盒 | OpenWrt固件 |
| ---- | ---- | ---- |
| s905x3 | [X96-Max+](https://tokopedia.link/uMaH09s41db), [HK1-Box](https://tokopedia.link/xhWeQgTuwfb), [H96-Max-X3](https://tokopedia.link/KuWvwoYuwfb), [Ugoos-X3](https://tokopedia.link/duoIXZpdGgb), [X96-Air](https://tokopedia.link/5WHiETbdGgb), [A95XF3-Air](https://tokopedia.link/ByBL45jdGgb) | openwrt_s905x3_k*.img |
| s905x2 | [X96Max-4G](https://tokopedia.link/HcfLaRzjqeb), [X96Max-2G](https://tokopedia.link/ro207Hsjqeb) | openwrt_s905x2_k*.img |
| s905x | [HG680P](https://tokopedia.link/HbrIbqQcGgb), [B860H](https://tokopedia.link/hnXvHn5uwfb) | openwrt_s905x_k*.img |
| s922x | [Belink](https://tokopedia.link/RAgZmOM41db), [Belink-Pro](https://tokopedia.link/sfTHlfS41db), [Ugoos-AM6-Plus](https://tokopedia.link/pHGKXuV41db) | openwrt_s922x_k*.img |
| s912 | [H96-Pro-Plus](https://tokopedia.link/jb42fsBdGgb), Octopus-Planet | openwrt_s912_k*.img |
| s905d | Phicomm-N1 | openwrt_s905d_k*.img |


#
#

- ## [内核是时时变动的，所以选择内核之前，一定要点击这里查看一下当前可用内核，随便搞的话，没有该内核，打包就失败，在编译脚本那里就会出现‘整理固件文件夹’步骤错误](https://github.com/ophub/amlogic-s9xxx-openwrt/tree/main/amlogic-s9xxx/amlogic-kernel)

#
#

- ## 打包固件机型和核心组合方法：
```
机型和核心组合设置在：build/openwrt_amlogic/diy-part.sh


amlogic_modelw为机型设置，多机型需要中间加‘_’间隔，比如 s922x_s912
amlogic_kernel为内核设置，多内核需要中间加‘_’间隔，比如 5.10.70_5.4.150
rootfs_size为rootfs分区大小，不能小于500，不懂就默认不要修改。
所有CPU型号为：s905x3_s905x2_s905x_s905d_s922x_s912
比如你要打包N1的固件，就选择s905d的，然后选择核心版本，核心版本上面的链接可以查看，多机型跟多核心都要中间加‘_’。
amlogic_kernel内核如果保持 5.10.70_5.4.150 不修改的话，每次编译都会默认同步作者推荐的最新版本。
云编译的时候可以在编译信息查看到你编译的内核版本详情


比如这样的，就是单机型+单核心组合打包
cat >$GITHUB_WORKSPACE/amlogic_openwrt <<-EOF
amlogic_model=s905d
amlogic_kernel=5.10.70
rootfs_size=1200
EOF


比如这样的，就是多机型+多核心组合打包，自由组合。
cat >$GITHUB_WORKSPACE/amlogic_openwrt <<-EOF
amlogic_model=s905x3_s905x2_s905x_s905d_s922x_s912
amlogic_kernel=5.10.70_5.4.150
rootfs_size=1200
EOF


请注意，不是组合越多就越好的，每个内核就打包一个固件而已，不是一个固件里面可以塞进去几个内核的，
要根据自己个人需求组合，要不然打包的固件太多，服务器空间不够用就打包失败了。
```

---

- ## 本地编译一键打包命令用法：
```
如果用的是我的一键本地编译脚本的话，一键打包命令也差不多意思，内核跟机型组合自己修改好就行了。

在Ubuntu确认你是进入了openwrt文件夹，如果不是的话就使用 cd openwrt 命令进入

比如多个机型内核：
sudo ./make -d -b s905x3_s905x2_s905x_s905d_s922x_s912 -k 5.10.70_5.4.150

比如单个机型内核：
sudo ./make -d -b s905d -k 5.10.70

比如单个机型双内核：
sudo ./make -d -b s905d -k 5.10.70_5.4.150
```


#
#
#

- ## 安装及升级 OpenWrt 的相关说明

- 选择和你的机顶盒型号对应的 OpenWrt 固件，使用 [Rufus](https://rufus.ie/) 或者 [balenaEtcher](https://www.balena.io/etcher/) 等工具将固件写入USB里，然后把写好固件的USB插入机顶盒。
#
- 安装固件：从浏览器登录 OpenWrt  → `系统菜单` → `晶晨宝盒` → `安装 OpenWrt`
#
- 升级固件：从浏览器登录 OpenWrt  → `系统菜单` → `晶晨宝盒` → `升级 OpenWrt`
#
---
- 若在 TF/USB 中使用 OpenWrt

- 从浏览器访问 OpenWrt 的默认 IP: 192.168.1.1 → 使用默认账户登录进入 OpenWrt → 系统菜单 → TTYD 终端 → 输入命令 →  `openwrt-tf`

- 激活剩余空间后，支持在 TF/USB 中升级内核和 OpenWrt 系统。
- ---

- ## Screenshot / 截图

![luci-app-amlogic](https://user-images.githubusercontent.com/68696949/121277810-f9ebd800-c903-11eb-9bf4-7c2b11f9a1d3.gif)
