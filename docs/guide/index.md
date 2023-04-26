---
title: 漫画站使用指南
editLink: true
outline: [2, 3]
---
# 漫画站使用指南
## 注册与登录

漫画站基于 [Komga](https://github.com/gotson/komga) 离线漫画服务器所搭建，由于记录账户阅读进度的功能，必须登录服务器上的账号才能进入服务器查看漫画。
虽然服务器设置了一个共享账号，但还是建议大家注册自己的账号使用，以免阅读进度与其他人产生冲突。


**可以通过以下方式获得服务器账号：**
### 1.1 使用[Github](https://github.com/)账号自行注册
::: tip 💡
 由于 Github 在国内无法稳定访问，推荐使用 [Watt ToolKit](https://steampp.net/) 或是 [Cloudflare Warp+](https://1.1.1.1/) 加速 Github 访问。
:::
自行注册 Github 账号后可直接访问漫画站[首页](https://comic.startrekcn.cn/)，点击登录按钮下方的[「*SIGN IN WITH GITHUB*」](https://github.com/)进行账号注册即可。

![SIGN IN WITH GITHUB](/assets/img/comic-site-guide/github-login.jpg)

自行注册之后系统会生成一个对应 Github 账号所绑定的*首要邮箱*生成一个账号，此时账号的密码是随机生成的，因此如果需要通过**邮箱+密码**的方式登录服务器就需要自行更改密码。在成功进入服务器页面请通过侧栏的[「*账号设置*」](https://comic.startrekcn.cn/account)修改您的密码。

![修改密码](/assets/img/comic-site-guide/pwd-reset.jpg)
<br>
<br>

### 1.2 联系管理员进行注册
::: warning 注意⚠️
我个人并不能做到频繁查看邮件，因此使用该方式注册可能会有较大延迟。
:::
请以**邮箱+密码**的格式发送邮件至 [i@narwh.ch](mailto:i@narwh.ch) 邮箱，收到邮件后我会使用发送邮箱作为用户名手动帮忙注册账号。如果希望自行设置密码，也可以直接告诉我让我首次生成随机密码后自行登录账号更改密码。无论如何，我强烈建议在注册登录之后更改自己的密码。
<br>
<br>

### 1.3 使用共享账号登录
::: warning 注意⚠️
由于共享账号人人皆可登录查看，因此漫画阅读记录将会受到别人的干扰。
:::
::: danger 警告🚫
如果有人恶意更改共享账号的密码，将会做封禁IPV4地址处理
:::

直接使用以下账号密码登录服务器:
::: details 点击查看账号密码
用户名：`guest@narwh.ch`
<br>密码：`guest`
:::
<br>
<br>
<br>

## 使用移动客户端访问漫画服务器

考虑到手机和平板上使用浏览器阅读漫画并不方便，因此可以通过移动客户端访问本漫画服务器。Komga 支持 [OPDS 协议](https://baike.baidu.com/item/opds/3579281)，因此理论上兼容所有支持 OPDS 协议的阅读器。

具体支持列表可以查看 [**Komga 文档**](https://komga.org/guides/) 。

### 2.1 使用 Tachiyomi (Android) 阅读

[Tachiyomi](https://tachiyomi.org/) 客户端可以点击[该链接](https://tachiyomi.org/download/)进行下载。

完成下载后到「*浏览*」页面中搜索「*komga*」插件并安装。

随后在插件的设置页面按图示填写号服务器地址、邮箱、密码即可连接至服务器。回到插件列表后点击插件即可访问漫画列表。

<img src="/assets/img/comic-site-guide/tachiyomi-komga.png" >
<br><br>

### 2.2 使用 Paperback ( iOS / iPadOS ) 阅读

下载 Paperback APP:  [**Paperback on AppStore**](https://apps.apple.com/us/app/paperback-a-komga-client/id1626613373)

::: danger 请注意
 国区未上架此APP，需要使用美区账号下载。
:::

参照以下流程完成服务器设置：
<br><br>
![](/assets/img/comic-site-guide/paperback-1.png)
<br>
![](/assets/img/comic-site-guide/paperback-2.png)