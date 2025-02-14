# [am-cf-auto-speed-test](https://github.com/ansoncloud8/am-cf-auto-speed-test)

#
▶️ **新人[YouTube](https://youtube.com/@am_clubs?sub_confirmation=1)** 需要您的支持，请务必帮我**点赞**、**关注**、**打开小铃铛**，***十分感谢！！！*** ✅
</br>🎁请 **follow** 我的[GitHub](https://github.com/amclubs)、给我所有项目一个 **Star** 星星（拜托了）！你的支持是我不断前进的动力！ 💖
</br>✅**解锁更多技能** [加入TG群【am_clubs】](https://t.me/am_clubs)、[YouTube频道【@am_clubs】](https://youtube.com/@am_clubs?sub_confirmation=1)、[【博客(国内)】](https://amclubss.com)、[【博客(国际)】](https://amclubs.blogspot.com) 
</br>✅点击观看教程[CLoudflare免费节点](https://www.youtube.com/playlist?list=PLGVQi7TjHKXbrY0Pk8gm3T7m8MZ-InquF) | [VPS搭建节点](https://www.youtube.com/playlist?list=PLGVQi7TjHKXaVlrHP9Du61CaEThYCQaiY) | [获取免费域名](https://www.youtube.com/playlist?list=PLGVQi7TjHKXZGODTvB8DEervrmHANQ1AR) | [免费VPN](https://www.youtube.com/playlist?list=PLGVQi7TjHKXY7V2JF-ShRSVwGANlZULdk) | [IPTV源](https://www.youtube.com/playlist?list=PLGVQi7TjHKXbkozDYVsDRJhbnNaEOC76w) | [Mac和Win工具](https://www.youtube.com/playlist?list=PLGVQi7TjHKXYBWu65yP8E08HxAu9LbCWm) | [AI分享](https://www.youtube.com/playlist?list=PLGVQi7TjHKXaodkM-mS-2Nwggwc5wRjqY)

这是一个自动测速CF优选IP后将IP更新至CF域名A记录的自动化脚本

测试运行环境ubuntu-18.04-standard_18.04.1-1_amd64

## 1. 单域名对单IP，测速并更新
<details>
<summary><code><strong>「 点击查看 speed.sh 脚本使用示例 」</strong></code></summary>
一键脚本
 
``` bash
$ wget -N -P cs https://raw.githubusercontent.com/ansoncloud8/am-cf-auto-speed-test/main/speed.sh && cd cs && chmod +x speed.sh 
$ sh speed.sh [测速国家代码] [端口] [域名数量] [主域名] [CloudFlare账户邮箱] [CloudFlare账户key] [自定义测速地址]
```
| 参数名| 中文解释| 一键脚本参数必填项 | 备注(注意!参数必须按顺序填写)  |
|--------------------------|----------------|-----------------|-----------------|
| area_GEC |测速国家代码 |√ | hk、sg、kr、jp、us等常用国家代码，默认hk |
| port |端口  | √ | 443、2053、2083、2087、2096、8443，默认443 |
| record_count |域名数量 | √ | 默认4 |
| zone_name |主域名 | √ | 默认xxxx.com |
| auth_email | CloudFlare账户邮箱 | √ | 默认xxxx@gmail.com |
| auth_key |CloudFlare账户key | √ | 默认xxxxxxxxxxxxxxx |
| speedurl |自定义测速地址 | × | 默认https://vipcs.cloudflarest.link |

## 事前准备
~~运行前先去CloudFlare创建4条A记录,A记录IP随意即可~~ 直接运行即可
```
默认 香港地区,端口443,数量4
hk-443-1.xxxx.com
hk-443-2.xxxx.com
hk-443-3.xxxx.com
hk-443-4.xxxx.com

如需自定义地区端口数量可自行调整
[测速国家代码]-[端口]-[域名数量].[主域名]

例如:
脚本命令:
sh speed.sh kr
对应创建域名
kr-443-1.xxxx.com
kr-443-2.xxxx.com
kr-443-3.xxxx.com
kr-443-4.xxxx.com

脚本命令:
sh speed.sh jp 8443
对应创建域名
jp-8443-1.xxxx.com
jp-8443-1.xxxx.com
jp-8443-1.xxxx.com
jp-8443-1.xxxx.com

脚本命令:
sh speed.sh jp 2096 2 google.com
对应创建域名
jp-2096-1.google.com
jp-2096-2.google.com

```

## 手动运行:
先修改speed.sh脚本内`auth_email`、`auth_key`、`zone_name`的值
```
auth_email="xxxx@gmail.com"  #你的CloudFlare注册账户邮箱 *必填
auth_key="xxxxxxxxxxxxxxx"   #你的CloudFlare账户key,位置在域名概述页面点击右下角获取api key。*必填
zone_name="xxxx.com"         #你的主域名 *必填
```

修改后运行以下命令即可
``` bash
sh speed.sh                       #测速默认香港地区,默认端口443,默认数量4,修改域名为默认    hk-443-[1~4].xxxx.com
sh speed.sh kr                    #测速韩国地区,默认端口443,默认数量4,修改域名为默认        kr-443-[1~4].xxxx.com
sh speed.sh jp 8443               #测速日本地区,自定义端口8443,默认数量4,修改域名为默认     jp-8443-[1~4].xxxx.com
sh speed.sh jp 2096 2 google.com  #测速日本地区,自定义端口2096,自定义数量2,修改自定义域名为 jp-2096-[1~2].google.com
```

## 定时任务:
先修改speed.sh脚本内`auth_email`、`auth_key`、`zone_name`的值
```
auth_email="xxxx@gmail.com"  #你的CloudFlare注册账户邮箱 *必填
auth_key="xxxxxxxxxxxxxxx"   #你的CloudFlare账户key,位置在域名概述页面点击右下角获取api key。*必填
zone_name="xxxx.com"         #你的主域名 *必填
```
| 参数名| 中文解释| 修改`auth_email`、`auth_key`、`zone_name`值之后的必填项 | 备注(注意!参数必须按顺序填写)  |
|--------------------------|----------------|-----------------|-----------------|
| area_GEC |测速国家代码 |× | hk、sg、kr、jp、us等常用国家代码，默认hk |
| port |端口  | × | 443、2053、2083、2087、2096、8443，默认443 |
| record_count |域名数量 | × | 默认4 |
| zone_name |主域名 | × | 默认xxxx.com |
| auth_email | CloudFlare账户邮箱 | × | 默认xxxx@gmail.com |
| auth_key |CloudFlare账户key | × | 默认xxxxxxxxxxxxxxx |
| speedurl |自定义测速地址 | × | 默认https://vipcs.cloudflarest.link |

默认测速端口是443,默认测速域名数量为4
``` bash
cd /root/cs && chmod +x speed.sh && sh speed.sh hk                    #测速香港地区,默认端口443,默认数量4,修改域名为默认        hk-443-[1~4].xxxx.com
cd /root/cs && chmod +x speed.sh && sh speed.sh kr                    #测速韩国地区,默认端口443,默认数量4,修改域名为默认        kr-443-[1~4].xxxx.com
cd /root/cs && chmod +x speed.sh && sh speed.sh jp 8443               #测速日本地区,自定义端口8443,默认数量4,修改域名为默认     jp-8443-[1~4].xxxx.com
cd /root/cs && chmod +x speed.sh && sh speed.sh jp 2096 2 google.com  #测速日本地区,自定义端口2096,自定义数量2,修改自定义域名为 jp-2096-[1~2].google.com
```

## 文件结构
运行脚本后会自动下载所需文件,所以推荐将脚本放在单独目录下运行
```
cs
 ├─ speed.sh        #脚本本体
 ├─ CloudflareST    #CloudflareST测速程序
 ├─ ip              #测速地区ip库
 │   ├─ HK-443.txt
 │   ├─ JP-443.txt
 │  ...
 │   └─ US-443.txt
 ├─ log             #测速结果
 │   ├─ HK-443.csv
 │   ├─ JP-443.csv
 │  ...
 │   └─ US-443.csv
 ├─ temp            #整理IP库的临时文件夹
 │   ├─ 132203-1-443.txt
 │  ...
 │   └─ hello-earth-ip.txt
 ├─ ip-443.txt      #指定端口的完整不分区IP库
...
 └─ ip-8443.txt
```
</details>

****

## 2. 单域名对多IP，测速并更新
<details>
<summary><code><strong>「 点击查看 speed_AIO.sh 脚本使用示例 」</strong></code></summary>
一键脚本
 
``` bash
$ wget -N -P cs https://raw.githubusercontent.com/ansoncloud8/am-cf-auto-speed-test/main/speed_AIO.sh && cd cs && chmod +x speed_AIO.sh 
$ sh speed_AIO.sh [测速国家代码] [端口] [IP数量] [主域名] [CloudFlare账户邮箱] [CloudFlare账户key] [自定义测速地址]
```
| 参数名| 中文解释| 一键脚本参数必填项 | 备注(注意!参数必须按顺序填写)  |
|--------------------------|----------------|-----------------|-----------------|
| area_GEC |测速国家代码 |√ | hk、sg、kr、jp、us等常用国家代码，默认hk |
| port |端口  | √ | 443、2053、2083、2087、2096、8443，默认443 |
| ips |域名数量 | √ | 默认4 |
| zone_name |主域名 | √ | 默认xxxx.com |
| auth_email | CloudFlare账户邮箱 | √ | 默认xxxx@gmail.com |
| auth_key |CloudFlare账户key | √ | 默认xxxxxxxxxxxxxxx |
| speedurl |自定义测速地址 | × | 默认https://vipcs.cloudflarest.link |

## 事前准备
~~运行前先去CloudFlare创建对应测速域名的A记录，A记录IP随意即可~~

~~**注意：您想获取多少IP数量就对应创建多少A记录，如使用默认443端口,则二级域名后可不带端口**~~

## 手动运行:
先修改speed.sh脚本内`auth_email`、`auth_key`、`zone_name`的值
```
auth_email="xxxx@gmail.com"  #你的CloudFlare注册账户邮箱 *必填
auth_key="xxxxxxxxxxxxxxx"   #你的CloudFlare账户key,位置在域名概述页面点击右下角获取api key。*必填
zone_name="xxxx.com"         #你的主域名 *必填
```

修改后运行以下命令即可
``` bash
sh speed_AIO.sh                       #测速默认香港地区,默认端口443,修改域名为默认    hk.xxxx.com
sh speed_AIO.sh kr                    #测速韩国地区,默认端口443,修改域名为默认        kr.xxxx.com
sh speed_AIO.sh jp 8443 6             #测速日本地区,自定义端口8443,修改域名为默认     jp-8443.xxxx.com 6条IP记录
sh speed_AIO.sh jp 2096 8 google.com  #测速日本地区,自定义端口2096,修改自定义域名为     jp-2096.google.com 8条IP记录
```

## 定时任务:
先修改speed.sh脚本内`auth_email`、`auth_key`、`zone_name`的值
```
auth_email="xxxx@gmail.com"  #你的CloudFlare注册账户邮箱 *必填
auth_key="xxxxxxxxxxxxxxx"   #你的CloudFlare账户key,位置在域名概述页面点击右下角获取api key。*必填
zone_name="xxxx.com"         #你的主域名 *必填
```
| 参数名| 中文解释| 修改`auth_email`、`auth_key`、`zone_name`值之后的必填项 | 备注(注意!参数必须按顺序填写)  |
|--------------------------|----------------|-----------------|-----------------|
| area_GEC |测速国家代码 |× | hk、sg、kr、jp、us等常用国家代码，默认hk |
| port |端口  | × | 443、2053、2083、2087、2096、8443，默认443 |
| ips |域名数量 | × | 默认4 |
| zone_name |主域名 | × | 默认xxxx.com |
| auth_email | CloudFlare账户邮箱 | × | 默认xxxx@gmail.com |
| auth_key |CloudFlare账户key | × | 默认xxxxxxxxxxxxxxx |
| speedurl |自定义测速地址 | × | 默认https://vipcs.cloudflarest.link |

默认测速端口是443,默认测速域名数量为4
``` bash
cd /root/cs && chmod +x speed_AIO.sh && sh speed_AIO.sh hk                    #测速香港地区,默认端口443,修改域名为默认        hk.xxxx.com
cd /root/cs && chmod +x speed_AIO.sh && sh speed_AIO.sh kr                    #测速韩国地区,默认端口443,修改域名为默认        kr.xxxx.com
cd /root/cs && chmod +x speed_AIO.sh && sh speed_AIO.sh jp 8443               #测速日本地区,自定义端口8443,,修改域名为默认     jp-8443.xxxx.com
cd /root/cs && chmod +x speed_AIO.sh && sh speed_AIO.sh jp 2096 6 google.com  #测速日本地区,自定义端口2096,修改自定义域名为      jp-2096.google.com
```

## 文件结构
运行脚本后会自动下载所需文件,所以推荐将脚本放在单独目录下运行
```
cs
 ├─ speed_AIO.sh        #脚本本体
 ├─ CloudflareST    #CloudflareST测速程序
 ├─ ip              #测速地区ip库
 │   ├─ HK-443.txt
 │   ├─ JP-443.txt
 │  ...
 │   └─ US-443.txt
 ├─ log             #测速结果
 │   ├─ HK-443.csv
 │   ├─ JP-443.csv
 │  ...
 │   └─ US-443.csv
 ├─ temp            #整理IP库的临时文件夹
 │   ├─ 132203-1-443.txt
 │  ...
 │   └─ hello-earth-ip.txt
 ├─ ip-443.txt      #指定端口的完整不分区IP库
...
 └─ ip-8443.txt
```
</details>

****

## ~~3. 单域名对多地区IP，汇总更新（无测速内容，只汇总更新域名）~~ 不实用，不维护了
<details>
<summary><code><strong>「 点击查看 CDNDomainUpdate.sh 脚本使用示例 」</strong></code></summary>
一键脚本

**注意：CDNDomainUpdate.sh 脚本必须与 测速结果log文件夹同目录**

``` bash
$ wget -N -P cs https://raw.githubusercontent.com/ansoncloud8/am-cf-auto-speed-test/main/CDNDomainUpdate.sh && cd cs && chmod +x CDNDomainUpdate.sh
$ sh CDNDomainUpdate.sh [汇总二级域名] [主域名] [CloudFlare账户邮箱] [CloudFlare账户key] 
```
| 参数名| 中文解释| 一键脚本参数必填项 | 备注(注意!参数必须按顺序填写)  |
|--------------------------|----------------|-----------------|-----------------|
| record_name | 汇总二级域名 |√ | 默认cdn,如只更新特定地区可填写hk、sg、kr、jp、us等常用国家代码， |
| zone_name |主域名 | √ | 默认xxxx.com |
| auth_email | CloudFlare账户邮箱 | √ | 默认xxxx@gmail.com |
| auth_key |CloudFlare账户key | √ | 默认xxxxxxxxxxxxxxx |

## 事前准备
运行前先去CloudFlare创建对应测速域名的A记录，A记录IP随意即可

**注意：您想汇总多少IP数量就对应创建多少A记录**

```
默认 二级域名cdn，汇总逻辑，在测速记录文件夹每个地区443端口各提取1条IP更新，如IP不够域名数量会继续增加各个地区IP数量

如需自定义地区端口数量可自行调整，
[二级域名].[主域名]

例如:
脚本命令:
sh CDNDomainUpdate.sh
对应创建域名
cdn.xxxx.com 
cdn.xxxx.com 
cdn.xxxx.com 
cdn.xxxx.com 

脚本命令:
sh CDNDomainUpdate.sh sp
对应创建域名
sp.xxxx.com
sp.xxxx.com
sp.xxxx.com
sp.xxxx.com

脚本命令:
如只更新特定地区可填写hk、sg、kr、jp、us等常用国家代码
sh CDNDomainUpdate.sh hk
对应创建域名
hk.xxxx.com
hk.xxxx.com
hk.xxxx.com
hk.xxxx.com

脚本命令:
sh CDNDomainUpdate.sh jp google.com
对应创建域名
jp.google.com
jp.google.com

```

## 手动运行:
先修改speed.sh脚本内`auth_email`、`auth_key`、`zone_name`的值
```
auth_email="xxxx@gmail.com"  #你的CloudFlare注册账户邮箱 *必填
auth_key="xxxxxxxxxxxxxxx"   #你的CloudFlare账户key,位置在域名概述页面点击右下角获取api key。*必填
zone_name="xxxx.com"         #你的主域名 *必填
```

修改后运行以下命令即可
``` bash
sh CDNDomainUpdate.sh                 #更新汇总IP至默认域名       cdn.xxxx.com
sh CDNDomainUpdate.sh sp              #更新汇总IP至自定义域名     sp.xxxx.com
sh CDNDomainUpdate.sh hk              #更新香港地区IP至对应域名   hk.xxxx.com
sh CDNDomainUpdate.sh jp google.com   #更新日本地区IP至对应域名   jp.google.com
```

## 定时任务:
先修改speed.sh脚本内`auth_email`、`auth_key`、`zone_name`的值
```
auth_email="xxxx@gmail.com"  #你的CloudFlare注册账户邮箱 *必填
auth_key="xxxxxxxxxxxxxxx"   #你的CloudFlare账户key,位置在域名概述页面点击右下角获取api key。*必填
zone_name="xxxx.com"         #你的主域名 *必填
```
| 参数名| 中文解释| 修改`auth_email`、`auth_key`、`zone_name`值之后的必填项 | 备注(注意!参数必须按顺序填写)  |
|--------------------------|----------------|-----------------|-----------------|
| record_name | 汇总二级域名 |√ | 默认cdn,如只更新特定地区可填写hk、sg、kr、jp、us等常用国家代码， |
| zone_name | 主域名 | √ | 默认xxxx.com |
| auth_email | CloudFlare账户邮箱 | √ | 默认xxxx@gmail.com |
| auth_key |CloudFlare账户key | √ | 默认xxxxxxxxxxxxxxx |

默认测速端口是443,默认测速域名数量为4
``` bash
cd /root/cs && chmod +x CDNDomainUpdate.sh && sh CDNDomainUpdate.sh                 #更新汇总IP至默认域名       cdn.xxxx.com
cd /root/cs && chmod +x CDNDomainUpdate.sh && sh CDNDomainUpdate.sh sp              #更新汇总IP至自定义域名     sp.xxxx.com
cd /root/cs && chmod +x CDNDomainUpdate.sh && sh CDNDomainUpdate.sh hk              #更新香港地区IP至对应域名   hk.xxxx.com
cd /root/cs && chmod +x CDNDomainUpdate.sh && sh CDNDomainUpdate.sh jp google.com   #更新日本地区IP至对应域名   jp.google.com
```

## 文件结构
```
cs
 ├─ CDNDomainUpdate.sh        #脚本本体
 └─ log             #测速结果
     ├─ CDN.csv     #创建汇总IP结果
     ├─ HK-443.csv
     ├─ JP-443.csv
    ...
     └─ US-443.csv

```
</details>

#### speed脚本内有 telegram 推送配置，有需要运行前自行填写telegram参数。

# 
<center>
<details><summary><strong> [点击展开] 赞赏支持 ~🧧</strong></summary>
*我非常感谢您的赞赏和支持，它们将极大地激励我继续创新，持续产生有价值的工作。*

- **USDT-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`
- **TRX-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`

<div align="center"> 
  <img src="https://github.com/user-attachments/assets/e6cdc42a-6374-4722-b833-601738f72196" width="200"></br> 
  TRC10/TRC20扫码支付 
</div> 
</details>
</center>

 #
 免责声明:
 - 1、该项目设计和开发仅供学习、研究和安全测试目的。请于下载后 24 小时内删除, 不得用作任何商业用途, 文字、数据及图片均有所属版权, 如转载须注明来源。
 - 2、使用本程序必循遵守部署服务器所在地区的法律、所在国家和用户所在国家的法律法规。对任何人或团体使用该项目时产生的任何后果由使用者承担。
 - 3、作者不对使用该项目可能引起的任何直接或间接损害负责。作者保留随时更新免责声明的权利，且不另行通知。
 
