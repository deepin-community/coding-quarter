### 任务描述

`dtkmount` 是 `dtkio` 项目中的一个子模块，它以共享库的形式发布。主要针对的是块设备和协议设备，可以获取这些设备的信息，以及挂载、卸载、监视它们。

基于 `dtkmount`，完成一个带 GUI 的设备监控 demo 程序，此应用程序应当满足：

1. 项目使用 `cmake` 管理，GUI 基于 `dtkgui`
2. 界面需求：
   - 显示设备列表，列表行数根据窗口大小动态排列；例如，300像素宽度显示3个 Item，窗口缩小到 200 像素后，显示两个 item，多余 item 显示在第二行，参照文件管理器计算机页面（若不好实现，则固定以表格形式显示也可，item 随窗口大小变化而变化）
   - item 内容：设备图标、设备名称、设备容量
     - 设备图标固定以 “drive-removable-media” 显示，即 `QIcon::fromTheme(“drive-removable-media”)`
     - 设备名称通过 `dtkmount` 的 `DBlockDevice::idLabel` 函数
     - 设备总容量通过 `dtkmount` 的 `DBlockDevice::size` 函数获取，已用容量以 `QStorageInfo` 类型，构造挂载点（挂载点通过 `dtkmount` 中 `DBlockDevice::mountPoints` 函数获取）的对象，调用其 `byteAvailable` 函数获取其可用容量，总量-可用容量为设备已用量，以字符串显示，例如 2GB/3GB；容量显示需格式化为大于等于 1 的最大单位，例如 1024KB 显示为 1MB；
     - item 中元素排列方式自定，可参照文件管理器计算机页面磁盘 item 的排列方式
3. 功能需求：
   - 程序启动后，界面显示当前系统中存在的可用磁盘，通过 `dtkmount` 可获取设备列表；
   - 未挂载的设备不显示设备容量，挂载了的设备皆显示
   - 设备接入后，插入 Item 到界面中，以设备名称的字母升序排列，例如设备 a, b，设备 a 显示在设备 b 之前
   - 设备移除后，从界面中移除 Item

### 环境的准备

由于 `dtkio` 尚未发布，故在 `deepin` 上还未集成，请自行编译打包安装 `dtkcore` 、`dtkio`。为方便起见，下述步骤假定您在使用 `deepin V20` ，并有管理员权限。

```bash
# 安装最新的 dtkcore
git clone https://github.com/linuxdeepin/dtkcore.git
cd dtkcore
sudo apt build-dep . # 安装编译依赖
dpkg-buildpackage -us -uc -b # 本地打包
sudo dpkg -i ../libdtkcore*  # 也可以手动选择不安装 dbgsym 和 doc 包

# 安装最新的 dtkio
git clone https://github.com/linuxdeepin/dtkio.git
cd dtkio
sudo apt build-dep . # 安装编译依赖
dpkg-buildpackage -us -uc -b # 本地打包
sudo dpkg -i ../libdtkmount*  # 也可以手动选择不安装 dbgsym 和 doc 包

```

### 验收标准

最终完成的应用程序应当能够提供下述功能：

- [ ] 能够恰当的运行和退出
- [ ] 代码符合 deepin 编码风格
- [ ] 项目用 CMake 管理，GUI 程序基于 DTK
- [ ] 界面显示所有的设备 item
- [ ] 已挂载的设备显示设备图标、设备名称、设备容量
- [ ] 未挂载的设备显示设备图标、设备名称
- [ ] 设备按照字母升序排列
- [ ] 设备移除后，从界面中移除 Item

我们通过对上述各项标准的完成数量来评估任务的完成程度

### 涉及的项目/提交到何处

- 此项目需要您最终将代码提交到 `linuxdeepin/dtkio` 仓库之中
- 在仓库中的 `dtkio/dtkmount/examples` 目录下存储您的代码

### 参考文档

- [dtkmount 开发文档](https://github.com/linuxdeepin/dtkio/tree/master/dtkmount/docs)
- [deepin 编码风格](https://github.com/linuxdeepin/deepin-styleguide)

### 联系方式

此任务的任务对接人为： zhangsheng@uniontech.com

可以通过邮件联系任务对接人获取其他更为方便的 IM 通讯方式。


