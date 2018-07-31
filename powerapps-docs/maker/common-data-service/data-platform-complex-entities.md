---
title: 需要 PowerApps 计划 2 许可证的复杂实体 |Microsoft Docs
description: Common Data Service (CDS) for Apps 中复杂实体的列表，这些实体需要 PowerApps 计划 2 许可证。
author: clwesene
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 07/17/2018
ms.author: clwesene
ms.openlocfilehash: 76c101f35e236ac6bf037d2b5b748ca1b943d61d
ms.sourcegitcommit: efea7ed5ad8e80c87ba423fb094fa94b4e864d75
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39266246"
---
# <a name="complex-entities-and-licensing"></a>复杂实体和许可
包含以下复杂服务器端逻辑的实体需要使用这些实体应用或流用户具有 PowerApps 计划 2 或 Microsoft Flow 计划 2 许可证：

* 代码插件。详细信息：[插件开发](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development))
* 实时工作流。 详细信息：[工作流进程](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes))

    > [!IMPORTANT]
    >  只有那些转换为实时工作流的工作流才可视为实时的和同步的。 后台运行的工作流仍可与合适的 PowerApps 计划配合使用，并且不需要额外许可证。

若要了解是否向实体添加复杂业务逻辑，请检查环境中配置的插件程序集和工作流的列表。

## <a name="complex-entities-installed-with-dynamics-365"></a>与 Dynamics 365 一起安装的复杂实体
下表列出的实体包含复杂服务器端逻辑，作为 Dynamics 365 应用程序安装的一部分现成可用。 此列表旨在作为指南。 根据环境中安装了哪些 Dynamics 365 应用程序和版本，复杂实体的列表可能会有所不同。

> [!NOTE]
>  如果使用 Common Data Service 且未安装 Dynamics 365 应用程序或第三方解决方案，则你的环境中不会有包含复杂服务器端逻辑的实体。

* 帐户
* 协议
* 协议预订日期
* 协议预订事件
* 协议预订产品
* 协议预订服务
* 协议预订服务任务
* 协议预订设置
* 协议发票日期
* 协议发票产品
* 协议发票设置
* 协议子状态
* 可预订资源
* 可预订资源预订
* 可预订资源预订标头
* 可预订资源类别
* 可预订资源类别分配
* 可预订资源特征
* 可预订资源组
* 预订警报
* 预订警报状态
* 预订状态
* 用例
* 特征
* 资格要求（已弃用）
* 竞争对手
* 联系人
* 客户资产
* 委派
* 费用
* 字段计算
* 字段服务价格列表项
* 筛选
* 关注
* 事件类型
* 事件类型产品
* 事件类型服务
* 事件类型服务任务
* 集成作业
* 集成作业详细信息
* 库存调整
* 库存调整产品
* 库存转移
* 发票
* 发票频率
* 发票行
* 发票行详细信息
* 日志
* 日志行
* 潜在客户
* 说明
* OData v4 数据源
* 商机
* 商机行
* 商机行详细信息
* 订单
* 订单发票产品
* 订单发票设置
* 订单行
* 付款
* 付款详细信息
* 发布配置
* 发布规则配置
* 邮政编码
* 价格列表
* 价格列表项
* 产品
* 项目
* 项目审批
* 项目合同行详细信息
* 项目合同行里程碑
* 项目合同行资源类别
* 项目合同行事务类别
* 项目参数
* 项目阶段
* 项目任务状态用户
* 项目团队成员注册
* 采购订单
* 采购订单帐单
* 采购订单产品
* 采购订单收据
* 采购订单收据产品
* 采购订单子状态
* 队列项
* 报价
* 报价预订事件
* 报价预订产品
* 报价预订服务
* 报价预订服务任务
* 报价预订设置
* 报价发票产品
* 报价发票设置
* 报价行
* 报价行详细信息
* 报价行里程碑
* 报价行资源类别
* 报价行事务类别
* 报价项目价格列表
* 评分模型
* 评分值
* 需求特征
* 需求资源类别
* 需求资源首选项
* 需求状态
* 资源请求
* 资源需求
* 资源需求详细信息
* RMA
* RMA 产品
* RMA 收据
* RMA 收据产品
* RMA 子状态
* 角色资格要求
* 角色价格
* RTV
* RTV 产品
* RTV 子状态
* 税务代码
* 税务代码详细信息
* 时间条目
* 时间组
* 时间组详细信息
* 休假请求
* 事务类别价格
* 用户
* 查看
* 墙面景观
* 仓库
* 工作订单
* 工作订单事件
* 工作订单产品
* 工作订单服务
* 工作订单服务任务
* 工作订单子状态
* 工作模板


## <a name="licensing"></a>许可
有关 PowerApps 和 Dynamics 365 许可证的详细信息，请参阅[许可概述](../../administrator/pricing-billing-skus.md)页面。

