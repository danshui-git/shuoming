- ## CPU型号跟机型的对照表

| 芯片  | 设备 | [可选内核](https://github.com/ophub/kernel/tree/main/pub/stable) | OpenWrt 固件 |
| ---- | ---- | ---- | ---- |
| a311d | [Khadas-VIM3](https://www.gearbest.com/boards---shields/pp_3008145189226460.html) | 全部 | openwrt_a311d_k*.img |
| s922x | [Beelink-GT-King](https://tokopedia.link/RAgZmOM41db), [Beelink-GT-King-Pro](https://www.gearbest.com/tv-box/pp_3008857542462482.html), [Ugoos-AM6-Plus](https://tokopedia.link/pHGKXuV41db), [ODROID-N2](https://www.tokopedia.com/search?st=product&q=ODROID-N2) | 全部 | openwrt_s922x_k*.img |
| s905x3 | [X96-Max+](https://tokopedia.link/uMaH09s41db), [HK1-Box](https://tokopedia.link/xhWeQgTuwfb), [H96-Max-X3](https://tokopedia.link/KuWvwoYuwfb), [Ugoos-X3](https://tokopedia.link/duoIXZpdGgb), [TX3](https://www.aliexpress.com/item/1005003772717802.html), [X96-Air](https://www.gearbest.com/tv-box/pp_3002885621272175.html), [A95XF3-Air](https://tokopedia.link/ByBL45jdGgb) | 全部 | openwrt_s905x3_k*.img |
| s905x2 | [X96Max-4G](https://tokopedia.link/HcfLaRzjqeb), [X96Max-2G](https://tokopedia.link/HcfLaRzjqeb), [MECOOL-KM3-4G](https://www.gearbest.com/tv-box/pp_3008133484979616.html) | 全部 | openwrt_s905x2_k*.img |
| s905l3a | [E900V22C/D](https://github.com/Calmact/e900v22c) | 全部 | openwrt_s905l3a_k*.img |
| s912 | [H96-Pro-Plus](https://www.gearbest.com/tv-box-mini-pc/pp_503486.html), [Tanix-TX92](http://www.tanix-box.com/project-view/tanix-tx92-android-tv-box-powered-amlogic-s912/), [VORKE-Z6-Plus](http://www.vorke.com/project/vorke-z6-2/), [Mecool-M8S-PRO-L](https://www.gearbest.com/tv-box/pp_3005746210753315.html), Octopus-Planet | 全部 | openwrt_s912_k*.img |
| s905d | [MECOOL-KI-Pro](https://www.gearbest.com/tv-box-mini-pc/pp_629409.html), Phicomm-N1 | 全部 | openwrt_s905d_k*.img |
| s905x | [HG680P](https://tokopedia.link/HbrIbqQcGgb), [B860H](https://www.zte.com.cn/global/products/cocloud/201707261551/IP-STB/ZXV10-B860H) | 全部 | openwrt_s905x_k*.img |
| s905w | [X96-Mini](https://tokopedia.link/ro207Hsjqeb), [TX3-Mini](https://www.gearbest.com/tv-box/pp_009748238474.html) | 5.4.* | openwrt_s905w_k*.img |
| s905 | [Beelink-Mini-MX-2G](https://www.gearbest.com/tv-box-mini-pc/pp_321409.html), [MXQ-PRO+4K](https://www.gearbest.com/tv-box-mini-pc/pp_354313.html) | 全部 | openwrt_s905_k*.img |

💡提示：当前 ***`s905`*** 的盒子只能在 `TF/SD/USB` 中使用，其他型号的盒子同时支持写入 `EMMC` 中使用。当前 ***`s905w`*** 系列的盒子只支持使用 `5.4` 内核，不能使用 5.10 或更高版本，其他型号的盒子可任选内核版本使用。每个盒子的 dtb 和 u-boot 请查阅[说明](https://github.com/ophub/amlogic-s9xxx-armbian/blob/main/build-armbian/armbian-docs/config_correspondence_of_amlogic_s9xxx_tv_box.md)。

#
- 可以指定打包所用型号有: `a311d`, `s905x3`, `s905x2`, `s905l3a`, `s905x`, `s905w`, `s905d`, `s905d-ki`, `s905`, `s922x`, `s922x-n2`, `s912`, `s912-m8s` 。

- 机型说明：`s922x-reva` 是 `s922x-gtking-pro-rev_a`，`s922x-n2` 是 `s922x-odroid-n2` ，`s912-m8s` 是 `s912-mecool-m8s-pro-l` ，`s905d-ki` 是 `s912-mecool-ki-pro`，`s905x2-km3` 是 `s905x2-mecool-km3` 
#

```sh
机型和核心组合设置在：build/openwrt_amlogic/diy-part.sh


amlogic_modelw为机型设置，多机型需要中间加‘_’间隔，比如 s922x_s912
amlogic_kernel为内核设置，多内核需要中间加‘_’间隔，比如 5.10.100_5.4.180
保持 5.10.100_5.4.180 -a true 不修改的话，每次编译都会默认同步上游仓库最新内核打包
rootfs_size为rootfs分区大小，不能小于500，不懂就默认不要修改。
组合方法通样适宜于本地打包的


比如这样的，就是单机型+单核心组合打包
cat >$GITHUB_WORKSPACE/amlogic_openwrt <<-EOF
amlogic_model=s905d
amlogic_kernel=5.10.70
rootfs_size=960
EOF


比如这样的，就是双机型+双核心组合打包
cat >$GITHUB_WORKSPACE/amlogic_openwrt <<-EOF
amlogic_model=s905x3_s905x2
amlogic_kernel=5.10.100_5.4.170
rootfs_size=960
EOF


这个组合就是全机型+自动检测最新双内核打包
cat >$GITHUB_WORKSPACE/amlogic_openwrt <<-EOF
amlogic_model=s905x3_s905x2_s905x_s905w_s905d_s922x_s912
amlogic_kernel=5.10.100_5.4.180 -a true
rootfs_size=960
EOF


请注意，不是组合越多就越好的，每个内核就打包一个固件而已，不是一个固件里面可以塞进去几个内核的，
要根据自己个人需求组合，要不然打包的固件太多，服务器空间不够用就打包失败了。
```
- [内核版本时时变动的，所以选择内核之前，一定要点击这里查看一下当前可用内核，随便搞的话，没有该内核，打包就失败](https://github.com/ophub/kernel/tree/main/pub/stable)
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

- 从浏览器访问 OpenWrt 输入IP，比如 192.168.1.1 → 使用默认账户登录进入 OpenWrt → 系统菜单 → TTYD 终端 → 输入命令 →  `openwrt-tf`

- 激活剩余空间后，支持在 TF/USB 中升级内核和 OpenWrt 系统。
- ---

- ## 晶晨宝盒 使用截图

![luci-app-amlogic](https://user-images.githubusercontent.com/68696949/121277810-f9ebd800-c903-11eb-9bf4-7c2b11f9a1d3.gif)
