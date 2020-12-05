# 网易云游戏自动签到

本脚本通过使用Github Action来进行[网易云游戏](https://cg.163.com/)签到操作，让你能够天天白嫖网易云游戏时长和云电脑！

喜欢就给我点个STAR吧！

签到时间是早上10点，如果有需要就自己修改.github/workflows/AutoSignin.yml中第12行的时间，时间遵循UTC时间，+8才是我们的时间

**请不要使用非master分支脚本，他们通常正在开发新功能，会有BUG出现**

## 赞助
点击下面的Badge其中一个就可以跳转到相应页面，感谢老板的支持！

<a href="https://afdian.net/@GamerNoTitle"><img src="https://img.shields.io/badge/%E7%88%B1%E5%8F%91%E7%94%B5-GamerNoTitle-%238e8cd8?style=for-the-badge" alt="前往爱发电赞助" width=auto height=auto border="0" /></a> <a href="https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo@master/img/Donate/WeChatPay.png"><img src="https://img.shields.io/badge/%E5%BE%AE%E4%BF%A1%E6%94%AF%E4%BB%98-GamerNoTitle-%2304BE02?style=for-the-badge" alt="使用微信赞助" width=auto height=auto border="0" /></a> <a href="https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo@master/img/Donate/AliPay.jpg"><img src="https://img.shields.io/badge/%E6%94%AF%E4%BB%98%E5%AE%9D%E6%94%AF%E4%BB%98-GamerNoTitle-%231678FF?style=for-the-badge" alt="使用支付宝赞助" width=auto height=auto border="0" /></a>

## 目录

- [使用方法](#使用方法)
- [变量获取](#变量内容获取)
- [Q&A](#qa)

## 使用方法

### 变量添加

1、Fork本仓库，按右上角的分支按钮（如图）

![](https://upimage.alexhchu.com/2020/11/22/e9b4bcf8e6a1d.png)

2、进入设置，设置变量`cookie`和`teleid` `teletoken` `SCKEY`（这三个可选）

[如何获取变量内容？请点这里](#变量内容获取)

![](https://upimage.alexhchu.com/2020/11/22/988724b77ca62.png)

![](https://upimage.alexhchu.com/2020/11/22/a7958e9f5582f.png)

![](https://upimage.alexhchu.com/2020/11/22/7213627d41fc1.png)

### 测试脚本

**请在当天没有签到的情况下测试！！！**

我们先进入Action界面，启用Action

![](https://upimage.alexhchu.com/2020/11/22/70dd262ae54f0.png)

然后我们进入对应的脚本，启用脚本，并进行测试

![](https://upimage.alexhchu.com/2020/11/22/457403bb7d3bb.png)

**只要测试通过就是没问题，如果你配置了TELEGRAM还会收到你的BOT给你发送的消息**

测试通过后，你就可以放着它不用管了，它会自己运行的~

## 变量内容获取

### cookie获取

首先我们进入[官网](https://cg.163.com)，进行登录，然后用<kbd>F12</kbd>打开开发者工具后使用<kbd>Ctrl</kbd>+<kbd>F5</kbd>进行刷新，会刷出很多结果

我们在里面找到`@me`这一项，然后在右边找到`Authorization`将冒号后面的内容复制下来就是我们所需要的Cookie

![](https://upimage.alexhchu.com/2020/11/22/bfb0e2dbd347a.png)

### teleid获取

用你的Telegram找到@userinfobot，点个Start，会直接给你回复你的ID，复制下id后面的数字就是teleid了

![](https://upimage.alexhchu.com/2020/11/22/e4c50250626a6.png)

### teletoken获取

找@BotFather进行机器人的创建，按照提示创建即可，会给你一个API TOKEN，如果一不小心点过去了可以用命令`/mybots`管理自己的bot，找到自己想要使用的bot并获取API就可以了

![](https://upimage.alexhchu.com/2020/11/22/0428751a3925e.png)

### SCKEY获取

访问[ServerChan官网](http://sc.ftqq.com/?c=code)，用你的Github账户登录，在`发送信息`可以看到你的SCKEY

![](https://upimage.alexhchu.com/2020/12/05/dff25704763d8.png)

## Q&A

## 错误代码

### telepot.exception.TelegramError

#### Chat not found

请先用你要接受信息的账户发个`/start`给你的bot，或者检查用户ID是否正确！

#### Not found

请检查自己的Telebot Token是否正确！

### urllib3.exceptions

#### MaxRetryError

`HTTPSConnectionPool(host='api.telegram.org', port=443): Max retries exceeded with url: /bot1166372402:AAFihK9Bq8_dPuBMDni8y90cZJvprqMFmAs/sendMessage`

出现这个错误，那就是Telegram的问题，Github连接不上Telegram服务器（大半是TG服务器炸了）

#### ReadTimeoutError

`HTTPSConnectionPool(host='api.telegram.org', port=443): Read timed out. (read timeout=30)`

出现这个错误，那就是Telegram的问题，Github连接不上Telegram服务器（大半是TG服务器炸了）~~（复制粘贴大法）~~