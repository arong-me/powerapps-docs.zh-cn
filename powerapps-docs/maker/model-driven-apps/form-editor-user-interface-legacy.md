---
title: Power Apps 的模型驱动应用程序窗体编辑器用户界面概述 | MicrosoftDocs
description: 了解用于在 Power Apps 中编辑窗体的窗体编辑器用户界面
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.assetid: 146f8035-4fcd-4572-8e71-4270cd150495
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: dbd648bd96d087ce34d8482d96507fa2391902b6
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109196"
---
# <a name="overview-of-the-model-driven-app-form-editor-user-interface"></a>模型驱动应用程序窗体编辑器用户界面概述

窗体编辑器在三个选项卡中显示命令：**文件**、**主页**和**插入**。  

- [“文件”选项卡](#file-tab)
- [“Home”选项卡](#home-tab)
- [“插入”选项卡](#insert-tab)
  
窗体编辑器划分为三个区域：**导航** 、**主体** 和**资源管理器** 。  

> [!div class="mx-imgBorder"] 
> ![窗体编辑器用户界面](media/form-user-interface.png)
  
**导航**  
位于左侧，使用导航区可以控制对相关实体的访问，或者添加链接或要在窗体的主窗格中显示的 URL。 若要编辑导航，必须先在**主页**选项卡的**选择**组中选择**导航**命令。

主窗体通过导航栏提供导航选项，但使用导航区中相同的数据来控制可用的导航选项。 详细信息：[编辑导航](use-the-form-editor-legacy.md)  


**正文** <br>
位于中心，使用主体区可控制窗体的布局。 可以选定并拖动窗体元素来调整其位置。 双击某个元素将打开该元素的属性。 

默认情况下，对于“案例”、“联系人”和“客户”主窗体，**摘要** 选项卡下的第一个分区显示**快速视图** 类型的客户或联系人卡片窗体。 对于自定义实体，此部分默认不可用。 您可以在其中插入一个新分区和快速视图窗体。 卡片窗体最多显示五个字段。 除了字段之外，该窗体不可能在蓝色磁贴中显示其他控件（即使快速视图窗体包含该窗体）。 
 
>[!NOTE] 
> 若要保留卡片窗体（如下图所示），建议不要将快速视图窗体移至窗体上的任何其他分区。

> [!div class="mx-imgBorder"] 
> ![卡格式](media/card-format.png)
   
详细信息：[创建和编辑快速视图窗体](create-edit-quick-view-forms.md)  
 
-   若要添加字段，可从**字段资源管理器** 中选择字段，然后将其拖到某个分区。  
  
    -   若要添加非字段元素，请选择要放置该元素的位置，然后使用**插入** 选项卡的相应命令添加该元素。  
  
    -   若要删除元素，请选择该元素，然后使用**主页** 选项卡上**编辑** 组中的**删除**命令。  
  
    -   若要编辑窗体的**标题** 或**脚注** 必须先在**主页**选项卡的**选择**组中选择对应的命令。  
  
**资源管理器**  
位于右侧，资源管理器区的内容取决于上下文。  
  
如果在**主页**选项卡的**选择**组中选择**主体**、**标题**或**脚注**，则将看到**字段资源管理器**。 使用**字段资源管理器** 将要显示的字段拖到窗体中的某个分区，或者拖到标题或脚注中。 可以在窗体中多次放入同一个字段。 使用**新建字段** 按钮可以快速创建新字段。  
  
如果在**主页**选项卡的**选择** 组中选择**导航**，则将看到**关系资源管理器**。 将其中的任何一个关系拖到导航区内的某个组中。 相同的关系无法添加两次。 关系的可用性取决于其配置方式。 如果将某个关系配置为不显示，则该关系不会在**关系资源管理器**中显示。 有关如何为关系配置默认显示选项的信息，请参阅[主实体的导航窗格项](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)。
  
可以使用**新建 1:N**和**新建 N:N** 按钮快速添加新实体关系。  

## <a name="file-tab"></a>“文件”选项卡

选择**文件**选项卡添加/查看以下选项：

- **新建活动**添加新活动
- **新建记录**添加新记录
- **工具**使用导入数据、重复检测和批量删除向导这样的选项
- **选项**更改默认显示设置来实现默认解决方案个性化设置，并管理您的电子邮件模板
    - 常规
    - 同步
    - 活动
    - 格式
    - 电子邮件模板
    - 电子邮件签名
    - 电子邮件
    - 隐私​​
    - 语言
- 帮助
- 关闭


## <a name="home-tab"></a>“Home”选项卡  
 **主页**选项卡显示下表中列出的命令：

> [!div class="mx-imgBorder"] 
> ![“主页”选项卡](media/home-tab.png)

|组|命令|说明|
|-----------|-------------|-----------------| 
|**保存**|**保存** **(Ctrl+S)**|保存该窗体。|
||**另存为**|用不同的名称创建此窗体的副本。|
||**保存并关闭**|保存窗体并关闭窗体编辑器。|
||**发布**|发布窗体。 详细信息：发布自定义项|
|**编辑**|**更改属性**|更改主体中选定项目的属性。<br /><br /> 依据所选项目，将看到以下分区：<br /><br /> -   [选项卡属性](tab-properties-legacy.md)<br />-   [分区属性](section-properties-legacy.md)<br />-   [常见字段属性](common-field-properties-legacy.md)<br />-   [特殊字段属性](special-field-properties-legacy.md)<br />-  [子网格属性](sub-grid-properties-legacy.md)<br />-   [快速视图控件属性](quick-view-control-properties-legacy.md)|
||**删除**|移除所选项目。|
||**撤消** **(Ctrl+Z)**|撤消前一操作。|
||**恢复** **(Ctrl+Y)**|恢复前一操作。|
|**选择**|**正文**|编辑窗体的主体。|
||**页眉**|编辑窗体标题。|
||**页脚**|编辑窗体页脚。|
||**导航**|编辑窗体导航。<br /><br /> 详细信息：[编辑导航](use-the-form-editor-legacy.md)
|**表单**|**业务规则**|使用业务规则资源管理器查看、编辑或创建新的业务规则。 **注意：** 对于交互式窗体，只有“实体”和“所有窗体”范围受支持。<br /><br /> 详细信息：[创建和编辑业务规则](create-business-rules-recommendations-apply-logic-form.md)|
||**窗体属性**| 详细信息：[窗体属性](form-properties-legacy.md)|  
||**预览版**|使用此项查看发布后窗体的外观。 您还可以预览与事件关联的测试脚本。|         
||**启用安全角色**|使用此选项可设置哪些安全角色可以访问窗体。 详细信息：[控制对窗体的访问](control-access-forms.md) **重要信息：** 如果您创建一个新窗体，则只有系统管理员和系统定制员安全角色可以访问该窗体。 在人员可以使用该窗体之前，您必须向其他安全角色分派访问权限。|  
||**显示依赖项**|查看哪些解决方案组件依赖此窗体，以及此窗体需要哪些解决方案组件。 |  
||**托管属性**|托管属性命令有两个属性**可自定义**和**可以删除**。 将这些属性设置为 False 意味着该窗体在放入解决方案后将不可自定义且无法删除，将该解决方案导出为托管解决方案，将该托管解决方案导入到其他环境。 详细信息：[托管属性](../common-data-service/solutions-overview.md#managed-properties)| 
|**升级**|**合并窗体**|如果适用，此选项允许您将此窗体与之前版本的 Dynamics 365 窗体合并|
  

## <a name="insert-tab"></a>“插入”选项卡  
> [!div class="mx-imgBorder"] 
> ![“插入”选项卡](media/insert-tab.png)
 
插入选项卡显示下表中列出的命令：

|组|命令|说明|
|-----------|-------------|-----------------| 
||**节**|在所选选项卡中添加一个分区。可以加入一个包含一至四栏的分区。<br /><br /> 还可以在交互式窗体中插入一个参考面板。 参考面板也作为一个分区添加到“主 - 交互式体验”窗体。 默认情况下，参考面板分区添加到“案例”、“客户”、“联系人”和“自定义实体”窗体中。<br /><br /> 详细信息：[部分属性](section-properties-legacy.md)|  
|**3 选项卡**|**三列**|插入三列式等宽型选项卡。<br /><br /> 详细信息：[选项卡属性](tab-properties-legacy.md)|  
||**三列**|插入带有更宽的中间列的三列式选项卡。|  
|**2 选项卡**|**两列**|插入一个二栏选项卡，右栏较宽。|  
||**两列**|插入一个二栏选项卡，左栏较宽。|  
||**两列**|插入一个二栏等宽选项卡。|  
|**1 个选项卡**|**一列**|插入一个一栏选项卡。|  
|**控件**|**子网格**|为子网格设置格式，然后将其插入窗体。<br /><br /> 详细信息：[子网格属性](sub-grid-properties-legacy.md)|  
||**空格**|插入空格。|  
||**快速视图窗体**|插入快速视图窗体。<br /><br /> 详细信息：[快速视图控件属性](quick-view-control-properties-legacy.md)|  
||**Web 资源**|插入 Web 资源，以便将其他位置的内容嵌入一页中。<br /><br /> 详细信息：[Web 资源属性](web-resource-properties-legacy.md)|  
||**IFRAME**|可以向窗体添加 IFRAME 以便在一个窗体中集成另一网站的内容。| 
||**时间线**|在窗体中插入日程表控件。 此控件显示与窗体上实体相关的活动的日程表。|  
||**导航链接**|使用此选项，您可以将链接插入到窗体导航。|  
||**计时器**|向实体窗体插入计时器控件以跟踪时间，并和 SLA 做比对。 详细信息：[添加计时器控件](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/add-timer-control-case-form-track-time-against-sla)|
||**知识库搜索**|插入一个可供用户搜索知识文章的搜索控件。 详细信息：[知识库搜索控件](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/add-knowledge-base-search-control-forms)|  
||**关系助手**|使用此选项，可以在窗体中插入关系助手控件。|

>[!Note] 
>主窗体不支持以下组件：<br> <ul> <li>Bing 地图 <br><li>Yammer <br><li>活动源 <br> </li> </ul>


## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)  
