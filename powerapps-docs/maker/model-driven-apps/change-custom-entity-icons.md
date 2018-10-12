---
title: 在 PowerApps 中更改模型驱动应用自定义实体图标 | Microsoft Docs
definition: Learn how to change the icon for a custom entity
ms.custom: ''
ms.date: 05/17/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 477f9792-8207-49ef-8968-45274b5355a8
caps.latest.revision: 19
ms.author: matp
manager: kvivek
tags:
- Links to topic not migrated
ms.openlocfilehash: c625ac14905e49879eb6dc93eff706a7dab18433
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669297"
---
# <a name="change-model-driven-app-custom-entity-icons"></a>更改模型驱动应用自定义实体图标 

在创建自定义实体时，系统自动向其分配一个默认图标。 默认情况下，所有自定义实体的图标都是一样的。 使用自定义图标可以区分自定义实体的外观。 不能修改分配给系统实体的图标。  
  
 可以为每个自定义实体上传三种类型的实体图标。 

|图标类型  |描述  |
|---------|---------|
|**统一接口图标**|必须是可缩放的矢量图形 (.svg) 图标 |
|**Web 应用程序中的图标**|.svg、.gif、.png 或 .jpg 格式的图像，大小为 16x16 像素。|
|**实体窗体的图标**|.svg、.gif、.png 或 .jpg 格式的图像，大小为 32x32 像素。|

> [!NOTE]
> 所有图像文件的大小都不能超过 10 KB。
>
> 若将可缩放的矢量图形 (.svg) 图像用作 Web 应用程序中的图标或者实体窗体的图标，必须使用默认大小。 SVG 为 XML 文档，因此可以使用文本编辑器编辑 [svg](https://developer.mozilla.org/docs/Web/SVG/Element/svg) 元素的[宽度](https://developer.mozilla.org/docs/Web/SVG/Attribute/width)和[高度](https://developer.mozilla.org/docs/Web/SVG/Attribute/height)值，从而定义该图像的默认大小。

系统将每种类型的图标都存储为 Web 资源。 先创建 Web 资源再设置图标，即可使用图标；也可以在设置值时选择“新建”，以便在“查找记录”对话框中新建 Web 资源。 详细信息：[创建或编辑 Web 资源以扩展应用](create-edit-web-resources.md)

## <a name="set-the-icons-for-a-custom-entity"></a>设置自定义实体的图标。

必须使用解决方案资源管理器来设置实体图标。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="set-entity-icons"></a>设置实体图标

1. 选择命令栏上的“更新图标”。  
  
2. 在“选择新图标”对话框的“Web 客户端”选项卡上，选择位于“Web 应用中的图标”或“实体窗体图标”下、“新建图标”右侧的“浏览”按钮![查找按钮](media/lookup-button-4.gif)。
3. 选择或创建合适的 Web 资源，再选择“确定”。 
4. 在“统一接口”选项卡中，为“新建图标”字段执行同样的操作。
5. 选择“确定”关闭“选择新图标”对话框
6. 在命令栏的“文件”菜单上选择“保存”。  
7. 完成更改后，请发布这些更改。 在解决方案资源管理器中选中实体后，选择命令栏中的“发布”。
  
## <a name="community-tools"></a>社区工具

**[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)** 是 XrmToolBox 社区为 Dynamics 365 Customer Engagement 开发的工具。 请参阅 [Developer tools for Common Data Service for Apps](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools)（适用于 Common Data Service for Apps 的开发人员工具）主题，了解社区开发的工具。

> [!NOTE]
> 社区工具不是 Microsoft 的产品，开发者不会扩展对社区工具的支持。 若对工具有疑问，请与发布者联系。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。

## <a name="next-steps"></a>后续步骤  
[创建实体](../common-data-service/create-edit-entities.md)<br />
[编辑实体](../common-data-service/edit-entities.md)
