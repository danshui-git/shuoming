# 《.github/workflows》里面的脚.yml主文件本部分说明
#
- `REPO_URL: https://github.com/coolsnowwolf/lede` （更换链接可以编译不一样大神的固件）
#
- `REPO_BRANCH: master`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（跟上面链接对应的分支，比如Lienol大神的就有dev-19.07跟dev-master分支，要编译什么固件就要写什么的）
#
- `FEEDS_CONF: feeds.conf.default`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（可以在根目录创建一个feeds.conf.default文件，也是自定义插件使用）
#
- `CONFIG_FILE: diy.config`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（在根目录创建.config跟主文件.yml配对，名字随便写，保持.config格式就可以，这个文件叫什么名字，就要在.yml文件这里写上对应的名字）如果你创建多个主文件，就创建多个.config文件配对`（比如我在根目录创建的是diy.config，就要在这里写上对应的文件名字diy.config）`
#
- `DIY_OP_SH: diy-lede.sh`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（在根目录创建.sh跟主文件.yml配对，名字随便写，保持.sh格式就可以，这个文件叫什么名字，就要在.yml文件这里写上对应的名字）如果你创建多个主文件，就创建多个.sh文件配对`（比如我在根目录创建的是diy-lede.sh，就要在这里写上对应的文件名字diy-lede.sh）`
#
- `SSH_ACTIONS: true`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（SSH远程连接服务器配置固件，true开,false关）
#
- `UPLOAD_BIN_DIR: false`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（上传BIN文件夹（固件+IPK）到github空间,跟上传固件二选一即可,true开,false关）
#
- `UPLOAD_FIRMWARE: true`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（上传固件到github空间,跟上传BIN文件夹二选一即可,true开,false关）
#
- `UPLOAD_COWTRANSFER: false`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（上传固件到奶牛网盘,true开,false关）
#
- `UPLOAD_WETRANSFER: false`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（上传固件到WETRANSFER网盘,true开,false关）
<font color=000000>红色文字</font>
