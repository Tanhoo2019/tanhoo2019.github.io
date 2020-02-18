# Ssr搭建教程(转)


随着服务器的入门门槛越来越低，使用自己的服务器搭建一个梯子或者放一些自己的网站（博客）也越来越简单。下面主要总结一下使用服务器搭建梯子的方法。

## 购买服务器

现在服务器的价格越来越便宜了，像[百度智能云](https://cloud.baidu.com/product/bcc.html)/[阿里云](https://www.aliyun.com/product/ecs?spm=5176.12825654.h2v3icoap.14.54212c4ac5L6uQ)/[腾讯云](https://cloud.tencent.com/product/cvm)/[华为云](https://www.huaweicloud.com/product/ecs.html)等都推出了自己的学生优惠计划：[启航校园计划](https://cloud.baidu.com/campaign/campus-2018/index.html?unifrom=eventpage)/[云翼计划](https://promotion.aliyun.com/ntms/act/campus2018.html)/[云+校园](https://cloud.tencent.com/act/campus)/[云创校园计划](https://developer.huaweicloud.com/campus)，每月只需 ¥9-¥10 就可以使用一台低配的服务器，用来放一些 web 服务是十分划算的。

但是这些厂商的学生机都是放在国内的服务器，均不能搭梯子（那你说个**……），还是可以用来放网站和学习服务器的嘛^_^。

国内厂商也推出了放在国外的服务器，但价格都相对较贵。所以可以到一些国外的服务器提供商购买，如 [DigitalOcean](https://www.digitalocean.com/)，[Vultr](https://www.vultr.com/) 或 [Bandwagonhost](https://bandwagonhost.com/)。

### DigitalOcean

如果你是学生，这里强势推荐一下 [DigitalOcean](https://www.digitalocean.com/)，你可以在 [GitHub 教育认证链接](https://education.github.com/pack/join)认证为学生用户，就可以直接得到 DO 的 $50 优惠券代码，如果按照 DO 的最低配置 VPS 算，够使用 10 个月了。

而且，使用这个[推荐注册链接](https://m.do.co/c/4a7d2507a4ad)你还可以得到额外的 100 刀优惠（有效期两个月）。


注册时唯一麻烦的地方是需要绑定 PayPal 账户并支付 5 刀验证支付能力，当然这 5 刀也会进入 DO 的账户。
简单测试之后发现 DO 的 SFO2 的服务器延迟是最低的，你也可以根据自己的常用网络环境进行测试：[测试地址](http://speedtest-sfo2.digitalocean.com/)。



## SSR部署

如果你是 macOS/Linux，则可以直接通过 `ssh` 命令来连接服务器；如果是Windows，则需要通过 XShell/[FinalShell](http://www.hostbuf.com/t/988.html)等软件来连接。
登录服务器后，使用 [ToyoDAdoubi](https://github.com/ToyoDAdoubi) 大神写的一件部署脚本直接部署，以 CentOS 系统为例，命令如下：

```
yum -y install wget
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh
chmod +x ssr.sh
./ssr.sh
```

Copy



![SSR部署脚本](https://gitee.com/ShaneTian/ImageBed/raw/master/images/ssr.png)

安装过程，除了端口/密码需自定义外，混淆/协议等使用默认即可，还有确认安装文件的，输入 `y` 确认即可。

## BBR加速

使用 [Chikage](https://github.com/chiakge) 大神做的魔改版 BBR 加速一件部署脚本，代码如下：

```
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"
chmod +x tcp.sh
./tcp.sh
```

Copy



![BBR一键加速脚本](https://gitee.com/ShaneTian/ImageBed/raw/master/images/tcp.png)

接下来按照流程安装，推荐使用 BBRplus 或 BBR 魔改版进行加速：

1. 安装内核；
2. 重启 VPS；
3. 运行 `./tcp.sh` 脚本；
4. 使用对应内核的加速。

## SSR客户端下载

- Windows客户端：[下载地址](https://github.com/shadowsocksr-backup/shadowsocksr-csharp/releases)
- Mac客户端：[下载地址](https://github.com/shadowsocksr-backup/ShadowsocksX-NG/releases)
- 安卓客户端：[下载地址](https://github.com/shadowsocksr-backup/shadowsocksr-android/releases)
- iPhone客户端：[在线安装地址](https://freeid.xyz/)

安装好之后在软件中输入部署 SSR 时设置的信息即可成功登录。若忘记了自己的配置信息可重新运行 `./ssr.sh` 脚本查看账号信息。



## 参考

> [https://github.com/Alvin9999/new-pac/wiki/%E8%87%AA%E5%BB%BAss%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%95%99%E7%A8%8B](https://github.com/Alvin9999/new-pac/wiki/自建ss服务器教程)
> https://www.94ish.me/1635.html
> https://www.weiweiblog.cn/cloud/