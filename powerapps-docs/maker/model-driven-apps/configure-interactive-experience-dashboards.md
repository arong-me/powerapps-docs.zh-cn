---
title: 配置 PowerApps 中模型驱动应用程序的交互式体验仪表板 | Microsoft Docs
description: 了解如何配置 PowerApps 中的交互式体验仪表板
keywords: 交互式仪表板; Customer Service; Microsoft Dynamics 365; 交互式服务中心
author: Mattp123
ms.author: matp
manager: kvivek
ms.custom: ''
ms.date: 05/21/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: d1446a95-14bf-4b15-a905-72fce07f4c76
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-model-driven-app-interactive-experience-dashboards"></a>配置模型驱动应用程序的交互式体验仪表板

交互式体验仪表板可以成为应用用户（如服务代表）查看工作负荷信息和采取行动的一站式工作区。 它们完全可配置，以安全角色为基础，且可跨多个流实时传送工作负荷信息。 交互式仪表板用户不需要在应用程序中翻页查找特定记录；他们可以直接从仪表板执行操作。 

 交互式体验仪表板有两种形式：多流和单流。 此外，多流仪表板可以是主页仪表板或实体特定仪表板。 实体特定仪表板是在用户界面的不同部分中配置的，且部分预加载了特定于实体的配置信息。  
  
 多流仪表板通过多个数据流实时显示数据。 您可以在仪表板上配置的流的数量没有限制。 一个流中的数据只能基于一个实体，但每个流可以基于一个不同的实体。 在实体特定仪表板中，所有流均基于同一实体。 数据从各种视图或队列中流出，例如**我的活动**、**我的案例**或**银行队列中的案例**。 
  
 单流仪表板通过一个基于实体视图或队列的流来显示实时数据。 磁贴位于仪表板的右侧，并且始终都会显示。 单流仪表板通常对第 2 层服务领导或经理很有帮助，他们监控数量较少但更复杂或已升级的案例。  
  
 多流仪表板和单流仪表板包含提供相关记录的数目的交互式图表（例如按优先级或按状态显示的案例）。 这些图表也充当可视筛选器。 可视筛选器（交互式图表）基于多个实体且位于单流仪表板中，数据流中的实体定义了可视筛选器实体。   
  
 用户可以通过全局筛选器和期限筛选器应用更多筛选。 全局筛选器在字段级别上对所有图表起作用，也对基于筛选器实体（您在配置可视筛选器时指定筛选器实体）的流和磁贴起作用。 
  
> [!NOTE]
>  交互式仪表板可识别解决方案，并可作为一个解决方案导出然后导入到不同的环境。 但是，流和磁贴所基于的队列不可识别解决方案。 在将仪表板解决方案导入到目标系统之前，必须通过**设置** > **服务管理** > **队列**在目标系统中手动创建队列。 在创建队列后，将仪表板解决方案导入到目标系统，然后编辑基于队列的流或磁贴，以正确地分配新创建的队列。  
  
 本主题中的插图用标头窗格显示多流仪表板和单流仪表板。 在标题下面您将看到可视筛选器和流。 在单流仪表板中，您还会看到磁贴。 对于每个仪表板类型，还显示了若干不同的布局，您可以从中进行选择。 仪表板标头包含了以下控件和可选择的图标，从左至右分别为：仪表板选取器、刷新、可视筛选器图标、全局筛选器图标和时间范围筛选器。  
  
### <a name="multi-stream-dashboard-standard-view"></a>多流仪表板标准视图  
 在多流仪表板中，您将看到顶部有一行可视筛选器，其下方是数据流。  
 
![多流交互式仪表板](../model-driven-apps/media/interactive-dashboards-multi-stream.png) 
   
### <a name="multi-stream-dashboard-tile-view"></a>多流仪表板磁贴视图  
 同一个仪表板，只不过是在磁贴视图中。  
  
 ![多流交互式仪表板磁贴视图](../model-driven-apps/media/interactive-dashboards-multi-stream-tiles.png "多流交互式仪表板磁贴视图")  
  
### <a name="multi-stream-dashboard-layouts"></a>多流仪表板布局  
 对于多流仪表板，您可以从四种不同的布局中进行选择。  

 > [!div class="mx-imgBorder"] 
 > ![多流仪表板布局](../model-driven-apps/media/interactive-dashboards-multi-stream-layout.png "多流仪表板布局")  
  
### <a name="multi-stream-entity-specific-dashboard"></a>多流实体特定仪表板  
 此处显示了 `Case` 实体的实体特定仪表板。  
  
 ![打开案例仪表板](../model-driven-apps/media/interactive-dashboard-cases-dashboard.PNG "打开案例仪表板")  
  
### <a name="single-stream-dashboard"></a>单流仪表板  
 单流仪表板由左侧的数据流和右侧的可视筛选器和磁贴组成。  
  
 ![单流交互式服务中心仪表板](../model-driven-apps/media/interactive-dashboards-single-stream.png "单流交互式服务中心仪表板")  
  
### <a name="single-stream-dashboard-layouts"></a>单流仪表板布局  
 对于单流仪表板，您可以从四种不同的布局中进行选择。  
 
 > [!div class="mx-imgBorder"] 
 > ![单流仪表板布局。](../model-driven-apps/media/interactive-dashboards-single-stream-layout.png "单流仪表板布局。")  
  
<a name="BKMK_Enable"></a>   
## <a name="configure-entities-fields-and-security-roles-for-the-interactive-dashboards"></a>为交互式仪表板配置实体、字段和安全角色  
 在配置交互式仪表板时，您的第一个任务是为交互式体验启用实体、字段和安全角色。  
  
### <a name="entities-enabled-for-interactive-experience"></a>为交互式体验启用的实体
 统一接口中支持的所有实体都为交互式体验仪表板启用。
  
### <a name="configure-fields"></a>配置字段  
 若要在全局筛选器中显示某个字段并在数据流排序中包含该字段，您必须设置两个标志，如下面有关案例实体的 **IsEscalated** 字段的示例所示。  

 > [!div class="mx-imgBorder"] 
 > ![为全局筛选器和排序启用字段](../model-driven-apps/media/global-filter-sort-8.png "为全局筛选器和排序启用字段")  
  
### <a name="configure-global-filter-fields"></a>配置全局筛选器字段  
 若要在全局筛选器中显示某个字段，您必须为此字段设置**以交互式体验的形式显示在全局筛选器中**。 当单击仪表板标头上的全局筛选器图标时，您配置的字段将在全局筛选器浮出控件窗口中显示。 在浮出控件窗口中，服务代表可以选择他们要在图表中，以及在基于筛选器实体的流和磁贴中对其进行全局筛选的字段。 有关筛选器实体的详细信息，请参阅本主题后面的“配置多流交互式仪表板”部分。  
  
 此处显示全局筛选器浮出控件窗口：  
  
 ![添加两个全局筛选器字段](../model-driven-apps/media/interactive-dashboards-global-filter-two-fields.png "添加两个全局筛选器字段")  
  
> [!NOTE]
>  当您基于优先级或状态等字段配置可视筛选器（交互式图表）时，最好还启用这些字段（优先级、状态）以便在全局筛选器中显示。  
  
以下过程提供了设置全局筛选器标志的步骤：
  
1. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2. 在**组件**下，展开**实体**，然后展开所需实体。 如果您需要的实体未显示，请选择**添加现有**来添加它。  
  
3.  在导航窗格中，选择**字段**，然后在网格中，双击要启用的字段。  
  
4.  在**常规**选项卡中，选中**以交互式体验的形式显示在全局筛选器中**复选框。 选择**保存并关闭**。  
  
5.  选择**发布**以便使所做的更改生效。  
  
6.  选择**准备客户端自定义**。  
  
### <a name="configure-sortable-fields"></a>配置可排序字段  
 若要在排序流数据中使用某个字段，您必须为此字段设置**在交互式体验仪表板中可排序**标志。 当用户选择流标头上的**更多 (…)** 时，您为排序配置的字段将在**编辑属性**浮出控件对话框中的下拉列表中显示。 以下插图显示了浮出控件对话框，并在**排序依据**下拉列表中显示了可用于排序的字段的列表。 默认排序始终在**修改时间**字段上设置。  
  
 ![按下拉列表排序](../model-driven-apps/media/interactive-dashboard-sortable-fields-dropdown.png "按下拉列表排序")  
  
以下过程提供了设置排序标志的步骤：
  
1. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。   
2. 在**组件**下，展开**实体**，然后展开所需实体。 如果您需要的标准实体未显示，请选择**添加现有**来添加它。  
  
3.  在导航窗格中，选择**字段**，然后在网格中，双击要启用的字段。  
  
4.  在**常规**选项卡中，选中**在交互式体验仪表板中可排序**复选框。 选择**保存并关闭**。  
  
5.  选择**发布**以便使所做的更改生效。  
  
6.  选择**准备客户端自定义**。  
  
### <a name="enable-security-roles"></a>启用安全角色  
 选择并启用能够查看交互式仪表板的安全角色。  
  
以下过程提供了为交互式体验启用安全角色的步骤：
  
1. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2. 在**组件**下，选择**仪表板**。  
  
4.  在网格中，选择所需的交互式仪表板并选择任务栏上的**启用安全角色**。  
  
5.  在**分派安全角色**对话框，选择**仅向这些选定安全角色显示**选项，然后选择要启用的角色。 选择**确定**。  
  
6.  选择**发布**以便使所做的更改生效。  
  
7.  选择**准备客户端自定义**。  
  
 ![启用安全角色](../model-driven-apps/media/interactive-dashboards-enable-security-roles.png "启用安全角色")  
  
 ![分派安全角色](../model-driven-apps/media/interactive-dashboards-assign-security-roles.png "分派安全角色")  
  
<a name="BKMK_Configure"></a>   
## <a name="configure-interactive-experience-dashboards"></a>配置交互式体验仪表板  
 以下部分介绍如何配置各种类型的交互式仪表板。  
  
### <a name="configure-a-multi-stream-interactive-dashboard-using-the-4-column-layout"></a>使用 4 列布局来配置多流交互式仪表板  
 
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2.  选择**模型驱动**（左下方）。  
  
3.  选择**数据** > **实体** > 选择所需实体。 

4.  选择**仪表板**选项卡，然后在工具栏上选择**添加仪表板**。  
  
5.  选择布局，2、3 或 4 列宽。  
  
6.  仪表板窗体打开后，在窗体的顶部填写筛选信息，如下所示。  
 
 > [!div class="mx-imgBorder"] 
 > ![添加可视筛选器](../model-driven-apps/media/interactive-dashboards-add-visual-filters.png "添加可视筛选器")  
  
   - **筛选器实体**：可视筛选器（交互式图表）和全局筛选器属性基于此实体。  
      
    - **实体视图**：可视筛选器（交互式图表）基于此视图。  
      
    - **筛选依据**：对其应用时间范围筛选器的字段。  
      
    - **时间范围**：**筛选依据**字段的默认时间范围筛选器值。  
      
 指定筛选信息后，请开始为图表和数据流添加组件。 若要添加组件，只需选择图表或流中间的元素，当对话框出现时，输入所需的信息，如以下插图所示。  
  
 添加**按优先级列出的案例**圆环图。
  
 > [!div class="mx-imgBorder"] 
 > ![添加环形图组件。](../model-driven-apps/media/interactive-dashboards-add-chart-circle.png "添加环形图组件。")  
  
 某些图表（例如条形图或饼图）呈现了系统中的数据存储。 圆环图和标记图作为静态图像加载，不会显示实际数据的预览。  
  
> [!NOTE]
>  为可视筛选器配置的图表可以使用**筛选器**实体以及相关实体的字段。 当您使用基于相关实体字段的图表时，客户服务代表可使用这些相关实体字段筛选图表。 基于相关实体的字段通常具有以下格式的图表配置窗口：“字段名称（实体名称）”，如**修改者(代理)** 字段。 若要创建多实体图表，必须将相关实体的字段添加至任何视图，然后在创建图表时使用这些字段。  
 
 > [!div class="mx-imgBorder"] 
 > ![为可视筛选器创建图表](../model-driven-apps/media/interactive-dashboard-visual-charts-x-y-axes.PNG "为可视筛选器创建图表")  
  
 接下来，配置流。 就像在图表中添加组件一样，选择流面板内的元素。 当对话框出现时，根据您想要流使用的元素，选择**视图**或**队列**。 输入所需信息，如以下插图所示。  
  
> [!NOTE]
>  **队列**选项在仅适用于启用队列的实体的对话框中可用。 对于实体仪表板，如果实体未启用队列，将不会在对话框中看到**队列**选项。 对于未启用队列的实体，只可使用仪表板流中的**视图选项**。  
  
 为**可供处理的项**配置流，如下所示：  
  
 ![添加“我的可用案例”流。](../model-driven-apps/media/interactive-dashboards-add-stream-case.png "添加“我的可用案例”流。")  
  
 下图是图表面板的示例，从左至右分别为：圆环图、标记图和条形图：  
 
 > [!div class="mx-imgBorder"] 
 > ![所有交互式图表](../model-driven-apps/media/interactive-dashboards-add-all-charts.png "所有交互式图表")  
  
 此插图是具有若干流的流面板的一个示例：  
 
 > [!div class="mx-imgBorder"] 
 > ![添加所有流](../model-driven-apps/media/interactive-dashboards-add-all-streams.png "添加所有流")  
  
 完成配置仪表板后，请保存它然后发布自定义项，以便使所做的更改生效。 此外，请确保选择**准备客户端自定义**。  
  
#### <a name="edit-or-delete-individual-streams-of-an-existing-dashboard"></a>编辑或删除现有仪表板的单个流  
  
1. 登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。   
  
2. 选择**模型驱动**（左下方）、**数据** > **实体** > 选择所需实体。 选择**仪表板**选项卡。  
  
     -或-  
   
   打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)，然后在**组件**下选择**仪表板**。
  
3.  在网格中，选择要编辑的交互式仪表板，以将其打开。  
  
4.  选择要编辑的流以选中它，然后选择**编辑组件**。  
  
5.  根据您想要将视图还是队列添加至流，选择流的视图或队列详细信息，然后选择**设置**。  
  
6.  选择**保存**。  
  
 您还可从仪表板删除单个流。 为此，选择该流，然后在命令栏上，选择**删除**。  
  
### <a name="configure-an-entity-specific-dashboard"></a>配置实体特定仪表板  
 实体特定仪表板是多流仪表板。 配置此仪表板类似于配置主页多流仪表板，但您要在 UI 中的不同位置执行此操作，还有其他细微差异。 例如，实体特定仪表板中的某些字段已预设为您为其创建仪表板的实体，您不必选择实体。  
  
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2.  选择**模型驱动**（左下方）。  
  
3.  选择**数据** > **实体** > 选择所需实体。 

4.  选择**仪表板**选项卡，然后在工具栏上选择**添加仪表板**。  
  
5.  选择布局，2、3 或 4 列宽。    
  
6.  当仪表板窗体打开时，**筛选器实体**将预设为您为其创建仪表板的实体。 **实体视图**下拉列表包含该实体的可用视图。 选择视图并在页面上填写剩下的必需信息。  
  
 剩下的设置与上一部分中所述的主页多流仪表板设置十分相似。  
  
### <a name="configure-a-single-stream-dashboard"></a>配置单流仪表板  
 配置单流仪表板与配置多流仪表板类似。 所有 UI 导航步骤均与多流仪表板的相同。 您可以选择包含磁贴的布局，也可以选择不包含磁贴的布局。 如果包含磁贴，则磁贴将始终在仪表板上显示。 若要配置磁贴，请选择磁贴中间的图标。 当**添加磁贴**窗口打开时，请填写所需数据。 下图是磁贴设置的一个示例。  
  
 ![向单流仪表板添加磁贴](../model-driven-apps/media/interactive-dashboard-add-tile-single-stream.png "向单流仪表板添加磁贴")  
  
<a name="BKMK_ConfigureColors"></a>   
## <a name="configure-dashboard-colors"></a>配置仪表板颜色  
 对于所有**选项集**和**两个选项**类型字段（如 `Case` 实体的**案例类型**、**IsEscalated**或**优先级**），您可以配置某个特定颜色，该颜色将在图表和流中针对特定字段值显示。 例如，在交互式图表中，高优先级案例可以显示为红色，中优先级案例可以显示为蓝色，低优先级案例可以显示为绿色。 在流中，工作项说明旁边的颜色中将有一条细竖线。  
  
> [!NOTE]
>  颜色编码不可用于标记图和圆环图。 这些图表在仪表板上显示为白色、灰色和黑色阴影。  
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
2.  在**组件**下，展开**实体**，然后展开所需实体。 如果您需要的实体未显示，请选择**添加现有**来添加它。  
  
3.  在导航窗格中，选择**字段**。 在网格中，双击要为其配置颜色的字段。  
  
4.  在**常规**选项卡中的**类型**子区域中，选择**是**然后选择**编辑**。  
  
5.  当**修改列表值**对话框出现时，在**颜色**文本框中设置新值。 选择**确定**。  
  
     选择**保存并关闭**。  
  
7.  选择**发布**以便使所做的更改生效。  
  
在以下示例中，我们将更改**IsEscalated**字段的颜色。 使用**编辑**按钮打开**修改列表值**对话框：  
 
 > [!div class="mx-imgBorder"] 
 > ![更改仪表板中的颜色](../model-driven-apps/media/interactive-dashboards-change-color-edit-button.PNG "更改仪表板中的颜色")  
  
当**修改列表值**对话框打开时，选择颜色，如下所示：  
  
 ![修改仪表板颜色](../model-driven-apps/media/interactive-dashboards-modify-color-value.png "修改仪表板颜色")  
  
### <a name="next-steps"></a>后续步骤  
 
[创建或编辑仪表板](create-edit-dashboards.md)
 
