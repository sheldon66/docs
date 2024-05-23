# 聚合查询

<PluginInfo name="workflow-aggregate" link="/handbook/workflow/plugins/aggregate"></PluginInfo>

用于对某个数据表的满足条件的数据进行聚合函数查询，并返回对应的统计结果。常用于处理报表相关的统计数据。

节点的实现上基于数据库的聚合函数，目前仅支持对一个数据表的单字段进行统计，统计结果的数值会保存在节点的结果中供后续其他节点使用。

## 安装

内置插件，无需安装。

## 使用手册

### 创建节点

在工作流配置界面中，点击流程中的加号（“+”）按钮，添加“聚合查询”节点：

![创建聚合查询节点](https://static-docs.nocobase.com/7f9d806ebf5064f80c30f8b67f316f0f.png)

### 节点配置

![聚合查询节点_节点配置](https://static-docs.nocobase.com/57362f747b9992230567c6bb5e986fd2.png)

#### 聚合函数

支持 SQL 中的 `COUNT`、`SUM`、`AVG`、`MIN` 和 `MAX` 共 5 种聚合函数，选择其中一种对数据进行聚合查询。

#### 目标类型

聚合查询的目标可以通过两种模式选择，一种是直接选择目标数据表和其中的一个字段，另一种是通过流程上下文已有的数据对象，选择其对多的关系数据表及字段，进行聚合查询。

#### 去重

即 SQL 中的 `DISTINCT`，去重的字段与选择的数据表字段相同，暂时不支持两者选不同的字段。

#### 筛选条件

与普通的数据表查询时的筛选条件类似，可以使用流程的上下文变量。

### 示例

聚合目标为“数据表数据”比较容易理解，这里以“统计新增文章后该文章分类的总文章数”为例，介绍聚合目标为“关联数据表数据”的用法。

首先，创建两张数据表：“文章”和“分类”，其中文章有一个多对一关系字段指向分类表，同时创建反向关系字段分类一对多文章：

| 字段名   | 类型           |
| -------- | -------------- |
| 标题     | 单行文本       |
| 所属分类 | 多对一（分类） |

| 字段名   | 类型           |
| -------- | -------------- |
| 分类名称 | 单行文本       |
| 包含文章 | 一对多（文章） |

接下来创建一个数据表事件触发的工作流，选择文章表新增数据后触发。

之后增加一个聚合查询节点，配置如下：

![聚合查询节点_示例_节点配置](https://static-docs.nocobase.com/542272e638c6c0a567373d1b37ddda78.png)

这样在工作流被触发后，聚合查询节点中将会统计新增文章的分类下所有文章的数量，并保存为节点的结果。