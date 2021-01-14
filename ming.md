# 各命令说明

### 首先要说明的是，很多命令都会用到关键字符串这个是很主要的，你要确定这个关键字符串在当前文件里面是独一无二的，可以很长也可以很短，可以不完整的，也可以是完整的一句
#
# 1
#
    sed -i "/danshui/a\281677160" xxx/123.txt

- 先查找关键字符串danshui，然后在danshui字符串下一行插入281677160，xxx/123.txt是文件

- 比如:在源码的zzz-default-settings文件关键字符串下面增加一行代码，zzz-default-settings文件在源码的package/lean/default-settings/files里面，然后正确的整个路径就是：package/lean/default-settings/files/zzz-default-settings

- ######  下面的文件我都拿zzz-default-settings做举例了，意思就是xxx/123.txt变成package/lean/default-settings/files/zzz-default-settings

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
# 2
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
# 3
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
# 4
#  
    sed -i 's/danshui/281677160/g' xxx/123.txt
- 先查找关键字符串danshui，然后替换成你想要的，比如我现在danshui替换成281677160，xxx/123.txt是文件，要注意的是关键字符串不能带有/的

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

- sed -i 's/$1$V4UetPzk$CYXluq4wUazHjmCDBCqXF.:0/$1$K8/hZkV0$9JIcU2UgNv.ApnS6Q3RGj.:18631/g' package/lean/default-settings/files/zzz-default-settings

#
#
# 5
#  
- 使用命令拉取别人的仓库

- 比如拉取我的插件包

      git clone https://github.com/281677160/openwrt-package package/danshui
      
 - 这个其实很好理解的 git clone 就是下载，下载东西肯定得有地址啊，https://github.com/281677160/openwrt-package 就是地址，下载了后要存放在什么地方呢？ 源码的package文件夹就是存放地方，存放的时候要不要建立一个文件夹来存放呢？如果需要的话，就在package后面跟一个文件夹名字，名字你随便改，不过不能跟源码里面的文件夹重名
 
 - 这样拉取的是别人主仓库，怎么看是不是主仓库呢？就是用链接打开后直接能见的就是主仓库，还可以有分支的，如果要拉取分支怎么办呢？在链接前面加个分支号就好了
 
       git clone -b 19.07 https://github.com/281677160/openwrt-package package/danshui
       
 - 就这样就OK了，加个-b 然后分支名称，那个19.07就是我插件包的另外一个分支，如果你们拉取别人的仓库，要拉取其他分支，就改成他的分支名称就可以了
 
#
#
# 6
#  
- 单独拉取特定的插件或者文件，比如单独拉取插件包的luci-app-clash

      svn co https://github.com/281677160/openwrt-package/trunk/luci-app-clash package/luci-app-clash
      
- 这个关系就跟上面差不多了，就不多说了，重点要说的是这个链接是有改变的，怎么改变法呢？整个链接真正的是这样的，这个原始链接怎么来呢?比如你在别人的仓库看到某个插件，再点开那个插件的文件夹，然后在浏览器复制完整链接就是了。如果有分支的，你想要分支的插件，就先选择了分支再打开插件文件夹然后在复制链接就可以了。

      https://github.com/281677160/openwrt-package/tree/master/luci-app-clash
      
- 大家看清楚没有？链接里面是带有分支名称的，还有一个tree，就是这个了 tree/master 把这里替换成 trunk 就可以了，主仓库就这样拉取，如果要拉取分支的呢？也简单的，把tree改成branches就行，比如

      svn co https://github.com/281677160/openwrt-package/branches/19.07/luci-app-eqos package/luci-app-eqos
