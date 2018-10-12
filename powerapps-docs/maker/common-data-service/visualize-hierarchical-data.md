---
title: 使用模型驱动应用可视化分层数据 | MicrosoftDocs
description: 了解如何查询和可视化分层的相关数据
ms.custom: ''
ms.date: 06/02/2018
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
ms.author: matp
manager: kvivek
ms.openlocfilehash: bed8662d7d9475215df8e92490702b68e36574e2
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669161"
---
# <a name="visualize-hierarchical-data-with-model-driven-apps"></a>使用模型驱动应用可视化分层数据

> [!NOTE]
> 分层数据可视化效果仅适用于为 **Web** 客户端配置的模型驱动应用。 可视化效果不适用于**统一接口**客户端。 详细信息：[使用应用设计器创建模型驱动应用](../model-driven-apps/create-edit-app.md)

将实体配置为具有分层自引用关系时，可以使用该层次结构配置可视化效果。 详细信息：[定义和查询按层次结构相关的数据](../common-data-service/define-query-hierarchical-data.md)

默认具有可用的可视化效果的实体包括[帐户](/powerapps/developer/common-data-service/reference/entities/account)、[位置](/powerapps/developer/common-data-service/reference/entities/position)和[用户](/powerapps/developer/common-data-service/reference/entities/systemuser)。 在这些实体的网格视图中，可在记录名称左侧看到描绘层次结构图表的图标。 默认情况下，并非所有记录都显示层次结构图标。 使用分层关系关联的记录会显示此图标。  
  
 ![具有层次结构的帐户](media/account-list-with-hierarchy.png)  
  
 如果选择层次结构图标，则可以查看层次结构，左侧是树状视图，右侧是磁贴视图，如下所示：  
  
 ![帐户树状和磁贴视图](media/hierachy-security-accounts-tile-view.png)  
  
 可以为其他一些实体启用层次结构。 这些实体包括[联系人](/powerapps/developer/common-data-service/reference/entities/contact)和[团队](/powerapps/developer/common-data-service/reference/entities/team)。 可为层次结构启用所有自定义实体。  
  
创建可视化效果时要记住的重要事项：  
  
- 每个实体只能将一个 (1:N) 自引用关系设置为分层。 在自引用关系中，主实体和相关实体必须属于同一类型。  
- 层次结构或可视化效果仅基于一个实体。 可以描绘在多个级别显示帐户的帐户层次结构，但不能在同一层次结构可视化效果中显示帐户和联系人。 
- 可在磁贴中显示的最大字段数为四个。 如果向用于磁贴视图的“快速窗体”添加更多字段，则仅显示前四个字段。 

## <a name="hierarchy-settings"></a>层次结构设置

若要为层次结构启用可视化效果，必须将层次结构连接到快速视图窗体。 只能使用解决方案资源管理器执行此设置。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

层次结构设置与解决方案资源管理器中的实体相关联。 

1. 在[查看实体](../common-data-service/create-edit-entities-solution-explorer.md#view-entities)时，选择“层次结构设置”。
2. 如果存在现有层次结构设置，则可以对其进行编辑。 否则，请单击“新建”创建一个新的层次结构设置。
    
    > [!NOTE]
    > 如果不存在层次结构设置，则实体不符合配置层次结构的条件。
    >只能有一个层次结构设置 

1. 设置以下字段中的数据：

|字段|描述|
|--|--|
|**名称**|*必填。* 为层次结构设置添加唯一名称。 这通常就是实体的名称。 此值将包含解决方案发布者的自定义前缀。|
|**默认快速视图窗体**|*必填。* 从现有的快速视图窗体中进行选择，或选择“新建”打开快速视图窗体编辑器，以创建新的快速视图窗体。|
|**分层关系**|*必填。* 如果已为实体定义了分层关系，则将在此处设置值。 如果没有值，请选择“将关系标记为已启用层次结构”打开一个对话框，以选择一个可用的自引用关系。|
|**Description**|包括此层次结构的用途说明，以便将来自定义系统的人可以理解为什么要这样做。|
    

可视化效果的相同分层设置只设置一次，但同时适用于 Web 客户端和移动客户端。 在平板电脑中，视觉对象以适合较小外形规格的修改过的格式呈现。 分层可视化效果所需的可自定义组件可识别解决方案，因此，它们可以像任何其他自定义项一样在组织之间传输。 可以使用窗体编辑器自定义快速窗体，以便配置可视化效果中所示的属性。
  
## <a name="visualization-walk-through"></a>可视化效果演练

我们来看一个为自定义实体创建可视化效果的示例。 我们创建了一个名为 `new_Widget` 的自定义实体，创建了一个 (1:N) 自引用关系 `new_new_widget_new_widget`，并将其标记为分层，如下所示。  
  
![小组件关系定义](media/widget-relationship-definition.png)  
  
接下来，在“层次结构设置”网格视图中，我们选择 了`new_new_widget_new_widget` 分层关系。 在窗体中，我们填写了必填字段。 如果尚未将 (1:N) 关系标记为分层，则通过窗体上的链接可返回到关系定义窗体，可在该窗体中将关系标记为分层。  

> [!IMPORTANT]
> 每个实体一次只能有一个分层关系。 将此更改为其他自引用关系可能会产生重大影响。 详细信息：[定义分层数据](../common-data-service/define-query-hierarchical-data.md#define-hierarchical-data)
  
![层次结构设置](media/hierarchy-settings.png)  
  
对于“快速视图窗体”，我们创建了一个名为“小组件层次结构磁贴窗体”的快速窗体。 在此窗体中，我们在每个磁贴中添加了四个要显示的字段。  
  
![为小组件创建快速窗体](media/create-quickform.png)  
  
完成设置后，我们创建了两条记录：标准小组件和高级小组件。 通过使用查找字段使高级小组件成为标准小组件的父级后，`new_Widget` 网格视图描绘了层次结构图标，如下所示：  
  
![小组件的层次结构网格](media/widget-hierarchy-grid.png)  
  
> [!NOTE]
>  在使用分层关系关联记录之前，层次结构图标不会出现在记录网格视图中。  
  
选择层次结构图标将显示 `new_Widget` 层次结构，左侧是树状视图，右侧是磁贴视图，并显示两条记录。 每个磁贴均包含我们在“小组件层次结构磁贴窗体”中提供的四个字段。  
  
![小组件的树状和磁贴视图](media/widget-tree-tiles.png)  

可以根据需要选择使用显示整个层次结构的树状视图，或使用描绘层次结构较小部分的磁贴视图。 这两种视图并排显示。 可通过展开和收缩层次结构树来浏览层次结构。 

### <a name="see-also"></a>另请参阅 

[定义和查询按层次结构相关的数据](../common-data-service/define-query-hierarchical-data.md)<br />
[视频：层次结构可视化效果](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)