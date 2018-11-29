---
title: 实体的许可证要求 | Microsoft Docs
description: 阐述面向应用程序的 Common Data Service (CDS) 内实体的许可证要求。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/01/2018
ms.author: clwesene
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="license-requirements-for-entities"></a>实体的许可证要求
应用程序制造者可以使用面向应用程序的 Common Data Service (CDS) 内提供的多数实体（包括自定义实体或属于通用数据模型一部分的实体）来为有 PowerApps 计划 1 或 Microsoft Flow 计划 1 许可证的用户创建应用程序和流。 在有些情况下，实体包含复杂的业务逻辑或绑定到需要应用程序用户具有特定许可证的 Dynamics 365 应用程序。 


|实体    |说明    |要求    |
|---------|---------|---------|
|具有复杂业务逻辑的实体   | 这些是使用复杂的服务器端业务逻辑的实体。 例如，使用实时工作流或代码插件的任何实体。       |  [PowerApps 计划 2](https://powerapps.microsoft.com/pricing/) 或者 [Flow 计划 2](https://flow.microsoft.com/pricing/)        |
|受限实体  |  这些不是面向应用程序的 Common Data Service 的标准实体，但包括在 Dynamics 365 customer engagement 应用程序或第三方解决方案中。 例如，知识文章、目标和权利实体。     |  [Dynamics 365 计划](https://dynamics.microsoft.com/pricing/)      | 


> [!NOTE]
> 使用这些实体的应用程序和流需要应用程序和流用户获得适当许可-不是应用程序或流的制造者或开发人员。

## <a name="entities-with-complex-business-logic"></a>具有复杂业务逻辑的实体
包含以下复杂服务器端逻辑的实体需要使用这些实体的应用程序或流用户具有 PowerApps 计划 2 或 Microsoft Flow 计划 2 许可证：

* 代码插件（有关详细信息，请参阅[插件开发](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development)）
* 实时工作流（有关详细信息，请参阅[工作流过程](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)）

    > [!NOTE]
    >  只转换为实时工作流的工作流被视为实时和同步。 在后台运行的工作流仍可以用于相应的 PowerApps 计划且不需要额外许可证。

若要了解您是否已向实体添加了复杂的业务逻辑，请查看在您的环境中配置的插件程序集和工作流的列表。 有关在安装 Dynamics 365 应用程序之后可能包含服务器端逻辑的实体列表，请参阅[需要 PowerApps 计划 2 许可证的复杂实体](data-platform-complex-entities.md)  

### <a name="impacting-license-requirements-when-adding-complex-business-logic"></a>当添加复杂的业务逻辑时影响许可证要求
应用程序制造者可以向面向应用程序的 CDS 内的实体添加代码插件和实时工作流，但这样做可能会更改已经部署的应用程序的用户的许可证要求。 应用程序制造者在向实体添加复杂的业务逻辑时应当谨慎，应先检查哪些应用程序使用该实体，以及这些应用程序的用户是否具有适当的许可证。

## <a name="restricted-entities"></a>受限实体
绑定到 Dynamics 365 应用程序的功能的某些实体需要应用程序用户有该应用程序的相应许可证（如果他们希望创建、更新或删除实体内的记录）。 有关受限实体的完整列表，请参阅[需要 Dynamics 365 许可证的受限实体](data-platform-restricted-entities.md)。

## <a name="licensing-examples"></a>许可示例
Barb 和 Isaac 在使用面向应用程序的 CDS 存储数据的 PowerApps 中创建应用程序。

Barb 创建两个画布应用程序：

* 应用程序 1 &ndash; 使用约会实体以及存储相关信息的自定义实体。
* 应用程序 2 &ndash; 使用约会实体以及事件实体，其是受限实体

Isaac 创建两个模型驱动应用程序：

* 应用程序 3 &ndash; 使用约会实体以及存储相关信息的自定义实体。
* 应用程序 4 &ndash; 使用约会实体以及事件实体，其是受限实体

Barb 和 Isaac 需要以下许可证：
* Barb 需要 PowerApps 计划 1 许可证来使用面向应用程序的 CDS 创建画布应用程序。 如果她需要创建数据库或创建自定义实体，她将需要 PowerApps 计划 2 许可证。

* Isaac 需要 PowerApps 计划 2 许可证来生成模型驱动应用程序。

应用程序用户需要以下许可证：
* 应用程序 1 的用户只需要 PowerApps 计划 1 或计划 2 许可证，因为该应用程序不包含具有复杂业务逻辑的任何实体或受限实体。

* 应用程序 2 的用户需要 Dynamics 365 for Customer Service Enterprise edition 许可证（或 Dynamics 365 或 Dynamics 365 Customer Engagement 计划），因为该应用程序包含受限实体。

* 应用程序 3 的用户需要 PowerApps 计划 2 许可证，因为它是模型驱动应用程序。

* 应用程序 4 的用户需要 Dynamics 365 for Customer Service Enterprise edition 许可证（或 Dynamics 365 或 Dynamics 365 Customer Engagement 计划），因为该应用程序包含受限实体。

    Dynamics 365 for Customer Service 计划包含 PowerApps 计划 2 许可证，让用户可以运行模型驱动应用程序。

现在，让我们看看当 Isaac 向 Barb 和 Isaac 都在其应用程序中使用的自定义实体添加实时工作流时会发生什么。

Barb 和 Isaac 需要以下许可证：
* Barb 仍需要 PowerApps 计划 1 许可证来使用面向应用程序的 CDS 创建画布应用程序。

* Isaac 仍需要 PowerApps 计划 2 许可证来生成模型驱动应用程序。

应用程序用户需要以下许可证：
* 应用程序 1 的用户现在需要 PowerApps 计划 2 许可证，因为该应用程序包含具有实时工作流的实体。

* 应用程序 2 的用户仍需要 Dynamics 365 for Customer Service Enterprise edition 许可证（或 Dynamics 365 或 Dynamics 365 Customer Engagement 计划），因为该应用程序包含受限实体。 

* 应用程序 3 的用户仍需要 PowerApps 计划 2 许可证，因为它是模型驱动应用程序。

* 应用程序 4 的用户仍需要 Dynamics 365 for Customer Service Enterprise edition 许可证（或 Dynamics 365 或 Dynamics 365 Customer Engagement 计划），因为该应用程序包含受限实体。

    Dynamics 365 for Customer Service 计划包含 PowerApps 计划 2 许可证，让用户可以运行模型驱动应用程序。

受此更改影响的唯一应用程序是应用程序 1，其之前需要 PowerApps 计划 1 许可证，但现在需要 PowerApps 计划 2 许可证，因为它包含具有复杂业务逻辑的实体。 

## <a name="more-about-licensing"></a>有关许可的更多信息
有关 PowerApps 和 Dynamics 365 许可证的详细信息，请参阅[许可概述](../../administrator/pricing-billing-skus.md)。
