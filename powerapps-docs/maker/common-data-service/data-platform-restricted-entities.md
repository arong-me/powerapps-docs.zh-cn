---
title: 要求 Dynamics 365 许可证的受限实体 | Microsoft Docs
description: Common Data Service for Apps 中需要 Dynamics 365 许可证的受限实体列表。
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: cds
ms.date: 05/01/2018
ms.author: clwesene
ms.openlocfilehash: 508f58b48f2dd51bf25f23905cc3513db90ed1ce
ms.sourcegitcommit: 45fac73f04aa03b5796ae6833d777f4757e67945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>要求 Dynamics 365 许可证的受限实体
应用创建者可使用 Common Data Service (CDS) for Apps 提供的大部分实体来为仅拥有 PowerApps 计划 1 许可证的用户创建应用和流。 但是，某些实体包含需要应用用户具有 PowerApps 计划 2 或 Microsoft Flow 计划 2 许可证的复杂业务逻辑（有关详细信息，请参阅[实体许可证要求](data-platform-entity-licenses.md)）。 即使是较小的与 Dynamics 365 产品相关联的实体集，如果要在实体内创建、更新或删除记录，也要求画布和模型驱动应用用户具有对应 Dynamics 365 产品的许可证。 这些被称为受限实体。

实体受限于 Dynamics 365 许可证，可能有以下几种原因：

* 实体用于存储和维护产品特定的配置数据，这些数据通常不在应用程序之外使用。
* 这些实体在 Dynamics 365 产品中使用时，通常随附以特定方式创建和维护数据的高级逻辑。

如果某个应用和流仅从实体读取信息，则不需要 Dynamics 365 许可证，只需要适合的 PowerApps 或 Microsoft Flow 许可证。 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>用于创建、更新和删除操作的受限实体
下表为在实体中创建、更新或删除存储的数据的 PowerApps 和 Microsoft Flow 应用用户列出了受限实体和相关的 Dynamics 365 许可要求。 

|实体  |逻辑名称  |必需的许可证  |
|---------|---------|---------|
实际 |msdyn_actual |Dynamics 365 for Field Service <br> 或 Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
业务流程协议 |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
预订日记 | msdyn_bookingjournal|Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
预订安装程序元数据 | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> 或 Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
预订时间戳 | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
工作单业务流程用例 |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
配置 |msdyn_configuration |Dynamics 365 for Field Service <br> 或 Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
授权 | 授权 | 适用于客户服务的 Dynamics 365，企业版 <br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
估价行|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
估价|msdyn_estimate |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
事实|msdyn_fact |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
现场服务设置 |msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
现场服务系统作业 |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
目标 | 目标 | Dynamics 365 for Sales Professional， <br>或 Dynamics 365 for Sales，企业版 <br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
事件 | 事件 | 适用于客户服务的 Dynamics 365，企业版 <br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
库存日志 |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
发票流程 |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
差旅 | 差旅 | Dynamics 365 for Marketing <br> 或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
知识文章 | knowledgearticle | 适用于客户服务的 Dynamics 365，企业版 <br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
部门 |msdyn_organizationalunit |Dynamics 365 for Field Service <br> 或 Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
产品库存 |msdyn_productinventory |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
项目参数|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
项目阶段| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
项目任务依赖|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
项目任务|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
项目团队成员|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
采购单业务流程 | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
资源分配详细信息（已弃用）|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
资源分配|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
资源限制（已弃用） |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
路由规则设置 | routingrule | 适用于客户服务的 Dynamics 365，企业版 <br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
班次表设置 |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> 或 Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
日程安排参数 |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> 或 Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
SLA| sla | 适用于客户服务的 Dynamics 365，企业版 <br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
系统用户调度员设置 |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> 或 Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
事务连接|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
事务源|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
事务类型|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
唯一编号|msdyn_uniquenumber |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
工作单业务流程 |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划
工作单详细信息生成队列（已弃用）|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>或 Dynamics 365 客户参与计划 <br> 或 Dynamics 365 计划

## <a name="licensing"></a>许可
有关 PowerApps 和 Dynamics 365 许可证的详细信息，请参阅[许可概述](../../administrator/pricing-billing-skus.md)页。

