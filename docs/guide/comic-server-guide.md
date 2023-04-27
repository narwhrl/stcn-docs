---
title: 漫画服务器使用指南
editLink: true
outline: [2, 3]
next: false
---

<script setup>
import { VPTeamMembers } from 'vitepress/theme'

const members = [
    {
        avatar: 'https://www.github.com/narwhrl.png',
        name: 'Narwhrl',
        title: '撰写',
        links: [
        { icon: 'github', link: 'https://github.com/narwhrl' },        
        { 
            icon:         { 
          svg: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--! Font Awesome Pro 6.4.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. --><path d="M488.6 104.1C505.3 122.2 513 143.8 511.9 169.8V372.2C511.5 398.6 502.7 420.3 485.4 437.3C468.2 454.3 446.3 463.2 419.9 464H92.02C65.57 463.2 43.81 454.2 26.74 436.8C9.682 419.4 .7667 396.5 0 368.2V169.8C.7667 143.8 9.682 122.2 26.74 104.1C43.81 87.75 65.57 78.77 92.02 78H121.4L96.05 52.19C90.3 46.46 87.42 39.19 87.42 30.4C87.42 21.6 90.3 14.34 96.05 8.603C101.8 2.868 109.1 0 117.9 0C126.7 0 134 2.868 139.8 8.603L213.1 78H301.1L375.6 8.603C381.7 2.868 389.2 0 398 0C406.8 0 414.1 2.868 419.9 8.603C425.6 14.34 428.5 21.6 428.5 30.4C428.5 39.19 425.6 46.46 419.9 52.19L394.6 78L423.9 78C450.3 78.77 471.9 87.75 488.6 104.1H488.6zM449.8 173.8C449.4 164.2 446.1 156.4 439.1 150.3C433.9 144.2 425.1 140.9 416.4 140.5H96.05C86.46 140.9 78.6 144.2 72.47 150.3C66.33 156.4 63.07 164.2 62.69 173.8V368.2C62.69 377.4 65.95 385.2 72.47 391.7C78.99 398.2 86.85 401.5 96.05 401.5H416.4C425.6 401.5 433.4 398.2 439.7 391.7C446 385.2 449.4 377.4 449.8 368.2L449.8 173.8zM185.5 216.5C191.8 222.8 195.2 230.6 195.6 239.7V273C195.2 282.2 191.9 289.9 185.8 296.2C179.6 302.5 171.8 305.7 162.2 305.7C152.6 305.7 144.7 302.5 138.6 296.2C132.5 289.9 129.2 282.2 128.8 273V239.7C129.2 230.6 132.6 222.8 138.9 216.5C145.2 210.2 152.1 206.9 162.2 206.5C171.4 206.9 179.2 210.2 185.5 216.5H185.5zM377 216.5C383.3 222.8 386.7 230.6 387.1 239.7V273C386.7 282.2 383.4 289.9 377.3 296.2C371.2 302.5 363.3 305.7 353.7 305.7C344.1 305.7 336.3 302.5 330.1 296.2C323.1 289.9 320.7 282.2 320.4 273V239.7C320.7 230.6 324.1 222.8 330.4 216.5C336.7 210.2 344.5 206.9 353.7 206.5C362.9 206.9 370.7 210.2 377 216.5H377z"/></svg>'
        }, 
            
            link: 'https://space.bilibili.com/7179789' }
        ]
    },
]
</script>

# 漫画服务器使用指南 <Badge type="warning" text="BETA" />

<VPTeamMembers size="small" :members="members" />

## 注册与登录

漫画站基于 [Komga](https://github.com/gotson/komga) 离线漫画服务器所搭建。基于记录账户阅读进度的功能，必须登录服务器上的账号才能进入服务器查看漫画。
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

## 使用移动客户端访问

考虑到手机和平板上使用浏览器阅读漫画并不方便，因此可以通过移动客户端访问本漫画服务器。Komga 支持 [OPDS 协议](https://baike.baidu.com/item/opds/3579281)，因此理论上兼容所有支持 OPDS 协议的阅读器。

具体支持列表可以查看 [**Komga 文档**](https://komga.org/guides/) 。

### 2.1 使用 Tachiyomi <Badge type="tip" text="Android" />  阅读

[Tachiyomi](https://tachiyomi.org/) 客户端可以点击[该链接](https://tachiyomi.org/download/)进行下载。

完成下载后到「*浏览*」页面中搜索「*komga*」插件并安装。

随后在插件的设置页面按图示填写号服务器地址、邮箱、密码即可连接至服务器。回到插件列表后点击插件即可访问漫画列表。

<img src="/assets/img/comic-site-guide/tachiyomi-komga.png" >
<br><br>

### 2.2 使用 Paperback <Badge type="tip" text="iOS / iPadOS" />  阅读

下载 Paperback APP:  [**Paperback on AppStore**](https://apps.apple.com/us/app/paperback-a-komga-client/id1626613373)

::: danger 请注意
 国区未上架此APP，需要使用美区账号下载。
:::

参照以下流程完成服务器设置：
<br><br>
![](/assets/img/comic-site-guide/paperback-1.png)
<br>
![](/assets/img/comic-site-guide/paperback-2.png)