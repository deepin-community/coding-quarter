### 任务描述

完善 `xdg-desktop-portal-dde` 的`screenshot`,`Wallpaper`接口。

关于`screenshot`的完整如[xdg-desktop-portal关于screenshot](https://flatpak.github.io/xdg-desktop-portal/index.html#gdbus-org.freedesktop.impl.portal.Screenshot)描述。具体效果可以尝试在kde或者gnome上使用flameshot等截图工具(然而flameshot等通用截图工具现在一般在wayland下才使用xdp)，如果截图工具实现了这类高级功能的话，gnome和kde会给出弹窗让你选择截图的内容。

关于`Wallpaper`接口内容内容在[xdp Wallpaper](https://flatpak.github.io/xdg-desktop-portal/index.html#gdbus-org.freedesktop.impl.portal.Wallpaper)可以找到，需要了解的接口有dde-daemon `org.deepin.daemon.Appearance`的 `SetMonitorBackground`方法。（然而v20上的xdg-desktop-portal并没有wallpaper的接口，所以你可能需要在v23或者其他发行版的dde桌面环境进行调试，或者可以选择自己编译新的xdg-desktop-portal）

仓库位于
[xdg-desktop-portal-dde](https://github.com/linuxdeepin/xdg-desktop-portal-dde)

要求：

- 项目使用`CMake`管理

### 环境准备

需要准备装有dde桌面环境的发行版，kwin后端

调试工具可以选择 [ashpd-demo](https://github.com/bilelmoussaoui/ashpd),可能需要flatpak环境

基本的开发工具包括qt5-base,cmake等。

环境配置过程如下

``` bash
sudo cp misc/dde.portal /usr/share/xdg-desktop-portal/portals/

cmake -B build
cmake --build build

./build/src/xdg-desktop-protal-dde
```

接下来可以使用`ashpd-demo`调用截图功能进行调试，(然而这个demo只能截全图，也许之后会自己实现一个完整的demo进行测试)

### 验收标准

最终程序实现下述功能中其一:

  - [ ] 可以实现xdp中完整的截图功能，例如弹窗选择窗口
  - [ ] 可以通过xdp设置桌面背景


### 涉及到的项目/提交到何处
  - 最终提交代码到 `linuxdeepin/xdg-desktop-portal-dde`中

### 参考资料

  - [xdg-desktop-portal-kde](https://invent.kde.org/plasma/xdg-desktop-portal-kde)
  - [xdg-desktop-portal详细协议](https://flatpak.github.io/xdg-desktop-portal/index.html#gdbus-org.freedesktop.impl.portal.Wallpaper)

### 联系方式

您可以到下面群组获得帮助

- [Matrix](https://matrix.to/#/#deepin-community:matrix.org)
