- # 电报机器人推送，TOKEN跟ID获取方式

- 1、 首先你得有个[telegram](https://telegram.org/)，推送消息需要 TELEGRAM_BOT_TOKEN 跟 TELEGRAM_CHAT_ID

- 2、 整一个电报机器人, 在你的 telegram 搜索BotFather, 然后在与它的对话框中输入 /start 然后出来一堆命令符的，按 /newbot 指令,会出来一堆英文，意思是建立了一个新的机器人，问你机器人叫什么名字，你按你意思随便打一个就好了，比如叫danshui,在聊天框输入danshui发送，如果名字没给占用就可以继续下一步了，如果名字给占用了就继续设计名字，你们自己看看英文提示吧，比如danshui没给占用，下一步就继续要给机器人一个称呼，这个称呼得加 _bot 结尾，随便都可以，我就按习惯的继续用 danshui_bot 如果名字没给占用，他就出来一堆英文还有带上你刚刚建立的 danshui_bot 的名字在里面，[这个 danshui_bot 是一个链接来的，就是你的机器人了，点一下这个链接进入你的机器人，随便给他发一个信息，什么内容都可以，这个随便给它发信息是很重要的，关系到你能不能获得ID的问题](#)，然后回来看那堆英文里面有大写 HTTP API: 后面跟着一串东西的，比如 
-     9876543201:FEDCBA_dfoiuweSWEczgxT7-l4r9Y 这个就是你的TELEGRAM_BOT_TOKEN

- 这串东西不应泄露给他人,否则被人滥用的话会导致该bot被禁止.


- 3、 找到你的 TELEGRAM_CHAT_ID，在你的Telegram搜索 @get my id ，就跟加好友一样，搜索出来有好几Get My ID个机器人的，随便点一个，然后聊天窗口那里点开始聊天，就能显示出你的TELEGRAM_CHAT_ID

- 4、TELEGRAM_BOT_TOKEN 跟 TELEGRAM_CHAT_ID生成好了，接下来到你自己的仓库，点Settings，再点左边的Secrets，然后点右上角的`New repositonry secret`，然后在Name下面的方框写上名字，名字为（TELEGRAM_BOT_TOKEN）不包括括号，Value下面大方框放进9876543201:FEDCBA_dfoiuweSWEczgxT7-l4r9Y，点下面的绿色按钮Add secret保存即完成

- 5、接下来再按`New repositonry secret`，然后在Name下面的方框写上名字，名字为（TELEGRAM_CHAT_ID）不包括括号，Value下面大方框放进1239000174，点下面的绿色按钮Add secret保存即完成

- [《存放密匙方法的图片形式介绍，此链接里面的倒数第三个图片开始就是密匙存放方法》](https://github.com/danshui-git/shuoming/blob/master/jm.md#%E8%8E%B7%E5%8F%96%E5%AF%86%E5%8C%99%E5%90%8E%E6%88%91%E4%BB%AC%E7%8E%B0%E5%9C%A8%E5%8E%BB%E6%82%A8%E9%9C%80%E8%A6%81%E5%AF%86%E5%8C%99%E7%9A%84%E4%BB%93%E5%BA%93%E5%AD%98%E6%94%BE%E5%AF%86%E5%8C%99)

- 6、设置完毕后如果打开了SSH连接的话，到了SSH这个步骤会自动把代码发送给你，也可以用于编译前后的信息提示。

#
---
#

- # pushplus推送，TOKEN的获取方式


- 1、pushplus推送，[点击这里](http://www.pushplus.plus/push1.html)，微信扫码登录，就可以看到你的token了
#
- 2、复制好pushplus你的token后，接下来到你自己的仓库，点Settings，再点左边的Secrets，然后点右上角的New repositonry secret，然后在Name下面的方框写上名字，名字为（PUSH_PLUS_TOKEN）不包括括号，Value下面大方框放进密匙，点下面的绿色按钮Add secret保存即完成
- [《存放密匙方法的图片形式介绍，此链接里面的倒数第三个图片开始就是密匙存放方法》](https://github.com/danshui-git/shuoming/blob/master/jm.md#%E8%8E%B7%E5%8F%96%E5%AF%86%E5%8C%99%E5%90%8E%E6%88%91%E4%BB%AC%E7%8E%B0%E5%9C%A8%E5%8E%BB%E6%82%A8%E9%9C%80%E8%A6%81%E5%AF%86%E5%8C%99%E7%9A%84%E4%BB%93%E5%BA%93%E5%AD%98%E6%94%BE%E5%AF%86%E5%8C%99)
