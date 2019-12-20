---
title: 在 Power Apps 中更改模型驱动应用程序的自定义实体图标 | MicrosoftDocs
definition: Learn how to change the icon for a custom entity
ms.custom: ''
ms.date: 05/17/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7d45a3fc5afae25f2a4e254c033f4e35be20c0ff
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2869247"
---
# <a name="change-model-driven-app-custom-entity-icons"></a>更改模型驱动应用程序的自定义实体图标 

在创建自定义实体时，其将被自动分配默认图标。 所有自定义实体默认均使用相同图标。 使用自定义图标区分自定义实体的外观。 您不能修改分配给系统实体的图标。  
  
 您可以为每个自定义实体上传三种类型的实体图标。 

|图标类型  |说明  |
|---------|---------|
|**统一接口图标**|必须是可扩展矢量图形 (.svg) 图标 |
|**Web 应用程序中的图标**|.svg、.gif、.png 或 .jpg 格式的图像，尺寸为 16x16 像素。|
|**实体窗体图标**|.svg、.gif、.png 或 .jpg 格式的图像，大小为 32x32 像素。|

> [!NOTE]
> 所有图像文件的大小必须不能超过 10 KB。
>
> 当使用可扩展矢量图形 (.svg) 图像作为 **Web 应用程序中的图标**或**实体窗体图标**，必须为其设置默认大小。 因为 SVG 为 XML 文档，您可以使用文本编辑器编辑 [svg](https://developer.mozilla.org/docs/Web/SVG/Element/svg) 元素的[宽度](https://developer.mozilla.org/docs/Web/SVG/Attribute/width)和[高度](https://developer.mozilla.org/docs/Web/SVG/Attribute/height)值，以定义图像的默认大小。

图标的每个类型存储为一个 Web 资源。 您可以先创建 Web 资源，然后设置要使用它们的图标，也可以通过在设置值时选择**新建**来在**查找记录**对话框中创建新 Web 资源。 详细信息：[创建或编辑 Web 资源以扩展应用程序](create-edit-web-resources.md)

## <a name="set-the-icons-for-a-custom-entity"></a>设置自定义实体的图标。

必须使用解决方案资源管理器来设置实体图标。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="set-entity-icons"></a>设置实体图标

1. 在命令栏上，选择**更新图标**。  
  
2. 在**选择新图标**对话框中，在 **Web 客户端**选项卡中，在 **Web 应用程序中的图标**或**实体窗体图标**下的**新图标**右侧，选择**浏览**按钮 ![查找按钮](media/lookup-button-4.gif)。
3. 选择或创建相应的 Web 资源，然后选择**确定**。 
4. 在**统一接口**选项卡上，对**新图标**字段执行相同操作。
5. 选择**确定**以关闭**选择新图标**对话框
6. 在命令栏，在**文件**菜单上，选择**保存**。  
7. 完成更改后，发布自定义项。 在命令栏中选择**发布**，实体在解决方案资源管理器中选择。
  
## <a name="community-tools"></a>社区工具

**[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)** 是一款 XrmToolbox 社区为 Power Apps 开发的工具。 请参阅 [Common Data Service 的开发人员工具](/powerapps/developer/common-data-service/developer-tools)主题了解社区开发的工具。

> [!NOTE]
> 这些社区工具不是 Microsoft 的产品，因此不能将支持延伸到这些社区工具。 如果有与该工具相关的疑问，请联系发布者。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。

## <a name="next-steps"></a>后续步骤  
[创建实体](../common-data-service/create-edit-entities.md)<br />
[编辑实体](../common-data-service/edit-entities.md)
