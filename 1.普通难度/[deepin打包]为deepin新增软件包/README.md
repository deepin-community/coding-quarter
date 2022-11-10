### 任务描述

为deepin仓库新增常用软件包，通过deepin-commity工作流集成到仓库中。

1. 选择具有一定流行度的软件包新增至deepin仓库中

2. 软件包选项应符合软件包引入指南

3. 确保软件包通过依赖完整性检查

   以下是选择的一些常用软件包

   

   | package                                                      | Remark                |
   | ------------------------------------------------------------ | --------------------- |
   | distrobox                                                    | 依赖 docker，podman等 |
   | sway                                                         | 依赖 wlroots seatd    |
   | hvml                                                         |                       |
   | apt-build<br/>apt-cacher<br/>apt-clone<br/>apt-config-auto-update<br/>apt-dater<br/>apt-dater-host<br/>apt-dpkg-ref<br/>apt-forktracer<br/>apt-file<br/>apt-mirror<br/>apt-offline<br/>apt-rdepends<br/>apt-setup<br/>apt-show-source<br/>apt-src<br/>apt-transport-in-toto<br/>apt-transport-s3<br/>apt-transport-tor<br/>apt-venv<br/>apt-xapian-index<br/> ... | apt系列工具包         |
   | android-androresolvd<br/>android-file-transfer<br/>android-framework-23<br/>android-platform-art<br/>android-platform-build<br/>android-platform-dalvik<br/>android-platform-development<br/>android-platform-external-boringssl<br/>android-platform-external-doclava<br/>android-platform-external-jsilver<br/>android-platform-external-libselinux<br/>android-platform-external-nist-sip<br/>android-platform-external-rappor<br/> ... | android系列工具包     |

   这里只列举了部分软件包，可以自行选择当前仓库未提供的软件包。
### 环境的准备

deepin v23环境构建，需掌握仓库管理，debian打包构建等基础知识

### 验收标准

- [ ] 确保所有的CI检查正常通过
- [ ] 软件包流转至testing仓库中
- [ ] 确保引入软件包的依赖完备性
- [ ] 确保所引入软件包不影响现有系统环境
### 涉及的项目/提交到何处

* 学习deepin-community组织下的相关工作流
* 学习OBS平台的使用
* 相关项目提交至[deepin-community](https://github.com/deepin-community)组织下

### 预计工作量

改任务可多人进行,可自由选择新增的软件包，故不设预计工作量

### 参考文档

[Debian 新维护者手册](https://www.debian.org/doc/manuals/maint-guide/index.zh-cn.html)

[Debian存储库](https://wiki.debian.org/DebianRepository)

[deepin社区贡献指南](https://wiki.deepin.org/zh/01_deepin%E9%85%8D%E5%A5%97%E7%94%9F%E6%80%81/01_deepin%E5%85%A5%E9%97%A8/02_%E5%BC%80%E5%8F%91%E7%9B%B8%E5%85%B3/02_%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97/deepin%E7%A4%BE%E5%8C%BA%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97)

[deepin-community协作指南](https://wiki.deepin.org/zh/01_deepin%E9%85%8D%E5%A5%97%E7%94%9F%E6%80%81/01_deepin%E5%85%A5%E9%97%A8/02_%E5%BC%80%E5%8F%91%E7%9B%B8%E5%85%B3/02_%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97/deepin-community%E5%8D%8F%E4%BD%9C%E6%B5%81%E7%A8%8B)



### 联系方式

[deepin-pkg](https://github.com/deepin-community/SIG/tree/master/sig/deepin-pkg)

