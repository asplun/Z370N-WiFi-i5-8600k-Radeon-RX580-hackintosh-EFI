
# Z370N WiFi-i5 8600k-Radeon RX850-hackintosh EFI


更新于2019.9.19     系统版本Mac OS 10.14.6

假如你的主板甚至配置和我相同，那么你可以尝试直接使用这个EFI文件进行安装。（同主板都可以尝试）

> 其实这是我找人定制的EFI文件，因为睡眠问题在我的hackintosh一直得不到解决：只能黑屏假睡眠，主机电源是亮的，并且不能唤醒。

目前声卡、有线网卡、无线网卡、蓝牙、显卡驱动正常，睡眠正常，通过集显实现视频硬解，**iMessage和facetime无法使用，请勿登录**（除非刷入白苹果序列号洗白或者运气好hackintosh的序列号本身就能用）。

![QQ20190919-134229](https://tva1.sinaimg.cn/large/006y8mN6ly1g74uiuh1swj31hd0u0qd1.jpg)

![QQ20190919-134350](https://tva1.sinaimg.cn/large/006y8mN6ly1g74ujm8i7zj30oo0gftbc.jpg)![QQ20190919-134409](https://tva1.sinaimg.cn/large/006y8mN6ly1g74ujr88fwj30ga09t0uj.jpg)



## 目录

```bash
└── z370n-wifi-hackintosh
    ├── EFI       ---- MacOS引导文件
    ├── nvram.plist ---- 功能文件
    ├── README.md   ---- README.md 
```

只需要在安装Mac OS之后将EFI文件夹和nvram.plist文件放入系统EFI分区根目录即可。**请务必备份并删除原来的EFI引导文件。**



## 关于配置

这是我自配的主机配置：

| 硬件         | 型号                                                  |
| ------------ | ----------------------------------------------------- |
| 主板         | 技嘉 z370n-wifi                                       |
| CPU          | i5-8600K                                              |
| CPU散热      | 利民银箭130                                           |
| 显卡         | RX580蓝宝石超白金（满血版）                           |
| 内存         | 海盗船 8Gx2                                           |
| SSD          | Samsung 860 EVO 512（Mac OS）+intel 760P 256（Win10） |
| 电源         | EVEA 金牌全模组 600W                                  |
| 机箱|小号傻瓜超人K77   |                                  
| 蓝牙wifi网卡 | BCM94360CD                                            |

硬件选择上技嘉主板对Hackintosh的支持是比较好的最推荐，这也是我购买这块主板的原因。由于短期不需要上9代u，所以买的z370的板子，甚至现在刷新了bios其实也是支持9代u的。

i5-8600K是1k2捡垃圾的，不算太亏。

**显卡如果也想选择580的话一定要看清楚不要买2048p版本，目前京东都是这个版本！！**标准2304SP才是免驱卡。由于macOS Mojave 10.14.x 系统Hackintosh已经不支持目前中高端的NVIDIA显卡了。所以，显卡最好用A卡，比如：RX480、RX560、RX 570、RX580、Vega56、Vega64。其中**Vega 56、Vega 64** 无需搭配集显也可完全硬件加速。

**特别注意：**三星 **970 EVO Plus** 和 三星 **PM981** 无法做为macOS系统盘安装原版，会导致死机，即使作为从盘，也会导致macOS死机。

最后，**请不要使用XMP**

## 设置BIOS

BIOS设置是很有必要的，可以有效避免很多问题。

我的BIOS版本：`F13` 注意：F13的BIOS是最新的，主要3200频率内存条不兼容的问题！刚好我需要。**稳定的F10其实最好。**

>1. Save & Exit → Load Optimized Defaults  恢复默认
>2. BIOS > CSM Support > Disabled（必需禁用）
>3. Chipset → Vt-d : Disabled（一般禁用）
>4. Сhipset ▸ Internal Graphics = **Enabled**（启用）   如果使用vega 64，可以禁用集显
>5. Сhipset ▸ DVMT Pre-Allocated = **128MB**
>6. Сhipset ▸ DVMT Total Gfx Mem = **256MB**

实际上，即使使用默认的BIOS设置，Hackintosh也可以启动。但是还是设置这些可以更放心。

开机按`Del`进入BIOS界面，其实技嘉BIOS是可以设置中文的，摸索一下，设置BIOS难度很小。



## 安装Mac OS

Mac OS 10.14.6镜像以及安装教程请移步**[黑果小兵的blog](https://blog.daliansky.net/macOS-Mojave-10.14.6-18G87-Release-version-with-Clover-5033-original-image.html)**



## 使用硬件解码

一般带有集显的CPU支持使用集显硬解，如果使用vega64或者想用独显硬解，则需要在BIOS禁用集显，并且在**Clover Configurator**中**将机型变换为iMac Pro1.1**

![QQ20190919-134637](https://tva1.sinaimg.cn/large/006y8mN6ly1g74ub6tvusj30zj0iu0xt.jpg)

![QQ20190919-150724](https://tva1.sinaimg.cn/large/006y8mN6ly1g74ucynk54j30gj05y7ae.jpg)



## 蓝牙/WIFI网卡

默认的主板上的蓝牙/WIFI网卡不能用于Hackintosh。你需要更换为兼容的网卡，有非常多的网卡能够兼容黑苹果，我使用的是BCM94360CD四天线的网卡，甚至我准备了天线贴在主机后。其实可以使用mac笔记本网卡，可以让主板的wifi模块发挥作用，而不是像我一样。



## Z370N-WIFI主板USB端口位置

![QQ20190919-144504](https://tva1.sinaimg.cn/large/006y8mN6ly1g74u70k656j30m6096dlx.jpg)



## 系统更新

Mac OS 10.14.6 小版本的系统更新可以直接按照正常白苹果，使用软件更新进行，如升级10.15.x那就是另一段折腾的过程了，愿君成功。

## 免责声明

EFI出于交流分享，如果又任何使用上的文件更新将在github上传。理论上EFI不会损坏任何硬件或者软件，如有任何损失，本人不承担任何责任。下载安装即同意本声明。
