> [!WARNING]
>
> 耳机音质是一个相当玄学的话题,调节eq的目的在于让自己满意,**要相信自己的耳朵**
>
> 人云亦云的话没准会因为另一个人的生理特征不一样因而导致你的体验变差
>
> 本人不是老烧,麻烦懂行的不要拷打我()

*本文内容可能与其他相关教程存在较大出入,见谅*

## 原理讲解

每个耳机都有自己的频响曲线,频响曲线由硬件决定,并且可以通过声学设备测定

有那么几条理想的频响曲线,它们的声学效果是最好的

eq(equalizer)的目的正是在于将耳机的频响曲线修正到理想的效果

均衡器软件会根据eq文件调节某个频率的输出效果来达到这个目的

由此可见每个耳机都有独特的eq文件

所以网上的eq文件不是为你的耳机特制的,还得要手动制作

## eq文件制作

### 频响曲线csv获取

首先你需要知道自己耳机的**名字**

这里的名字是可用于搜索的英文名称

例

- 潜25 -- Qian25

- 太空漫游2Ultra --Space travel Ultra 2

此外不同型号之间差了一个字可能在频响曲线大相径庭,要确定型号确实是你的耳机

然后打开[这个网站](https://graph.hangout.audio/headphones/)

点击左上角搜索你的耳机,点进去

然后点击红圈的位置让多条曲线缩成一条平均曲线

![](https://raw.githubusercontent.com/Lychee0829/lychee0829.github.io/refs/heads/main/img/1/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE_20261025_103951.png)

点击图像上面的Screenshot,保存

然后把图片涂抹成这个样子

![](https://raw.githubusercontent.com/Lychee0829/lychee0829.github.io/refs/heads/main/img/1/Space%20Travel%202%20Ultra.png)

打开[automeris.io: Computer vision assisted data extraction from charts using WebPlotDigitizer](https://automeris.io)

登陆然后选择文件选择你的图片

选择2D XY Axes

然后Celibrate

随后右侧的X-Axis设为Log

在坐标原点点一个点,右上角有放大镜,在x1里面输入这个点的x坐标

在x轴离原点较远的地方点另一个点,在x2里面输入这个点的x坐标

在坐标原点点一个点,在y1里面输入这个点的y坐标

在y轴离原点较远的地方点另一个点,在y2里面输入这个点的y坐标

点错了按Remove Grid撤销

完事了然后点击Calibrate,点击右边的Run

显示一堆点,**并且都在频响曲线上面**

**有不在曲线上的把图片的那一部分涂抹了然后重来**

没有问题点View Data

点击Download .CSV

### 获取eq文件

打开[AutoEq](https://autoeq.app/)

点击搜索框最右边的打开文件的图标

打开你下载的csv文件

在Profiles里面点击Show advanced

点击Targets

入耳耳机就点带in ear的

不是就看看over-ear

点select equalizer app

不同系统不同方法

> [!NOTE]
>
> 对于Windows
>
> 输入peace点进去
>
> 点下载图标

> [!NOTE]
>
> 对于Linux
>
> 输入easyeffects点进去
>
> 点下载图标

## 软件准备

在电脑上需要一个应用来加载你的eq

### 对于Windows

[Peace均衡器 v1.5.5.5下载_Peace均衡器 v1.5.5.5官方下载_3DM软件](https://soft.3dmgame.com/down/212530.html)

[Equalizer APO电脑版下载-Equalizer APO中文电脑版下载_3DM软件](https://soft.3dmgame.com/down/377967.html)

先安装第二个然后第一个

安装时有复选框,选自己的耳机

当然对钩可以都打上()

提示overwrite确认

重启系统或者重启音频服务

打开peace,选择第二个界面

点import,选择你在autoeq网站上下载的文件

反正ok就是了

然后观察到均衡器不是直线了

大功告成,当然可能重启一遍才生效()

### 对于Linux

软件在这

[GitHub - wwmm/easyeffects: Limiter, compressor, convolver, equalizer and auto volume and many other plugins for PipeWire applications · GitHub](https://github.com/wwmm/easyeffects)

可以从自己发行版仓库搜编译的包,arch在extra有包

安装LinuxStudioPlugin和Zita

然后打开easyeffects

添加音效-均衡器-右下角三个点-导入APO预设

选择你在autoeq下载的

当然也可以用别的音效

个人喜欢[AUR (en) - easyeffects-digitalone1-presets-git](https://aur.archlinux.org/packages/easyeffects-digitalone1-presets-git)里面的LoudnessCrystal

当然使用预设了要再次导入APO
