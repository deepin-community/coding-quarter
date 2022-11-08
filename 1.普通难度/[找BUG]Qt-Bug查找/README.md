### 任务描述

​	使用deepin v20系统上提供Qt5、Qt6基础环境，参考https://bugreports.qt.io/ 或 https://forum.qt.io/ 查找Qt bug，基于QtCreator编写demo在deepin上测试系统提供Qt5、Qt6是否存在Qt bug（官方未修复），如果存在提交发现Qt bug与复现demo。



### 环境的准备

- 开发环境搭建

sudo apt build-dep qtcreator //注意配置源deb-src

sudo apt install qtcreator

sudo apt-get install  qtbase5-dev   qt5-default  // Qt5

sudo apt-get install qt6-base-dev  //Qt6

QtCreator 配置对应的qmake版本



### 验收标准

 [ ] Bug 真实有效，且Qt上游最新代码中还未修复（必须满足）

 [ ] 可以根据复现步骤和demo复现问题

根据反馈问题严重程度与复现demo评估任务完成程度



### 涉及的项目/提交到何处

参考https://bugreports.qt.io/ 查找Qt源码 bug，在deepin上编写demo复现验证bug。

根据发现问题在对应项目上新建issues。



- Qt5提交位置：

https://github.com/deepin-community/qtbase-opensource-src/issues

- Qt6提交位置：

https://github.com/deepin-community/qt6-base/issues



### 参考文档

- [Qt官方bug提交网站](https://bugreports.qt.io/ )
- [Qt官方社区](https://forum.qt.io/)

### 联系方式

此任务的对接人为： luyaning@uniontech.com

可以通过邮件联系。

此外，您也可以在 linuxdeepin github 创建讨论主题来进行交流@Dami-star进行沟通。
