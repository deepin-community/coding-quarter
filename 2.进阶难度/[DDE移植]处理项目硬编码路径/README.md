### 任务描述

DDE 中使用了相当多的硬编码，比如 /usr/bin, /usr/share，这对可移植性是无益的。为了适配 NixOS, 必须进行非常多的 patch。实际上，存在不使用硬编码同时也不影响原有功能的更加通用的方案：一个简单的情形是，调用 /usr/bin/xxx, 可以直接改为调用 xxx, 这会从系统变量 PATH 指定的路径中寻找 xxx，此外还有使用 QStandardPaths 替换等情况，在参考资料有详细介绍。

目前大部分硬编码可以根据 [dde-nixos](https://github.com/linuxdeepin/dde-nixos) 给出的 patch 大致了解。

加分项：寻找并修复 dde-nixos 中遗漏了的硬编码路径

### 验收标准

- Patch 应用后软件功能在 deepin 和 NixOS 中均正常
- 建议在 [https://github.com/linuxdeepin/developer-center/issues/3374] 中跟踪 patch 合并情况

### 参考资料

- https://deepin-community.github.io/sig-dde-porting/posts/hardcode/ 这篇文章总结了一下避免各类硬编码的方案，欢迎扩充和纠正
- https://deepin-community.github.io/sig-dde-porting/posts/gnuinstalldirs/ 一些与安装路径有关硬编码可以结合 cmake 的 configure_file 处理 
- https://github.com/linuxdeepin/developer-center/issues/3374 这里记录了一些已经进行的工作，你的 pr 也可以链接到这里方便统计
- https://github.com/linuxdeepin/developer-center/issues/3402 与插件硬编码有关的讨论
- [QStandardPaths](https://doc.qt.io/qt-5/qstandardpaths.html)
- [XDG 规范介绍](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html)
- [应用 xdg 规范的 go 示例](https://github.com/v2rayA/v2rayA/pull/393)
- [xdg 规范的 qt 实现](https://github.com/lxqt/libqtxdg)


如果项目硬编码过多，建议先改确定可以改的，之后再尝试剩下的，分多次 pr。

预计用时：2 个月

### 涉及的项目/提交到何处

  应当提交到对应 DDE 项目中

### 联系方式

dde-nixos 维护者： [rewine](https://github.com/wineee)

建议加入 DDE 移植 SIG 的交流群:
- [Matrix](https://matrix.to/#/#dde-port:matrix.org)
- [Telegram](https://t.me/ddeport)