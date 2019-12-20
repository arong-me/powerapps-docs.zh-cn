---
title: 使用解决方案资源管理器为 Common Data Service 创建和编辑全局选项集 | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 060d749fe3f8c7f3d2e0870b99a836571c29bd86
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865903"
---
# <a name="create-and-edit-global-option-sets-for-common-data-service-using-solution-explorer"></a>使用解决方案资源管理器为 Common Data Service 创建和编辑全局选项集

解决方案资源管理器为创建和编辑 Common Data Service 的全局选项集提供一种方法。

[Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 <br />详细信息： 
- [创建和编辑 Common Data Service 的全局选项集](create-edit-global-option-sets.md)
- [创建选项集](custom-picklists.md)

## <a name="open-solution-explorer"></a>打开解决方案资源管理器

您创建的任何全局选项集的名称中都包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义项前缀，请确保您使用的非托管解决方案中的自定义项前缀是您希望此全局选项集具有的前缀。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-global-option-sets"></a>查看全局选项集

打开解决方案资源管理器后，在**组件**下选择**选项集**。

![查看全局选项集](media/view-global-option-sets-solution-explorer.png)

> [!NOTE]
> 有些系统全局选项集不可自定义。 这些选项可能随更新或新版本更改，因此，除非您确定您的要求符合 Common Data Service 使用这些值的方式。

## <a name="create-a-global-option-set"></a>创建全局选项集

> [!NOTE]
> 在您将全局选项集用于自定义字段内之前无需创建它。 在创建新选项集字段时，您可以选择创建新全局选项集或使用现有的选项集。 请参阅[选项集字段选项](create-edit-field-solution-explorer.md#option-set-field-options)

在查看全局选项集时，单击**新建**打开定义全局选项集的窗体。

![创建全局选项集](media/create-global-option-set-solution-explorer.png)

键入将向具有系统管理员或定制员角色的用户显示的**显示名称**，他们将在定义使用此全局选项集的新字段时选择此选项集。 此名称将不向使用您的应用程序的用户显示。

**名称**字段值将根据您输入的**显示名称**为您生成。 它将在您使用的解决方案的上下文中包含解决方案发布商的自定义项前缀。 您可以在保存前更改**名称**字段值的生成的部分。

为全局选项集键入**描述**。 

> [!TIP]
> 使用**描述**说明此全局选项集的用途。 此值对应用程序的用户不可见，而是向具有系统管理员或定制员角色可能需要了解为何创建此特定全局选项集的其他用户显示。

### <a name="configure-options"></a>配置选项

[!INCLUDE [cc_configure-option-set-options-solution-explorer](../../includes/cc_configure-option-set-options-solution-explorer.md)]

## <a name="edit-a-global-option-set"></a>编辑全局选项集

在查看全局选项集时，选择您要编辑的选项集来打开面板以对选项集进行编辑。

除了更改分配给选项的**名称**字段值或数字**值**，您可以在创建全局选项集时进行可以进行的任何更改。

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-global-option-set"></a>删除全局选项集

若要删除全局选项集，在查看列表时选择 ![删除命令](media/delete.gif) 命令栏中的命令。

> [!IMPORTANT]
> 如果全局选项集已被字段使用，您将无法删除它直到该字段被删除。
  
### <a name="see-also"></a>另请参阅
 
[创建和编辑 Common Data Service 的全局选项集](create-edit-global-option-sets.md)<br />
[创建选项集](custom-picklists.md)<br />
[创建和编辑字段](create-edit-fields.md)<br />
[开发人员文档：自定义全局选项集](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)
