- ## CPU型号跟机型的对照表

| 型号  | 机顶盒 | OpenWrt固件 |
| ---- | ---- | ---- |
| s905x3 | [X96](https://tokopedia.link/uMaH09s41db), [HK1](https://tokopedia.link/xhWeQgTuwfb), [H96](https://tokopedia.link/KuWvwoYuwfb), [Ugoos-X3](https://tokopedia.link/duoIXZpdGgb), [X96-Air](https://tokopedia.link/5WHiETbdGgb), [A95XF3-Air](https://tokopedia.link/ByBL45jdGgb) | openwrt_s905x3_v*.img |
| s905x2 | [X96Max-4G](https://tokopedia.link/HcfLaRzjqeb), [X96Max-2G](https://tokopedia.link/ro207Hsjqeb) | openwrt_s905x2_v*.img |
| s905x | [HG680P](https://tokopedia.link/HbrIbqQcGgb), [B860H](https://tokopedia.link/hnXvHn5uwfb) | openwrt_s905x_v*.img |
| s922x | [Belink](https://tokopedia.link/RAgZmOM41db), [Belink-Pro](https://tokopedia.link/sfTHlfS41db), [Ugoos-AM6-Plus](https://tokopedia.link/pHGKXuV41db) | openwrt_s922x_v*.img |
| s912 | [H96-Pro-Plus](https://tokopedia.link/jb42fsBdGgb), Octopus-Planet | openwrt_s912_v*.img |
| s905d | Phicomm-N1 | openwrt_s905d_v*.img |


#
#

- ## [查看最新可用核心型号](https://github.com/281677160/openwrt-package/tree/kernel/kernel)

#
#

- ## 打包固件机型和核心组合方法 
```
机型和核心组合设置在：build/openwrt_amlogic/diy-part.sh


amlogic_modelw为机型设置，多机型需要中间加‘_’间隔，比如s922x_s912
amlogic_kernel为内核设置，多内核需要中间加‘_’间隔，比如5.12.12_5.4.127
rootfs_size为rootfs分区大小，不能小于500，不懂就默认不要修改
所有CPU型号为：s905x3_s905x2_s905x_s905d_s922x_s912
比如你要打包N1的固件，就选择s905d的，然后选择核心版本，核心版本上面的链接可以查看，多机型跟多核心都要中间加‘_’
amlogic_kernel内核如果保持5.12.12_5.4.127不修改的话，每次编译都会默认同步作者的最新版本，云编译的时候可以在编译信息查看到你编译的内核版本详情


比如这样的，就是单机型+单核心组合打包
cat >$GITHUB_WORKSPACE/amlogic_openwrt <<-EOF
amlogic_model=s905d
amlogic_kernel=5.12.12
rootfs_size=1200
EOF


比如这样的，就是多机型+多核心组合打包，自由组合。
cat >$GITHUB_WORKSPACE/amlogic_openwrt <<-EOF
amlogic_model=s905x3_s905x2_s905x_s905d_s922x_s912
amlogic_kernel=5.12.12_5.4.127
rootfs_size=1200
EOF


请注意，不是组合越多就越好的，要根据自己个人需求组合，要不然打包的固件太多，服务器空间不够用就打包失败了。



如果用的是我的一键本地编译的话，一键打包命令也差不多意思

比如多个机型内核：
sudo ./make -d -b s905x3_s905x2_s905x_s905d_s922x_s912 -k 5.12.12_5.4.127

比如单个机型内核：
sudo ./make -d -b s905d -k 5.12.12

比如单个机型双内核：
sudo ./make -d -b s905d -k 5.12.12_5.4.127

```

#
#
#

- ## luci-app-amlogic 插件使用说明

- 安装固件：从浏览器登录 OpenWrt  → `系统菜单` → `晶晨宝盒` → `安装 OpenWrt`
#
- 升级固件：从浏览器登录 OpenWrt  → `系统菜单` → `晶晨宝盒` → `升级 OpenWrt`
#

## Screenshot / 截图

![luci-app-amlogic](https://user-images.githubusercontent.com/68696949/121277810-f9ebd800-c903-11eb-9bf4-7c2b11f9a1d3.gif)
