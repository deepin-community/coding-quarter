### 任务描述

`deepin-anything` 是一个文件搜索工具，它主要包含一个服务和一个内核模块，其中内核模块监听虚拟文件系统事件，后通过 `genl` 进行事件广播；而服务会通过 `genl` 接收内核模块发送的虚拟文件系统事件并对文件索引进行更新，另外基于文件索引服务会通过 `DBus` 接口向外提供搜索服务。

基于 `deepin-anything`，完成一个带 GUI 的虚拟文件系统监控 demo 程序，此应用程序应当满足：

1. 项目 GUI 基于 `dtkdeclarative` （行云设计）；
2. 界面需求：
   - 显示块设备树，用户勾选上一个设备，则可显示该设备上发生的文件事件；
   - 显示收到的文件事件。
3. 功能需求：
   - 程序启动后，界面显示当前系统中存在的可用块设备，并按树形展示，可通过命令 `lsblk` 或目录 `/dev` 获取块设备信息；
   - 实时显示收到的文件事件；
   - 支持根据块设备进行文件事件过滤；
   - 支持文件事件的搜索、清空、导出。

### 环境的准备

下述步骤假定您在使用 `deepin V20` ，并有管理员权限。

```bash
# 通过包管理安装最新的 deepin-anything
sudo apt install deepin-anything-dev deepin-anything-dkms

# 或者通过源码安装
git clone https://github.com/linuxdeepin/deepin-anything.git
cd deepin-anything
sudo apt build-dep deepin-anything # 安装编译依赖
dpkg-buildpackage -us -uc -nc # 本地打包
sudo dpkg -i deepin-anything-dev_*.deb deepin-anything-dkms_*.deb

# 所需的头文件为 /usr/include/deepin-anything/vfs_genl.h
```

### 验收标准

最终完成的应用程序应当能够提供下述功能：

- [ ] 能够恰当的运行和退出；
- [ ] 代码符合 `deepin` 编码风格；
- [ ] 项目 GUI 基于 `dtkdeclarative` （行云设计）；
- [ ] 界面显示块设备树；
- [ ] 界面实时显示文件事件；
- [ ] 支持根据块设备进行文件事件过滤；
- [ ] 支持文件事件的搜索；
- [ ] 支持文件事件的清空；
- [ ] 支持文件事件的导出。

我们通过对上述各项标准的完成数量来评估任务的完成程度

### 涉及的项目/提交到何处

- 此项目需要您最终将代码提交到 `linuxdeepin/deepin-anything` 仓库之中；
- 在仓库中的 `examples` 目录下存储您的代码。

### 参考文档

- [libnl](http://www.infradead.org/~tgr/libnl/)
- [genl demo](https://github.com/wangrong1069/genl_demo)
- [deepin 编码风格](https://github.com/linuxdeepin/deepin-styleguide)

### 联系方式

此任务的任务对接人为： wangrong@uniontech.com


