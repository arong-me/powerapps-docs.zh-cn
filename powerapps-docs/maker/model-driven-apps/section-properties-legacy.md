---
title: Power Apps 中模型驱动应用主窗体的部分属性 | MicrosoftDocs
description: 了解主窗体的分区属性
Keywords: 主窗体; 部分属性; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 03/23/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 2d3af6e9-e8a4-4129-b708-383b2740c015
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 25d2edd58bf146f9537af87a0b7564b4ce421395
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166562"
---
# <a name="model-driven-app-form-section-properties"></a>模型驱动应用程序的窗体分区属性

 窗体中的分区占据选项卡栏中的可用空间。 分区有一个可显示的标签，该标签下可能会显示一条线。  
  
 分区最多可以有 4 栏，并包括用于显示分区中字段标签显示方式的选项。  
  
 标题和脚注类似于分区，但不能删除。 如果标题和脚注中没有内容，则不会显示。

## <a name="section-properties-in-form-designer"></a>窗体设计器中的部分属性

1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。 

3.  在窗体列表中，打开**主**类型的窗体。 若要在另一个选项卡中打开窗体，请选择**更多命令** ![“更多命令”按钮](media/more-commands.gif "窗体的“更多命令”按钮")，然后选择**编辑窗体** > **在新选项卡中编辑窗体**。

4.  选择其中一个部分查看部分属性。

    > [!div class="mx-imgBorder"]
    > ![部分属性](media/new-section-properties.png "窗体设计器中的部分属性")

|属性|说明|  
|---------|--------------|  
|**节标签**|**必需**：可本地化的分区标签，向用户显示。|  
|**名称**|**必需**：分区的唯一名称，在脚本中引用分区时使用该名称。 该名称只能包含字母数字字符和下划线。|  
|**隐藏标签**|经常使用不带标签的分区，用于控制其中的字段格式。|
|**锁定节**|这将防止意外删除分区，并可阻止用户删除内容。<br /><br /> 删除分区时将不仅删除分区，还会删除其中的所有字段。<br /><br /> 对于要删除此分区的人，需要在删除分区前更改此设置。|  
|**隐藏节**|是否显示分区是可选的，并可使用脚本来控制。 详细信息：[可见性选项](visibility-options-legacy.md)|  
|**在电话上隐藏**|选择您是否希望在电话上提供此选项卡。|  
|**格式设置**|分区中最多可指定四栏。|  

## <a name="section-properties-in-classic-form-designer"></a>经典窗体设计器中的部分属性

您可以从 Power Apps 站点在解决方案资源管理器中访问**部分属性**。

1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。 

3.  在窗体列表中，打开**主**类型的窗体。 

4.  选择**切换到经典**在经典窗体设计器中编辑窗体。

5.  在一个部分内双击查看部分属性。 

    > [!div class="mx-imgBorder"]
    > ![部分属性](media/section-properties.png "解决方案资源管理器中的部分属性")
  
|选项卡|属性|说明|  
|---------|--------------|-----------------|  
|**显示器**|**名称**|**必需**：分区的唯一名称，在脚本中引用分区时使用该名称。 该名称只能包含字母数字字符和下划线。|  
||**标签**|**必需**：可本地化的分区标签，向用户显示。|  
||**在窗体上显示此分区的标签**|经常使用不带标签的分区，用于控制其中的字段格式。|  
||**在分区顶部显示一条线**|分区顶部有一条线可以帮助划分窗体布局。|  
||**字段标签宽度**|**必需**：设置一个介于 50 和 250 之间的值，用于指定字段标签允许的空间。<br /><br /> 标题和脚注元素也有此属性。|  
||**可见性**|是否显示分区是可选的，并可使用脚本来控制。 详细信息：[可见性选项](visibility-options-legacy.md)|  
||**可用性**|选择您是否希望在电话上提供此选项卡。|  
||**在窗体上锁定分区**|这将防止意外删除分区，并可阻止用户删除内容。<br /><br /> 删除分区时将不仅删除分区，还会删除其中的所有字段。<br /><br /> 对于要删除此分区的人，需要在删除分区前更改此设置。|  
|**格式设置**<br /><br /> 标题和脚注组件也有此属性。|**布局**|分区中最多可指定四栏。|  
||**字段标签对齐方式**|分区中的字段标签可左对齐、右对齐或中心对齐。|  
||**字段标签位置**|分区中的字段标签可以放在字段的边上或顶部。|  


也可以添加一种名为**参考面板**的新型分区。 参考面板是一种单列分区。 您可以在参考面板分区中插入子网格、快速视图控件或知识库搜索控件。 您在参考面板中添加的每个控件在运行时均以垂直选项卡的形式显示在面板中。 您可以拖放参考面板分区中的各个控件。 运行时的默认选项卡是参考面板中添加的第一个控件。 其他选项卡按照它们添加到窗体编辑器中的顺序显示。 若要删除选项卡，请使用键盘上的 Delete 键。  
  
插入参考面板时，默认情况下它将作为选项卡中最后一个部分添加。每个窗体只能添加一个参考面板。  
  
> [!IMPORTANT]
>  默认情况下，参考面板分区锁定在这些标准窗体中，包括“案例”、“客户”和“联系人”窗体。 若要删除或更改该分区，必须将其解锁。 

## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
