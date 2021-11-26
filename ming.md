# 各命令说明

### 首先要说明的是，很多命令都会用到关键字符串这个是很主要的，你要确定这个关键字符串在当前文件里面是独一无二的，可以很长也可以很短，可以不完整的，也可以是完整的一句
#
### 拉取插件的命令放在diy-1.sh文件，其他命令一般都是放在diy-2.sh使用，请大家勿搞错了
#

- #### 以下所有命令的关键字符串我都使用 mwan.htm 你们要明白你们要干什么的时候在该文件怎么找出独一无二的关键字符串就好了

- ####  下面的文件我都拿zzz-default-settings做举例了，文件在源码的package/lean/default-settings/files里面，然后正确的整个路径就是：package/lean/default-settings/files/zzz-default-settings

---
# 第1条
#
- 先查找关键字符串mwan.htm，然后在这个关键字符串下面增加一行代码
```yaml
    命令：sed -i "/mwan.htm/a\281677160" package/lean/default-settings/files/zzz-default-settings

- 示例
###### 如果文件原本是这样的
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

##### 用了命令后
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    281677160                                                      <------ 用了命令后，这里增加一行代码了
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

###### 要记住，这个增加方法，用了后只会对齐第一格的，如果不是第一格就能生效的文件就不能用，比如原来的文件是空了格的，你这样加进去就可能造成格式错误导致编译错误了
       
       rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    281677160                        <------ 用了命令后，这里增加一行代码了，但是跟文件夹本来的源码不对称，可能造成格式错误了
       rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm

      rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm
```
---
#
---
# 第2条
#

- 先查找关键字符串mwan.htm，然后把这一行代码最前面的#号去掉
```yaml
    命令：sed -i 's/^#\(.*mwan.htm\)/\1/' package/lean/default-settings/files/zzz-default-settings

- 示例
###### 如果文件原本是这样的
    #rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    #rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    #rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

##### 用了命令后
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm       <------ 用了命令后，前面的 # 去掉了
    #rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    #rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm
    
###### 其实这个命令你们很经常见的，那就是增加lede源码的ShadowSocksR Plus+
    sed -i 's/^#\(.*helloworld\)/\1/' feeds.conf.default
```
---    
    
#
---
# 第3条
#    
- 先查找关键字符串mwan.htm，然后在这一行代码最前面增加 # 号
```yaml
    命令：sed -i 's@.*mwan.htm*@#&@g' package/lean/default-settings/files/zzz-default-settings

- 示例
###### 如果文件原本是这样的
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

##### 用了命令后
    #rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm     <------ 用了命令后，前面增加一个 # 号，这样就忽略了这行代码了
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm
    
###### 其实这个命令你们很经常见的，那就是把密码改成空
    sed -i 's@.*CYXluq4wUazHjmCDBCqXF*@#&@g' package/lean/default-settings/files/zzz-default-settings
```
---    
#
#
---
# 第4条
#  
- 先查找关键字符串mwan.htm，然后替换成你想要的，要注意的是关键字符串不能带有 / 的
```yaml
    命令：sed -i 's/mwan.htm/281677160/g' package/lean/default-settings/files/zzz-default-settings

- 示例
###### 如果文件原本是这样的
    rm -f /usr/lib/lua/luci/view/admin_status/index/mwan.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm

##### 用了命令后
    rm -f /usr/lib/lua/luci/view/admin_status/index/281677160   <------ 用了命令后，mwan.htm替换成281677160
    rm -f /usr/lib/lua/luci/view/admin_status/index/upnp.htm
    rm -f /usr/lib/lua/luci/view/admin_status/index/ddns.htm
    
###### 其实这个命令你们很经常见的，那就是替换ip
    sed -i 's/192.168.1.1/192.168.2.2/g' package/base-files/files/bin/config_generate
    
- 这个用的比较多，也可在编译的时候替换成你想要的密码的，固件安装好，修改好秘密后，用 [WinSCP](https://winscp.net/eng/download.php) 进入固件，然后在etc文件夹找到 shadow 文件，打开后会有一串加密的密码
类似这样的 root:$1$K8/hZkV0$9JIcU2UgNv.ApnS6Q3RGj.:18631:0:99999:7::: 你们自己去看看，然后在源码的package/lean/default-settings/files/zzz-default-settings对比一下他的密码就明白了
  
###### 原密码
    root::0:0:99999:7:::/root:$1$V4UetPzk$CYXluq4wUazHjmCDBCqXF.:0:0:99999:7:::
  

- 我的替换方式是这样的

      sed -i 's/$1$V4UetPzk$CYXluq4wUazHjmCDBCqXF.:0/$1$K8/hZkV0$9JIcU2UgNv.ApnS6Q3RGj.:18631/g' package/lean/default-settings/files/zzz-default-settings
```
---
#
#
---
# 第5条
#  
- 使用命令拉取别人的仓库

- 比如我要拉取这个仓库：

      https://github.com/281677160/openwrt-package
      
 - 这个其实很好理解的 git clone 就是下载，下载东西肯定得有地址啊，https://github.com/281677160/openwrt-package 就是地址，下载了后要存放在什么地方呢？ 源码的package文件夹就是存放地方，就在package后面跟一个文件夹名字，名字你随便改，不过不能跟源码里面的文件夹重名，如果你拉的是单独插件的话，一般来说改成插件名字容易记忆，比如拉取的是ssr plus就是这样写的，package/luci-app-ssr-plus

- 还有就是拉取别人插件的时候要注意看人家写的内容，有没有需要什么依赖的，需要的话要一起拉取了，要不然拉了也是没用的。

- 下面就列出一下示例：

      git clone https://github.com/fw876/helloworld package/luci-app-ssr-plus
      git clone https://github.com/vernesong/OpenClash package/luci-app-openclash
      git clone https://github.com/jerrykuku/luci-app-vssr package/luci-app-vssr
      git clone https://github.com/xiaorouji/openwrt-passwall package/luci-app-passwall
      git clone https://github.com/frainzy1477/luci-app-clash package/luci-app-clash
      git clone https://github.com/281677160/openwrt-package package/danshui
 
 - 上面那样拉取的是别人主仓库，怎么看是不是主仓库呢？就是用链接打开后直接能见的就是主仓库，还可以有分支的，如果要拉取分支怎么办呢？在链接前面加个分支号就好了
 
       git clone -b 19.07 https://github.com/281677160/openwrt-package package/danshui
       
 - 就这样就OK了，加个-b 然后分支名称，那个19.07就是我插件包的另外一个分支，如果你们拉取别人的仓库，要拉取其他分支，就改成他的分支名称就可以了，要注意格式，该有空格的地方要有空格
--- 
#
#
---
# 第6条
#  
- 单独拉取特定的插件，比如单独拉取我插件包的luci-app-clash

      svn co https://github.com/281677160/openwrt-package/trunk/luci-app-clash package/luci-app-clash
      
- 这个关系就跟上面差不多了，也是要地址，路径的，重点要说的是这个链接是有改变的，怎么改变法呢？整个链接真正的链接看下面的，这个原始链接怎么来呢?比如你在别人的仓库看到某个插件，再点开那个插件的文件夹，然后在浏览器复制完整链接就是了。如果有分支的，你想要分支的插件，就先选择了分支再打开插件文件夹然后在复制链接就可以了。

      https://github.com/281677160/openwrt-package/tree/master/luci-app-clash  <--- 在浏览器上复制出来的真正链接
      
      https://github.com/281677160/openwrt-package/trunk/luci-app-clash        <--- 用的时候修改过的链接，认真对比一下就懂了
      
- 大家看清楚没有？链接里面是带有分支名称的，还有一个tree，就是这个了 tree/master 把这里替换成 trunk 就可以了，主仓库就这样拉取，如果要拉取分支的呢？也简单的，把tree改成branches就行，比如
     
      https://github.com/281677160/openwrt-package/tree/19.07/luci-app-eqos   <--- 在浏览器上复制出来的真正链接
      
      https://github.com/281677160/openwrt-package/branches/19.07/luci-app-eqos   <--- 把链接修改好，把tree/19.07改成branches/19.07，然后前面加svn co 后面加路径

      svn co https://github.com/281677160/openwrt-package/branches/19.07/luci-app-eqos package/luci-app-eqos  <--- 然后就变成这个完整拉取链接
