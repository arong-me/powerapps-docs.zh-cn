---
title: 创建解决方案 | MicrosoftDocs
description: 了解如何创建解决方案
ms.custom: ''
ms.date: 03/20/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: e21a4876-08b4-417a-a644-c577a27c5cf1
caps.latest.revision: 12
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 59c041d7fe74e1a1dbbce9f1516057d324447478
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162183"
---
# <a name="create-a-solution"></a>创建解决方案

若要仅查找和使用自定义的组件，请创建一个解决方案，并在其中完成所有自定义。 然后，在添加、编辑和创建组件时，请始终记住在自定义解决方案的上下文中进行工作。 这样，您就可以轻松导出解决方案，以将其导入到其他环境或作为备份。   
  
有关解决方案概念的详细信息，请参阅[使用解决方案](solutions-overview.md)。  
  
1.  登录 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后从左侧导航中选择**解决方案**。 
  
2.  选择**新建解决方案**，然后填写解决方案的必填字段。
  
    |字段|说明|  
    |-----------|-----------------|  
    |**显示名称**|在解决方案列表中显示的名称。 以后可以更改此属性。|  
    |**姓名**|解决方案的唯一名称。 这是使用您在“显示名称”字段中输入的值生成的。 可以在保存解决方案之前编辑此值，但在保存了解决方案之后，将无法对其进行更改。|  
    |**发布者**|可以选择默认发布商，也可以创建一个新发布商。 建议您为组织创建要在其中使用解决方案的环境中一致使用的发布商。 详细信息：[解决方案发布商概述](change-solution-publisher-prefix.md) |  
    |**版本**|输入您的解决方案的版本号。 此数据仅在导出解决方案时有重要意义。 在导出解决方案时，版本号将包括在文件名中。|  
  
3.  选择**保存**。  
  
 在保存了解决方案之后，可能需要在非必填字段中添加信息。 这些步骤是可选的。 使用**说明**字段描述解决方案，并选择 HTML Web 资源作为解决方案的**配置页** 。 配置页通常由分发解决方案的 ISV 使用。 完成此设置后，一个新的**配置**节点会出现在**信息**节点下面以显示此 Web 资源。 开发人员将使用该页面来加入允许您设置配置数据或启动其解决方案的指令或控件。  
  
<a name="BKMK_AddSolutionComponents"></a>   

## <a name="add-solution-components"></a>添加解决方案组件  
 在创建了解决方案之后，其中不会包含任何解决方案组件。 您可以创建新的解决方案组件，也可以使用列表菜单中的**添加现有**按钮添加默认解决方案中的任何解决方案组件。  
  
 执行此操作时，可能会出现**缺少必需组件** 对话框。  
   
 ![添加必需组件对话](media/crm-itpro-cust-addrequiredcomponents.PNG "添加必需组件对话")  
  
 此对话框提醒您该解决方案组件依赖于其他解决方案组件。 如果选择**否，不包含必需组件** ，则解决方案可能会在您将其导入到所有这些必需组件都不存在的其他组织中时可能会失败。 如果解决方案导入成功，则另一解决方案中的行为可能并不与原始组织完全相同，因为组件的配置方式不同于源解决方案中的组件。  
  
选择实体组件时，建议您使用解决方案细分，以便在分发解决方案更新时仅包括新的或更新的实体组件。 利用解决方案细分，您可以在包含所选实体资产（例如实体字段、窗体和视图）的解决方案中工作，而不是包含所有资产的整个实体。 详细信息：[使用细分解决方案](use-segmented-solutions-patches-simplify-updates.md)
  
 如果您不打算导出解决方案，或者只打算将其导出为非托管解决方案并将其重新导入回同一组织，则不必包括必需组件。 如果曾导出解决方案，则将看到另一个警告，指示缺少某些必需组件。 如果只是要将该解决方案导入回同一组织，可可忽略此警告。 不使用第三方编辑工具编辑应用程序导航或功能区的步骤会期望您将解决方案重新导出到同一组织。  

<!-- >
> [!IMPORTANT]
>  If you plan to include appointments in solutions, we strongly recommend that you don’t include only appointments and only recurring appointments in separate solutions. If you install and uninstall separate solutions with different appointment types, you’ll encounter a SQL Server error and you’ll have to re-create the appointments.  -->

## <a name="publish-changes"></a>发布更改 

 有些对用户界面进行更改自定义项需要先发布，然后用户才能在应用程序中使用它们。 
 
### <a name="publish-your-customizations"></a>发布自定义项

1.  在左侧导航中选择**解决方案**。

2.  选择要发布以打开的解决方案。

3.  在命令列表中，选择**发布所有自定义项**。  

![发布所有自定义项](media/publish-all-customizations.PNG "发布所有自定义项")  
  
> [!IMPORTANT]
>  准备自定义项可能需要花费一些时间。 如果看到一条消息说明浏览器页面不响应，请等待页面响应，请勿将其关闭。  

### <a name="see-also"></a>另请参阅
 [使用解决方案](use-solution-explorer.md)
