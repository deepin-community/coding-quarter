### 任务描述

为保持仓库软件包同步上游的更新，我们计划开发自动化工具检查上游软件包的状态对比当前仓库软件包是否存在落后版本的情况

方案一：
1. 根据debian目录Homepage字段定位上游软件包位置
2.  Homepage描述可能不是软件包最上游的地址，需要手动更改
3.  根据软件包上游仓库Tag对比当前仓库的版本
4.   筛选出当前仓库版本低于上游仓库的软件包
4.   记录源码名称 当前版本 上游版本

方案二：
1. 根据debian/watch字段定位上游软件包地址
2. devscripts 提供了uscan可参考实现
3. 对比当前版本与上游版本差异 
4. 记录源码名称 当前版本 上游版本

### 环境的准备

deepin v23环境

### 验收标准

- [ ] 自动化对比版本差异
- [ ]  记录的信息提交到指定仓库
- [ ]  github actions工作流可正常运作
### 涉及的项目/提交到何处

* 相关项目批量提交至[deepin-community/ci-test](https://github.com/deepin-community/ci-test)下

### 预计工作量

单人80H

### 参考文档

[Debian 新维护者手册](https://www.debian.org/doc/manuals/maint-guide/index.zh-cn.html)

[Debian存储库](https://wiki.debian.org/DebianRepository)

[reprepro 使用说明](https://manpages.debian.org/bullseye-backports/reprepro/reprepro.1.en.html)

[aptly使用说明](https://www.aptly.info/doc/overview/)

[debian/watch](https://wiki.debian.org/debian/watch)

[deepin社区贡献指南](https://wiki.deepin.org/zh/01_deepin%E9%85%8D%E5%A5%97%E7%94%9F%E6%80%81/01_deepin%E5%85%A5%E9%97%A8/02_%E5%BC%80%E5%8F%91%E7%9B%B8%E5%85%B3/02_%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97/deepin%E7%A4%BE%E5%8C%BA%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97)

### 联系方式

[deepin-pkg](https://github.com/deepin-community/SIG/tree/master/sig/deepin-pkg)

