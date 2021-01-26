# 结合大神们的帖子，修复NTFS格式优盘不自动挂载和热拨插卡机问题

- 把以下代码全部放入diy-2.sh里面生效，不过不支持Lienol源码，Lienol源码是不是本来就支持我也没测试了，lede源码用了后就测试没问题，Lienol源码你们自己测试看看，不过要用在Lienol源码上要把里面的ntfs-3g-utils去掉，要不然冲突，编译错误

---
```yaml
mkdir -p files/etc/hotplug.d/block && svn co https://github.com/281677160/openwrt-package/branches/usb/block files/etc/hotplug.d/block
ntfs="DEFAULT_PACKAGES += usbutils fdisk ntfs-3g-utils badblocks kmod-usb-ohci-pci kmod-usb-uhci kmod-usb-hid e2fsprogs wpad \
kmod-usb2-pci kmod-usb3 kmod-usb-storage-extras kmod-usb-storage-uas kmod-fs-ext4 kmod-fs-vfat "
sed -i "s/DEFAULT_PACKAGES += /$ntfs/" target/linux/*/Makefile
```
---
#
#
#

- 以上是自动搞定，还可以手动的，[手动说明](https://github.com/danshui-git/shuoming/blob/master/NTFS%E6%A0%BC%E5%BC%8F%E4%BC%98%E7%9B%98%E6%8C%82%E8%BD%BD)
