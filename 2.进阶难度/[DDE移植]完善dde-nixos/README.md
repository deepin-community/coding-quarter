### 任务描述

DDE 是深度桌面环境的简称， 基于 Qt 开发，目前主要在 deepin 操作系统中使用，也可以在其他 Linux 发行版中使用。

目前在 NixOS 上的移植有了很大进展，但仍然有可以提升的地方，欢迎合作参与。

#### 任务介绍及工作量预估

1：构建 NixOS DDE 的 live 镜像

> 编写 iso.nix 用于构建一个预装 DDE 桌面环境的 iso 镜像，方便不熟悉 nix 使用的用户快速体验。

参考资料：https://nixos.wiki/wiki/Creating_a_NixOS_live_CD

预计用时：3 天

软件常规升级以及 bug 修复，需要对 Nix 和 C++ 都有一定了解。

2：常规升级

deepin-screensaver 是 DDE 的屏保程序，暂时没有打包进入 dde-nixos，可以用作学习练手。[预计用时：2天]

目前 dde-nixos 的软件大部分软件比较新，因此现有任务很少，欢迎希望长期合作的同学参与，未来的目标是 nixpkgs 维护稳定版， dde-nixos 维护最新版，用于测试。

如果发现有需要更新，可以提交 pr, 进行一次普通软件更新预计半小时。

3： bug 修复任务：很大一部分的 bug 修复需要对 NixOS 有了解，难度比常规升级高一些

- [ ] 控制中心新建用户时报错 useradd 无法找到
- [ ] 控制中心设置系统语言功能无法使用，可能与硬编码相关
- [ ] 截图录屏可以通过命令行启动，但通过dock插件启动无法录屏
- [ ] （高难度）dde-grand-search 无法搜索文件（可能与 deepin-anything 提供的内核模块有关）

详见：https://github.com/linuxdeepin/dde-nixos/issues/4

普通 bug 预计耗时 1 天每个，高难度暂不预计，可尝试挑战。

注意及时与 rewine 联系，防止重复工作。

### 涉及的项目/提交到何处

  代码应提交到 https://github.com/linuxdeepin/dde-nixos

  任务分类二, 应当同时提交到对应 DDE 项目

### 联系方式

dde-nixos 维护者： [rewine](https://github.com/wineee)

建议加入 DDE 移植 SIG 的交流群:
- [Matrix](https://matrix.to/#/#dde-port:matrix.org)
- [Telegram](https://t.me/ddeport)
