### 任务描述

`GSettings` 是一套可使用多个 `storage backends` 的 `API` ，默认使用 `dconf` 作为 `backend`  。`GSettings` 的配置文件是 `xml` 格式的，文件需以 `.gschema.xml` 结尾，文件名通常与 `id` 相同。配置文件安装在 `/usr/share/glib-2.0/schemas/` 目录下，手动添加进去的文件需要执行 `glib-complie-schemas` 命令让其生效。

`DConfig` 配置策略是由 `deepin` 自主研发的一套存储规范，涉及主要包括配置描述文件(`meta`)、配置存储文件(`cache`)、覆盖机制配置文件(`override`)， 应用需要配置的为 `meta` 和 `override`（可选）文件，它们均为 `json` 格式的文件。

基于 `DConfig` 及 `GSettings` 接口，完成一个配置转换小工具，此应用程序应当满足：

1. 项目使用 `cmake` 管理，基于 `dtkcore` 
2. 熟悉 `DConfig` 及 `GSettings` 相关概念及实现。
3. 功能需求：
   - 支持解析 `GSettings` 的 `.gschema.xml` 配置文件转换 `DConfig` 配置需要的 `json` 文件，包括描述信息，默认值等都需要相同
      ```bash
      # 仅供参考
      gsettings2dconfig  -i ./com.deepin.dde.dock.module.gschema.xml -o ./com.deepin.dde.dock.module.json
      ```
   - 支持 **双向** 转发配置 `GSettings` <==> `DConfig` ，即 `GSettings` 配置项变化时同步到 `DConfig`配置项，一样的 `DConfig` 配置项变化时同步到 `GSettings` 配置项。
      ```bash
      # 仅供参考
      gsettings2dconfig --proxy -id com.deepin.dtk -path /dtk/deepin/deepin-terminal -appid dtk.deepin.deepin-terminal -resource com.deepin.dtk
      ```
   - 支持同步配置  `GSettings` 配置到 `DConfig` 
      ```bash
      # 仅供参考
      gsettings2dconfig --sync -id com.deepin.dtk -path /dtk/deepin/deepin-terminal -appid dtk.deepin.deepin-terminal -resource com.deepin.dtk
      ```

### 环境的准备

下载并安装最新 `deepin` 操作系统；

为方便起见，下述步骤假定您在使用 `deepin V20` 。
- 检查 `gsetings` 是否安装正确，直接终端输入 `gsettings`，是否出现 `gsettings` 帮助文档；

- 安装 `libdtkcore-dev`, `libgsettings-qt-dev`
```
sudo apt install libdtkcore-dev libgsettings-qt-dev
```


### 验收标准

最终完成的应用程序应当能够提供下述功能：

- [ ] 能够恰当的运行和退出
- [ ] 代码符合 deepin 编码风格
- [ ] 项目用 CMake 管理，程序基于 DTK
- [ ] 支持 `gschema` 文件转 `meta` 文件
- [ ] 支持 `GSettings` 信号同步到 `DConfig`
- [ ] 帮助文档提示友好

我们通过对上述各项标准的完成数量来评估任务的完成程度

### 涉及的项目/提交到何处

- 此项目需要您最终将代码提交到 `linuxdeepin/dde-app-services` 仓库之中
- 在仓库中的 `dde-app-services/dconfig-center/` 目录下存储您的代码

### 预计工作量 116h

- 创建环境 4h
- 熟悉需求 8h
- 熟悉 `DConfig` 及 `GSettings` 相关资料 8h
- 设计 10h
- 代码编写 60 h
- 自测 16h
- 验收及沟通 8h


### 参考文档
- [GSettings 简介](https://www.jianshu.com/p/69289aee550b)
- [DConfig 规范](./%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%E8%A7%84%E8%8C%83.md)

- [dtkcore](https://github.com/linuxdeepin/dtkcore)
- [dde-app-services](https://github.com/linuxdeepin/dde-app-services)

### 联系方式

此任务的任务对接人为： yeshanshan@uniontech.com

