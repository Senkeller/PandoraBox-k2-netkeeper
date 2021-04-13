
# 免责声明
> 免责声明：
>
> 1. 在根据本教程进行实际操作时，如因您操作失误导致出现的一切意外，包括但不限于路由器变砖、故障、数据丢失等情况，概不负责；
> 2. 该技术仅供学习交流，请勿将此技术应用于任何商业行为，所产生的法律责任由您自行承担；
> 3. 部分学校明令禁止使用路由器上网，本教程仅用于交流使用，安装路由器的行为完全是您个人意志所决定的，如您已成功安装，请在 24 小时内重置路由器至原出产状态；
> 4. 请按照学校推荐的方式连接到互联网，如因个人问题受到相关校规追责，由您自行承担。





# 注意，斐讯K2P用户必看

> 部分同学反映斐讯K2P根据本教程刷完以后工作不正常，现已由[@Xue-JW](<https://github.com/Xue-JW>)同学解决；
>
> 使用斐讯K2P的同学，请直接下载[K2P专用文件](https://github.com/shengqiangzhang/Drcom-GDUT-HC5661A-OpenWrt/files/2974860/k2p.zip)完成刷机教程；
>
> 如果您看不懂[K2P专用文件](https://github.com/shengqiangzhang/Drcom-GDUT-HC5661A-OpenWrt/files/2974860/k2p.zip)中的教程，请先看完本教程后再尝试，本教程对新手较为友好，请耐心看完。




# 前言

本教程教您如何在PandoraBox下使用路由器上校园网(城院、斐迅k2为例)

本教程适合在PandoraBox使用进行拨号上网的用户，同时，要求您的路由器支持刷入第三方系统，如openwrt，PandoraBox。由于是针对新手的教程，所以叙述部分可能会比较冗杂，您可自行跳到不同的章节。

本教程以斐迅k2为例，不同型号路由器所对应的教程略有不同，请您注意。


本教程非原创，在以下开发者的基础上进行改进：

[GJXS](https://www.gjxslisa.club/2018/10/27/drcom/?)、[NickHopps](https://blog.csdn.net/liucheng2012560/article/details/78755309)、[陈浩南](https://chn.moe/sub/study/index.php/archives/20/)、[ChengTheRipper](https://github.com/ChengTheRipper）



# 刷入前准备
	1 路由器本身带有breed（具体刷入过程，不在多加赘述。）
	2下载所需要的文件 以`斐迅k2`为例,点击这里[PandoraBox]（https://raw.githubusercontent.com/Senkeller/PandoraBox-k2-netkeeper/main/K2-netkeeper%E7%A0%B4%E8%A7%A3%E6%96%87%E4%BB%B6.zip）
	3 路由器lan口用网线连接电脑



## 其他固件下载()

	其他固件可用putty连接后 键入以下命令查看`路由器CPU的型号`，以确定我们要刷什么版本的固件

`cat /proc/cpuinfo`


以下是几种常见的路由器型号对应的OpenWrt固件下载链接：

| 路由器版本            | 下载链接                                                     |
| --------------------- | ------------------------------------------------------------ |
| 极路由1(HC6361)       | [openwrt-18.06.2-ar71xx-generic-hiwifi-hc6361-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ar71xx/generic/openwrt-18.06.2-ar71xx-generic-hiwifi-hc6361-squashfs-sysupgrade.bin) |
| 极路由1S(HC5661**A**) | [openwrt-18.06.2-ramips-mt76x8-hc5661a-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ramips/mt76x8/openwrt-18.06.2-ramips-mt76x8-hc5661a-squashfs-sysupgrade.bin) |
| 极路由1S(HC5661)      | [openwrt-18.06.2-ramips-mt7620-hc5661-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ramips/mt7620/openwrt-18.06.2-ramips-mt7620-hc5661-squashfs-sysupgrade.bin) |
| 极路由2(HC5761)       | [openwrt-18.06.2-ramips-mt7620-hc5761-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ramips/mt7620/openwrt-18.06.2-ramips-mt7620-hc5761-squashfs-sysupgrade.bin) |
| 极路由3(HC5861)       | [openwrt-18.06.2-ramips-mt7620-hc5861-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ramips/mt7620/openwrt-18.06.2-ramips-mt7620-hc5861-squashfs-sysupgrade.bin) |
| 极路由4(HC5962)       | [openwrt-18.06.2-ramips-mt7621-hc5962-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ramips/mt7621/openwrt-18.06.2-ramips-mt7621-hc5962-squashfs-sysupgrade.bin) |
| 极路由enjoy(HC5861B)  | 暂无                                                         |
| 斐讯K1                | [openwrt-18.06.2-ramips-mt7620-psg1208-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ramips/mt7620/openwrt-18.06.2-ramips-mt7620-psg1208-squashfs-sysupgrade.bin) |
| 斐讯K2(五个网口)      | [openwrt-18.06.2-ramips-mt7620-psg1218a-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ramips/mt7620/openwrt-18.06.2-ramips-mt7620-psg1218a-squashfs-sysupgrade.bin) |
| 斐讯K2C(四个网口)     | [openwrt-18.06.2-ramips-mt7620-psg1218b-squashfs-sysupgrade.bin](http://downloads.openwrt.org/releases/18.06.2/targets/ramips/mt7620/openwrt-18.06.2-ramips-mt7620-psg1218b-squashfs-sysupgrade.bin) |

> `说明:`由于路由器版本太多，若您在上面没有找到对应的路由器型号，请自行查找





## 开始刷入OpenWrt固件

本小节的步骤请严格按照先后顺序操作。

1. 用网线让路由器的LAN口与电脑的网口相连接； 
2. PC设置为自动获取IP(一般默认自动获取IP)；
3. 路由器断电(就是拔插头)； 
4. 首先按住reset不放！，确保没有松开reset键后，然后，插入路由器电源； 
5. 保持按住reset 3-4秒左右，路由器灯开始一闪一闪的时候，松开reset；
6. PC网卡获取到192.168.1.x的地址 （如未获取到手工设置），一般是192.168.1.1 ；
7. 浏览器访问 192.168.1.1，接着你就会看到一个uboot控制台的界面。



为了保险起见，首先进行固件备份，以备不时之需。严重强烈建议极路由用户刷Breed后，第一次进入后台就备份一次，这样以后想要重新刷回官方系统时原有功能不会受到影响，仍然能够访问云平台。

![](./img/6.png)



现在正是开始刷入PandoraBox固件，依次点击固件更新→勾选固件→点击选择文件，选择我分享的文件中的PandoraBox-19.01-mt7620-k2.bin



安装完成后会自动重启，这时可以不断刷新浏览器，直到管理界面显示出来，如果没有显示，建议稍后使用192.168.1.1访问管理页面。

账号:root

密码:默认为admin

![](./img/7.png)





# 步骤四:安装pppoe插件

## 安装现成插件

这里以`城院校园网为例`，其他固件请自行获得相兼容的pppoe插件，

<br />
<br />



# 步骤五:配置上网

1.点击 Network -> Wireless（无线）。如果提示 Disabled（已禁用）就点击 Enable（启用）。可能只有一个 2.4G 的，也可能有一个 2.4G 的、一个 5G 的。点 2.4G 的 Edit(编辑) 按钮。

- ESSID：填 WiFi 的名字。



2.点击 Wireless Security（无线安全）

- Encryption（加密）：改选为`WPA2-PSK`
- Key（密码）：填 WiFi 密码

- 点击 Save & Apply（保存并应用）



3.用网线把路由器的wan口，连接上光猫的lan口，电脑中打开学校的沃派客户端，登陆出现“正在身份验证” “核对账号密码” 最后出现错误代码691 此时尝试打卡网页，若正常上网就可以

这样，WiFi 基本就可以正常联网啦。



要是之前，教程就到此结束了，但最近城院宽带更新了，新加了ua检测，普通的开热点共享wifi的形式就不行了，
此时我们可以用 Privoxy 代理 插件从而实现ua伪装，下面就开始教程




# 步骤六:配置防检测

## 同步时间

NTP 就是用来同步两台电脑上的时钟的协议。接下来先启用 pand 自带的 NTP 服务器，然后将局域网内所有时钟校正的请求都发给路由器上的 NTP 服务器（也就是说，无视局域网内的电脑原本想要和哪台服务器同步时间，而强制将路由器上的时钟作为标准），这样局域网内所有的电脑上的时间都会变得一致。

点击 System（系统）->System（系统），只需要在管理页面中修改几个设置就可以了。

- 配置 NTP 服务。点击 System -> System。

  - 勾选 Enable NTP client（启用 NTP 客户端）和 Provide NTP server（作为 NTP 服务器提供服务）。

  - NTP server candidates（候选 NTP 服务器）四个框框分别填写

    `cn.pool.ntp.org`、`pool.ntp.org`、`time.apple.com`。

点击 Save & Apply 按钮。

- 配置防火墙转发。点击 Network -> Firewall（防火墙），然后点击 Custom Rules 标签，在大框框里另起一行，添加下面的代码：

  ```bash
  iptables -t nat -N ntp_force_local
  iptables -t nat -I PREROUTING -p udp --dport 123 -j ntp_force_local
  iptables -t nat -A ntp_force_local -d 0.0.0.0/8 -j RETURN
  iptables -t nat -A ntp_force_local -d 127.0.0.0/8 -j RETURN
  iptables -t nat -A ntp_force_local -d 192.168.0.0/16 -j RETURN
  iptables -t nat -A ntp_force_local -s 192.168.0.0/16 -j DNAT --to-destination 192.168.1.1
  ```

  第六行最后的`192.168.1.1`需要修改为你的路由器的管理页面地址。例如，你的管理页面地址是`192.168.10.1`，那么这一行代码需要修改为：

  ```bash
  iptables -t nat -A ntp_force_local -s 192.168.0.0/16 -j DNAT --to-destination 192.168.10.1
  ```

  然后点击 Restart Firewall（重启防火墙）。

  ![](./img/19.png)

  

## 修改 HTTP 头的 UA标志

**UA 中包含了操作系统版本等信息，而 HTTP 协议没有对这些信息加密，因此别人可以从这里看到这个数据包发自 Windows 电脑还是安卓手机等(所以根据这个原理，能够实现检测到超过1台设备立即强制断网的效果)。接下来把所有 HTTP 头中的 UA 都改得一样(伪装成只有一台设备，所以就不会被强制断网了)。**



接下来，需要安装好 Privoxy 并正确配置，然后将所有 HTTP 流量转发给 Privoxy 代理，并在 Privoxy 中替换 UA。

- 安装 Privoxy。进入路由器管理页面，点击 System(系统) -> Software（软件包）。
  - 点击 Update lists（刷新列表）按钮，等待几分钟。如果提示好几条“Signature check passed”那么这一步执行成功；如果卡死了，几分钟后再进入这个页面，看到了很长很长的软件列表，那也是成功了。
  - 在 Filter（过滤器）中填写`luci-app-privoxy`，点击 Find package（查找软件包）按钮。点击下方“luci-app-privoxy”对应的 Install（安装）按钮。如果提示好几条“Configuring xxxx”，那么就是执行成功了；如果卡死后再进入管理页面，看到有一个 Services（服务）菜单，菜单里有 Privoxy WEB proxy（Privoxy 网络代理），那也是成功了。

  ![](./img/13.png)



- 配置 Privoxy 设置。点击 Services -> Privoxy WEB proxy。
  - Files and Directories（文件和目录）：Action Files 删除到只剩一个框，填入`match-all.action`。Filter files 和 Trust files 均留空。
  - Access Control（访问控制）：Listen addresses 填写`0.0.0.0:8118`，Permit access 填写`192.168.0.0/16`。Enable action file editor 勾选。
  - Miscellaneous（杂项）：Accept intercepted requests 勾选。
  - Logging（日志）：全部取消勾选。

点击 Save & Apply。

![](./img/14.png)



![](./img/15.png)



![](./img/16.png)



![](./img/17.png)



![](./img/18.png)



- 配置防火墙转发。点击 Network -> Firewall（防火墙），然后点击 Custom Rules 标签，在大框框里另起一行(**注意，之前已经添加了6行代码，不要把刚刚添加的几行代码给删除了**)，添加下面的代码：

  ```
  iptables -t nat -N http_ua_drop
  iptables -t nat -I PREROUTING -p tcp --dport 80 -j http_ua_drop
  iptables -t nat -A http_ua_drop -m mark --mark 1/1 -j RETURN
  iptables -t nat -A http_ua_drop -d 0.0.0.0/8 -j RETURN
  iptables -t nat -A http_ua_drop -d 127.0.0.0/8 -j RETURN
  iptables -t nat -A http_ua_drop -d 192.168.0.0/16 -j RETURN
  iptables -t nat -A http_ua_drop -p tcp -j REDIRECT --to-port 8118
  ```

点击 Restart Firewall（重启防火墙）按钮。

![](./img/20.png)





- 使用 Privoxy 替换 UA。
打开`http://config.privoxy.org/edit-actions-list?f=0`，
如果打不开，请重启路由器多测试几遍。点击 Edit 按钮。
在Action 那一列中，hide-user-agent 改选为 Enable（绿色），在右侧 User Agent string to send 框中填写以下内容：
`Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.64 Safari/537.11`

`其它全部选择为 No Change （紫色）。此处非常重要`，
	最后点击 Submit 按钮，再次重启路由器

![](./img/21.png)



![](./img/22.png)



- 验证防检测效果。

  手机连接到该路由器的WIFI，使用手机(注意关闭**为屁嗯**后再测试)
  在浏览器打开[http://www.user-agent.cn/](http://www.user-agent.cn/)，查看结果是否为 Mozilla/5.0 (X11; Linux x86_64)，而不是android或者iphone。
  部分andriod11的手机 无法进行ua伪装 
  当手机连上wifi后检测出的ua结果为 Mozilla/5.0 (X11; Linux x86_64)  则说明成功了
  
  还有就是低调使用哈，我无所谓 反正没几天爷就毕业了 qaq
  
  
  注意关闭**为屁嗯**后再测试！注意关闭**为屁嗯**后再测试！注意关闭**为屁嗯**后再测试！

  ![](./img/25.png)
  
  ![](./img/26.png)
  
  ![](./img/23.png)
  
  ![](./img/24.png)

  

## 设置定时重启

	（对于晚上准时断电的城院来说，没什么区别）
	
由于使用了Privoxy代理，会使得所有的http流量均被转发到Privoxy，时间一久，网络会变成异常慢。为了保证良好的网络，可以每天凌晨让路由器自动重启一遍以恢复路由器系统响应速度。

打开以下页面，键入以下代码(具体时间可自行更改)：

```
40 2 * * * sleep 5 && touch /etc/banner && reboot   //每天凌晨2点40分路由器自动重启
40 4 * * * sleep 5 && touch /etc/banner && reboot   //每天凌晨4点40分路由器自动重启
40 6 * * * sleep 5 && touch /etc/banner && reboot   //每天凌晨6点40分路由器自动重启
```



![](./img/11.png)



提交后，然后打开以下页面，重启`cron`服务

![](./img/12.png)



至此，所有步骤均已配置完毕，可以安心上网了。


