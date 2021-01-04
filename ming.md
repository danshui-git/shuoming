##### 各命令说明

###### 首先要说明的是，很多命令都会用到关键字符串这个是很主要的，你要确定这个关键字符串在当前文件里面是独一无二的，可以很长也可以很短，可以不完整的，也可以是完整的一句

       sed -i "/danshui/a\281677160" xxx/123.txt

先查找关键字符串danshui，然后在danshui字符串下一行插入281677160，xxx/123.txt是文件

比如:在源码的zzz-default-settings文件关键字符串下面增加一行代码，zzz-default-settings文件在源码的package/lean/default-settings/files里面

然后就可以写出整个命令了：sed -i "/mwan.htm/a\281677160" package/lean/default-settings/files/zzz-default-settings

示例
文件原本是这样的
rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

用了命令后
rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
281677160
rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

要记住，这个增加方法，用了后只会在
