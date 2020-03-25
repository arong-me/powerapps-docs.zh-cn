---
title: Power Apps 中模型驱动应用的主窗体演示 | MicrosoftDocs
description: 了解主窗体在不同设备上显示时如何呈现
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: da3ac59a-5413-46cb-b355-1987e42e3853
caps.latest.revision: 35
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 03eca0ade83c4d241eca9e4f7a6004232aac2b87
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108036"
---
# <a name="how-model-driven-app-main-forms-appear-on-different-devices"></a>模型驱动应用程序的主窗体在不同设备上的显示方式

主窗体供所有模型驱动应用客户端使用。 此窗体提供一致的用户体验，不论用户使用的是 Web 浏览器、适用于手机的 Dynamics 365、适用于平板电脑的 Dynamics 365 或 Dynamics 365 for Outlook。  
  
<a name="BKMK_MainFormPresentations"></a>   
## <a name="main-forms"></a>主窗体  
 为某个实体存在的任何主窗体可能会以不同方式显示，具体取决于下表中的因素。 在设计个主窗体时，请考虑其在不同表现形式下的工作方式。  
  
|演示文稿|说明|  
|------------------|-----------------|  
|**已更新**|对于 Dynamics 365 (online) 与 Dynamics 365 on-premises 中的[更新后的实体和经典实体](create-design-forms.md#updated-versus-classic-entities)和任何自定义实体，更新后的窗体提供了新的用户体验。 这些窗体具有较新的命令栏设计，并启用其他功能，如自动保存和业务流程。|  
|**Dynamics 365 for tablets**| Dynamics 365 for tablets 以针对平板电脑优化的方式呈现主窗体的内容。|  
|**Dynamics 365 for phones**| Dynamics 365 for phones 以针对手机优化的方式呈现主窗体的内容。|  
|**经典**|这些窗体适用于尚未更新的实体。 这些窗体使用功能区，而不使用命令栏以及窗体左侧的导航窗格。<br /><br /> 这些窗体采用两栏布局。|  
  
<a name="BKMK_MainFormComponentsForUpdatedEntities"></a>   
## <a name="updated-forms"></a>更新的窗体  
 此图展示了更新的实体窗体中的常用组件。  
  
 ![图表显示 Dynamics 365 中的更新实体窗体结构](media/updated-form-diagram.png "图表显示 Dynamics 365 中的更新实体窗体结构")  
  
 对于更新的实体，窗体的布局可适应广泛的显示屏和窗口大小。 当窗口宽度减少时，选项卡列会下移，从而可以向下滚动来使用它们，而无需压缩或者滚动到右侧。  
  
 下表汇总了更新的实体的主窗体的可用组件。  
  
|组件|摘要|  
|---------------|-------------|  
|**导航栏**|使用站点地图中的数据以支持移动到应用程序的不同区域。<br /><br /> 在经典窗体中使用的导航窗格未包括在更新的窗体中。 在记录的上下文中，导航栏提供对相关记录的视图的访问。 不需要使用导航窗格或导航栏导航到相关记录，添加配置的子网格即可显示有用的相关实体记录，从而可为大多数人提供更好的体验。|  
|**命令栏**|使用为功能区定义的数据为记录提供相关命令。<br /><br /> 前五个命令显示时后跟一个省略号 (![“更多命令”按钮](media/not-available.gif "更多命令按钮"))，可提供弹出式菜单来选择其他命令。|  
|**图像**|如果实体有图像字段，并且实体**主图像** 选项设置为**默认图像** ，则当将窗体配置为显示图像时，图像可以在标题中显示。|  
|**页眉**|放在标题中的字段在用户向下滚动到窗体的主体时仍然可见。<br /><br /> 标题中最多可放四个字段。 标题中不允许有多行文本、Web 资源或 iFrame。 标题和脚注与分区有一些共同的属性。|  
|**流程控件**|如果某个实体有活动的业务流程，则会在标题下显示流程控件。 详细信息：[业务流程](/flow/business-process-flows-overview)|  
|**正文**|主体是窗体可滚动的部分，其中包含选项卡。|  
|**选项卡**|在窗体的主体中，选项卡提供水平分隔。 选项卡有一个可显示的标签。 如果显示了标签，则可通过选择标签来展开或折叠选项卡，以显示或隐藏其内容。<br /><br /> 选项卡最多包含三栏，每栏的宽度可设置为总宽度的百分比。 创建新选项卡时，每个栏会预填充一个分区。|  
|**节**|分区占据选项卡栏中的可用空间。 分区有一个可显示的标签，该标签下可能会显示一条线。<br /><br /> 分区最多可以有四栏，并包括用于显示分区中字段标签显示方式的选项。|  
|**字段**|字段显示控件，用户用于查看或编辑实体记录中的数据。 可以将字段格式设置成在分区中最多占用四栏。|  
|**空格**|空格可用于向分区栏中添加空白空间。|  
|**子网格**|子网格可用于显示窗体中的列表。 使用子子网格显示图表的功能在更新的实体的窗体中不可用。|  
|**快速视图窗体**|快速视图窗体显示窗体上查找字段引用的记录中的数据。 作为查找目标的实体必须要有一个快速视图窗体，然后才能将其添加到窗体中。 详细信息：[创建和编辑快速视图窗体](create-edit-quick-view-forms.md)|  
|**Web 资源**|可将 HTML 和 Microsoft Silverlight Web 资源添加到主窗体中，但它们不会在使用 Dynamics 365 for phones and tablets 时显示。|  
|**iFrame**|您配置为显示另一网站的网页的内联框架。 **重要提示：**  <ul><li>在 iFrame 中显示的页面在其他域时，适用于安全性更高的级别浏览器。 这可能使 iFrame 的内容在与窗体的数据交互的要求更加复杂化。</li><li>不支持在另一个实体窗体中显示嵌入 iFrame 的实体窗体。 
|**Bing 地图**|当此控件出现在更新的实体的窗体中，并且系统设置**启用 Bing 地图** 使用有效的 Bing 地图密钥启用时，可以在窗体中使用一次此控件来显示某个更新的实体中的某个地址的位置。 详细信息：[配置必应地图](configure-bing-maps-legacy.md)|  
|**页脚**|可以向脚注中添加任意数量的字段、Web 资源或 iFrame。 在脚注中显示的字段是只读的。 标题和脚注与分区有一些共同的属性。|  
|**状态栏**|状态栏显示记录的状态字段、通知区域和保存按钮。|  
  
<a name="BKMK_CRMforTabletsPresentation"></a>   
## <a name="dynamics-365-for-phones-and-tablets-forms"></a>适用于手机和平板电脑的 Dynamics 365 窗体  
 大多数系统实体和自定义实体可用于 Dynamics 365 for phones and tablets。 这些实体的主窗体已转换为针对手机或平板电脑优化的表示形式。  
  
<a name="BKMK_EntitiesEnabledForCRMForTablets"></a>   
### <a name="entities-enabled-for-dynamics-365-for-phones-and-tablets"></a>为适用于手机和平板电脑的 Dynamics 365 启用的实体  
 只有为 Dynamics 365 for phones and tablets 启用的实体才使用主窗体的这种表示形式。 详细信息：[在 Dynamics 365 for phones and tablets 中显示的实体](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_CustomEntity)  
  
### <a name="form-design"></a>窗体设计  
 Dynamics 365 for phones and tablets 采用了许多主窗体元素，并以针对手机或平板电脑优化的方式呈现它们。 下图显示了从 Web 应用程序到平板电脑和手机应用程序的回流。  
  
 **Web 应用程序**  
  
 ![Dynamics 365 窗体从 Web 应用程序回流](media/custon-reflow-web-app.png "Dynamics 365 窗体从 Web 应用程序回流")  
  
 **平板电脑应用程序**  
  
 ![Dynamics 365 窗体回流到平板电脑应用程序](media/reflow-tablet-app.png "Dynamics 365 窗体回流到平板电脑应用程序")  
  
 **手机应用程序**  
  
 ![Dynamics 365 窗体回流到手机应用程序](media/custon-reflow-phone-app.png "Dynamics 365 窗体回流到手机应用程序")  
  
 窗体元素在 Dynamics 365 for tablets 中转换为广角全景布局，用户可在其中扫动屏幕来更改视口中的可见元素。 在 Dynamics 365 for phones 中，用户扫动屏幕查看其他元素的列或窗格，流程控制显示在每个列上方。  
  
### <a name="view-port-element"></a>视口元素  
 在窗体的上下文中，以下项目在视口中始终可见：  
  
 **导航栏**  
 导航栏是针对触屏优化的网站地图表示形式。 详细信息：[更改导航选项](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_NavigationOptions)  
  
 **主页**  
 家庭按钮将用户带到仪表板，其是 Dynamics 365 for phones and tablets 的启动页面。  
  
 **流程控件**  
 如果实体启用了业务流程，则将在 Dynamics 365 for tablets 中搜索控件旁边的右上角，以及 Dynamics 365 for phones 中屏幕顶部显示。  
  
 **搜索**  
 用户可以点按搜索控件，打开屏幕以搜索记录。  
  
 **命令栏**  
 默认情况下，显示在 Web 浏览器中运行的应用中的某些命令不会显示在 Dynamics 365 for phones and tablets 应用程序中。 类似于 Web 应用程序，命令栏是上下文相关的，而且根据当前显示的视图和选择类型，可用命令也是会有所变化的。 详细信息[更改命令](https://docs.microsoft.com/dynamics365/customer-engagement/customize/customize-phones-tablets#BKMK_ChangeCommands)  
  
### <a name="form-elements"></a>窗体元素  
 显示的窗体元素取自主窗体，并呈现为用户可通过视口看到的一系列面板。  
  
 在 Dynamics 365 for tablets 中，第一个面板显示有关记录存在的关系的联系信息。 在 Dynamics 365 for phones 中，第一个面板还显示关系磁贴上方窗体的标题字段。  
  
 ![适用于平板电脑的 Dynamics 365 的关系面板](media/mobile-app-form-relationships.png "适用于平板电脑的 Dynamics 365 的关系面板")  
  
 对于“联系人”和“用户”窗体，顶层项目显示记录的通信卡。 通信卡提供用于发起与用户的通信的按钮。 对于其他实体，如果主窗体中嵌入了“联系人”快速视图窗体，则将显示通信卡。  
  
 可以根据实体关系显示其他磁贴，但是，您不能自定义下列实体的磁贴：  
  
|实体|磁贴|  
|------------|-----------|  
|客户|负责人 |  
|联系人|公司名称，负责人|  
|潜在顾客|负责人 |  
|商机​​|帐户，负责人|  
  
 您可以使用窗体编辑器自定义其余磁贴。 顺序是固定的，但是，您可以设置哪些元素在关系面板中可见。  
  
 在 Dynamics 365 for tablets 中，第二个面板以窗体上第一个选项卡的名称开头。 标题中包括的所有字段都包括在内，然后是第一个选项卡的内容。在 Dynamics 365 for phones 中，标题在第一列中显示。  
  
 ![适用于平板电脑的 CRM 的第一个面板](media/mobile-app-form-first-panel.png "适用于平板电脑的 CRM 的第一个面板")  
  
 如果窗体有一个活动的流程，则第三个选项卡将在 Dynamics 365 for tablets 中显示该流程当前阶段的任务。 在 Dynamics 365 for phones 中，流程控件浮动在窗格上方，被选中时会在用户当前窗格上展开，其始终可见、可操作。  
  
 窗体的其余面板将包含窗体中选项卡的内容。 现有的任何子网格显示为单独的面板。  
  
 Dynamics 365 for phones and tablets 的窗体始终显示选项卡和子网格的标签。 不应用**在窗体上显示标签** 设置。  
  
> [!NOTE]
>  若要优化在移动设备中的性能，对象数量应限制为 5 个选项卡或 75 个字段和 10 个子网格。  
  
 Dynamics 365 for phones and tablets 的窗体不支持以下操作：  
   
-   Bing 地图  
  
-   Yammer
  
-   活动源  
  
-   主题化  
  
 此外，实体图像会在列表视图和联系人卡片中显示，但不会在实际窗体中显示。  
  
<a name="BKMK_MultipleForms"></a>   
### <a name="multiple-forms"></a>多个窗体  
 Dynamics 365 for phones and tablets 支持多个窗体，但不向可以访问多个窗体的用户提供在窗体之间切换的方式。 用户将按其有权访问的窗体顺序看到第一个窗体。  
  
 例如，如果您有商机实体的以下主窗体，并且分派有每个主窗体的以下安全角色，则将看到下表中所示的窗体顺序。  
  
|窗体顺序|表单名称|安全角色|  
|----------------|---------------|--------------------|  
|1|**销售窗体一**|销售员|  
|2|**销售窗体二**|销售员和销售经理|  
|3|**销售窗体三**|销售经理|  
|4|**销售窗体四**|销售副总裁|  
  
-   具有销售员角色的人将始终看到**销售窗体一**。  
  
-   具有销售经理角色的人将始终看到**销售窗体二**。  
  
-   具有销售副总裁角色的人将始终看到**销售窗体四**。  
  
<a name="BKMK_ClassicPresentation"></a>   
## <a name="classic-forms"></a>经典窗体  
 下图显示了经典表示形式中使用的主窗体组件。  
  
 ![主要窗体元素](media/elements.png "主要窗体元素")  
  
 更新的实体的窗体从经典窗体继承了许多组件，但存在明显的区别。  
  
 使用经典表示形式的窗体不包括导航栏，并且使用功能区而不是命令栏。 这些窗体不支持实体图像、流程控件、快速视图窗体、自动保存或 Bing 地图。 标题中的字段不可编辑。  
  
 窗体助理向特定实体（如 `Article`）公开。  
  
## <a name="next-steps"></a>后续步骤  
 [创建和设计窗体](create-design-forms.md)   

 
