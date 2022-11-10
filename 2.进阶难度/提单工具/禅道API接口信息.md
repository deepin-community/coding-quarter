# 提交BUG的接口
## 接口类型
POST
## 接口地址
```python
/bug-create-[productID]-[branch]-[extras].json
```
## 参数信息
| 参数列表  | 类型   | 描述                                                |
| --------- | ------ | --------------------------------------------------- |
| productID | int    |                                                     |
| branch    | string |                                                     |
| extras    | string | others params, forexample, projectID=10,moduleID=10 |

*POST参数*

| 参数列表    | 类型       | 描述                                                         |
| ----------- | ---------- | ------------------------------------------------------------ |
| product     | int        | 所属产品 *必填                                               |
| title       | string     | Bug标题 *必填                                                |
| openedBuild | int\|trunk | 影响版本 *必填                                               |
| branch      | int        | 分支/平台                                                    |
| module      | int        | 所属模块                                                     |
| project     | int        | 所属项目 *必填                                               |
| assignedTo  | string     | 指派给                                                       |
| deadline    | date       | 截止日期 日期格式：YY-mm-dd，如：2019-01-01                  |
| type        | string     | Bug类型 取值范围： \| baselineedition \| docerror \| reliable \| compatible \| modifyimport \| codeerror \| config \| install \| security \| performance \| standard \| designdefect \| system \| app \| desktop \| kernel \| newfeature \| page_display \| experience \| function \| interface \| operation_prompt \| not_involve*必填 |
| os          | string     | 操作系统 取值范围： \| ios \| android \| deepin \| uos \| all \| windows \| others |
| browser     | string     | 浏览器 取值范围： \| uos \| all \| ie \| chrome \| firefox \| other |
| color       | string     | 标题颜色 颜色格式：#RGB，如：#3da7f5                         |
| severity    | int        | 严重程度 取值范围：1 \| 2 \| 3 \| 4                          |
| pri         | int        | 优先级 取值范围：0 \| 1 \| 2 \| 3 \| 4                       |
| steps       | string     | 重现步骤                                                     |
| mailto      | string     | 抄送给 填写帐号，多个账号用','分隔。                         |
| keywords    | string     | 关键词                                                       |
