

## 前言

为了消除**歧义**……本文提到的设备是Surface Pro7***而不是***7+

说句实在话，**折腾之前是需要认真考虑究竟值不值得上CachyOS的**

因为显而易见，surface本来就是巨硬亲儿子，windows体验更好是不出所料的

问题集中在

- 触摸屏需要使用社区内核，驱动没有并入主线

- 摄像头社区内核明确[不支持](https://github.com/linux-surface/linux-surface/wiki/Camera-Support)，要自己动手

- 主流社区内核版本不新（6.x,截止于26/10）

- fcitx5会占用虚拟键盘

- 触摸体验不如意（无法解决）

- 安全启动失效

- 基本不能使用wine/proton进行游戏（见下文）

下文会提供解决一些问题的思路

安全启动有解决方案，我没有折腾，难度很大

## 安装

下载cachyos镜像（tuna和ustc把iso镜像删了）然后塞到有ventoy的u盘里或者直接烧录

关机状态按电源和音量加进入UEFI菜单，选择Security，安全启动选择None，不然读不到u盘 

然后到启动选项看见usb storage左滑点ok

剩下的按照常规的方法就可以了

下文的出现的桌面环境为KDE Plasma

## 触摸驱动&内核

Surface的触摸驱动没有并入主线，只能用社区打包的内核

直接用必应搜`surface linux`搜出来的是[这个](https://github.com/linux-surface/linux-surface),内核版本6.19,并且没有编译优化

那么有什么选择呢?有的兄弟,有的

这是一个针对Surface有编译优化的最新[内核](https://github.com/Steefzar/linux-cachyos-surface-latest)

按照说明安装完了重启就有了触摸

## 摄像头驱动

> 表格来自https://github.com/linux-surface/linux-surface/wiki/Camera-Support

| Surface Pro 7 | IPU4 | OV5693 🚫 | OV8865 🚫 | OV7251 🚫 |
| ------------- | ---- | -------- | -------- | -------- |

吓哭了,啥也没有

不过[房主有神器](https://github.com/Lychee0829/surfacepro7-camera-ir)

花3块5用dsh写的,能用但是太折磨,回头如果我真用摄像头会再次优化的

## 虚拟键盘

可以参照

https://forum.manjaro.org/t/tip-how-to-make-qtvkbd-works-on-wayland/34275

https://forum.archlinuxcn.org/t/topic/13973/5

我的看法

- 我没设任何环境变量但是它确实能用

- 如果配置了按Shift更换输入法,在使用虚拟键盘时不会生效,应该额外设置Ctrl+空格然后按照这个进行切换




