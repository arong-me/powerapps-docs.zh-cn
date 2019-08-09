---
title: 在 PowerApps 中使用模型驱动应用程序的主窗体及其组件 | Microsoft Docs
description: 了解如何在基于统一接口的应用中使用主窗体及其组件
keywords: 主窗体；Customer Service；客户服务中心；Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 43bfface-4dc2-411d-99a1-83e934646989
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-model-driven-app-main-form-and-its-components"></a>使用模型驱动应用程序的主窗体及其组件

基于统一接口的应用中的窗体提供提供最优代理生产力的改进的用户体验，并可帮助在处理相关记录时维护上下文。 您可在解决方案资源管理器中查看加入的窗体。 新窗体的窗体类型为**主**。

本主题介绍了如何编辑“主”窗体，以及如何添加或更改窗体的各个元素。

## <a name="open-the-form-editor"></a>打开窗体编辑器

若要编辑窗体或者添加或更改元素，请使用窗体编辑器。 窗体编辑器让您可以编辑所有基于统一接口的应用的窗体。

请按照下方给出的过程访问窗体编辑器。 

> [!NOTE]
> 如果在编辑窗体的过程中创建任何新的解决方案组件，则组件的名称将使用默认解决方案的解决方案发布商自定义前缀，并且这些组件将仅包含在默认解决方案中。 如果要将任何新的解决方案组件包含在某个特定的非托管解决方案中，则应通过该非托管解决方案打开窗体编辑器。


### <a name="access-the-form-editor-through-app-designer-in-powerapps"></a>在 PowerApps 中通过应用程序设计器访问窗体编辑器

1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2.  在左侧导航窗格上选择**应用程序**，选择所需的应用程序，然后在工具栏上选择**编辑**。  

3. 在应用设计器区域中，选择向下键 ![应用程序设计器的向下箭头](media/down-arrow-app-designer.png) 在实体旁边查看可用于该实体的窗体。 

4. 选择打开设计器按钮 ![打开与](media/site-map-designer.png)要编辑的窗体对应的设计器。

   ![应用程序设计器中的窗体编辑器](media/app-designer-forms.png)
 
5. 在窗体设计器中，进行更改然后选择**保存**保存更改，然后选择**发布**发布它们以在应用程序中使用。 

> [!NOTE]
> 如果您对应用进行了其他更改，请使用应用级发布选项发布更改。 请参阅[使用应用程序设计器验证和发布应用程序](validate-app.md)以了解详细信息。

> [!NOTE]
> Webclient 主窗体还与客户服务中心兼容，并可使用应用程序设计器编辑。


### <a name="access-the-form-editor-through-the-default-solution"></a>通过默认解决方案访问窗体编辑器

1.  登录到 [PowerApps](https:///?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。  

3. 在窗体列表中，打开**主**类型的窗体。

### <a name="access-the-form-editor-for-an-unmanaged-solution"></a>访问非托管解决方案的窗体编辑器

1. 打开[解决方案](advanced-navigation.md#solutions)。
2. 双击要使用的非托管解决方案。 解决方案类型（托管或非托管）显示在**包类型**列中。
3. 在组件列表，使用要编辑的窗体找到实体。 如果没有实体，则需要添加实体。

#### <a name="add-an-entity-to-an-unmanaged-solution"></a>将实体添加到非托管解决方案

1. 在解决方案资源管理器中打开非托管解决方案，选择**实体**节点，并在列表上方的工具栏上，选择**添加现有**。

     > [!div class="mx-imgBorder"] 
     > ![添加现有实体](media/add-existing-entity.png)

2. 在**选择解决方案组件**对话框中，将**组件类型**选择器设置为**实体**，选择要添加的实体，然后选择**确定**。

3. 出现**缺少必需组件**对话框时，如果不打算将此非托管解决方案导出到其他组织，则可选择**否，不包含必需组件** 。 如果此时您不想包含缺少的必需组件，可以在以后添加这些组件。 将来导出此解决方案时，您会再次收到通知。

4. 在解决方案资源管理器中，展开具有要编辑的窗体的实体，然后选择**窗体** 。

5. 在窗体列表中，打开**主**类型的窗体。

#### <a name="publish-the-changes-for-use-in-the-app"></a>发布更改以在应用中使用

有些对用户界面进行更改自定义项需要先发布，然后用户才能在应用程序中使用它们。 要发布您的自定义项，请在解决方案资源管理器工具栏上选择**发布所有自定义项**。

## <a name="form-editor-user-interface"></a>窗体编辑器用户界面

若要详细了解窗体编辑器用户界面，请参阅[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)。

## <a name="form-properties"></a>窗体属性

若要详细了解窗体属性，请参阅[窗体属性](form-properties-legacy.md)。

## <a name="visibility-options"></a>可见性选项  
 多种窗体元素类型有默认显示或隐藏的选项。 选项卡、分区和字段都提供了此选项。 通过使用窗体脚本或业务规则，可以控制这些元素的可见性来创建动态窗体，从而提供适应窗体中条件的用户界面。 
  
> [!NOTE]
>  建议不要通过隐藏窗体来加强安全性。 隐藏元素时，用户可通过多种方式查看窗体中的所有元素和数据。 若要了解详细信息，请参阅[显示或隐藏窗体元素](visibility-options-legacy.md)。 
  
## <a name="tab-properties"></a>选项卡属性  

在窗体的主体中，选项卡提供水平分隔。 选项卡有一个可显示的标签。 如果显示了标签，则可通过选择标签来展开或折叠选项卡，以显示或隐藏其内容。 若要详细了解选项卡属性，请参阅[选项卡属性](tab-properties-legacy.md)。


## <a name="section-properties"></a>分区属性  

窗体中的分区占据选项卡栏中的可用空间。 分区有一个可显示的标签，该标签下可能会显示一条线。 若要详细了解分区属性，请参阅[分区属性](section-properties-legacy.md)。
  
## <a name="timeline"></a>时间线  
 日程表显示特定实体的相关活动。  
  
 支持的活动类型包括：任务、约会、电话联络、电子邮件、社交活动、自定义活动。  
  
 日程表还显示注释以及系统和用户公告。 它显示将**相关**字段设置为您正在查看的实体的那些活动。 对于注释，**相关**字段不对用户可见；该字段在日程表中创建之时便是隐式的。  
  
 日程表中显示的每个活动都将包含相同的快速操作（在活动的命令栏上提供）。  

## <a name="common-field-properties"></a>常见字段属性  

若要详细了解常见字段属性，请参阅[常见字段属性](common-field-properties-legacy.md)。 
  
## <a name="special-field-properties"></a>特殊字段属性  
 所有字段都有[常见字段属性](common-field-properties-legacy.md)中列出的属性，但有些字段还有其他属性。 若要了解详细信息，请参阅[特殊字段属性](special-field-properties-legacy.md)。

  
## <a name="sub-grid-properties"></a>子网格属性  

可以配置窗体上的子网格以显示记录列表或图表。 若要详细了解子网格属性，请参阅[子网格属性](sub-grid-properties-legacy.md)。

## <a name="quick-view-control-properties"></a>快速视图控件属性  

窗体上的快速视图控件显示在窗体上的查找中选择的记录中的数据。 若要了解快速视图控件属性，请参阅[快速视图控件属性](quick-view-control-properties-legacy.md)。
  
## <a name="web-resource-properties"></a>Web 资源属性  

您可以添加或编辑表单上的 web 资源，使其对应用用户而言更具吸引力或更有用。 窗体支持的 Web 资源有图像、HTML 文件或 Silverlight 控件。 详细了解 Web 资源属性。 转到 [Web 资源属性](web-resource-properties-legacy.md)。 
  
## <a name="iframe-properties"></a>IFRAME 属性  

可以向窗体添加 iFrame 以便在一个窗体中集成另一网站的内容。 若要详细了解 IFRAME 属性，请参阅 [IFRAME 属性](iframe-properties-legacy.md)。 
  
## <a name="edit-navigation"></a> 编辑导航  
 通过窗体中的导航，用户可以查看相关记录的列表。 每个实体关系都具有控制其是否应显示的属性。 详细信息：[主要实体的导航窗格项](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)
  
 可以在窗体编辑器中覆盖配置为要显示的任何实体关系。  
  
 有关分步说明，请参阅[添加相关实体的窗体导航](add-edit-form-navigation-related-entities.md)。
  
 若要编辑导航，必须先在**主页**选项卡上的**选择** 组中选择**导航**。  
  
 在**关系资源管理器** 中，可以按 1:N（一对多）或 N:N（多对多）关系筛选可用关系，也可以查看所有可用关系。 禁用并选中**仅显示未用关系** 复选框。 因此，您只能添加每种关系一次。  
  
 若要通过**关系资源管理器**添加关系，只需双击要添加的关系，就会将其添加到在导航区中当前选择的关系下面。 双击导航区域中的关系，而您可以更改**显示**区域中的标签。您可以在**名称**选项卡上查看有关该关系的信息。 使用**编辑**按钮可打开实体定义。  
  
 导航区中有五个组。 可以拖动这些组来重新确定其位置，双击它们可以更改标签，但不能删除它们。 这些组仅在其中有内容时显示。 如果您不希望显示某个组，就不要向其添加任何内容。  
  
## <a name="configure-event-handlers"></a>配置事件处理程序  

事件处理程序包括一个对 JavaScript Web 资源的引用，以及一个在 Web 资源内定义的将在事件发生时执行的函数。 若要了解配置事件处理程序的详细信息，请参阅[配置事件处理程序](configure-event-handlers-legacy.md)。 
  
## <a name="next-steps"></a>后续步骤  
 [创建和设计窗体](create-design-forms.md)   
 [创建和编辑快速创建窗体](create-edit-quick-view-forms.md)   
 [创建和编辑快速视图窗体](create-edit-quick-view-forms.md)
