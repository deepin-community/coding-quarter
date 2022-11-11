### 任务描述

deepin-tweak 是 deepin 社区开发的高级设置工具，在开发该项目的功能时，必须保证系统中存在相关接口，如果接口不存在，需要先修改对应的项目，添加接口后再开发 deepin-tweak 的功能。

deepin 系统使用 [com.deepin.daemon.Grub2](https://github.com/linuxdeepin/dde-daemon/) DBus 接口作为调整 Grub 的方法。

本任务的要求是，在分类中开发一个页面，用来调整 Grub 引导的参数，例如默认启动项，等待时间等。如果 com.deepin.daemon.Grub2 的方法不足以支撑功能，需要修改 dde-daemon 项目增加对应的接口。

对界面设计不强制要求，但需要考虑美观性，建议界面设计采用 `竖型排列`，一个功能占用独立的一行。

> 认领本任务前需要确保对 Grub、golang 和 qml 有一定的了解。

### 环境准备

deepin-tweak 和 dde-daemon 使用 git 作为版本控制系统，在提交代码时，需要遵守社区贡献指南。

可以通过以下方式快速安装依赖:

修改 `/etc/apt/sources.list`，解除 deb-src 的 `#` 注释。

```shell
sudo apt update
sudo apt build-dep deepin-tweak dde-daemon
```

通过以上方式就可以安装构建依赖。

`com.deepin.daemon.Grub2` 在 dde-daemon 的 grub2 目录下，入口文件是 `grub2_ifc.go`。

deepin-tweak 分类的增加方式为修改 `src/maincomponentsplugin/qml/` 下的文件，增加分类的方式是：

1. 修改 CategoryModel.qml，增加一个 BootMenu 的分类
2. 在 Categories 目录新增 BootMenu.qml
3. 在 Categories/BootMenu.qml 开发界面，并通过 DBus 调用 `com.deepin.daemon.Grub2` 的接口

### 验收标准

最终完成的应用程序应当能够提供下述功能：

- [ ] 调整默认启动项
- [ ] 调整引导等待时间
- [ ] 调整默认壁纸
- [ ] 调整默认主题
- [ ] 新增的分类支持中英国际化

我们通过对上述各项标准的完成数量来评估任务的完成程度

### 涉及的项目/提交到何处

- 此项目需要您最终将代码提交到 [`linuxdeepin/deepin-tweak`](https://github.com/linuxdeepin/deepin-tweak) 仓库之中
- 依赖的项目修改提交到 [`linuxdeepin/dde-daemon`](https://github.com/linuxdeepin/dde-daemon) 仓库之中

### 预计工作量

此任务预计总耗时 `5 周`。其中 `1 周` 调试开发环境，`1 周` 分析 deepin-tweak / dde-daemon(grub2) 项目代码，`1 周` 修改 dde-daemon 增加接口，`1 周` 修改 deepin-tweak 增加界面，`1 周` 调试及代码提交评审。

### 参考文档

- [deepin 编码风格](https://github.com/linuxdeepin/deepin-styleguide)
- [社区贡献 commit 规范](https://github.com/linuxdeepin/developer-center/wiki/Commit-%E6%8F%90%E4%BA%A4%E4%BF%A1%E6%81%AF%E8%A7%84%E8%8C%83)

### 联系方式

此任务的任务对接人为： zhangdingyuan@uniontech.com

可以通过邮件联系任务对接人获取其他更为方便的 IM 通讯方式。
