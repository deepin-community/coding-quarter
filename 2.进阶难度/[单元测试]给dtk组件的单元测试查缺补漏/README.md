### 任务描述

给 DTK 组件检查单元测试覆盖率，对未覆盖的接口添加相应的单元测试。

1. 此任务需要一些`Qt`、`CMake`的基础
2. 此任务需要能准确识别 DTK 的公有接口和私有接口
3. 以公有接口为第一优先级，私有接口次之
4. 此任务分两步进行：
    1. 先查找单元测试缺失的接口，并在对应的项目上提`issue`
    2. 将此`issue`链接发给对应项目负责人确认是否有效，确认有效后，可以提单元测试`pr`关联该`issue`

项目列表及链接：
* [dtkcore](https://github.com/linuxdeepin/dtkcore)
* [dtkgui](https://github.com/linuxdeepin/dtkgui)
* [dtkwidget](https://github.com/linuxdeepin/dtkwidget)
* [dtkdeclarative](https://github.com/linuxdeepin/dtkdeclarative)

### 环境的准备

本环境以`dtkcore`为例，其他项目大同小异。

1. 下载并安装`Deepin`操作系统
2. 进入系统后安装开发环境，可选择您喜欢的 IDE 进行安装
3. 为方便起见，以下以`qtcreator`为 IDE，`dtkcore`项目为例搭建开发环境：
    1. 安装 qtcreator：`apt install qtcreator`
    2. 安装基本开发依赖：`apt install cmake git qtbase5-dev debhelper dpkg-dev`
    3. 下载项目源文件：`git clone https://github.com/linuxdeepin/dtkcore.git`，注意换成个人仓库的 url
    4. 执行`cd dtkcore`并执行`dpkg-checkbuilddeps`检查项目依赖
    5. 使用`apt install xxx`来安装检查出来的依赖
    6. 最后即可使用 qtcreator 打开该项目进行编辑

### 验收标准

最终完成该任务应当满足以下要求：
- [ ] 提交 PR 前必须先创建 Issue
- [ ] 创建的 PR 必须关联对应的 Issue，并且该 Issue 已被确认为有效
- [ ] 提交的 PR 能跑过所有 ci 并被批准合入

### 涉及的项目/提交到何处

所有 DTK 组件的单元测试，均需以 PR 的形式提交到对应的仓库。

### 预计工作量

- 熟悉 Github 提交流程：1天
- 搭建开发环境：1天
- 提交 Issue 和 PR：视提交量而定

### 参考文档

DTK 组件所有单元测试均在`tests`目录，请在项目中查看相关源码。
DTK 组件所有公有接口均在`include`目录进行声明，请在项目中查看相关源码。
关于如何编写单元测试，可参考[gtest](http://google.github.io/googletest/)相关资料和项目源码。

### 联系方式

此任务的对接人为：guoyao@uniontech.com
