---
title: 更改解决方案发布商前缀 | MicrosoftDocs
ms.custom: ''
ms.date: 05/11/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: ece684h8-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="change-the-solution-publisher-prefix"></a>更改解决方案发布商前缀

您所做的每个自定义项都是解决方案的一部分。 每个解决方案都有有一个发布商。 默认情况下，您在 PowerApps 内使用的解决方案将是与 **Common Data Service 默认发布商**关联的 **Common Data Services 默认解决方案**。

将为发布商随机分配默认自定义项前缀，例如，可能是 `cr8a3`。 这意味着为您的组织创建的元数据的每个新项目的名称都会将此前缀附加到用于唯一标识项目的名称前面。 如果您创建名为 **Animal** 的新实体，Common Data Service 使用的唯一名称将是 `cr8a3_animal`。 所有新字段（属性）、关系或选项集选项同样如此。

除非您分发解决方案以便它可以与为其他解决方案发布商创建的元数据项目一同安装，自定义项前缀是什么确实不重要。 使用您的应用程序的多数用户都不会看到它。 但会向开发人员以及执行生成报表等任务的其他技术人员公开。 它提供了一种了解哪些解决方案添加到项目的快速方法。

为此，很多用户喜欢更改解决方案发布商前缀以使它更有意义，特别是在查看元数据项目（包括从其他解决方案导入的项目）时。 

> [!NOTE]
> 如果更改解决方案发布商前缀，您应在创建新元数据项目前更改。 您不能更改元数据项目的名称。
> 在更改自定义项前缀值时，确保用 Tab 键跳转到下一个字段。 **选项值前缀** 将根据自定义前缀自动生成一个编号。 在将选项添加到选项集时将使用此编号，并提供一个指示符，指示使用了那个解决方案来添加选项。 

## <a name="change-the-solution-publisher-prefix-for-the-common-data-service-default-publisher"></a>更改 Common Data Service 默认发布商的解决方案发布商前缀  

 1. 在 PowerApps 门户中，选择左下角的**模型驱动**。
 2. 单击左侧导航区域的**高级**打开 **Common Data Services 默认解决方案**
 3. 在解决方案资源管理器中，选择左侧导航的**信息**区域。
 4. 单击**发布商**链接打开 **Common Data Service 默认发布商**窗体。
 5. 将**前缀**字段值编辑为所需的自定义项前缀。
 6. 单击**保存并关闭**。
  
## <a name="change-the-solution-publisher-prefix-for-any-publisher"></a>更改任意发布商的解决方案发布商前缀

分发其解决方案的用户通常在其创建的解决方案内工作，而不是 **Common Data Services 默认解决方案**。 通常在创建解决方案时设置自定义项前缀。 您可以通过执行以下步骤来更改您使用的其他非托管解决方案的自定义项前缀： 

 1. 在 PowerApps 门户中，选择左下角的**模型驱动**。
 2. 单击左侧导航区域的**高级**打开 **Common Data Services 默认解决方案**
 3. 编辑页面的 URL，将 `dynamics.com` 后面的部分全部删除并重新加载页面。
 4. 导航到**设置** > **自定义** > **自定义**。 
 5. 单击**发布商**。 现在您可以看到可用发布商的列表。
 6. 单击您要编辑的发布商以打开发布商窗体。
 7. 将**前缀**字段值编辑为所需的自定义项前缀。
 6. 单击**保存并关闭**。
  
