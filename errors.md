- ## 编译错误自查法

- 【开编译固件】步骤出现错误的话，首先就去【下载软件包】的步骤查看你编译进固件的插件是否缺依赖，比如以下图片
- # <img src="https://github.com/danshui-git/shuoming/blob/master/doc/er2.png" />
---
- 如果以上没有发现缺依赖，或者说虽然有插件缺依赖，但是你又没选择这个插件，那就下载日志查看错误了，下载日志方法看下面图片
- # <img src="https://github.com/danshui-git/shuoming/blob/master/doc/er4.png" />
- 日志下载来后解压压缩包，里面会有一个【编译 xxx】的文件夹，文件夹里面找一份【开始编译固件.txt】的文件，然后搜索【Error 1】还有【Error 2】，看看对应那一行显示什么错误，或者附近也看看，很多编译错误都是很明显的，一般都能看出来

- 下面我拿2个编译错误为例：
---
- # <img src="https://github.com/danshui-git/shuoming/blob/master/doc/er5.png" />
- 上面这个图片的错误是找出来了，但是看不太明白，实在是我也不知道那里错了，如果是出现这个情况的话，你就把你编译的文件夹里面的.config配置文件，只保留机型的3项，然后再编译一次，如果还出现错误，那就是源码有问题，源码有问题就去找该源码的作者，在他的仓库提issues，我每个文件夹都有标注出源码出处的链接的，提issues的时候要把错误的详细也发过去，这样人家才知道你什么错误怎么解决
---
- 再来看个简单点的，以下图片为例
- # <img src="https://github.com/danshui-git/shuoming/blob/master/doc/er7.png" />
