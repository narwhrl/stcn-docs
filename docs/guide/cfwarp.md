---
title: 使用 Cloudflare WARP 加速访问
editLink: true
outline: [2, 3]
next: false
---

<script setup>
import { VPTeamMembers } from 'vitepress/theme'

const members = [
    {
        avatar: '/narwhrl.jpg',
        name: 'Narwhrl',
        title: '撰写',
        links: [
        { icon: 'github', link: 'https://github.com/narwhrl' },        
        { 
            icon:         { 
          svg: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--! Font Awesome Pro 6.4.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. --><path d="M488.6 104.1C505.3 122.2 513 143.8 511.9 169.8V372.2C511.5 398.6 502.7 420.3 485.4 437.3C468.2 454.3 446.3 463.2 419.9 464H92.02C65.57 463.2 43.81 454.2 26.74 436.8C9.682 419.4 .7667 396.5 0 368.2V169.8C.7667 143.8 9.682 122.2 26.74 104.1C43.81 87.75 65.57 78.77 92.02 78H121.4L96.05 52.19C90.3 46.46 87.42 39.19 87.42 30.4C87.42 21.6 90.3 14.34 96.05 8.603C101.8 2.868 109.1 0 117.9 0C126.7 0 134 2.868 139.8 8.603L213.1 78H301.1L375.6 8.603C381.7 2.868 389.2 0 398 0C406.8 0 414.1 2.868 419.9 8.603C425.6 14.34 428.5 21.6 428.5 30.4C428.5 39.19 425.6 46.46 419.9 52.19L394.6 78L423.9 78C450.3 78.77 471.9 87.75 488.6 104.1H488.6zM449.8 173.8C449.4 164.2 446.1 156.4 439.1 150.3C433.9 144.2 425.1 140.9 416.4 140.5H96.05C86.46 140.9 78.6 144.2 72.47 150.3C66.33 156.4 63.07 164.2 62.69 173.8V368.2C62.69 377.4 65.95 385.2 72.47 391.7C78.99 398.2 86.85 401.5 96.05 401.5H416.4C425.6 401.5 433.4 398.2 439.7 391.7C446 385.2 449.4 377.4 449.8 368.2L449.8 173.8zM185.5 216.5C191.8 222.8 195.2 230.6 195.6 239.7V273C195.2 282.2 191.9 289.9 185.8 296.2C179.6 302.5 171.8 305.7 162.2 305.7C152.6 305.7 144.7 302.5 138.6 296.2C132.5 289.9 129.2 282.2 128.8 273V239.7C129.2 230.6 132.6 222.8 138.9 216.5C145.2 210.2 152.1 206.9 162.2 206.5C171.4 206.9 179.2 210.2 185.5 216.5H185.5zM377 216.5C383.3 222.8 386.7 230.6 387.1 239.7V273C386.7 282.2 383.4 289.9 377.3 296.2C371.2 302.5 363.3 305.7 353.7 305.7C344.1 305.7 336.3 302.5 330.1 296.2C323.1 289.9 320.7 282.2 320.4 273V239.7C320.7 230.6 324.1 222.8 330.4 216.5C336.7 210.2 344.5 206.9 353.7 206.5C362.9 206.9 370.7 210.2 377 216.5H377z"/></svg>'
        }, 
            
            link: 'https://space.bilibili.com/7179789' },
        { 
            icon:         { 
          svg: '<i class="fa-solid fa-arrow-up-right-from-square"></i>'
        }, 
            
            link: 'https://narwh.ch' }
        ]
    },
]

</script>

# 使用 <a href="https://1.1.1.1" target="_blank">Cloudflare WARP <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:24px;"></i></a> 加速访问 <Badge type="warning" text="编写中" />

<VPTeamMembers size="small" :members="members" />

## 1.0 为什么需要用到 <a href="https://1.1.1.1" target="_blank" class="cus-link">WARP <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:18px;"></i></a> 
之前在 <a href="https://video.startrekcn.cn/index.php/patch.html" target="_blank" class="cus-link">更新日志 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a> 中已经提到，由于负担不起站点巨量的流量费用（7天就达到了吓人的 2.2T），全站的片源都将转移到出站流量不收费的 Cloudflare R2 对象储存服务上。

由于 Cloudflare 仅有非常昂贵的商业版才会提供国内节点，因此连接储存服务器的节点均在海外，每当晚上的国际带宽进出口晚高峰时期，国内直连使用视频站就可能会出现明显的卡顿/掉包现象。

因此，使用代理软件加速视频资源的访问就显得很有必要了。下面介绍的 <a href="https://1.1.1.1" target="_blank">Cloudflare Warp+ <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a> 不仅能够免费使用，而且能完美解决这个问题。

::: tip ✨
虽然说确实能免费使用 [Cloudflare WARP <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i>](https://1.1.1.1)，但正常情况下要使用其实是需要付费的，只是利用了 Cloudflare 提供的「**邀请新用户注册获得 WARP+ 流量**」的优惠得到的免费流量（实际使用质量和付费版一致），至于有财力付费使用的，我还是推荐付费支持 Cloudflare ~
:::

## 2.0 在 iOS / iPadOS 上安装使用 <Badge type="tip" text="iOS / iPadOS" />

### 2.1 在 AppStore 下载安装 WARP
前往 <a href="https://1.1.1.1" target="_blank" class="cus-link">链接 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>，点击按钮安装 <a href="https://itunes.apple.com/us/app/1-1-1-1-faster-internet/id1423538627" target="_blank" class="cus-link">AppStore 上的 1.1.1.1: Faster Internet  <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>

::: danger 请注意
 AppStore 国区未上架此APP，需要使用美区账号下载。
:::

### 2.2 配置 WARP

- 打开 WARP，按流程同意用户协议并安装 <em>VPN</em> 配置文件。
- 点击右上方进入设置，将运行模式暂时切换至「<strong><em>1.1.1.1</em></strong>」，并回到主界面进行一次连接。

<img src="/assets/img/cfwarp/2.png"><br>

### 2.3 为密钥增加流量

::: tip
如果你已经拥有科学上网工具，可以直接跳过此步骤前往 <a href="/guide/cfwarp.html#_5-1-获取使用流量多达-22pb-的许可密钥">条目 5.1 <i class="fa-solid fa-arrow-right-from-bracket" style="font-size:12px;"></i></a>。
:::

此时我们会发现，自己的 WARP+ 并没有流量。这时候就要用到邀请用户的方式获取流量了，当然并不是说真的让你去邀请其他小伙伴注册来获得流量，由于 WARP+ 的注册机制非常宽松，几乎是任何一个设备都可以随意进行注册。因此这里我们用到一个 Python 脚本进行自动刷注册获得邀请流量奖励，该脚本可以在云服务平台上运行。
- 再次点击右上方进入设置，再按顺序进入 <strong>高级-诊断</strong>。 
- 找到「<strong><em>ID</em></strong>」这一栏，长按并拷贝一长串ID码。

<img src="/assets/img/cfwarp/2.png">

<br>

- 使用浏览器进入 <a href="https://replit.com/@narwhrl/warp-plus" target="_blank" class="cus-link">链接 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>。
- 点击屏幕中央的运行 icon，等待加载完成后在控制台中「Enter the User ID:」后粘贴输入刚才拷贝的ID码，按下回车键运行。
- 等待程序自动运行即可，获取到足够量即可停止运行。

<img src="/assets/img/cfwarp/3.png">
<br>
<img src="/assets/img/cfwarp/4.png">
<br>

### 2.4 开始使用

- 在上一步中获取了足够的流量后，回到 APP 界面中，会发现流量已经增加。
- 将运行模式切换回「<strong><em>WARP+</em></strong>」，回到主界面重新连接即可使用。

<img src="/assets/img/cfwarp/5.png">

::: tip 
也许你会觉得这样子刷出来的流量并不够用。在后面 <a href="/guide/cfwarp.html#_5-1-获取使用流量多达-22pb-的许可密钥" class="cus-link">条目 5.1 <i class="fa-solid fa-arrow-right-from-bracket" style="font-size:12px;"></i></a> 我将会讲到如何获取并使用密钥。
:::

<br>

## 3.0 在 Android 上安装使用 <Badge type="tip" text="Android" />

### 3.1 在 PlayStore 下载安装 WARP

前往 <a href="https://1.1.1.1" target="_blank" class="cus-link">链接 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>，跳转到 PlayStore 安装 <a href="https://play.google.com/store/apps/details?id=com.cloudflare.onedotonedotonedotone" target="_blank" class="cus-link">1.1.1.1 + WARP: Safer Internet  <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>

::: danger 请注意
 Google PlayStore 国内无法直连，如果没有科学上网工具的可以使用 <a href="https://oss.narwhrl.site/WARP_6.26.apk" target="_blank">链接 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a> 下载该APP。
:::

### 3.2 配置 WARP

- 打开 WARP，同意用户协议，点击右上方进入设置，将运行模式暂时切换至「<strong><em>1.1.1.1</em></strong>」
- 回到主界面进行预连接，按要求安装 <em>VPN</em> 配置文件。

<img src="/assets/img/cfwarp/6.png"><br>

### 3.3 为密钥增加流量

::: tip
如果你已经拥有科学上网工具，可以直接跳过此步骤前往 <a href="/guide/cfwarp.html#_5-1-获取使用流量多达-22pb-的许可密钥">条目 5.1 <i class="fa-solid fa-arrow-right-from-bracket" style="font-size:12px;"></i></a>。
:::

此时我们会发现，自己的 WARP+ 并没有流量。这时候就要用到邀请用户的方式获取流量了，当然并不是说真的让你去邀请其他小伙伴注册来获得流量，由于 WARP+ 的注册机制非常宽松，几乎是任何一个设备都可以随意进行注册。因此这里我们用到一个 Python 脚本进行自动刷注册获得邀请流量奖励，该脚本可以在云服务平台上运行。
- 再次点击右上方进入设置，再按顺序进入 <strong>高级-诊断</strong>。 
- 找到「<strong><em>ID</em></strong>」这一栏，长按并复制这一长串ID码。

<img src="/assets/img/cfwarp/7.png">

<br>

- 使用浏览器进入 <a href="https://replit.com/@narwhrl/warp-plus" target="_blank" class="cus-link">链接 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>。
- 点击运行，等待加载完成后在控制台中「Enter the User ID:」后粘贴输入刚才复制的 ID 码，按下回车键运行。
- 等待程序自动运行即可，获取到足够量即可停止运行。

<img src="/assets/img/cfwarp/8.png">
<br>

### 3.4 开始使用

- 在上一步中获取了足够的流量后，回到 APP 界面中，会发现流量已经增加。
- 将运行模式切换回「<strong><em>WARP+</em></strong>」，回到主界面重新连接即可使用。

<img src="/assets/img/cfwarp/9.png">

::: tip 
也许你会觉得这样子刷出来的流量并不够用。在后面 <a href="/guide/cfwarp.html#_5-1-获取使用流量多达-22pb-的许可密钥">条目 5.1 <i class="fa-solid fa-arrow-right-from-bracket" style="font-size:12px;"></i></a> 我将会讲到如何获取并使用密钥。
:::

<br>

### 3.5 重置安全密钥
如果发现自己的手机点击连接后却一直卡在连接中，可采取以下方法：
- 再次点击右上方进入设置，再按顺序进入 <strong>高级-连接选项</strong>。
- 点击「<strong><em>重置安全密钥</em></strong>」，回到主界面重新连接即可使用。

<img src="/assets/img/cfwarp/10.png">

<br>

## 4.0 在 Windows(PC) 上安装使用 <Badge type="tip" text="Windows" />

### 4.1 下载安装 Warp+

前往 <a href="https://1.1.1.1" target="_blank" class="cus-link">链接 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>，直接点击按钮 <a href="https://play.google.com/store/apps/details?id=com.cloudflare.onedotonedotonedotone" target="_blank" class="cus-link"><i class="fa-brands fa-windows"></i> Windows  <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a> 下载`msi`文件并安装。

### 4.2 更换密钥

由于 Windows 客户端并没有邀请机制，需要用到移动客户端，所以这里并不赘述如何获取用户 ID 码并刷取流量。

可以在复制 Windows 客户端的许可密钥后导入到移动客户端进行流量刷取，移动客户端如何更换许可密钥请看 <a href="/guide/cfwarp.html#_5-1-获取使用流量多达-22pb-的许可密钥" class="cus-link">条目 5.1 <i class="fa-solid fa-arrow-right-from-bracket" style="font-size:12px;" ></i></a>，流量刷取具体可以看前面 <a href="/guide/cfwarp.html#_2-3-为密钥增加流量" class="cus-link">条目 2.3 <i class="fa-solid fa-arrow-right-from-bracket" style="font-size:12px;"></i></a> 是如何刷取流量的，你也可以选择直接更换有大量流量的许可密钥。

下面详述如何更换密钥：
- 在右下角 Windows 任务托盘中找到 Cloudflare WARP 的图标，点击图标调出 WARP 客户端界面.
- 点击右下角的 <a class="cus-link"> <i class="fa-solid fa-gear"></i>齿轮</a> 图标，进入「偏好设置」。
- 进入子菜单「账户」，点击「使用其他密钥」，粘贴其他拥有流量的许可密钥，点击确定。

<img src="/assets/img/cfwarp/11.png">
<br>
<img src="/assets/img/cfwarp/12.png">
<br>
<img src="/assets/img/cfwarp/13.png">

### 4.4 开始使用
- 回到最开始的客户端界面点击连接按钮即可连接。

::: danger 请注意
 Windows 客户端不同于其他客户端，默认的链接方式是创建一个虚拟网卡，类似于 [Clash For Windows 的 TAP 模式 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i>](https://docs.cfw.lbyczf.com/contents/tap)，系统的所有流量（包括 UWP）会经过 WARP 代理，而忽略 Windows 本身的 UWP 应用网络回环。
:::

## 5.0 进一步使用

### 5.1 获取使用流量多达 22PB 的许可密钥

或许你会觉得用 Replit 上托管的 Python 脚本每 20s 刷 1GB 的流量的方式过于低效，有没有一次提供大量流量的方法呢？

因为 WARP+ 的流量是和用户所使用的许可密钥相绑定的，所以只要更换了拥有大量流量的许可密钥就可以用上大量流量。

在前面的教程中，我们已经成功刷取了一定流量，现在需要用到这些流量来获得许可密钥了。

- 下载并安装 <a href="https://telegram.org/" class="cus-link" target="_blank"><i class="fa-brands fa-telegram"></i> Telegram <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>，登录自己的 TG 账号，若没有账号则需要注册。

::: tip Notes
 Telegram 在国内已经被防火墙屏蔽，没有其他科学上网工具的话需要开启 WARP+ 才能正常使用。刚刚获得的流量现在就可以派上用场了。
:::

- 在浏览器中打开 <a href="https://t.me/generatewarpplusbot" class="cus-link" target="_blank"><i class="fa-brands fa-telegram"></i> 链接 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>，在 Telegram 中天街该机器人。
- 按机器人要求关注 TG 频道  <a href="https://t.me/warpplus" class="cus-link" target="_blank"><i class="fa-brands fa-telegram"></i> Warp Plus <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>。
- 向机器人发送消息 「<strong><em>/generate</em></strong>」。
- 完成机器人要求的算术验证，获取许可密钥。

<img src="/assets/img/cfwarp/15.png">

- 打开 WARP APP，点击右上方进入设置界面。
- 依次进入 <strong>账户-按键</strong>，点击「<strong><em>更改密钥</em></strong>」。
- 输入获得的许可密钥，点击右上角储存。
- 如果使用的是 Android 客户端，则需要重置安全密钥，见 <a href="/guide/cfwarp.html#_3-5-重置安全密钥" class="cus-link">条目 3.5 -- 重置安全密钥 <i class="fa-solid fa-arrow-right-from-bracket" style="font-size:12px;"></i></a>。
  
::: tip Notes
 Windows 客户端更换密钥的方法前面已经讲述过，这里不再赘述，见 <a href="/guide/cfwarp.html#_4-2-更换密钥">条目 4.2 -- 更换密钥 <i class="fa-solid fa-arrow-right-from-bracket" style="font-size:12px;"></i></a>。
:::

### 5.2 其他获取流量的方法

参考：
- <a href="https://github.com/Zeus-Kernel-Development/warp-plus-cloudflare" class="cus-link" target="_blank"><i class="fa-brands fa-github"></i> Zeus-Kernel-Development/warp-plus-cloudflare <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>
- <a href="https://github.com/totoroterror/warp-cloner" class="cus-link" target="_blank"><i class="fa-brands fa-github"></i> totoroterror/warp-cloner <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>
- <a href="https://github.com/demoniclust/warp-plus-cloudflare-1" class="cus-link" target="_blank"><i class="fa-brands fa-github"></i> demoniclust/warp-plus-cloudflare-1 <i class="fa-solid fa-arrow-up-right-from-square" style="font-size:12px;"></i></a>