# Trigger Configuration

## 创建触发器

创建工作流时，类型选择“操作前事件”：

![创建操作前事件](https://static-docs.nocobase.com/2add03f2bdb0a836baae5fe9864fc4b6.png)

## 选择数据表

拦截工作流的触发器中首先要配置的是操作对应的数据表：

![拦截事件配置_数据表](https://static-docs.nocobase.com/8f7122caca8159d334cf776f838d53d6.png)

然后选择拦截模式，可以选择仅对绑定了该工作流的操作按钮拦截，也可以选择针对该数据表的所选操作都拦截（不区分来自哪个表单，也无需绑定对应工作流）：

## 拦截模式

![拦截事件配置_拦截模式](https://static-docs.nocobase.com/145a7f7c3ba440bb6ca93a5ee84f16e2.png)

目前支持的操作类型有“创建”、“更新”和“删除”，可以同时选择多个操作类型。
