- 1, Telegram方面的设置, 首先你得有个telegram账号并安装好桌面端.

- 1.1 整一个telegram bot, 可以通过点击这里来创建:TelegramBotFather, 在与它的对话框中输入 /start /newbot 等指令,按照提示一步步,到最后获得一个新bot,以及一串形如以下的token:

987654321:FEDCBA_dfoiuweSWEczgxT7-l4r9Y

- 这串东西不应泄露给他人,否则被人滥用的话会导致该bot被禁止.

- 1.2 找到你的telegram chat_id:

- 1.2.1 用客户端往bot发言, 内容是什么不重要

- 1.2.2 将前面获得的token替换掉这个url中的XYZ部分, https://api.telegram.org/botXYZ/getUpdates

- 它实际上应该看上去应该是这样的: https://api.telegram.org/bot987654321:FEDCBA_dfoiuweSWEczgxT7-l4r9Y/getUpdates 然后访问这个url, 在返回的json中你很容易可以找到id这个键(与username,first_name)相近. 那串数字(139000174)就是要找的id
