---
title: 需要 Dynamics 365 许可证的受限实体 | Microsoft Docs
description: 需要 Dynamics 365 许可证的 Common Data Service 中的受限实体列表。
author: KumarVivek
ms.service: powerapps
ms.topic: reference
ms.date: 04/15/2020
ms.author: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9656f9db1a00fe82a2788b20513014bc49a09d4f
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "3264916"
---
# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>需要 Dynamics 365 许可证的受限实体

> [!IMPORTANT]
> 本主题已过期，将很快更新以反映自 2019 年 10 月 1 日起适用的最新许可变化。 有关实体许可要求的最新信息，请参阅 [Power Apps 许可指南](https://go.microsoft.com/fwlink/p/?linkid=2085130)。

应用开发者可以使用 Common Data Service 内提供的大多数实体来为只有 Power Apps 计划 1 许可证的用户创建应用和流。 不过，有些实体包含需要应用用户有 Power Apps 计划 2 或 Power Automate 计划 2 许可证的复杂业务逻辑（有关详细信息，请参阅[实体的许可证要求](data-platform-entity-licenses.md)）。 如果需要创建、更新或删除实体内的记录，即使更小的绑定到 Dynamics 365 产品的一组实体也需要画布和模型驱动应用程序用户具有相应 Dynamics 365 产品的许可证。 这些实体称为*受限*实体。

实体可能由于下列原因被限制，需要有 Dynamics 365 许可证：

* 此实体用于存储和维护通常不在应用程序之外使用的产品特定配置数据。
* 实体由高级逻辑附带，高级逻辑在用于 Dynamics 365 产品中时以特定方式创建和维护数据。

如果应用或流只读取实体的信息，不需要 Dynamics 365 许可证，只需要适当的 Power Apps 或 Power Automate 许可证。 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>用于创建、更新和删除操作的受限实体
下表列出了受限实体以及创建、更新或删除实体内所存储数据的 Power Apps 和 Power Automate 应用用户的关联的 Dynamics 365 许可要求。 

|实体  |逻辑名称  |必需许可证  |
|---------|---------|---------|
实际值 |msdyn_actual |Dynamics 365 for Field Service <br> **或** Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
协议业务流程 |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
预订日记帐 | msdyn_bookingjournal|Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
预订设置元数据 | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> **或** Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
预订时间戳 | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
案例 | 事件 | Dynamics 365 for Customer Service Enterprise edition <br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
案例到工作订单业务流程 |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
配置 |msdyn_configuration |Dynamics 365 for Field Service <br> **或** Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
权利 | 权利 | Dynamics 365 for Customer Service Enterprise edition <br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
估算明细|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
估算|msdyn_estimate |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
事实|msdyn_fact |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
Field Service 设置 |msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
Field Service 系统作业 |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
目标 | 目标 | Dynamics 365 for Sales Professional， <br>**或** Dynamics 365 for Sales, Enterprise edition， <br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
库存日记帐 |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
发票流程 |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
旅程 | 旅程 | Dynamics 365 for Marketing <br> **或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
知识文章 | knowledgearticle | Dynamics 365 for Customer Service Enterprise edition <br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
部门 |msdyn_organizationalunit |Dynamics 365 for Field Service <br> **或** Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
产品库存 |msdyn_productinventory |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
项目参数|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
项目阶段| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
项目任务依赖关系|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
项目任务|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
项目团队成员|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
采购订单业务流程 | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
资源分派详细信息（已弃用）|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
资源分派|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
资源限制（已弃用） |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
传递规则集 | routingrule | Dynamics 365 for Customer Service Enterprise edition <br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
日程安排板设置 |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> **或** Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
日程安排参数 |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> **或** Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
SLA| sla | Dynamics 365 for Customer Service Enterprise edition <br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
系统用户计划程序设置 |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> **或** Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
交易连接|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
交易起源|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
交易类型|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
唯一编号|msdyn_uniquenumber |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
工作订单业务流程 |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划
工作订单详细信息生成队列（已弃用）|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>**或** Dynamics 365 Customer Engagement 计划 <br> **或** Dynamics 365 计划

## <a name="licensing"></a>许可
有关 Power Apps 和 Dynamics 365 许可证的详细信息，请参阅[许可概述](../../administrator/pricing-billing-skus.md)页面。

