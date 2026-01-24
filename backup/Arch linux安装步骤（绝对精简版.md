***写于24/11/16***
> [!WARNING]
> 非新手向，新手看这个https://arch.icekylin.online/guide/rookie/basic-install.html

~文章写于24/11/16，内容可能过时~
文章更新于26/01/25，内容可能过时

## 准备
访问https://mirrors.sdu.edu.cn/mirror  ，点开常用镜像下载链接，下载Archlinux镜像
下载ventoy,地址https://mirrors.sdu.edu.cn/github-release/1731742885/github-release/ventoy_Ventoy/v1.0.99/
下载完后制作启动盘，把镜像塞进去，然后重启，引导进入ventoy，选择archlinux
systemctl stop reflector.service
## 连接网络
iwctl
device list
station wlan0 get-networks
station wlan0 connect 网络名称
exit
## 安装
archinstall
移动到Mirrors项敲回车，选择China
分区自己看着办
User account 选择，选择 Add a user，输入用户名、密码，并且确认作为 Superuser，然后 Confirm and exit
Timezone 选项，键入 /shanghai，搜索选择 Asia/Shanghai
然后install
## 善后一阶段
pacman -S networkmanager vim sudo zsh zsh-completions
reboot
## 善后二阶段
systemctl enable --now NetworkManager
nmcli dev wifi list 
nmcli dev wifi connect "Wi-Fi名" password "密码"
hwclock --systohc
vim /etc/locale.gen
locale-gen
echo 'LANG=en_US.UTF-8'  > /etc/locale.conf
vim ~/.bash_profile
添加export EDITOR='vim'
vim /etc/pacman.conf
～去掉 [multilib] 两行注释开32位库～
加入
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
pacman -Syyu
pacman -S plasma konsole dolphin
systemctl enable sddm
systemctl start sddm
sudo pacman -S sof-firmware alsa-firmware alsa-ucm-conf
sudo pacman -S ntfs-3g
sudo pacman -S adobe-source-han-serif-cn-fonts wqy-zenhei
sudo pacman -S noto-fonts noto-fonts-cjk noto-fonts-emoji noto-fonts-extra
sudo pacman -S chromium 
sudo pacman -S ark 
~sudo pacman-key --lsign-key "farseerfc@archlinux.org"~
sudo pacman -S archlinuxcn-keyring
sudo pacman -S yay

打开 System Settings > Language and Regional Settings > 在 Language 中点击 Add languages... > 选择中文加入 ADD，再拖拽到第一位 > 点击 Apply
sudo pacman -S fcitx5-im
sudo pacman -S fcitx5-chinese-addons
sudo pacman -S fcitx5-material-color
~vim ~/.config/environment.d/im.conf
加入
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus~
进入系统设置>键盘>虚拟键盘,启用fcitx5
sudo systemctl enable --now bluetooth
https://github.com/wuhgit/CustomPinyinDictionary 
把词库配置一下
## 至此，大事已成