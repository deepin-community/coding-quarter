### 任务描述

DDE 是深度桌面环境的简称， 基于 Qt 开发，目前主要在 deepin 操作系统中使用，也可以在其他 Linux 发行版中使用。
目前 Fedora 上已经打包了 DDE 的组件，但是存在版本无法即时得到更新， 缺少部分组件， 适配不完整存在 bug 等问题。

本次任务的目标是将 DDE 的组件完好移植到 Fedora 上， 能够顺畅使用:
1. 需要升级过时的 DDE 软件包
2. 需要打包缺少的部分组件
3. 需要修复 Fedora DDE 存在的 bug, 整理/编写 patch

目前 DDE 在其他发行版也有移植，比如 Arch, openSUSE, ALT 等, 可以参考这些发行版的移植工作。处理 bug 时可以看看其他发行版是否已有修复方案。

### 环境的准备

目前各个版本的 Fedora 都有 DDE 组件, 推荐使用新的版本(Fedora 37 或者 rawhide)进行维护。

安装 Deepin 桌面环境 `sudo dnf group install "Deepin Desktop" -y`

- 初步体验:
```
# 下载打包源码
fedpkg co --anonymous deepin-calculator
cd deepin-calculator
# 下载项目源码,如需升级,需要从上游自行下载
fedpkg sources
fedpkg prep # 解压源码,并打补丁
## 这里可以尝试修改
# 本地编译
sudo dnf builddep deepin-calculator. # 安装依赖
fedpkg local
# 使用 mock 编译, 可以获得干净的构建环境
fedpkg mockbuild
# 另外 mock 可以提供 release 参数, 指定构建的发行版号
fedpkg --release rawhide mockbuild # 在 fedora 37 上也可以构建 rawhide 的包
```

- 基础贡献流程
1. 参考文档 [Package Maintainers](https://docs.fedoraproject.org/en-US/package-maintainers/)，注册 Fedora 帐号，签署 CLA，并配置 SSH key
2. 在 https://src.fedoraproject.org 寻找自己感兴趣的包， 并 fork 到自己的帐号下
3. 使用 git clone 下载自己 fork 的包
4. 修改后使用 git 常规工作流管理(add/commit) 
5. 使用 fedpkg push 推送到自己的 fork (其实可以 git push 但是只有 packager groups 的用户可以使用 ssh)
6. "Open PR" 给 Fedora packager 等待审核

- 如果您有意愿参与，欢迎成为 Fedora packager 参与项目维护，更多内容请阅读 Package Maintainers 系列参考文档

### 验收标准

- 软件常规升级/维护/新增打包/Patch整理被 Fedora 仓库接受
- 自己编写的 Patch 可以被验证解决了特定问题

### 涉及的项目/提交到何处

dtk 核心库
- [ ] dtkcommon
- [ ] dtkcore
- [ ] dtkgui
- [ ] dtkwidget
    建议更新到 5.5 最新版, 而非 5.6
- [ ] deepin-qt5integration
- [ ] deepin-qt5platform-plugins 

预估用时：4天

常规库和工具:
- [ ] udisks2-qt5
- [ ] disomaster
- [ ] docparser
- [ ] gio-qt
- [ ] deepin-gettext-tools 
- [ ] deepin-pw-check
- [ ] deepin-qt-dbus-factory
- [ ] deepin-polkit-agent
- [ ] deepin-desktop-schemas

预估用时： 一周

桌面环境核心组件:

- [ ] deepin-control-center
- [ ] deepin-dock
- [ ] deepin-launcher
- [ ] deepin-session-ui
- [ ] deepin-session-shell
- [ ] deepin-kwin
- [ ] deepin-file-manager
- [ ] deepin-daemon(golang)
- [ ] deepin-api(golang)
- [ ] startdde(golang)
- [ ] deepin-app-services (新软件)
    使用 dconfig 的新版应用需要依赖此包
- [ ] deepin-network-core (新软件)
    控制中心和 dock 的网络模块， deepin-network-utils 已弃用

这部分是最重要的工作，同时也是难点，耗时预估 1~3 天每个， 总体上需要40天左右。

golang 软件包:
- [ ] deepin-go-lib
- [ ] deepin-go-dbus-factory
- [ ] deepin-go-x11-client
- [ ] deepin-api
- [ ] deepin-desktop-schemas
- [ ] deepin-pw-check
- [ ] golang-deepin-go-lib
- [ ] golang-github-linuxdeepin-dbus-factory
- [ ] golang-github-linuxdeepin-go-x11-client

预计耗时一周。

DDE 常规应用维护:

- [ ] deepin-draw
- [ ] deepin-calculator
- [ ] deepin-editor
- [ ] deepin-image-editor
- [ ] deepin-image-viewer
- [ ] deepin-calendar
- [ ] deepin-system-monitor
- [ ] deepin-terminal
- [ ] deepin-screensaver
- [ ] deepin-shortcut-viewer

此类项目一般难度中等或偏低,预计耗时一周

(可选项) 由于 fedora 对音视频编解码器的授权要求严格, 一些 ffmpeg 相关格式支持无法进入官方源, 可以尝试能否通过阉割功能打包下列软件:
- [ ] image-editor
- [ ] deepin-movie-reborn 
- [ ] deepin-music
- [ ] deepin-screen-recorder
- [ ] deepin-voice-note


资源/艺术类软件包:

- [ ] deepin-wallpapers
需要更新最新版去掉 CC-BY-NC 3.0 协议壁纸
- [ ] deepin-gtk-theme
- [ ] deepin-sound-theme
- [ ] deepin-account-faces
- [ ] deepin-icon-theme
- [ ] deepin-desktop-base

此类项目理论上级难度较低,预计需要的时间: 1天

### 提交到何处

  代码应当首先提交到 Rawhide 分支

  编写的 patch 如非 fedora 的特殊需求, 应当同时提交到上游(DDE)项目

### 参考文档

- [Fedora 发行版上安装深度桌面](https://wiki.deepin.org/zh/%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98FAQ/DDE/Fedora36%E5%AE%89%E8%A3%85%E6%B7%B1%E5%BA%A6%E6%A1%8C%E9%9D%A2)
- [Package Maintainers](https://docs.fedoraproject.org/en-US/package-maintainers/)
    该系列文档介绍了如何成为 fedora 包维护者,以及软件包新增,维护和更新的方法
- [Fedora Packaging Guidelines](https://docs.fedoraproject.org/en-US/packaging-guidelines/)
    Fedora 打包的详细教程,介绍了 Spec 文件的语法,以及打包的一些注意事项
    包含了 Cmake/C++/Golang 的打包
- [Archlinux DDE](https://archlinux.org/packages/?sort=&q=deepin)
- [dde-nixos](https://github.com/linuxdeepin/dde-nixos)
- [src-openeuler](https://gitee.com/organizations/src-openeuler) 搜索 deepin
- [Alt Linux](https://bugzilla.altlinux.org/41341)

Fedora DDE 应用版本原则上跟随 Arch 更新的, 可以参考对应的依赖, 编译参数, patch 的写法

### 联系方式

fedora DDE: https://fedoraproject.org/wiki/SIGs/DeepinDE

DDE 移植 SIG: https://www.deepin.org/index/docs/sig/sig/dde-porting/README.md

建议加入 DDE 移植 SIG 的交流群:
- [Matrix](https://matrix.to/#/#dde-port:matrix.org)
- [Telegram](https://t.me/ddeport)

DDE移植遇到的问题可以反馈到:
  https://github.com/linuxdeepin/developer-center/issues