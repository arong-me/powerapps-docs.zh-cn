---
title: 在 PowerApps 中使用解决方案 | MicrosoftDocs
description: 了解如何使用解决方案创建或自定义应用
ms.custom: ''
ms.date: 10/28/2019
ms.reviewer: tapanm
ms.service: powerapps
ms.topic: article
author: caburk
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: caburk
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 57df12285848d67a8cd85016aec0bbb033fef89a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703147"
---
# <a name="use-solutions-in-powerapps"></a>在 PowerApps 中使用解决方案

 在 PowerApps 内，您可以通过选择左侧导航中的**解决方案**查看解决方案列表。 然后可以选择解决方案来查看其所有组件。 
 
> [!div class="mx-imgBorder"]  
> ![具有所有组件的演示解决方案](media/solution-all-items-list.PNG "具有所有组件的演示解决方案")  
 
> [!NOTE]
>  解决方案体验仅在线可用，且仅可用于环境版本 9.1.0.267 及以后版本。 若要检查您的版本，请转到 [PowerApps 管理中心](https://admin.powerapps.com/)> **环境** > 选择您的环境 > **详细信息**选项卡。对于早期版本环境，选择解决方案将在经典体验中打开它。  
 
 您可以通过在项目中滚动来滚动浏览解决方案中的所有组件。 如果列表中有超过 100 个项目，您可以选择**加载另外 100 个项目**来查看更多项目。 
 
> [!div class="mx-imgBorder"]  
> ![加载更多组件](media/load-more.PNG "加载更多组件")  

 ## <a name="search-and-filter-in-a-solution"></a>在解决方案中搜索和筛选
 
 您还可以按名称搜索特定组件。 
 
> [!div class="mx-imgBorder"]  
> ![搜索组件](media/solution-search-box.png "搜索组件")  
 
 或者按组件类型在列表中筛选所有项目。
  
> [!div class="mx-imgBorder"]  
> ![按类型筛选组件](media/solution-filter.PNG "按类型筛选组件")  
 
 ## <a name="contextual-commands"></a>上下文命令
 
 在您选择每个组件时，命令栏中的可用操作会发生变化，具体取决于选择的组件的类型，以及解决方案是默认还是托管解决方案。 
 
> [!div class="mx-imgBorder"]  
> ![组件特定命令](media/component-commands.png "组件特定命令")  
 
 如果未选择任何组件，命令栏将显示已应用到解决方案本身的操作。 
 
> [!div class="mx-imgBorder"]  
> ![解决方案特定命令](media/solution-commands.PNG "解决方案特定命令")  
 
 ## <a name="create-components-in-a-solution"></a>在解决方案中创建组件
 使用非托管或默认的解决方案，您可以使用**新建**命令来创建不同类型的组件。 这会将您带入不同的创建体验，具体取决于您选择的组件类型。 完成创建组件后，组件将被添加到解决方案中。 
 
> [!div class="mx-imgBorder"]  
> ![在解决方案中创建新组件](media/solution-new-component.PNG "在解决方案中创建新组件")  
 
 ## <a name="add-an-existing-component-to-a-solution"></a>向解决方案添加现有组件
 
 对于属于非托管解决方案但不是默认的解决方案，可以使用**添加现有**命令导入尚不在解决方案中的组件。  
 
> [!div class="mx-imgBorder"]  
> ![向解决方案添加现有组件](media/solution-add-existing-component.PNG "向解决方案添加现有组件")  
  
 对于托管解决方案，仅某些命令可用，您将看到一条消息，如下所示。 您需要将其添加到另一个已创建的非托管解决方案，才能自定义组件。 组件可能不可自定义。 详细信息：[托管属性](solutions-overview.md#managed-properties)

> [!div class="mx-imgBorder"]  
> ![托管解决方案](media/managed-solution.PNG "托管解决方案")  

 您需要执行的许多自定义将涉及到实体。 您可以使用**实体**筛选器以显示可进行某种程度的自定义的当前解决方案中的所有实体的列表。 在钻取实体后，您可以查看组成实体的组件，如以下屏幕截图中的客户实体所示。 
   
> [!div class="mx-imgBorder"]  
> ![显示展开客户实体的演示解决方案](media/solution-entity-account.png "显示展开客户实体的演示解决方案")  

## <a name="classic-solution-explorer"></a>经典解决方案资源管理器

在 PowerApps 中，您可以通过选择左侧导航窗格中的**解决方案**，然后选择命令栏中的**切换到经典**，来查看经典方案资源管理器。 经典解决方案资源管理器是之前通过 PowerApps 中的**设置 > 高级自定义**区域提供的。 

## <a name="known-limitations"></a>了解限制

以下限制适用于解决方案中画布应用、流和自定义连接器的使用。 

- 区域应用触发的流在解决方案中不可用。
- 如果画布应用在托管解决方案中打包，它将无法在目标环境中编辑和重新发布。 如果应用需要在目标环境中进行编辑，请使用非托管解决方案。 
- 连接需要身份验证和同意，这需要交互式用户会话，因此无法通过解决方案进行传输。 导入解决方案后，请播放应用以验证连接。 您也可以在导入解决方案之前在目标环境中创建连接。 
-   作为共同负责人共享到 Azure Active Directory (AAD) 安全组的画布应用不能添加到解决方案中。 取消共享应用，然后再将其添加到解决方案中。
-   区域应用不显示在经典解决方案资源管理器中。 使用现代化体验。
-   画布应用访问（CRUD 和安全性）在 PowerApps 中完全托管，而不是在 Common Data Service 数据库中。
- 画布应用和流不支持数据库操作，例如备份、还原和复制。 这些操作可能会损坏画布应用和流。
- 删除托管解决方案不会回滚到其他画布应用版本。 而是删除应用的所有版本。
- 导入包含流的解决方案将不会自动创建或关联所需的连接。 必须编辑流以修复连接。
  - 如果使用托管解决方案，则会在非托管层创建可用自定义项。 因此，流的后续解决方案更新将不会得到反映。 
- “团队流”列表中将不显示基于解决方案创建的流。 必须通过解决方案访问它们。 
- 按钮触发的流在解决方案中不可用。
- 从 Microsoft 365 应用程序（如 Excel）触发的流在解决方案中不可用。
- 连接到 SharePoint 的流在解决方案中不可用。
- 解决方案中的流不支持委派身份验证。 例如，流访问权限不会基于具有对流从其创建的 SharePoint 列表的访问权限而自动授予。
- 在解决方案外部创建的自定义连接器目前无法添加到解决方案中。


 有关自定义解决方案中的单个组件的详细信息，请参阅以下主题：  
  
-   有关实体、实体关系、字段和消息自定义，请参阅[元数据](create-edit-metadata.md)。  
  
-   有关实体窗体，请参阅[窗体](../model-driven-apps/create-design-forms.md)。  
  
-   有关进程，请参阅[流程](../model-driven-apps/guide-staff-through-common-tasks-processes.md)。  
  
-   有关业务规则，请参阅[业务规则](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)。  
