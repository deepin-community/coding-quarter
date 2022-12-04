### 任务描述

DDE 是深度桌面环境的简称， 基于 Qt 开发，目前主要在 Deepin 操作系统中使用，也可以在其他 Linux 发行版中使用。
目前 deepin-overlay 上已经打包了 DDE 的组件，但是存在版本无法即时得到更新， 缺少部分组件， 适配不完整存在 bug 等问题。
目前已经完整适配的架构有 amd64 / riscv 部分适配 loong 架构

本次任务的目标是将 DDE 的组件完好移植到 deepin-overlay 上， 能够顺畅使用:
1. 需要升级过时的 DDE 软件包
2. 需要打包缺少的部分组件
3. 需要修复 deepin-overlay 存在的 bug, 整理/编写 patch
4. 需要修复 loong 架构其他软件的适配 并且需要的的软件提到主线 keyword
5. [中级] 新架构移植 arm64 增加适配
6. [高级] 新架构移植 mips64el 增加适配 并设计方案对于 linuxdeepin 的 mips64 强制开龙芯扩展优化进行优化/修改 合并到上游

目前 DDE 在其他发行版也有移植，比如 Arch, openSUSE, Fedora 等, 可以参考这些发行版的移植工作。处理 bug 时可以看看其他发行版是否已有修复方案。

### 验收标准

- 软件常规升级/维护/新增打包/Patch整理被 deepin-overlay/main-tree 仓库接受
- 自己编写的 Patch 可以被验证解决了特定问题

### 参考文档

- [Archlinux DDE](https://archlinux.org/packages/?sort=&q=deepin)
- [Basic guide to write Gentoo Ebuilds](https://wiki.gentoo.org/wiki/Basic_guide_to_write_Gentoo_Ebuilds)
- [devmanual](https://devmanual.gentoo.org/index.html)

### 联系方式

DDE 移植 SIG: https://www.deepin.org/index/docs/sig/sig/dde-porting/README.md

建议加入 DDE 移植 SIG 的交流群:
- [Matrix](https://matrix.to/#/#dde-port:matrix.org)
- [Telegram](https://t.me/ddeport)

DDE移植遇到的问题可以反馈到:
  https://github.com/linuxdeepin/developer-center/issues
