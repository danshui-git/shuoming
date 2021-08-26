- 1、固件发布需要一个密匙（定时更新固件也需要），首先登陆你的github，[点击这里](https://github.com/settings/tokens)，再点击｛Generate new token｝，Note下面的方框随便写个名字，然后勾选repo，然后到最下面点击绿色按钮Generate token，然后就会生成密匙，比如（c1a8c4dd060519axxxxxxxxb06eac46d82985b0b）,复制下来保存好，因为如果你有同一个账号多个仓库需要发布固件的话也是需要用上的
#
- 2、发布密匙生成好了，接下来到你自己的仓库，点Settings，再点左边的Secrets，然后点右上角的New repositonry secret，然后在Name下面的方框写上名字，名字为（REPO_TOKEN）不包括括号，Value下面大方框放进密匙，点下面的绿色按钮Add secret保存即完成
---
- 1、微信推送通知也需要一个密匙，[点击这里](https://sct.ftqq.com)，登录Server酱，然后点击[消息通道]扫码[登入网站],按说明获取密匙,一般使用企业微信的方法获取密匙,需要注册一下企业微信,里面都有说明的了,你们自己研究吧,新版的微信通知弄的挺麻烦的,不过也是一次性的问题,弄好就行了,还有一个新版微信通知一天只能发送5条消息,要想多发的话得购买会员
#
- 2、通知密匙生成好了，接下来到你自己的仓库，点Settings，再点左边的Secrets，然后点右上角的New repositonry secret，然后在Name下面的方框写上名字，名字为（SCKEY）不包括括号，Value下面大方框放进密匙，点下面的绿色按钮Add secret保存即完成
---
- 1、pushplus推送，[点击这里](http://www.pushplus.plus/push1.html)，微信扫码登录，就可以看到你的token了
#
- 2、复制好pushplus你的token后，接下来到你自己的仓库，点Settings，再点左边的Secrets，然后点右上角的New repositonry secret，然后在Name下面的方框写上名字，名字为（PUSH_PLUS_TOKEN）不包括括号，Value下面大方框放进密匙，点下面的绿色按钮Add secret保存即完成
---
#
- 两个密匙都正确使用后就可以使用微信通知跟发布功能了，友情提示：密匙注意不要随便泄露
#
- ### 发布密匙获取跟存放密匙的我做了图片教程，微信的密匙你们按上面的获取就可以了，存放是一样的。《[图片教程](https://github.com/danshui-git/shuoming/blob/master/jm.md)》
#

#

- ## 微信推送代码

```yml
    - name: 微信通知
      uses: emon100/Action-Serverchan@v2
      if: env.SERVERCHAN_SCKEY == 'true'
      with:
        SCKEY: ${{ secrets.SCKEY }}
        text: 主人${{matrix.target}}编译开始啦
        desp: 主人您要编译的[${{matrix.target}}]固件正在努力耕耘中(${{env.CangKu}}仓库的#${{env.Run_number}}号),请耐心等待......
```        
        
        
        
```yml  
    - name: 微信通知
      uses: emon100/Action-Serverchan@v2
      if: steps.organizer.outputs.status == 'success' && env.SERVERCHAN_SCKEY == 'true'
      with:
        SCKEY: ${{ secrets.SCKEY }}
        text: 恭喜主人${{matrix.target}}固件编译成功！
        desp: 我亲爱的主人您使用${{matrix.target}}文件夹编译的[ ${{ env.CODE }}-${{ env.TARGET_PROFILE }} ]固件(${{ env.CangKu }}仓库的#${{ env.Run_number }}号)顺利编译完成了！
```
#
---
#
- ## pushplus推送代码


```yml
    - name: PUSHPLUS信息通知
      if: env.SERVERCHAN_SCKEY == 'true'
      run: |
        curl -k --data token="${{ secrets.PUSH_PLUS_TOKEN }}" --data title="开始编译【${{matrix.target}}】" --data "content=🎉 主人：您正在使用【${{matrix.target}}】文件夹编译固件中(${{env.CangKu}}仓库的#${{env.Run_number}}号),请耐心等待...... 😋💐" "http://www.pushplus.plus/send"
```

```yml
    - name: PUSHPLUS信息通知
      if: steps.organizer.outputs.status == 'success' && if: env.SERVERCHAN_SCKEY == 'true'
      run: |
        curl -k --data token="${{ secrets.PUSH_PLUS_TOKEN }}" --data title="[${{ env.CODE }}-${{ env.TARGET_PROFILE }}]编译成功" --data "content=我亲爱的✨主人✨：您使用【${{matrix.target}}】文件夹编译的[${{ env.CODE }}-${{ env.TARGET_PROFILE }}]固件(${{env.CangKu}}仓库的#${{env.Run_number}}号)顺利编译完成了！💐" "http://www.pushplus.plus/send"
```


#
#
# - 把电报机器人通知改成微信通知或者pushplus推送方法
#
<img src="https://github.com/danshui-git/shuoming/blob/master/doc/thm1.png" />
<img src="https://github.com/danshui-git/shuoming/blob/master/doc/thm2.png" />
<img src="https://github.com/danshui-git/shuoming/blob/master/doc/thm3.png" />
<img src="https://github.com/danshui-git/shuoming/blob/master/doc/thm4.png" />
<img src="https://github.com/danshui-git/shuoming/blob/master/doc/thm5.png" />
