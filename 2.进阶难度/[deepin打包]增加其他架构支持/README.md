### 任务描述

为保持仓库软件包同步deepin上游的更新，我们计划先行构建riscv与loong相关的软件包，以out-of-tree的形式维护，后续会计划并入主线

1. 补充deepin-riscv64软件包
2. 构建deepin-loong64打包基础
3. 补充deepin-loong64软件包
4. 部分软件包升级同步到deepin主线
5. 完成riscv/loong的软件移植

### 环境的准备

deepin v23环境[可选]

### 验收标准

- [ ] 对于deepin-community仓库的pull request
- [ ] 对于obs的request
- [ ] 可以观察到的其他交付方式

### 预计工作量

无工作量预计 长期维护任务到活动结束为止

### 参考文档

[Debian 新维护者手册](https://www.debian.org/doc/manuals/maint-guide/index.zh-cn.html)

[Debian存储库](https://wiki.debian.org/DebianRepository)

[reprepro 使用说明](https://manpages.debian.org/bullseye-backports/reprepro/reprepro.1.en.html)

[aptly使用说明](https://www.aptly.info/doc/overview/)

[deepin社区贡献指南](https://wiki.deepin.org/zh/01_deepin%E9%85%8D%E5%A5%97%E7%94%9F%E6%80%81/01_deepin%E5%85%A5%E9%97%A8/02_%E5%BC%80%E5%8F%91%E7%9B%B8%E5%85%B3/02_%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97/deepin%E7%A4%BE%E5%8C%BA%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97)

### 联系方式

### 联系方式

deepin-riscv64 SIG: https://www.deepin.org/index/docs/sig/sig/deepin-riscv64/README

建议加入 deepin-riscv64 SIG 的交流群:
- [Matrix](https://matrix.to/#/#deepin-risc-v:matrix.org)

打包移植遇到的问题可以反馈到:
  https://github.com/linuxdeepin/developer-center/issues
