## 引语

在Arch Linux中i18n文件全部存放在`/usr/share/locale/`中

中文的翻译文件被放在`/usr/share/locale/zh_CN/`

而命令行软件输出的汉化文件在`/usr/share/locale/zh_CN/LC_MESSAGES/`

在此目录里有大量以命令为文件名的.mo二进制翻译文件

本文的目的就是反编译,修改并且再次编译并替换原.mo文件

## 前置条件

需要安装[gettext](https://archlinux.org/packages/core/x86_64/gettext/)包和一个po编辑软件,推荐[podedit](https://archlinux.org/packages/extra/x86_64/poedit/)

```bash
# pacman -S gettext poedit
```

## 复制/备份原文件

```bash
cp /usr/share/locale/zh_CN/LC_MESSAGES/SOURCE.mo ~/Documents 
cd ~/Documents
mkdir mobkup
cp ./SOURCE.mo ./mobkup
# 将SOURCE.mo替换成你想要的文件
```

## 反编译/修改/编译

```bash
msgunfmt ./SOURCE.mo -o ./TARGET.po 
```

然后使用编辑器打开po文件,poedit支持Ctrl+F快速搜索原文和译文

改完了保存

然后编译以后替换

```bash
rm SOURCE.mo
msgfmt ./TARGET.po -o ./SOURCE.mo
cp ./SOURCE.mo /usr/share/locale/zh_CN/LC_MESSAGES/SOURCE.mo
```

## 完成

以下是效果

```bash
❯ sudo pacman -Syu
lychee0829 ,给我密码~ (｡•̀ᴗ-)✧
:: 正在和软件包数据库谈判...
 kde-unstable 新鲜美味😋
 core-testing                                                    5.0 KiB  34.2 KiB/s 00:00 [#####################################################] 100%
 core 新鲜美味😋
 extra-testing                                                 199.9 KiB   569 KiB/s 00:00 [#####################################################] 100%
 extra                                                           8.3 MiB  4.65 MiB/s 00:02 [#####################################################] 100%
 archlinuxcn                                                  1368.8 KiB  1353 KiB/s 00:01 [#####################################################] 100%
:: 启动全面系统滚挂喵(*´∀`)~♥...
让我看看软件依赖什么...
让我看看软件和谁过不去...

软件包 (48) dtc-1:1.8.1-1  leancrypto-1.8.0-1  man-pages-zh_cn-1.6.4.4-1  python-typing_extensions-4.16.0-1  qemu-audio-alsa-11.0.2-2
            qemu-audio-dbus-11.0.2-2  qemu-audio-jack-11.0.2-2  qemu-audio-oss-11.0.2-2  qemu-audio-pa-11.0.2-2  qemu-audio-pipewire-11.0.2-2
            qemu-audio-sdl-11.0.2-2  qemu-audio-spice-11.0.2-2  qemu-base-11.0.2-2  qemu-block-curl-11.0.2-2  qemu-block-dmg-11.0.2-2
            qemu-block-nfs-11.0.2-2  qemu-block-ssh-11.0.2-2  qemu-chardev-spice-11.0.2-2  qemu-common-11.0.2-2  qemu-desktop-11.0.2-2
            qemu-hw-display-qxl-11.0.2-2  qemu-hw-display-virtio-gpu-11.0.2-2  qemu-hw-display-virtio-gpu-gl-11.0.2-2
            qemu-hw-display-virtio-gpu-pci-11.0.2-2  qemu-hw-display-virtio-gpu-pci-gl-11.0.2-2  qemu-hw-display-virtio-gpu-pci-rutabaga-11.0.2-2
            qemu-hw-display-virtio-gpu-rutabaga-11.0.2-2  qemu-hw-display-virtio-vga-11.0.2-2  qemu-hw-display-virtio-vga-gl-11.0.2-2
            qemu-hw-display-virtio-vga-rutabaga-11.0.2-2  qemu-hw-uefi-vars-11.0.2-2  qemu-hw-usb-host-11.0.2-2  qemu-hw-usb-redirect-11.0.2-2
            qemu-hw-usb-smartcard-11.0.2-2  qemu-img-11.0.2-2  qemu-system-x86-11.0.2-2  qemu-system-x86-firmware-11.0.2-2  qemu-ui-curses-11.0.2-2
            qemu-ui-dbus-11.0.2-2  qemu-ui-egl-headless-11.0.2-2  qemu-ui-gtk-11.0.2-2  qemu-ui-opengl-11.0.2-2  qemu-ui-sdl-11.0.2-2
            qemu-ui-spice-app-11.0.2-2  qemu-ui-spice-core-11.0.2-2  qemu-vhost-user-gpu-11.0.2-2  sdl3-3.4.12-1  super-productivity-18.13.1-1

总共下了：   24.49 MiB
安装大小：  117.60 MiB
实际变化：    7.50 MiB

:: 这是要安装吗？ [Y/n] 
```