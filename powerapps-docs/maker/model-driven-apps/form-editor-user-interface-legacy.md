---
title: PowerApps 的模型驱动应用窗体编辑器用户界面概述 | MicrosoftDocs
description: 了解窗体编辑器用户界面，以在 PowerApps 中编辑窗体
keywords: 窗体; 主窗体; 统一接口应用; Dynamics 365 for customer engagement
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.assetid: 146f8035-4fcd-4572-8e71-4270cd150495
ms.openlocfilehash: a44987e7b8809dea46f164224974a21a2d9a5010
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669271"
---
# <a name="overview-of-the-model-driven-app-form-editor-user-interface"></a>模型驱动应用窗体编辑器用户界面概述

窗体编辑器在三个选项卡中显示命令：“文件”、“开始”以及“插入”。  

- [“文件”选项卡](#file-tab)
- [“开始”选项卡](#home-tab)
- [“插入”选项卡](#insert-tab)
  
窗体编辑器分为三个区域：“导航”、“正文”和“资源管理器”。  

![窗体编辑器用户界面](media/form-user-interface.png)
  
**导航**  
可使用左侧导航区域控制对相关实体的访问，或将链接添加至要在窗体主窗格中显示的 URL 中。 若要编辑导航，必须先在“开始”选项卡的“选择”组中选择“导航”命令。

主窗体通过导航栏提供导航选项，但使用导航区域中的相同数据来控制可用的导航选项。 详细信息：[编辑导航](use-the-form-editor-legacy.md)  


**正文** <br>
可使用正中的正文区域控制窗体布局。 可以选择并拖动窗体元素来进行放置。 双击元素可打开该元素的属性。 

默认情况下，对于“案例”、“联系人”和“帐户”主窗体，“摘要”选项卡下的第一部分会显示“快速视图”类型的帐户或联系人卡窗体。 对于自定义实体，默认情况下不显示此部分。 可在其中插入新的分区或快速视图窗体。 卡窗体最多显示五个字段。 除字段以外，无法在蓝色磁贴中显示其他控件，即使是快速视图窗体包含的控件也无法显示。 
 
>[!NOTE] 
> 若要保留卡窗体（如下图所示），建议不要将快速视图窗体移动至窗体上的任何其他分区。

![卡窗体](media/card-format.png)
   
详细信息：[创建和编辑快速视图窗体](create-edit-quick-view-forms.md)  
 
-   若要添加字段，请从“字段资源管理器”中选择它，并将其拖进分区。  
  
    -   若要添加非字段元素，请选择其放置位置，然后使用“插入”选项卡中的适当命令将其添加。  
  
    -   若要删除元素，选择该元素，然后使用“开始”选项卡“编辑”组中的删除命令将其删除。  
  
    -   若要编辑窗体的“页眉”或“页脚”，必须先在“开始”选项卡的“选择”组中选择对应的命令。  
  
**资源管理器**  
资源管理器位于右侧，该区域的内容取决于上下文。  
  
在“开始”选项卡的“选择”组中选择“正文”、“页眉”或“页脚”时，将看到“字段资源管理器”。 使用“字段资源管理器”来拖动想在窗体分区中显示的字段，或想在页眉或页脚中显示的字段。 可在一个窗体中多次使用同一字段。 “新建字段”按钮可用作创建新字段的快捷方式。  
  
在“开始”选项卡的“选择”组中选择“导航”时，将看到“关系资源管理器”。 将其中任一关系拖动到导航区域内的某个组中。 不能重复添加同一关系。 关系的可用性取决于它们的配置方式。 如果将关系配置为不显示，则它不会显示在“关系资源管理器”中。 若要详细了解如何配置关系的默认显示选项，请参阅[主要实体的导航窗格项](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)。
  
可使用“新建 1:N”和”新建 N:N”按钮作为添加新实体关系的快捷方式。  

## <a name="file-tab"></a>“文件”选项卡

选择“文件”选项卡，添加/查看以下选项：

- “新建活动”：添加新活动
- “新建记录”：添加新记录
- “工具”：使用“导入数据”、“重复检测”和“批量删除向导”等选项
- “选项”：更改默认显示设置，对默认解决方案进行个性化设置，以及管理自己的电子邮件模板
    - 常规
    - 同步
    - 活动
    - 格式
    - 电子邮件模板
    - 电子邮件签名
    - 电子邮件
    - 隐私
    - 语言
- 帮助
- 关闭


## <a name="home-tab"></a>“开始”选项卡  
 “开始”选项卡显示下表中列出的命令：

![home-tab](media/home-tab.png)

|组|命令|描述|
|-----------|-------------|-----------------| 
|**保存**|**保存****(Ctrl+S)**|保存窗体。|
||**另存为**|使用其他名称创建窗体副本。|
||**保存并关闭**|保存窗体并关闭窗体编辑器。|
||**发布**|发布窗体。 详细信息：发布自定义窗体|
|**编辑**|**更改属性**|更改正文中选定项的属性。<br /><br /> 根据所选项，查看以下部分：<br /><br /> -   [选项卡属性](tab-properties-legacy.md)<br />-   [分区属性](section-properties-legacy.md)<br />-   [通用字段属性](common-field-properties-legacy.md)<br />-   [特殊字段属性](special-field-properties-legacy.md)<br />-  [子网格属性](sub-grid-properties-legacy.md)<br />-   [快速视图控件属性](quick-view-control-properties-legacy.md)|
||**删除**|删除所选项。|
||**撤消****(Ctrl+Z)**|撤销上一个操作。|
||**恢复****(Ctrl+Y)**|恢复上一个操作。|
|**选择**|**正文**|编辑窗体正文。|
||**页眉**|编辑窗体页眉。|
||**页脚**|编辑窗体页脚。|
||**导航**|编辑窗体导航。<br /><br /> 详细信息：[编辑导航](use-the-form-editor-legacy.md)
|**窗体**|**业务规则**|使用“业务规则”资源管理器查看、编辑或创建新的业务规则。 请注意：交互式窗体仅支持“实体”和“全部窗体”。<br /><br /> 详细信息：[创建和编辑业务规则](create-business-rules-recommendations-apply-logic-form.md)|
||**窗体属性**| 详细信息：[窗体属性](form-properties-legacy.md)|  
||预览|用于查看发布后的窗体外观。 还可以预览测试与窗体事件关联的脚本。|         
||**启用安全角色**|使用此选项设置有权访问该窗体的安全角色。 详细信息：[控制对窗体的访问](control-access-forms.md)。重要说明：若新建了一个窗体，只有系统管理员和系统定制员安全角色有权访问该窗体。 必须向其他安全角色分配访问权限，他们才能使用该窗体。|  
||**显示依赖项**|查看依赖于此窗体的解决方案组件，以及此窗体必需的解决方案组件。 详细信息：[解决方案依赖项](../common-data-service/overview.md)|  
||**托管​​属性**|托管属性命令包含两种属性：“可自定义”和“可删除”。 若将这两种属性设为 false，那么将该窗体包含在解决方案中，然后将该解决方案导出为托管解决方案并导入其他环境后，将无法自定义该窗体也无法将其删除。 详细信息：[托管属性](../common-data-service/solutions-overview.md#managed-properties)| 
|**升级**|**合并窗体**|在适用的情况下，可使用此选项将此窗体与旧版 Dynamics 365 窗体合并|
  

## <a name="insert-tab"></a>“插入”选项卡  
![insert-tab](media/insert-tab.png)
 
“插入”选项卡显示下表中的命令：

|组|命令|描述|
|-----------|-------------|-----------------| 
||**分区**|向所选选项卡添加分区。添加的分区可包含一到四列。<br /><br /> 还可以在交互式窗体中插入引用面板。 在主交互式体验窗体中，引用面板也可作为分区添加到正文。 默认情况下，引用面板分区将添加到“案例”、“帐户”、“联系人”和自定义实体窗体。<br /><br /> 详细信息：[分区属性](section-properties-legacy.md)|  
|**3 个选项卡**|**三列**|插入三列式等宽选项卡。<br /><br /> 详细信息：[选项卡属性](tab-properties-legacy.md)|  
||**三列**|插入三列式选项卡，且中间列较另两列更宽。|  
|**2 个选项卡**|**两列**|插入二列式选项卡，其中右侧列较宽。|  
||**两列**|插入二列式选项卡，其中左侧列较宽。|  
||**两列**|插入二列式等宽选项卡。|  
|**1 个选项卡**|**一列**|插入一列式选项卡。|  
|**控件**|**子网格**|设置子网格的格式并将其插入窗体。<br /><br /> 详细信息：[子网格属性](sub-grid-properties-legacy.md)|  
||**空格**|插入空格。|  
||**快速视图窗体**|插入快速视图窗体。<br /><br /> 详细信息：[快速视图控件属性](quick-view-control-properties-legacy.md)|  
||**Web 资源**|插入 Web 资源，在一个页面中嵌入其他位置的内容。<br /><br /> 详细信息：[Web 资源属性](web-resource-properties-legacy.md)|  
||**IFRAME**|可在窗体插入 IFRAME，将其他网站中的内容集成到窗体中。| 
||**日程表**|在窗体中插入日程表控件。 此控件显示与窗体上的实体相关的活动日程表。|  
||**导航链接**|可使用此选项将链接插入窗体导航。|  
||**计时器**|将计时器控件插入实体窗体，以便跟踪 SLA 的时间。 详细信息：[添加计时器控件](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customer-service/add-timer-control-case-form-track-time-against-sla)|
||**知识库搜索**|插入搜索控件，用户可使用该控件搜索知识库中的文章。 详细信息：[知识库搜索控件](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customer-service/add-knowledge-base-search-control-forms)|  
||**关系助手**|可使用此选项在窗体中插入关系助手控件。|

>[!Note] 
>主窗体中不支持以下组件：<br> <ul> <li>必应地图 <br><li>Yammer <br><li>活动源 <br> </li> </ul>


## <a name="next-steps"></a>后续步骤

[使用主窗体及其组件](use-main-form-and-components.md)  
