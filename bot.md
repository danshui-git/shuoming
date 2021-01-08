#### 电报机器人推送消息设置

- 1、 首先你得有个[telegram](https://telegram.org/)，推送消息需要 TELEGRAM_BOT_TOKEN 跟 TELEGRAM_CHAT_ID

- 2、 整一个电报机器人, 在你的 telegram 搜索BotFather, 然后在与它的对话框中输入 /start 然后出来一堆命令符的，按 /newbot 指令,会出来一堆英文，意思是建立了一个新的机器人，问你机器人叫什么名字，你按你意思随便打一个就好了，比如叫danshui,在聊天框输入danshui发送，如果名字没给占用就可以继续下一步了，如果名字给占用了就继续设计名字，你们自己看看英文提示吧，比如danshui没给占用，下一步就继续要给机器人一个称呼，这个称呼得加_bot结尾，随便都可以，我就按习惯的继续用 danshui_bot 如果名字没给占用，他就出来一堆英文还有带上你刚刚建立的 danshui_bot 的名字在里面，这个名字是一个链接来的，就是你的机器人了，点一下这个链接进入你的机器人，随便给他发一个信息，什么内容都可以，然后回来看那个堆英文里面有大写 HTTP API: 后面跟着一串东西的，比如 
-     9876543201:FEDCBA_dfoiuweSWEczgxT7-l4r9Y 这个就是你的TELEGRAM_BOT_TOKEN

- 这串东西不应泄露给他人,否则被人滥用的话会导致该bot被禁止.

- 3、 找到你的TELEGRAM_CHAT_ID:

-  如果前面你已经点了你自己创建的机器人的名字 danshui_bot 链接来发送过一次信息了就继续下面步骤，如果没有请去点击发送一次

-  将前面获得的TELEGRAM_BOT_TOKEN替换掉下面这个url中的XXYY部分,
-     https://api.telegram.org/botXXYY/getUpdates

- 把TELEGRAM_BOT_TOKEN替换掉XXYY应该是这样的:   
-     https://api.telegram.org/bot9876543201:FEDCBA_dfoiuweSWEczgxT7-l4r9Y/getUpdates   
- 然后在浏览器访问这个链接, 然后出来一串字符的，在字符里面找到message_id，需要注意的是这一串字符里面有3组阿拉伯数字的，你找"message_id":1,"from":{"id":1239000174,"is_bot" 1239000174这个就是你的TELEGRAM_CHAT_ID

-     总结你获得的TELEGRAM_BOT_TOKEN为：9876543201:FEDCBA_dfoiuweSWEczgxT7-l4r9Y

-     你获得的TELEGRAM_CHAT_ID为：1239000174

4、TELEGRAM_BOT_TOKEN 跟 TELEGRAM_CHAT_ID生成好了，接下来到你自己的仓库，点Settings，再点左边的Secrets，然后点右上角的`New repositonry secret`，然后在Name下面的方框写上名字，名字为（TELEGRAM_BOT_TOKEN）不包括括号，Value下面大方框放进9876543201:FEDCBA_dfoiuweSWEczgxT7-l4r9Y，点下面的绿色按钮Add secret保存即完成

5、接下来再按`New repositonry secret`，然后在Name下面的方框写上名字，名字为（TELEGRAM_CHAT_ID）不包括括号，Value下面大方框放进1239000174，点下面的绿色按钮Add secret保存即完成

6、要记住，4跟5步的TELEGRAM_BOT_TOKEN 跟 TELEGRAM_CHAT_ID都要是你自己获得的

7、完毕



#
#
#
#
#
##### 编译增加电报机器人信息推送
###### 有需要的你们自己加上，或者直接替换微信通知也可以，这个机器人推送消息比微信的好多了，没做好token跟id也不会出现错误而停止编译的


        - name: 电报机器人信息通知
          run: |
            curl -k --data chat_id="${{ secrets.TELEGRAM_CHAT_ID }}" --data "text=🎉 主人您要编译的[${{ env.WXFB_MESSAGE }}]固件正在努力耕耘中,请耐心等待...... 😋" "https://api.telegram.org/bot${{ secrets.TELEGRAM_BOT_TOKEN }}/sendMessage"



        - name: 电报机器人信息通知
          run: |
            curl -k --data chat_id="${{ secrets.TELEGRAM_CHAT_ID }}" --data "text=我亲爱的✨主人✨您要编译的[${{ env.WXFB_MESSAGE }}]固件顺利编译完成了！
          
              完成时间：${{ env.date1 }}
          
              发布地址：${{ env.GITHUB_RELEASE }}
          
              奶牛快传：${{ env.COWTRANSFER_URL }}
          
              WeTransfer：${{ env.WETRANSFER_URL }}
          
              祝小主人见人爱，💐花见花开，车见车载，天天好心情🎈！！！" "https://api.telegram.org/bot${{ secrets.TELEGRAM_BOT_TOKEN }}/sendMessage" 
