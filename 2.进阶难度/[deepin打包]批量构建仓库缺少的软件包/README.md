### 任务描述

当前deepin v23仓库正处于建设中，相比于其他发行版缺乏很多软件包。

1. 调研对比其他发行版缺乏的软件包(需做筛选，去除当前仓库已包含软件包)
2. 编写自动化批量构建工具
3. 确保软件包通过依赖完整性检查
4. 构建产物上传至仓库

### 环境的准备

deepin v23环境构建，需掌握仓库管理，debian打包构建等基础知识

### 验收标准

- [ ] 不少于3000+ 新增软件包
- [ ] 根据软件包引入指南选择所需的上游软件包
- [ ] 确保引入软件包的依赖完备性
- [ ] 确保所引入软件包不影响现有系统环境
### 涉及的项目/提交到何处

* 本地自行调试
* 学习OBS平台的使用，可使用OBS平台进行批量构建
* 学习OBS平台的使用
* 提供构建好的仓库

### 预计工作量

单人80H

### 参考文档

[Debian 新维护者手册](https://www.debian.org/doc/manuals/maint-guide/index.zh-cn.html)

[Debian存储库](https://wiki.debian.org/DebianRepository)

[reprepro 使用说明](https://manpages.debian.org/bullseye-backports/reprepro/reprepro.1.en.html)

[aptly使用说明](https://www.aptly.info/doc/overview/)

[deepin社区贡献指南](https://wiki.deepin.org/zh/01_deepin%E9%85%8D%E5%A5%97%E7%94%9F%E6%80%81/01_deepin%E5%85%A5%E9%97%A8/02_%E5%BC%80%E5%8F%91%E7%9B%B8%E5%85%B3/02_%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97/deepin%E7%A4%BE%E5%8C%BA%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97)

### 联系方式

[deepin-pkg](https://github.com/deepin-community/SIG/tree/master/sig/deepin-pkg)

