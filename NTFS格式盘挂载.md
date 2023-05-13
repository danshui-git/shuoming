# NTFS格式盘挂载

1、在最新版的编译脚本的自定义设置文件（diy-part.sh）里面，

把 export Automatic_Mount_Settings="0" 改成 export Automatic_Mount_Settings="1" 搞定

````
export Automatic_Mount_Settings="1"
````

2、安装好固件后，插入U盘或移动硬盘 再次重启路由器 在openwrt的‘系统’-->挂载点 查看设备

如果U盘只有一个分区，就是/mnt/sda1，第二个分区是/mnt/sda2

如果用Hub接入多个U盘，第二个设备就是/mnt/sdb，以此类推

3、如果你编译有luci-app-samba或者luci-app-samba4的话，进入openwrt的网络共享中，添加共享目录例如/mnt/sda1，权限为777(即完全访问)。

至此就可以在网上邻居中看到路由器的这个共享文件夹了。
