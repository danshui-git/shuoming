- 1、固件发布需要一个密匙，首先登陆你的github，[点击这里](https://github.com/settings/tokens)，再点击｛Generate new token｝，Note下面的方框随便写个名字，然后勾选repo，然后到最下面点击绿色按钮Generate token，然后就会生成密匙，比如（c1a8c4dd060519axxxxxxxxb06eac46d82985b0b）,复制下来保存好，因为如果你有同一个账号多个仓库需要发布固件的话也是需要用上的
#
- 2、发布密匙生成好了，接下来到你自己的仓库，点Settings，再点左边的Secrets，然后点右上角的New repositonry secret，然后在Name下面的方框写上名字，名字为（REPO_TOKEN）不包括括号，Value下面大方框放进密匙，点下面的绿色按钮Add secret保存即完成
#
#
- 1、微信通知也需要一个密匙，[点击这里](http://sc.ftqq.com/3.version)，登录Server酱，然后在里面点击页面上的[登入网站],登陆成功后点击[SCKEY]，就能看到密匙了，比如（SCU107710Tfc3dbee243474cbxxxxxxxx14e1c23835f57bbe272a69）,复制下来保存好，因为如果你有同一个账号多个仓库需要微信通知的话也是需要用上的，再点击页面上的[微信推送]扫二维码加公众号
#
- 2、通知密匙生成好了，接下来到你自己的仓库，点Settings，再点左边的Secrets，然后点右上角的New repositonry secret，然后在Name下面的方框写上名字，名字为（SCKEY）不包括括号，Value下面大方框放进密匙，点下面的绿色按钮Add secret保存即完成
#
- 两个密匙都正确使用后就可以使用微信通知跟发布功能了，友情提示：密匙注意不要随便泄露
#
- ### 发布密匙获取跟存放密匙的我做了图片教程，微信的密匙你们按上面的获取就可以了，存放是一样的。《[图片教程](https://github.com/danshui-git/shuoming/blob/master/jm.md)》
#
#
<img src="https://github.com/danshui-git/shuoming/blob/master/doc/tz11.png" />

- ## 微信通知代码，默认使用的是电报的，需要微信推送的话，用代码替换掉电报的开始通知跟结束通知就可以了

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
