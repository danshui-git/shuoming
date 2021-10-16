# 编译时选择固件格式和修改overla空间方法
#
# <img src="https://github.com/danshui-git/shuoming/blob/master/doc/ov1.png" />
# <img src="https://github.com/danshui-git/shuoming/blob/master/doc/ov3.png" />
- ## 设置overla空间容量的数值请不要使用"128、256、512、1024、2048、4096"等死亡数值，容易造成编译之时因为空间不足而编译失败
#
#
- ### 还有一个tmp空间的顺便也说说，这个空间大小是取决于你机子的运行内存大小而定的，理论上是你运行内存容量的一半，但是一般都达不到的，比如说你是x86平台的，使用虚拟机安装openwrt的话，你分配1G内存给openwrt，那你的tmp空间就480M左右，2G就960多
