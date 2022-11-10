### 任务描述

 系统仓库由于软件包之间依赖的错综复杂，升级某一个软件包很容易导致其他软件包的依赖错误。

1. 仓库依赖完备性检查

2. 功能需求

  利用github Actions 部署自动化工作流，定时触发自动检查，批量进行软件包的安装卸载等操作，输出失败的软件包名称记录到github仓库指定文件中。

### 环境的准备

1. deepin v23版本环境 
### 验收标准

- [ ] 手动或者自动触发
- [ ] 可以多job并发进行
- [ ] 分类记录失败情况，安装失败 卸载失败  文件冲突 依赖冲突等
- [ ] 正确记录输出结果
### 涉及的项目/提交到何处

* 该工作流可以部署至个人项目中进行测试
* 自测完毕后可提交到[deepin-community/ci-test](https://github.com/deepin-community/ci-test) 仓库中

### 预计工作量
* 单人60H

### 参考文档
[GitHub Actions](https://docs.github.com/cn/actions)

[Debian 软件包管理系统基础](https://www.debian.org/doc/manuals/debian-faq/pkg-basics.zh-cn.html)

[Debian存储库](https://wiki.debian.org/DebianRepository)

[reprepro 使用说明](https://manpages.debian.org/bullseye-backports/reprepro/reprepro.1.en.html)

[aptly使用说明](https://www.aptly.info/doc/overview/)

### 联系方式

[deepin-pkg](https://github.com/deepin-community/SIG/tree/master/sig/deepin-pkg)

