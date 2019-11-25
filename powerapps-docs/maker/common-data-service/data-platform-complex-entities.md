---
title: 需要 PowerApps 计划 2 许可证的复杂实体 | Microsoft Docs
description: 需要 PowerApps 计划 2 许可证的 Common Data Service 中的复杂实体列表。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 09/26/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f5ec7419ea7369a57308e046ae820557303f0d15
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706623"
---
# <a name="complex-entities-and-licensing"></a>复杂的实体和许可

> [!IMPORTANT]
> 本主题已过期，将很快更新以反映自 2019 年 10 月 1 日起适用的最新许可变化。 有关实体许可要求的最新信息，请参阅 [PowerApps 许可指南](https://go.microsoft.com/fwlink/?linkid=2085130)。

包含以下复杂服务器端逻辑的实体需要使用这些实体的应用程序或流用户具有 PowerApps 计划 2 或 Microsoft Flow 计划 2 许可证：

* 代码插件。详细信息：[插件开发](/powerapps/developer/common-data-service/plug-ins)
* 实时工作流。 详细信息：[工作流过程](/flow/workflow-processes)

    > [!IMPORTANT]
    >  只转换为实时工作流的工作流被视为实时和同步。 在后台运行的工作流仍可以用于相应的 PowerApps 计划且不需要额外许可证。

若要了解您是否已向实体添加了复杂的业务逻辑，请查看在您的环境中配置的插件程序集和工作流的列表。

## <a name="complex-entities-installed-with-dynamics-365-apps"></a>随 Dynamics 365 应用安装的复杂实体
下表列出了包含现成的复杂服务器端逻辑的实体，这些实体是在 Dynamics 365 中安装模型驱动应用程序（如 Dynamics 365 Sales 和 Dynamics 365 Customer Service）的一部分。 此列表用作指南。 根据在您的环境中安装的 Dynamics 365 应用和版本，复杂实体的列表可能不同。

> [!NOTE]
>  如果您使用的是 Common Data Service 且未安装 Dynamics 365 应用程序或第三方解决方案，您的环境将没有包含复杂服务器端逻辑的实体。

* 客户
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
* 可预订的资源
* 可预订资源的预订
* 可预订资源的预订标题
* 可预订资源的类别
* 可预订资源的类别 Assn
* 可预订资源的特征
* 可预订资源组
* 预订警报
* 预订警报状态
* 预订状态
* 特征
* 资格要求（已弃用）
* 竞争对手
* 联系人
* 客户资产
* 委派
* 费用
* 字段计算
* Field Service 价目表项
* Filter
* 追随
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
* 发票明细详细信息
* 日记
* 日记帐行
* 潜在顾客
* 注释
* OData v4 数据源
* 商机
* 商机明细
* 商机明细详细信息
* 订单
* 订单发票产品
* 订单发票设置
* 订单明细
* 付款
* 付款详细信息
* 公告配置
* 公告规则配置
* 邮政编码
* 价目表
* 价目表项
* 产品
* 项目
* 项目审批
* 项目合同子项详细信息
* 项目合同子项里程碑
* 项目合同子项资源类别
* 项目合同子项交易类别
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
* 报价单
* 报价单预订事件
* 报价单预订产品
* 报价单预订服务
* 报价单预订服务任务
* 报价单预订设置
* 报价单发票产品
* 报价单发票设置
* 报价单明细
* 报价单行明细
* 报价单明细里程碑
* 报价单明细资源类别
* 报价单明细交易类别
* 报价单项目价目表
* 评分模型
* 评分值
* 要求特征
* 要求资源类别
* 要求资源首选项
* 要求状态
* 资源请求
* 资源要求
* 资源要求详细信息
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
* 税码
* 税码详细信息
* 时间条目
* 时间组
* 时间组详细信息
* 休息时间请求
* 交易类别价格
* 用户
* 视图
* 留言板视图
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

