---
title: PowerApps 中的模型驱动应用主窗体表示形式 | MicrosoftDocs
description: 了解如何主窗体在不同设备上显示时如何出现
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: da3ac59a-5413-46cb-b355-1987e42e3853
caps.latest.revision: 35
ms.author: matp
manager: kvivek
ms.openlocfilehash: b8dee40f6dbeba62128434b3eb122add9cb0b373
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667822"
---
# <a name="how-model-driven-app-main-forms-appear-on-different-devices"></a>模型驱动应用主窗体在不同设备上如何出现

主窗体由所有模型驱动应用客户端使用。 此窗体提供一致用户体验，无论用户是在使用 Web 浏览器、适用于手机的 Dynamics 365、适用于平板电脑的 Dynamics 365 还是 Dynamics 365 for Outlook。  
  
<a name="BKMK_MainFormPresentations"></a>   
## <a name="main-forms"></a>主窗体  
 针对实体存在的任何主窗体可能会根据下表中的因素以不同方式显示。 设计主窗体时，请考虑它在每个不同表示形式中的工作方式。  
  
|表示形式|描述|  
|------------------|-----------------|  
|**已更新**|对于 Dynamics 365（联机版）和 Dynamics 365 本地中的[已更新实体和经典实体](create-design-forms.md#updated-versus-classic-entities)以及任何自定义实体，已更新窗体提供新的用户体验。 这些窗体具有更新的命令栏设计，并实现了附加功能（如自动保存和业务流程）。|  
|**适用于平板电脑的 Dynamics 365**| 适用于平板电脑的 Dynamics 365 以针对平板电脑优化的方法呈现主窗体的内容。|  
|**适用于手机的 Dynamics 365**| 适用于手机的 Dynamics 365 以针对手机优化的方法呈现主窗体的内容。|  
|**经典**|这些窗体用于尚未更新的实体。 它们使用功能区（而不是命令栏）和窗体左侧的导航窗格。<br /><br /> 这些窗体具有两列布局。|  
  
<a name="BKMK_MainFormComponentsForUpdatedEntities"></a>   
## <a name="updated-forms"></a>已更新窗体  
 此图示表示已更新实体窗体中的常见组件。  
  
 ![图示显示 Dynamics 365 中的已更新实体窗体结构](media/updated-form-diagram.png "图示显示 Dynamics 365 中的已更新实体窗体结构")  
  
 对于已更新实体，窗体的布局适用于各种不同的显示和窗口大小。 随着窗口的宽度减小，选项卡列会向下移动，以便可以向下滚动来使用它们，而不是进行压缩或是需要向右滚动。  
  
 下表总结了已更新实体的主窗体的可用组件。  
  
|组件|摘要|  
|---------------|-------------|  
|**导航栏**|使用站点地图中的数据提供移动到应用程序不同区域的功能。<br /><br /> 经典窗体中使用的导航窗格未包含在已更新窗体中。 在记录的上下文中，通过导航栏可以访问相关记录的视图。 添加配置为显示有用相关实体记录的子网格（而不是使用导航窗格或使用导航栏导航到相关记录）可为大多数人提供更好的体验。|  
|**命令栏**|使用为功能区定义的数据提供用于记录的相关命令。<br /><br /> 会显示前五个命令，后跟省略号 (![“更多命令”按钮](media/not-available.gif "“更多命令”按钮"))，它提供用于选择其他命令的浮出菜单。|  
|**图像**|如果实体具有图像字段并且实体“主要图像”选项设置为“默认图像”，则在窗体配置为显示图像时可以在标题中显示图像。|  
|**页眉**|当用户向下滚动窗体正文时，页眉中放置的字段会保持可见。<br /><br /> 页眉中最多可以放置四个字段。 页眉中不允许使用多行文本、Web 资源或 iFrame。 页眉和页脚与节共享某些属性。|  
|**流程控件**|当实体具有活动业务流程时，流程控件会显示在页面下方。 详细信息：[业务流程](/flow/business-process-flows-overview)|  
|**正文**|正文是窗体中包含选项卡的可滚动部分。|  
|**选项卡**|在窗体正文中，选项卡提供水平分隔。 选项卡具有可以显示的标签。 如果显示标签，则可以通过选择标签来展开或折叠选项卡以显示或隐藏其内容。<br /><br /> 选项卡最多包含三列，每列的宽度可以设置为总宽度的百分比。 创建新选项卡时，每列都使用一个节进行预填充。|  
|**节**|节占用选项卡列中的可用空间。 节具有可以显示的标签，并且标签下可能会显示一条线。<br /><br /> 节最多可以具有四列，包含用于显示节中字段的标签如何显示的选项。|  
|**字段**|字段显示人们用于查看或编辑实体记录中的数据的控件。 字段格式可以设置为在一个节中最多占用四列。|  
|**分隔条**|通过分隔条可以向节列添加空的空间。|  
|**子网格**|通过子网格可以在窗体中显示列表。 使用子网格显示图表的功能在已更新实体的窗体中不可用。|  
|**快速视图窗体**|快速视图窗体显示窗体上查找字段所引用的记录中的数据。 作为查找目标的实体必须具有快速视图窗体，然后才能添加到窗体。 详细信息：[创建和编辑快速视图窗体](create-edit-quick-view-forms.md)|  
|**Web 资源**|HTML 和 Microsoft Silverlight Web 资源可以添加到主窗体，但在使用适用于手机和平板电脑的 Dynamics 365 时不会显示它们。|  
|**iFrame**|配置为显示来自其他网站的网页的嵌入式框架。 **重要说明：**  <ul><li>当 iFrame 中显示的页面位于其他域上时，浏览器会应用更高级别的安全性。 这可能会使有关 iFrame 的内容与窗体中数据进行交互的要求复杂化。</li><li>不支持在嵌入在其他实体窗体中的 iFrame 中显示实体窗体。 
|**必应地图**|当此控件呈现在已更新实体的窗体中，并且系统设置“启用 Bing 地图”已使用有效 Bing 地图密钥启用时，此控件可以在窗体中使用一次，以显示已更新实体中的一个地址的位置。 详细信息：[配置必应地图](configure-bing-maps-legacy.md)|  
|**页脚**|可以向页脚添加任何数量的字段、Web 资源或 iFrame。 字段在页脚中显示时是只读状态。 页眉和页脚与节共享某些属性。|  
|**状态栏**|状态栏显示记录、通知区域或保存按钮的状态字段。|  
  
<a name="BKMK_CRMforTabletsPresentation"></a>   
## <a name="dynamics-365-for-phones-and-tablets-forms"></a>适用于手机和平板电脑的 Dynamics 365 窗体  
 大多数系统实体和自定义实体可用于适用于手机和平板电脑的 Dynamics 365。 这些实体的主窗体会转换为针对手机或平板电脑而优化的表示形式。  
  
<a name="BKMK_EntitiesEnabledForCRMForTablets"></a>   
### <a name="entities-enabled-for-dynamics-365-for-phones-and-tablets"></a>为适用于手机和平板电脑的 Dynamics 365 启用的实体  
 只有为适用于手机和平板电脑的 Dynamics 365 启用的实体才使用此主窗体表示形式。 详细信息：[在适用于手机和平板电脑的 Dynamics 365 中显示的实体](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_CustomEntity)  
  
### <a name="form-design"></a>窗体设计  
 适用于手机和平板电脑的 Dynamics 365 采用许多主窗体元素，并以针对手机或平板电脑而优化的方式来呈现它们。 下图显示到从 Web 应用到平板电脑和手机应用的重排。  
  
 **Web 应用**  
  
 ![从 Web 应用进行的 Dynamics 365 窗体重排](media/custon-reflow-web-app.png "从 Web 应用进行的 Dynamics 365 窗体重排")  
  
 **平板电脑应用**  
  
 ![到平板电脑应用的 Dynamics 365 窗体重排](media/reflow-tablet-app.png "到平板电脑应用的 Dynamics 365 窗体重排")  
  
 **手机应用**  
  
 ![到手机应用的 Dynamics 365 窗体重排](media/custon-reflow-phone-app.png "到手机应用的 Dynamics 365 窗体重排")  
  
 窗体元素会在适用于平板电脑的 Dynamics 365 中转换为宽全景布局，其中用户轻扫屏幕可更改视区中可见的元素。 在适用于手机的 Dynamics 365 中，用户轻扫屏幕可查看不同列或不同窗格的元素，并且流程控件会出现在每列上方。  
  
### <a name="view-port-element"></a>视区元素  
 以下各项始终在窗体上下文的视区中可见：  
  
 **导航栏**  
 导航栏是针对触控优化的站点地图的表示形式。 详细信息：[更改导航选项](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_NavigationOptions)  
  
 **主页**  
 主页按钮使用户进入作为适用于手机和平板电脑的 Dynamics 365 起始页的仪表板。  
  
 **流程控件**  
 如果实体启用了业务流程，则它在适用于平板电脑的 Dynamics 365 中会出现搜索控件旁的右上角，在适用于手机的 Dynamics 365 中出现屏幕顶部。  
  
 **搜索**  
 用户可以点击搜索控件以打开用于搜索记录的屏幕。  
  
 **命令栏**  
 默认情况下，在 Web 浏览器中运行的应用中出现的某些命令不会出现在适用于手机和平板电脑的 Dynamics 365 应用中。 与 Web 应用程序类似，命令栏与上下文相关，因此可用命令因当前查看或选择的内容而异。 详细信息：[更改命令](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_ChangeCommands)  
  
### <a name="form-elements"></a>窗体元素  
 显示的窗体元素取自主窗体，显示为用户通过视区看到的一系列面板。  
  
 在适用于平板电脑的 Dynamics 365 中，第一个面板显示有关针对记录存在的关系的联系信息。 在适用于手机的 Dynamics 365 中，第一个面板还在关系磁贴上方显示窗体中的页眉字段。  
  
 ![适用于平板电脑的 Dynamics 365 关系面板](media/mobile-app-form-relationships.png "适用于平板电脑的 Dynamics 365 关系面板")  
  
 对于联系人和用户窗体，顶部项显示记录的通信卡。 通信卡提供用于发起与人员的通信的按钮。 对于其他实体，如果主窗体中嵌入了联系人快速视图窗体，则会显示通信卡。  
  
 可以基于实体关系显示其他磁贴，但无法为以下实体自定义磁贴：  
  
|实体|磁贴|  
|------------|-----------|  
|帐户|Owner|  
|联系人|公司名称、所有者|  
|潜在客户|Owner|  
|商机|帐户、所有者|  
  
 可以使用窗体编辑器自定义其余磁贴。 顺序是固定的，不过可以设置在关系面板中可见的元素。  
  
 在适用于平板电脑的 Dynamics 365 中，第二个面板以窗体上第一个选项卡的名称开头。 包含在页眉中包含的任何字段，然后是第一个选项卡的内容。在适用于手机的 Dynamics 365 中，页眉会出现在第一列中。  
  
 ![适用于平板电脑的 CRM 窗体第一个面板](media/mobile-app-form-first-panel.png "适用于平板电脑的 CRM 窗体第一个面板")  
  
 如果窗体没有活动流程，则在适用于平板电脑的 Dynamics 365 中，第三个选项卡显示流程当前阶段的任务。 在适用于手机的 Dynamics 365 中，流程控件浮动在窗格上方，当选中时会在用户的当前窗格上方展开，并且始终可见且可操作。  
  
 窗体的其余面板包含窗体中选项卡的内容。 找到的任何子网格都显示为单独的面板。  
  
 适用于手机和平板电脑的 Dynamics 365 窗体始终显示选项卡和子网格的标签。 “在窗体上显示标签”设置不适用。  
  
> [!NOTE]
>  若要优化移动设备上的性能，对象数需限制为 5 个选项卡或 75 个字段和 10 个子网格。  
  
 适用于手机和平板电脑的 Dynamics 365 窗体不支持以下功能：  
   
-   必应地图  
  
-   Yammer
  
-   活动源  
  
-   主题设置  
  
 此外，实体图像在列表视图和联系人卡片中可见，但在实际窗体中不可见。  
  
<a name="BKMK_MultipleForms"></a>   
### <a name="multiple-forms"></a>多个窗体  
 适用于手机和平板电脑的 Dynamics 365 支持多个窗体，但没有提供方法供用户在窗体之间切换（如果可以访问多个窗体）。 用户会看到他们有权访问的窗体顺序中的第一个窗体。  
  
 例如，如果对于商机实体有以下主窗体，并且为每个窗体分配了以下安全角色，则会看到下表中显示的窗体顺序。  
  
|窗体顺序|窗体名称|安全角色|  
|----------------|---------------|--------------------|  
|1|**销售窗体一**|销售员|  
|2|**销售窗体二**|销售员和销售经理|  
|3|**销售窗体三**|销售经理|  
|4|**销售窗体四**|销售副总裁|  
  
-   具有销售员角色的用户会始终看到**销售窗体一**。  
  
-   具有销售经理角色的用户会始终看到**销售窗体二**。  
  
-   具有销售副总裁角色的用户会始终看到**销售窗体四**。  
  
<a name="BKMK_ClassicPresentation"></a>   
## <a name="classic-forms"></a>经典窗体  
 下图显示经典表示形式中使用的主窗体组件。  
  
 ![主要窗体元素](media/elements.png "主要窗体元素")  
  
 已更新实体的窗体从经典窗体继承了许多组件，但存在显著差异。  
  
 使用经典表示形式的窗体不包含导航栏，并且使用功能区而不是命令栏。 这些窗体不支持实体图像、流程控件、快速视图窗体、自动保存或 Bing 地图。 页眉中的字段不可编辑。  
  
 为某些实体（如 `Article`）公开了窗体助理。  
  
## <a name="next-steps"></a>后续步骤  
 [创建并设计窗体](create-design-forms.md)   

 
