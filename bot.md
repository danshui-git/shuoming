#### 电报机器人推送消息设置

- 1、 首先你得有个[telegram](https://telegram.org/)，推送消息需要 TELEGRAM_BOT_TOKEN 跟 TELEGRAM_CHAT_ID

- 2、 整一个电报机器人, 在你的telegram点击一个跟放大镜一样的图标，搜索BotFather, 然后在与它的对话框中输入 /start 然后出来一堆命令符的，按 /newbot 指令,会出来一堆英文，意思是建立了一个新的机器人，问你机器人叫什么名字，你按你意思随便打一个就好了，比如叫danshui,如果名字没给占用就可以继续下一步了，如果名字给占用了就继续设计名字，你们自己看看英文提示吧，比如danshui没给占用，下一步就继续要给机器人一个称呼，这个称呼得加_bot结尾，随便都可以，我就按习惯的继续用 danshui_bot 如果名字没给占用，他就出来一堆英文还有带上你刚刚建立的 danshui_bot 的名字在里面，这个名字是一个链接来的，就是你的机器人了，点一下这个链接进入你的机器人，随便给他发一个信息，什么信息都可以，然后回来看那个堆英文里面有大写 HTTP API: 后面跟着一串东西的，比如 
-     9876543201:FEDCBA_dfoiuweSWEczgxT7-l4r9Y 这个就是你的TELEGRAM_BOT_TOKEN

- 这串东西不应泄露给他人,否则被人滥用的话会导致该bot被禁止.

- 3、 找到你的TELEGRAM_CHAT_ID:

-  如果前面你已经点了 danshui_bot 的名字链接来发送过一次内容了就继续下面步骤，如果没有请去点击发送一次

-  将前面获得的TELEGRAM_BOT_TOKEN替换掉这个url中的XXYY部分,
-     https://api.telegram.org/botXXYY/getUpdates

- 把TELEGRAM_BOT_TOKEN替换掉XXYY应该是这样的:   
-     https://api.telegram.org/bot987654321:FEDCBA_dfoiuweSWEczgxT7-l4r9Y/getUpdates   
- 然后在浏览器访问这个链接, 然后出来一串字符的，在字符里面找到message_id，需要注意的是这一串字符里面有3组阿拉伯数字的，你找"message_id":1,"from":{"id":1239000174,"is_bot" 1239000174这个就是你的TELEGRAM_CHAT_ID

-4、     总结你获得的TELEGRAM_BOT_TOKEN为：987654321:FEDCBA_dfoiuweSWEczgxT7-l4r9Y

-     你获得的TELEGRAM_BOT_TOKEN为：1239000174
