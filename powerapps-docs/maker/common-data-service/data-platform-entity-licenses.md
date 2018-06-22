---
title: 实体的许可证要求| Microsoft Docs
description: 介绍 Common Data Service (CDS) for Apps 中实体的许可证要求。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/01/2018
ms.author: clwesene
ms.openlocfilehash: 716e1c2b7e670d8a54e1106cd557bb509323ba8d
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2018
ms.locfileid: "34167095"
---
# <a name="license-requirements-for-entities"></a>实体的许可证要求
应用创建者可使用 Common Data Service (CDS) for Apps 中提供的大部分实体（包括自定义实体和部分常见数据模型实体），为仅有 PowerApps 计划 1 或 Microsoft Flow 计划 1 许可证的用户创建应用和流。 某些情况下，实体包含复杂的业务逻辑，或与要求应用用户具有特定许可证的 Dynamics 365 产品相关联。 有关可用计划的详细信息，请参阅 [PowerApps 定价页](https://powerapps.microsoft.com/pricing)。

> [!NOTE]
> 使用这些实体的应用和流需要应用和流用户拥有正确的许可证&mdash;而不是应用和流的创建者或开发人员。

## <a name="entities-with-complex-business-logic"></a>具有复杂业务逻辑的实体
包含以下复杂服务器端逻辑的实体需要使用这些实体应用或流用户具有 PowerApps 计划 2 或 Microsoft Flow 计划 2 许可证：

* 代码插件（有关详细信息，请参阅[插件开发](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development)）
* 实时工作流（有关详细信息，请参阅[工作流流程](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)）

    > [!NOTE]
    >  只有那些转换为实时工作流的工作流才可视为实时的和同步的。 后台运行的工作流仍可与合适的 PowerApps 计划配合使用，并且不需要额外许可证。

若要了解是否向实体添加复杂业务逻辑，请检查环境中配置的插件程序集和工作流的列表。

## <a name="impacting-license-requirements-when-adding-complex-business-logic"></a>添加复杂业务逻辑时影响许可证要求
应用创建者可将代码插件和实时工作流添加到 CDS for Apps 的实体中，但执行此操作可能会更改已部署应用的用户的许可证要求。 应用创建者在向实体添加复杂业务逻辑时应谨慎认真，首先检查使用该实体的具体应用以及这些应用的用户是否具有正确的许可证。

## <a name="entities-restricted-to-dynamics-365-licenses"></a>限制为 Dynamics 365 许可证的实体
与 Dynamics 365 产品功能关联的某些实体要求应用用户在创建、更新或删除实体内记录时需要具有该产品相应的许可证。 有关受限实体的完整列表，请参阅[要求 Dynamics 365 许可证的受限实体](data-platform-restricted-entities.md)。

## <a name="licensing-example"></a>许可示例
Barb 和 Isaac 正在使用 CDS for Apps 在 PowerApps 中创建应用，用于存储数据。

Barb 正在创建两个画布应用：

* 应用 1 &ndash; 使用联系人实体以及存储相关信息的自定义实体
* 应用 2 &ndash; 使用联系人实体以及属于受限实体的事件实体

Isaac 正在创建两个模型驱动应用：

* 应用 3 &ndash; 使用联系人实体以及存储相关信息的自定义实体
* 应用 4 &ndash; 使用联系人实体以及属于受限实体的事件实体

Barb 和 Isaac 需要以下许可证：
* Barb 需要 PowerApps 计划 1 许可证才能使用 CDS for Apps 创建画布应用。 如果她需要创建数据库或创建自定义实体，则应具有 PowerApps 计划 2 许可证。

* Isaac 需要 PowerApps 计划 2 许可证来构建模型驱动应用。

应用用户需要以下许可证：
* 应用 1 用户仅需要 PowerApps 计划 1 或计划 2 许可证，因为该应用不包含任何具有复杂业务逻辑的实体或受限实体。

* 应用 2 用户需要 Dynamics 365 for Customer Service 企业版许可证（或 Dynamics 365 或 Dynamics 365 Customer Engagement 计划），因为该应用包含受限实体。

* 应用 3 用户需要 PowerApps 计划 2 许可证，因为这是模型驱动应用。

* 应用 4 用户需要 Dynamics 365 for Customer Service 企业版许可证（或 Dynamics 365 或 Dynamics 365 Customer Engagement 计划），因为该应用包含受限实体。

    Dynamics 365 for Customer Service 计划包括 PowerApps 计划 2 许可证，允许用户运行模型驱动应用。

现在，我们一起看看 Isaac 向 Barb 和 Isaac 在其应用中使用的自定义实体添加实时工作流之后会发生什么。

Barb 和 Isaac 需要以下许可证：
* Barb 仍然需要 PowerApps 计划 1 许可证才能使用 CDS for Apps 创建画布应用。

* Isaac 仍然需要 PowerApps 计划 2 许可证来构建模型驱动应用。

应用用户需要以下许可证：
* 应用 1 用户现在需要 PowerApps 计划 2 许可证，因为该应用包含具有实时工作流的实体。

* 应用 2 用户仍然需要 Dynamics 365 for Customer Service 企业版许可证（或 Dynamics 365 或 Dynamics 365 Customer Engagement 计划），因为该应用包含受限实体。 

* 应用 3 用户仍然需要 PowerApps 计划 2 许可证，因为这是模型驱动应用。

* 应用 4 用户仍然需要 Dynamics 365 for Customer Service 企业版许可证（或 Dynamics 365 或 Dynamics 365 Customer Engagement 计划），因为该应用包含受限实体。

    Dynamics 365 for Customer Service 计划包括 PowerApps 计划 2 许可证，允许用户运行模型驱动应用。

唯一受此更改影响的应用是应用 1，它之前需要 PowerApps 计划 1 许可证，但现在需要 PowerApps 计划 2 许可证，因为它包含具有复杂业务逻辑的实体。 

## <a name="licensing"></a>许可
有关 PowerApps 和 Dynamics 365 许可证的详细信息，请参阅[许可概述](../../administrator/pricing-billing-skus.md)。
