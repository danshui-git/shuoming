

- 内核仓库选择说：

- [stable（稳定版）](https://github.com/ophub/kernel/releases/tag/kernel_stable)

- [dev（测试版）](https://github.com/ophub/kernel/releases/tag/kernel_dev)

- [flippy（unifreq版）](https://github.com/ophub/kernel/releases/tag/kernel_flippy)

- [rk3588（Rock-5B和HinLink-H88K专用版）](https://github.com/ophub/kernel/releases/tag/kernel_rk3588)

- [芯片型号对应什么机型说明](https://github.com/ophub/amlogic-s9xxx-openwrt/blob/main/README.cn.md#openwrt-%E5%9B%BA%E4%BB%B6%E8%AF%B4%E6%98%8E)

- [手动打包再次，或者多次打包固件说明](https://github.com/danshui-git/shuoming/blob/master/sddb.md)
#


```sh
机型和核心组合设置在[diy-part.sh]控制文件设置


export amlogic_model="此内填入可用芯片，或多芯片组合。比如：s905d 或 s905d_s905x2"

export amlogic_kernel="此内填入内核，或者多内核组合。比如：5.4.233 或 5.4.233_6.1.14"

export auto_kernel="true" 是否自动检测最新内核来打包（true为是，false为不是）
自动检测最新内核,比如您写的是 5.15.25 当前最高版本为 5.15.78 的话就自动打包5.15.78的,不自动检测的话,就打包 5.15.25

export rootfs_size="填入不低于2560的数值，数值越大空间越大，一般2560够了"

export kernel_usage="上游存放内核的仓库地址，可用仓库：stable、dev、flippy、rk3588"

可用芯片如下：
a311d,s922x,s922x-reva,s922x-ct2000,s905x3,s905x3-b,s905x2,s912,s912-m8s,tqc-a01,tanix-tx6,
s905d,s905d-ki,s905x,s905w,s905,s905l2,s905l3,s905l3a,s905l3b,s905lb-r3300l,rock5b,
h88k,r66s,r68s,h66k,h68k,e25,eaidk-610,king3399,tn3399,kylin3399,beikeyun,l1pro,vplus


比如单独打包N1的固件，只打包5.10内核的
export amlogic_model="s905d"
export amlogic_kernel="5.10.100"
export auto_kernel="true"
export rootfs_size="2560"
export kernel_usage="stable"
 
 
比如打包N1和的s922x，要打包出5.10内核跟6.1内核的固件
export amlogic_model="s905d_s922x"
export amlogic_kernel="5.10.100_6.1.20"
export auto_kernel="true"
export rootfs_size="2560"
export kernel_usage="stable"


请注意，不是组合越多就越好的，每个内核就打包一个固件而已，不是一个固件里面可以塞进去几个内核的，
要根据自己个人需求组合，要不然打包的固件太多，服务器空间不够用就打包失败了。
```
#
#

## 安装及升级 OpenWrt 的相关说明

- 选择和你的电视盒子型号对应的 OpenWrt 固件，使用 [Rufus](https://rufus.ie/) 或者 [balenaEtcher](https://www.balena.io/etcher/) 等工具将固件写入USB里，然后把写好固件的USB插入电视盒子。

- 提示：安装/升级等功能由 [luci-app-amlogic](https://user-images.githubusercontent.com/68696949/145738345-31dd85cf-5e43-444e-a624-f21a28be2a7c.gif) 提供可视化操作支持。

---
### 安装 OpenWrt

- 从浏览器访问 OpenWrt 的默认 IP: 192.168.1.1 → `使用默认账户登录进入 OpenWrt` → `系统菜单` → `晶晨宝盒` → `安装 OpenWrt` ，在支持的设备下拉列表中选择你的盒子，点击 `安装 OpenWrt` 按钮进行安装。

---
### 升级 OpenWrt

- 从浏览器访问 OpenWrt 的 IP 如: 192.168.1.1 →  `使用账户登录进入 OpenWrt` → `系统菜单` → `晶晨宝盒` → `手动上传更新 / 在线下载更新`

- 如果选择 `手动上传更新` OpenWrt固件，可以将[编译](https://github.com/281677160/build-actions)好 OpenWrt 固件压缩包，如 openwrt_s9xxx_k5.15.25_xxx.img.gz 进行上传（推荐上传压缩包，系统会自动解压。如果上传解压缩后的 xxx.img 格式的文件，可能会因为文件太大而上传失败），上传完成后界面将显示 `更新固件` 的操作按钮，点击即可更新。

- 如果选择 `手动上传更新` [OpenWrt 内核](https://github.com/ophub/kernel/tree/main/pub/stable)，可以将 `boot-xxx.tar.gz`, `dtb-amlogic-xxx.tar.gz`, `modules-xxx.tar.gz` 这 3 个内核文件上传（其他内核文件不需要，如果同时上传也不影响更新，系统可以准确识别需要的内核文件），上传完成后界面将显示 `更新内核` 的操作按钮，点击即可更新。

- 如果选择 `在线下载更新` OpenWrt 固件或内核，将根据`插件设置`中的`固件下载地址`和`内核下载地址`进行下载，你可以自定义修改下载来源，具体操作方法详见 [luci-app-amlogic](https://github.com/ophub/luci-app-amlogic) 的编译与使用说明。

---
### 在 TF/SD/USB 中使用 OpenWrt

- 从浏览器访问 OpenWrt 的默认 IP: 192.168.1.1 → `使用默认账户登录进入 OpenWrt` → `系统菜单` → `TTYD 终端` → 输入命令

```yaml
openwrt-tf
```

- 激活剩余空间后，支持在 TF/SD/USB 中升级内核和 OpenWrt 系统。

---
### 为 OpenWrt 创建 swap

- 如果你在使用 `docker` 等内存占用较大的应用时，觉得当前盒子的内存不够使用，可以创建 `swap` 虚拟内存分区，将 `/mnt/*4` 磁盘空间的一定容量虚拟成内存来使用。下面命令输入参数的单位是 `GB`，默认为 `1`。

- 从浏览器访问 OpenWrt 的默认 IP: 192.168.1.1 → `使用默认账户登录进入 OpenWrt` → `系统菜单` → `TTYD 终端` → 输入命令

```yaml
openwrt-swap 1
```

---
### 备份/还原 EMMC 原系统

- 支持在 `TF/SD/USB` 中对盒子的 `EMMC` 分区进行备份/恢复。建议您在全新的盒子里安装 OpenWrt 系统前，先对当前盒子自带的安卓 TV 系统进行备份，以便日后在恢复电视系统等情况下使用。

- 请从 `TF/SD/USB` 启动 OpenWrt 系统，浏览器访问 OpenWrt 的默认 IP: 192.168.1.1 → `使用默认账户登录进入 OpenWrt` → `系统菜单` → `TTYD 终端` → 输入命令

```yaml
openwrt-ddbr
```

- 根据提示输入 `b` 进行系统备份，输入 `r` 进行系统恢复。

💡提示：须使用 `/mnt/*4/` 空间进行存放 `BACKUP-arm-64-emmc.img.gz` 备份文件，未创建 `TF/SD/USB` 扩展分区的用户，须先使用 `openwrt-tf` 命令创建扩展分区。

---
### 控制 LED 显示

- 从浏览器访问 OpenWrt 的默认 IP: 192.168.1.1 → `使用默认账户登录进入 OpenWrt` → `系统菜单` → `TTYD 终端` → 输入命令

```yaml
openwrt-led
```

- 根据 [LED 屏显示控制说明]([https://github.com/ophub/amlogic-s9xxx-armbian/blob/main/build-armbian/armbian-docs/led_screen_display_control.md](https://github.com/ophub/amlogic-s9xxx-armbian/blob/main/build-armbian/documents/led_screen_display_control.md#led-%E5%B1%8F%E6%98%BE%E7%A4%BA%E6%8E%A7%E5%88%B6%E8%AF%B4%E6%98%8E)) 进行调试。

---
- ## 晶晨宝盒 使用截图

![luci-app-amlogic](https://user-images.githubusercontent.com/68696949/145738345-31dd85cf-5e43-444e-a624-f21a28be2a7c.gif)

---
- # 以上相关内容全部获取与[ophub/amlogic-s9xxx-openwrt](https://github.com/ophub/amlogic-s9xxx-openwrt)，需要更新更详细的内容可移步至此大佬仓库查看，感谢大佬的付出！
