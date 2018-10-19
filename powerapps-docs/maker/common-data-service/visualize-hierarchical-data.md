---
title: 使用模型驱动应用程序可视化分层数据 | MicrosoftDocs
description: 了解如何查询和可视化相关的分层数据
ms.custom: ''
ms.date: 09/19/2018
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="visualize-hierarchical-data-with-model-driven-apps"></a>使用模型驱动应用程序可视化分层数据

在将实体配置为有分层的自引用关系时，您可以使用该层次结构配置可视化项。 详细信息：[定义和查询按层次结构相关的数据](../common-data-service/define-query-hierarchical-data.md)

默认有可用可视化项的实体包括[客户](/powerapps/developer/common-data-service/reference/entities/account)、[职位](/powerapps/developer/common-data-service/reference/entities/position)和[用户](/powerapps/developer/common-data-service/reference/entities/systemuser)。 在这些实体的网格视图中，您可以看到描述层次结构图的图标，左边是记录名称。 在默认情况下，不是所有的记录都显示层次结构图标。 此图标为使用分层关系相关的记录显示。  
> [!div class="mx-imgBorder"] 
> ![“查看层次结构”按钮](media/view-hierarchy-button.png)  
  
 若您选择了层次结构图标，您可以查看层次结构，左边是树状视图，右边是磁贴视图，如下所示：  
  
> [!div class="mx-imgBorder"] 
> ![层次结构中的树和磁贴视图](media/tree-view-and-tile-view-in-hierarchy.png)  
  
 还有其他一些实体可以启用层次结构。 这些实体包括[联系人](/powerapps/developer/common-data-service/reference/entities/contact)和[团队](/powerapps/developer/common-data-service/reference/entities/team)。 可以为层次结构启用所有自定义实体。  
  
创建可视化项时切记：  
  
- 每个实体中，只能将一个 (1:N) 自引用关系设置为层次结构形式。 在自引用关系中，主要实体和相关实体必须属于同一类型。  
- 层次结构或可视化项只基于一个实体。 您可以描述客户层次结构以多层次显示客户，但是您不能在相同层次结构可视化中显示客户和联系人。 
- 可以在磁贴中显示的字段的最大数是 4 个。 如果您向用于磁贴视图的快速窗体添加更多字段，则只能显示前四个字段。 

## <a name="hierarchy-settings"></a>层次结构设置

若要为层次结构启用可视化项，您必须将层次结构与快速视图窗体连接。 这只能使用解决方案资源管理器执行。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

层次结构设置与解决方案资源管理器中的实体关联。 

1. 在[查看实体](../common-data-service/create-edit-entities-solution-explorer.md#view-entities)时，选择**层次结构设置**。
2. 如果存在现有的层次结构设置，您可以进行编辑。 否则，单击**新建**创建一个新设置。
    
    > [!NOTE]
    > 如果不存在层次结构设置，实体将不能配置层次结构。
    >可能只有一个层次结构设置 

1. 在以下字段中设置数据：

|字段|说明|
|--|--|
|**名称**|*必需。* 为层次结构设置添加唯一名称。 这通常就是实体的名称。 此值将包含解决方案发布商的自定义项前缀。|
|**默认快速视图窗体**|*必需。* 从现有的“快速视图”窗体选择或选择**新建**打开“快速视图”窗体编辑器新建一个。|
|**分导关系**|*必需。* 如果已为实体定义了分层关系，值将在此处设置。 如果没有值，选择**将关系标记为启用层次结构**打开对话框，从可用的自引用关系中选择一个。|
|**说明**|加入此层次结构的用途描述，以便未来自定义系统的用户可以了解为何进行自定义。|
    

同样的可视化项分层设置只需设置一次，但可同时应用于 Web 和移动客户端。 在平板电脑中，可视化对象采用适合更小外形规格的修改格式来显示。 层次结构可视化所需的可自定义组件是可以识别解决方案的，因此像其他自定义一样，可以在组织之间进行传输。 您可以通过使用表单编辑器自定义快速窗体，来配置可视化项中所显示的属性。
  
## <a name="visualization-walk-through"></a>可视化演练

请看为自定义实体创建可视化的示例。 我们创建了名为 `new_Widget` 的自定义实体，创建了 (1:N) 自引用关系 `new_new_widget_new_widget`，并将其标记为分层，如此处所示。  
  
![小组件关系定义](media/widget-relationship-definition.png)  
  
接下来，在**层次结构设置**网格视图中，我们选择了 `new_new_widget_new_widget` 分层关系。 在表单中，我们填充了所需字段。 如果您尚未将 (1:N) 关系标记为分层，表单的链接可返回到关系定义表单，您就可以将该关系标记为分层的了。  

> [!IMPORTANT]
> 每个实体一次只能有一个分层关系。 将此关系更改为其他自引用关系可能产生影响。 详细信息：[定义分层数据](../common-data-service/define-query-hierarchical-data.md#define-hierarchical-data)

> [!div class="mx-imgBorder"] 
> ![层次结构设置](media/hierarchy-settings.png)  
  
对于**快速窗体视图**，我们创建名为**Widget 层次结构磁贴窗体**的快速窗体。 在此窗体中，我们在每个磁贴中添加了四个显示字段。  

> [!div class="mx-imgBorder"] 
> ![小组件的快速创建窗体](media/create-quickform.png)  
  
在完成设置后，我们创建了两个记录：*标准小组件*和*高级小组件*。 在使用查找字段将“高级小组件”设置为“标准小组件”的父级后，`new_Widget` 网格视图显示了层次结构图标，如下所示：  

> [!div class="mx-imgBorder"] 
> ![小组件的层次结构网格](media/widget-hierarchy-grid.png)  
  
> [!NOTE]
>  在使用分层关系关联记录前，层次结构图标不会显示在记录网格视图中。  
  
选择层次结构图标将显示 `new_Widget` 层次结构，树视图位于左侧，磁贴视图位于右侧，显示两个记录。 每个磁贴包含我们在**部件层次结构磁贴窗体**中提供的四个字段。  

> [!div class="mx-imgBorder"] 
> ![小组件的树视图和磁贴视图](media/widget-tree-tiles.png)  

基于需要，用户可以在树状视图（显示整个层次结构）或磁贴视图（层次结构的较小部分的详细视图）之间选择。 两种视图并排显示。 可以通过展开和收缩层次结构树来浏览层次结构。 

### <a name="see-also"></a>另请参阅 

[定义和查询按层次结构相关的数据](../common-data-service/define-query-hierarchical-data.md)<br />
[视频：层次结构可视化](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
