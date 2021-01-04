# 各命令说明

### 首先要说明的是，很多命令都会用到关键字符串这个是很主要的，你要确定这个关键字符串在当前文件里面是独一无二的，可以很长也可以很短，可以不完整的，也可以是完整的一句
#
1
#
    sed -i "/danshui/a\281677160" xxx/123.txt

- 先查找关键字符串danshui，然后在danshui字符串下一行插入281677160，xxx/123.txt是文件

- 比如:在源码的zzz-default-settings文件关键字符串下面增加一行代码，zzz-default-settings文件在源码的package/lean/default-settings/files里面

- 然后就可以写出整个命令了：sed -i "/mwan.htm/a\281677160" package/lean/default-settings/files/zzz-default-settings

- 示例
###### 如果文件原本是这样的
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

###### 用了命令后
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    281677160
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

###### 要记住，这个增加方法，用了后只会对齐第一格的，如果不是第一格就能生效的文件就不能用，比如原来的文件是空了格的，你这样加进去就可能造成格式错误导致编译错误了
       
       rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    281677160
       rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
       rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm
#
#
2
#
    sed -i 's/^#\(.*danshui\)/\1/' xxx/123.txt

- 先查找关键字符串danshui，然后把这一行代码最前面的#号去掉，xxx/123.txt是文件

- 命令：sed -i 's/^#\(.*mwan.htm\)/\1/' package/lean/default-settings/files/zzz-default-settings

- 示例
###### 如果文件原本是这样的
    #rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    #rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    #rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

###### 用了命令后
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    #rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    #rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm
    
###### 其实这个命令你们很经常见的，那就是增加lede源码的ShadowSocksR Plus+
    sed -i 's/^#\(.*helloworld\)/\1/' feeds.conf.default
    
    
#
#
3
#    
    sed -i 's@.*danshui*@#&@g' xxx/123.txt
- 先查找关键字符串danshui，然后在这一行代码最前面增加#号，xxx/123.txt是文件

- 命令：sed -i 's@.*danshui*@#&@g' package/lean/default-settings/files/zzz-default-settings

- 示例
###### 如果文件原本是这样的
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

###### 用了命令后
    #rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm
    
###### 其实这个命令你们很经常见的，那就是把密码改成空
    sed -i 's@.*CYXluq4wUazHjmCDBCqXF*@#&@g' package/lean/default-settings/files/zzz-default-settings
    
#
#
4
#  
    sed -i 's/danshui/281677160/g' xxx/123.txt
- 先查找关键字符串danshui，然后替换成你想要的，比如我现在替换成281677160，xxx/123.txt是文件

- 命令：sed -i 's/mwan.htm/281677160/g' package/lean/default-settings/files/zzz-default-settings

- 示例
###### 如果文件原本是这样的
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

###### 用了命令后
    rm -f /usr/lib/lua/luci/view/admin_status/index/281677160
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm
    
###### 其实这个命令你们很经常见的，那就是替换ip
    sed -i 's/192.168.1.1/192.168.2.2/g' package/base-files/files/bin/config_generate
    
- 这个用的比较多，也可在编译的时候替换成你想要的密码的，固件安装好，修改好秘密后，用 WinSCP 进入固件，然后在etc文件夹找到 shadow 文件，打开后会有一串加密的密码
类似这样的 root:$1$K8/hZkV0$9JIcU2UgNv.ApnS6Q3RGj.:18631:0:99999:7::: 你们自己去看看，然后在源码的package/lean/default-settings/files/zzz-default-settings对比一下他的密码就明白了
  
###### 原密码
    root::0:0:99999:7:::/root:$1$V4UetPzk$CYXluq4wUazHjmCDBCqXF.:0:0:99999:7:::
  

- 我的替换方式是这样的

      sed -i 's/$1$V4UetPzk$CYXluq4wUazHjmCDBCqXF.:0/$1$K8/hZkV0$9JIcU2UgNv.ApnS6Q3RGj.:18631/g' package/lean/default-settings/files/zzz-default-settings

