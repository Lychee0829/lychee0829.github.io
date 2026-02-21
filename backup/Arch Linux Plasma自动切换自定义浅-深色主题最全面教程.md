## KDE Plasma

全局主题里面肯定是有你不想要的图标或者Plasma外观样式,这一节主要在于修改全局主题

进入`系统设置>颜色与主题>全局主题`选择浅色主题和深色主题

终端执行

`nano ～/.local/share/plasma/look-and-feel/你选择的浅色主题/contents/defaults`

以下是配置解释

```
[KSplash]
//plasma欢迎屏幕
[kcminputrc][Mouse]
//鼠标主题
[kdeglobals][Icons]
//图标主题
[kdeglobals][KDE]
//应用程序外观样式
```

如果更改了[KSplash]那就要把当前目录下的splash文件夹替换为新欢迎屏幕的文件夹

主题有空格空格用`-`代替，如Tela blue->Tela-blue

深色主题一样配置，完事记得重启

## 壁纸

KDE Plasma可以使用plasma-apply-wallpaperimage命令切换壁纸（这个b怎么这么长

例如`plasma-apply-wallpaperimage ~/Pictures/wall/4.png`

示例代码（自用）（日落日出时间不大精确）

```c
#include <stdlib.h>
//#include <unistd.h>
//#include <stdio.h>
#include <time.h>
#define SUNRISE 7
#define SUNSET 18
int main(){
    int now=0;
    time_t utctime;
    struct tm *timep;
    time(&utctime);
    timep = gmtime(&utctime);
    if(timep->tm_hour+8>24){
        now=timep->tm_hour+8-24;
    }
    else{
        now=timep->tm_hour+8;
    }
    //printf("%d\n",now);
    //sleep(5);
    if(now<SUNRISE||now>SUNSET){
        system("plasma-apply-wallpaperimage ~/Pictures/wall/4.png");
        //printf("night");
    }
    else {
        system("plasma-apply-wallpaperimage ~/Pictures/wall/2.png");
        //printf("day");
    }
    return 0;
}
```

用`swww`或者`waypaper`可能也可以,但是我没有成功,希望有高人指点