---
title: 创建用于管理项目的应用 | Microsoft 文档
description: 在此任务中，我们将从头开始生成应用。 使用此应用，用户可以分配项目经理并更新项目详细信息。
documentationcenter: na
author: mgblythe
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 06/12/2017
ms.author: mblythe
ms.openlocfilehash: fcf1bcec976e34f07745c315d75569bbc86e583f
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37899516"
---
# <a name="create-an-app-to-manage-projects"></a>创建用于管理项目的应用
> [!NOTE]
> 本文属于介绍如何将 PowerApps、Microsoft Flow 和 Power BI 与 SharePoint Online 结合使用的系列教程。 请确保已阅读[系列介绍](sharepoint-scenario-intro.md)，了解总体情况以及相关下载内容。

在此任务中，我们将从头开始生成应用。 使用此应用，用户可以分配项目经理并更新项目详细信息。 将看到第一个应用中的一些相同控件和公式，但这次更多的是自己生成应用。 虽然此过程更加复杂，但将能学到更多知识，所以我们认为这样的取舍很公平。

> [!TIP]
> 这个方案的[下载包](https://aka.ms/o4ia0f)包含此应用的最终版本 (project-details-app.msapp)。

## <a name="quick-review-of-powerapps-studio"></a>快速回顾 PowerApps Studio
PowerApps Studio 有三个窗格和一个功能区，可以在其中创建应用，就像在 PowerPoint 中创建幻灯片一样：

1. 左侧导航栏：可以显示所有应用屏幕和控件的分层视图，也可以显示屏幕缩略图
2. 中间窗格：包含正在处理的应用屏幕
3. 右侧窗格：可用于设置布局和数据源等选项
4. “属性”下拉列表：可用于选择向其应用公式的属性
5. 编辑栏：可用于添加公式来定义应用行为（就像在 Excel 中一样）
6. 功能区：可用于添加控件和自定义设计元素

![PowerApps Studio](./media/sharepoint-scenario-build-app/04-00-00-powerapps-studio.png)

## <a name="step-1-create-screens"></a>第 1 步：创建屏幕
在进行上面的回顾后，我们将开始生成应用。

### <a name="create-and-save-the-app"></a>创建并保存应用
1. 在 PowerApps Studio 中，依次单击或点击“新建”和“空白应用”下的“手机布局”。
   
    ![空白应用 -> 手机布局](./media/sharepoint-scenario-build-app/04-01-01-blank-phone-app.png)
2. 单击或点击“文件”，打开“应用设置”选项卡。输入名称“项目管理应用”。
   
    ![应用名称](./media/sharepoint-scenario-build-app/04-01-02-app-name.png)
3. 单击或点击“另存为”，确认应用是否将保存到云中，再单击右下角的“保存”。
   
    ![保存到云](./media/sharepoint-scenario-build-app/04-01-03-save-to-cloud.png)

4. 单击或点击右上角的 ![“返回到应用”图标](./media/sharepoint-scenario-build-app/icon-back-to-app.png) ，返回到应用。

### <a name="add-four-screens-to-the-app"></a>向应用添加四个屏幕
在这一步中，我们将为应用创建四个空白屏幕。 我们将使用不同的屏幕布局，具体视屏幕的用途而定。 稍后，我们将添加下面这些屏幕。

| **屏幕** | **用途** |
| --- | --- |
| **SelectTask** |起始屏幕；可转到其他屏幕 |
| **AssignManager** |向已获准的项目分配经理 |
| **ViewProjects** |查看包含摘要信息的项目列表 |
| **UpdateDetails** |查看和更新项目的详细信息 |

1. 在“开始”选项卡上，依次单击或点击“新建屏幕”和“可滚动屏幕”。
   
    ![可滚动屏幕](./media/sharepoint-scenario-build-app/04-01-03a-scrollable-screen.png)
2. 将屏幕重命名为“SelectTask”。
   
    ![重命名屏幕](./media/sharepoint-scenario-build-app/04-01-04-rename-screen.png)
3. 创建和重命名其他屏幕：
   
   1. 依次单击或点击“新建屏幕”和“可滚动屏幕”。 将屏幕重命名为“AssignManager”。
   2. 依次单击或点击“新建屏幕”和“列表屏幕”。 将屏幕重命名为“ViewProjects”。
   3. 依次单击或点击“新建屏幕”和“表单屏幕”。 将屏幕重命名为“UpdateDetails”。
4. 选择“Screen1”旁边的省略号 (...)，再单击或点击“删除”。
   
    ![删除屏幕](./media/sharepoint-scenario-build-app/04-01-04a-delete-screen.png)

此时，应用应如下图所示。

![所有应用屏幕](./media/sharepoint-scenario-build-app/04-01-05-all-screens.png)

## <a name="step-2-connect-to-a-sharepoint-list"></a>第 2 步：连接 SharePoint Online 列表
在这一步中，我们将连接“项目详细信息”SharePoint 列表。 虽然我们在此应用中只使用一个列表，但可以很容易地连接两个列表（若要扩展应用的话）。

1. 在左侧导航栏中，单击或点击“SelectTask”屏幕。
2. 在右侧窗格中，单击或点击“添加数据源”。
   
    ![连接到数据](./media/sharepoint-scenario-build-app/04-02-01-connect.png)
3. 单击或点击“新建连接”。
   
    ![新建连接](./media/sharepoint-scenario-build-app/04-02-02-new-connection.png)
4. 单击或点击“SharePoint”。
   
    ![SharePoint 连接](./media/sharepoint-scenario-build-app/04-02-03-sharepoint-connection.png)
5. 选择“直接连接(云服务)”，再单击或点击“创建”。
   
    ![直接连接(云服务)](./media/sharepoint-scenario-build-app/04-02-03a-sharepoint-cloud.png)
6. 输入 SharePoint URL，再单击或点击“前往”。
   
    ![SharePoint 连接 URL](./media/sharepoint-scenario-build-app/04-02-04-sharepoint-url.png)
7. 选择“项目详细信息”列表，再单击或点击“连接”。
   
    ![选择“项目详细信息”列表](./media/sharepoint-scenario-build-app/04-02-05-sharepoint-lists.png)
   
    此时，右侧窗格中的“数据源”选项卡显示已创建的连接。
   
    ![“数据源”选项卡](./media/sharepoint-scenario-build-app/04-02-06-data-sources.png)

## <a name="step-3-build-the-selecttask-screen"></a>第 3 步：生成“SelectTask”屏幕
在这一步中，我们将使用 PowerApps 提供的一些控件、公式和格式化选项，提供一种可转到应用中其他屏幕的途径。

### <a name="update-the-title-and-insert-introductory-text"></a>更新标题并插入介绍性文字
1. 在左侧导航栏中，选择“SelectTask”屏幕。
2. 在中间窗格中，选择默认“[标题]”，再在编辑栏中将“Text”属性更新为“"Contoso Project Management"”。
   
    ![编辑栏中的“Text”属性](./media/sharepoint-scenario-build-app/04-03-02-text-property.png)
3. 在“插入”选项卡上，单击或点击“标签”，再将标签向下拖到顶部横幅下方。
   
    ![添加标签](./media/sharepoint-scenario-build-app/04-03-03-text-default.png)
4. 在编辑栏中，为此标签设置下列属性：
   
   * “Color”属性的值为“DarkGray”

   * “Size”属性的值为“18”

   * “Text”属性的值为“"Click or tap a task to continue..."”
     
     ![更新标签文本](./media/sharepoint-scenario-build-app/04-03-04-text-updated.png)

### <a name="add-two-navigation-buttons"></a>添加两个导航按钮
1. 在“插入”选项卡上，单击或点击“按钮”，再将按钮拖到标签下方。
   
    ![“添加”按钮](./media/sharepoint-scenario-build-app/04-03-05-button-default.png)
2. 在编辑栏中，为此按钮设置下列属性：
   
   * “OnSelect”属性的值为“Navigate(AssignManager, Fade)”。 运行应用并单击此按钮时，将转到应用中的第二个屏幕，并在切换屏幕时采用淡化效果。

   * “Text”属性的值为“"Assign Manager"”

3. 重设按钮大小以容纳文本。
   
    ![更新按钮文本](./media/sharepoint-scenario-build-app/04-03-06-button-updated.png)
4. 插入另一个按钮，属性如下：
   
   * “OnSelect”属性的值为“Navigate(ViewProjects, Fade)”。

   * “Text”属性的值为“"Update Details"”
     
     ![更新按钮文本](./media/sharepoint-scenario-build-app/04-03-08-buttons-final.png)
     
     > [!NOTE]
     > 虽然此按钮的标签为“更新详细信息”，但会先转到“ViewProjects”屏幕，以选择要更新的项目。

### <a name="run-the-app"></a>运行应用
虽然应用尚不能执行许多操作，但可以根据需要运行应用：

1. 单击或点击“SelectTask”屏幕（应用始终以 PowerApps Studio 预览模式中的选定屏幕为起始屏幕）。

2. 单击或点击右上角的 ![“运行应用”图标](./media/sharepoint-scenario-build-app/icon-run-arrow.png) ，运行应用。

3. 单击或点击一个按钮，转到其他屏幕。

4. 单击或点击右上角的 ![“关闭应用预览”图标](./media/sharepoint-scenario-build-app/icon-close-preview.png) ，关闭应用。

## <a name="step-4-build-the-assignmanager-screen"></a>第 4 步：生成“AssignManager”屏幕
在这一步中，我们将使用库来显示所有已获准但尚未分配有经理的项目。 我们将添加其他控件，以便用户可以分配经理。

> [!NOTE]
>  虽然稍后将在应用中生成支持编辑项目的所有字段（包括经理字段）的页面，但生成这样的屏幕也很棒。

1. 保存到目前为止所做的更改。

2. 在左侧导航栏中，单击或点击“AssignManager”屏幕。

### <a name="update-the-title-and-insert-introductory-text"></a>更新标题并插入介绍性文字

1. 将“[标题]”更改为“分配经理”。

2. 添加具有以下属性的标签：
   
   * “Color”属性的值为“DarkGray”

   * “Size”属性的值为“18”

   * “Text”属性的值为“"Select a project, then assign a manager"”
     
     ![“AssignManager”屏幕布局](./media/sharepoint-scenario-build-app/04-04-01-layout.png)

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>添加用于返回到“SelectTask”屏幕的后退箭头

1. 单击或点击屏幕顶部附近的蓝色条。

2. 在“插入”选项卡上，依次单击或点击“图标”和“向左”。
   
    ![插入向左箭头](./media/sharepoint-scenario-build-app/04-04-02-icon-left.png)

3. 将此箭头移到蓝色条的左侧，并设置下列属性：
   
   * “Color”属性的值为“White”

   * “Height”属性的值为“40”

   * “OnSelect”属性的值为“Navigate(SelectTask, Fade)”

   * “Width”属性的值为“40”
     
     ![添加返回按钮](./media/sharepoint-scenario-build-app/04-04-03-left-arrow.png)

### <a name="add-and-modify-a-gallery"></a>添加和修改库

1. 在“插入”选项卡上，依次单击或点击“库”和“垂直”。
   
    ![添加垂直库](./media/sharepoint-scenario-build-app/04-04-04-gallery.png)

2. 从右侧窗格的“布局”菜单中选择“标题、副标题和正文”。 
   
    ![更改库布局](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    此时，库拥有正确的布局，但仍显示默认示例文本。 接下来，我们将解决此问题。
   
    ![显示默认文本的库](./media/sharepoint-scenario-build-app/04-04-05-gallery-default.png)

3. 为此库设置下列属性：
   
   * “BorderThickness”属性的值为“1”

   * “BorderStyle”属性的值为“Dotted”

   * “Items”属性的值为“Filter('Project Details', PMAssigned="Unassigned")”。 库中仅包含没有分配经理的项目。
     
     ![显示列表文本的库](./media/sharepoint-scenario-build-app/04-04-06-gallery-updated.png)

4. 在右侧窗格中，将字段更新为与以下列表一致：
   
   * **ApprovedDate**

   * **Status**

   * **Title**
     
     ![库字段](./media/sharepoint-scenario-build-app/04-04-07-gallery-fields.png)

5. 适当重设库中标签大小，并从库中首项中删除箭头（无需从此库转到任何位置）。
   
    ![删除箭头图标](./media/sharepoint-scenario-build-app/04-04-07a-remove-arrow.png)
   
    此时，屏幕应如下图所示。
   
    ![已设置格式的库](./media/sharepoint-scenario-build-app/04-04-07b-gallery-size-text.png)

### <a name="change-the-color-of-an-item-if-its-selected"></a>更改选定项的颜色

1. 选择库，并将“TemplateFill”属性设置为“If (ThisItem.IsSelected=true, Orange, White)”。

2. 在库中选择一项。 此时，屏幕应如下图所示。
   
    ![包含选定项的库](./media/sharepoint-scenario-build-app/04-04-08-gallery-selected.png)

### <a name="add-a-label-text-input-and-ok-button-to-submit-manager-assignments"></a>添加用于提交项目经理分配的标签、文本输入框和“确定”按钮

1. 单击或点击一直在处理的库外部。

2. 在“插入”选项卡上，单击或点击“标签”。 将此标签拖到库下面的左侧位置上。 为此标签设置下列属性：
   
   * “Size”属性的值为“20”

   * “Text”属性的值为“"Manager:"”
   
   ![添加“Manager:”标签](./media/sharepoint-scenario-build-app/04-04-09-controls-text.png)

3. 在“插入”选项卡上，依次单击或点击“文本”和“文本输入”。 将此文本输入框拖到库下面的中心位置上。 为此下拉框设置下列属性：
   
   * “Default”属性的值为“""”

   * “Height”属性的值为“60”

   * “Size”属性的值为“20”

   * “Width”属性的值为“250”
   
   ![添加文本输入框](./media/sharepoint-scenario-build-app/04-04-10-controls-text-box.png)

4. 在“插入”选项卡上，单击或点击“按钮”。 将此按钮拖到库下面的右侧位置上。 为此按钮设置下列属性：
   
   * “Height”属性的值为“60”

   * “OnSelect”属性的值为“Patch('Project Details', LookUp('Project Details', ID = Gallery1.Selected.ID), {PMAssigned: TextInput1.Text})”。 有关详细信息，请参阅[公式详解](#formula-deep-dive)。

   * 此公式用于更新“项目详细信息”列表，同时设置“PMAssigned”字段值。

   * “Size”属性的值为“20”

   * “Text”属性的值为“"OK"”

   * “Width”属性的值为“80”
   
   ![添加“确定”按钮](./media/sharepoint-scenario-build-app/04-04-11-controls-button.png)

此时，完成的屏幕应如下图所示。

![完成的“AssignManager”屏幕](./media/sharepoint-scenario-build-app/04-04-12-complete.png)

## <a name="step-5-build-the-viewprojects-screen"></a>第 5 步：生成“ViewProjects”屏幕
在这一步中，我们将更改“ViewProjects”屏幕上库的属性。 此库显示“项目详细信息”列表中的项。 先在此屏幕上选择一项，再在“UpdateDetails”屏幕上编辑详细信息。

1. 在左侧导航栏中，单击或点击“ViewProjects”屏幕。

2. 将“[标题]”更改为“查看项目”。

3. 在左侧导航栏中，单击或点击“ViewProjects”下的“BrowserGallery1”。

4. 从右侧窗格的“布局”菜单中选择“标题、副标题和正文”。 
   
    ![更改库布局](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    此时，库拥有正确的布局，但仍显示默认示例文本。
   
    ![显示默认文本的库](./media/sharepoint-scenario-build-app/04-04-04b-gallery-default.png)

5. 选择“刷新”按钮 ![“刷新”图标](./media/sharepoint-scenario-build-app/icon-refresh.png)，并将“OnSelect”属性设置为“Refresh('Project Details')”。

6. 选择“新建项”按钮 ![“添加新项”图标](./media/sharepoint-scenario-build-app/icon-add-item.png)，并将“OnSelect”属性设置为“NewForm(EditForm1); Navigate(UpdateDetails, ScreenTransition.None)”。

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>添加用于返回到“SelectTask”屏幕的后退箭头

1. 在左侧导航栏中，单击或点击“AssignManager”屏幕。

2. 选择并复制在此屏幕中添加的后退箭头。

3. 将箭头粘贴到“ViewProjects”屏幕中，再将它放置在“刷新”按钮的左侧。 
   
    ![返回按钮](./media/sharepoint-scenario-build-app/04-05-04-left-arrow-v.png)
   
    后退箭头的所有属性都会随之转移，包括“Navigate(SelectTask, Fade)”的“OnSelect”属性。

### <a name="change-the-data-source-for-the-browsegallery1-gallery"></a>更改“BrowseGallery1”库的数据源

1. 选择“BrowseGallery1”库，并将库的“Items”属性设置为“SortByColumns(Filter('Project Details', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))”。
   
    这会将库的数据源设置为“项目详细信息”列表，并按“Title”字段进行搜索和排序。

2. 选择库中首项的 ![“详细信息箭头”图标](./media/sharepoint-scenario-build-app/icon-details-arrow.png)，并将“OnSelect”属性设置为“Navigate(UpdateDetails, None)”。
   
    ![ “ViewProjects”屏幕库 -> 选择首项](./media/sharepoint-scenario-build-app/04-05-05b-gallery-arrow-v.png)

3. 在右侧窗格中，将字段更新为与以下列表一致：
   
   * **Status**

   * **PMAssigned**

   * **Title**
     
     ![库字段](./media/sharepoint-scenario-build-app/04-05-06-gallery-fields.png)
     
     此时，完成的屏幕应如下图所示。
     
     ![完成的“ViewProjects”屏幕](./media/sharepoint-scenario-build-app/04-05-07-viewprojects-final.png)

## <a name="step-6-build-the-updatedetails-screen"></a>第 6 步：生成“UpdateDetails”屏幕
在这一步中，我们将把“UpdateDetails”屏幕上的编辑表单与我们的数据源相连，并更改一些属性和字段。 在此屏幕上，可以编辑在“ViewProjects”屏幕上选择的项目的详细信息。

1. 在左侧导航栏中，单击或点击“UpdateDetails”屏幕。

2. 将“[标题]”更改为“更新详细信息”。

3. 在左侧导航栏中，单击或点击“UpdateDetails”下的“EditForm1”。

4. 为此表单设置下列属性：
   
   * “DataSource”属性的值为“Project Details”

   * “Item”属性的值为“BrowseGallery1.Selected”

5. 在仍选择此表单的情况下，在右侧窗格中单击或点击选中以下字段的复选框，顺序如下：
   
   * **Title**

   * **PMAssigned**

   * **Status**

   * **ProjectedStartDate**

   * **ProjectedEndDate**

   * **ProjectedDays**

   * **ActualDays**
     
     ![“编辑表单”字段](./media/sharepoint-scenario-build-app/04-06-03-edit-fields.png)
6. 选择“取消”按钮 ![“取消”图标](./media/sharepoint-scenario-build-app/icon-cancel.png)，并将“OnSelect”属性设置为“ResetForm(EditForm1); Back()”。

7. 选择“保存”按钮 ![复选标记“保存”图标](./media/sharepoint-scenario-build-app/icon-check-mark.png)，并检查“OnSelect”公式是否为“SubmitForm(EditForm1)”。 由于我们使用的是“编辑表单”控件，因此可以使用“Submit()”，而不是我们之前使用的“Patch()”。

此时，完成的屏幕应如下图所示（如果字段为空白，请务必在“ViewProjects”屏幕上选择一项）。

![“UpdateDetails”屏幕已完成](./media/sharepoint-scenario-build-app/04-06-06-edit-final.png)

## <a name="step-7-run-the-app"></a>第 7 步：运行应用
至此，应用已创建完成。我们将运行应用，看看它能否正常运行。 我们将在 SharePoint 网站上添加应用链接。 虽然可以在浏览器中运行应用，但可能必须先共享应用，然后其他人才能运行。 有关详细信息，请参阅[共享应用](https://powerapps.microsoft.com/guided-learning/learning-manage-share-apps)。

### <a name="add-a-link-to-the-app"></a>添加应用链接
1. 在 Office 365 应用启动器中，单击或点击“PowerApps”。
   
    ![Office 365 应用启动器中的“PowerApps”](./media/sharepoint-scenario-build-app/04-07-02a-waffle.png)

2. 在 PowerApps 中，依次单击或点击“项目管理应用”旁边的省略号 (...) 和“打开”。
   
    ![选择“项目管理应用”](./media/sharepoint-scenario-build-app/04-07-02b-select-app.png)

3. 复制浏览器中的应用地址 (URL)。
   
    ![复制应用 URL](./media/sharepoint-scenario-build-app/04-07-02ba-copy-url.png)

4. 在 SharePoint 中，单击或点击“编辑链接”。
   
    ![编辑 SharePoint 网站链接](./media/sharepoint-scenario-build-app/04-07-02c-edit-links.png)

5. 单击或点击“(+)链接”。
   
    ![将应用链接添加到 SharePoint 网站](./media/sharepoint-scenario-build-app/04-07-02d-add-link.png)

6. 输入“项目管理应用”，再粘贴应用地址。
   
    ![编辑链接属性](./media/sharepoint-scenario-build-app/04-07-02e-link-dialog.png)

7. 依次单击或点击“确定”和“保存”。
   
    ![保存链接更改](./media/sharepoint-scenario-build-app/04-07-02f-save.png)

### <a name="assign-a-manager-to-a-project"></a>向项目分配经理
至此，应用已位于 SharePoint 网站中。我们将担任项目审批者的角色，查找任何没有分配经理的项目，并向其中一个项目分配经理。 然后，我们将担任项目经理的角色，添加一些有关已分配给我们的项目的信息。

1. 首先，我们将查看 SharePoint 中的“项目详细信息”列表。 两个项目的“PMAssigned”列的值为“Unassigned”。 我们将在应用中查看这两个项目。
   
    ![SharePoint 列表中的未分配项目](./media/sharepoint-scenario-build-app/04-07-01-unassigned.png)

2. 单击或点击已创建的应用链接。

3. 在第一屏上，单击或点击“分配经理”。
   
    ![应用起始屏幕](./media/sharepoint-scenario-build-app/04-07-03-intro-screen.png)

4. 在“分配经理”屏幕上，可以看到列表中的两个未分配项目。 选择“新建 BI 软件”项目。
   
    ![包含选定项的库](./media/sharepoint-scenario-build-app/04-07-04-selected.png)

5. 在“经理”文本输入框中，输入“Joni Sherman”，再单击“确定”。
   
    此更改已应用于列表，并且库会进行刷新，因此只会显示剩余未分配的项目。
   
    ![向项目分配经理](./media/sharepoint-scenario-build-app/04-07-05-updated.png)

6. 返回到 SharePoint 列表，并刷新页面。 可以看到，项目条目现已更新为包含项目经理姓名。
   
    ![SharePoint 列表中的已分配项目经理](./media/sharepoint-scenario-build-app/04-07-07-assigned.png)

### <a name="update-details-for-the-project"></a>更新项目详细信息

1. 单击或点击 ![“返回”图标](./media/sharepoint-scenario-build-app/icon-back.png)，返回到第一屏，再单击或点击“更新详细信息”。
   
   ![应用起始屏幕](./media/sharepoint-scenario-build-app/04-07-08-intro-screen.png)

2. 在“查看项目”屏幕上的搜索框中输入“新建”。
   
   ![在应用库中搜索](./media/sharepoint-scenario-build-app/04-07-09-search-new.png)

3. 单击“新建 BI 软件”项的 ![“详细信息箭头”图标](./media/sharepoint-scenario-build-app/icon-details-arrow.png)。
   
   ![选定的库项](./media/sharepoint-scenario-build-app/04-07-10-select-project.png)

4. 在“更新详细信息”屏幕上，设置以下值：
   
   * “ProjectedStartDate”字段的值为“3/6/2017”

   * “ProjectedEndDate”字段的值为“3/24/2017”

   * “ProjectedDays”字段的值为“15”
   
   ![更新项详细信息](./media/sharepoint-scenario-build-app/04-07-11-update.png)

5. 单击或点击右上角的 ![复选标记图标](./media/sharepoint-scenario-build-app/icon-check-mark.png) ，将更改应用于 SharePoint 列表。

6. 关闭应用，再返回到列表。 可以看到，项目条目现已更新为包含更改后的日期和天数。
   
    ![更新后的 SharePoint 列表](./media/sharepoint-scenario-build-app/04-07-11-updated-list.png)

## <a name="formula-deep-dive"></a>公式详解
这是第二个有关 PowerApps 公式的选读部分。 在第一个公式详解部分中，我们探究了 PowerApps 为三屏应用中的浏览库生成的公式之一。 在本次详解中，我们将探究对第二个应用的“AssignManager”屏幕使用的公式。 公式如下：

**Patch ( 'Project Details', LookUp ( 'Project Details', ID = Gallery1.Selected.ID ), {PMAssigned: TextInput1.Text} )**

此公式有何用途？ 在库中选择一项并单击“确定”按钮后，此公式便会更新“项目详细信息”列表，将“PMAssigned”列设置为在文本输入框中指定的值。 此公式使用以下函数来实现用途：

* [Patch 函数](functions/function-patch.md)：用于修改数据源中的一条或多条记录。

* [LookUp 函数](functions/function-filter-lookup.md)：用于查找表中首条满足公式的记录。

在此公式中结合使用这些函数后的情况如下：

1. 单击“确定”按钮后，将调用“Patch”函数来更新“项目详细信息”列表。

2. 在“Patch”函数中，“LookUp”函数标识要更新“项目详细信息”列表中的哪一行。 为此，它会比较选定库项的 ID 与列表中的 ID。 例如，ID 为 12 表示应更新“新建 BI 软件”的条目。

3. 至此，“Patch”函数包含正确的 ID，可以将“PMAssigned”字段更新为“TextInput1.Text”中的值。

## <a name="next-steps"></a>后续步骤
本系列教程的下一步是[创建用于分析项目的 Power BI 报表](sharepoint-scenario-build-report.md)。

