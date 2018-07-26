---
title: 使用 Common Data Service for Apps 从头创建应用 | Microsoft Docs
description: 创建用于添加、更新和删除记录的应用。
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
ms.openlocfilehash: b7506ff3380855c6e3c51b22918366dde9c8549c
ms.sourcegitcommit: 0e9af8cace2bdc04750f4c5a70a3c4af8e3d2292
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2018
ms.locfileid: "39195119"
---
# <a name="create-an-app-from-scratch-using-common-data-service-for-apps"></a>使用 Common Data Service for Apps 从头创建应用

生成一个应用，以使用（内置的）标准实体和/或（组织创建的）自定义实体来管理 Common Data Service for Apps 中存储的数据。

使用 Common Data Service 生成应用时，无需从 PowerApps 建立连接，而处理 SharePoint、Dynamics 365 或 Salesforce 等数据源时则需要这样做。 只需指定要显示、管理或在应用中用于这两种活动的实体即可。

## <a name="prerequisites"></a>先决条件

- 在从头开始创建应用之前，请通过[生成应用](data-platform-create-app.md)并自定义应用的[库](customize-layout-sharepoint.md)、[窗体](customize-forms-sharepoint.md)和[卡](customize-card.md)来熟悉 PowerApps 基础知识。
- [切换到一个环境](working-with-environments.md)，该环境中已创建带有示例数据的数据库。 如果有合适的许可证，则可以[创建环境](../../administrator/create-environment.md)以满足此需要。

## <a name="open-a-blank-app"></a>打开一个空白应用

1. 登录 [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    ![PowerApps 主页](./media/data-platform-create-app-scratch/sign-in.png)

1. 在“生成类似应用”下，悬停在“从空白开始”磁贴上，单击或点击手机图标，然后单击或点击“生成此应用”。

    ![空白应用磁贴](./media/data-platform-create-app-scratch/blank-app.png)

    可从头开始设计一个在手机或其他设备（如平板电脑）上使用的应用；本主题将重点介绍如何设计在手机上使用的应用。

## <a name="specify-an-entity"></a>指定实体

1. 在屏幕中间，单击或点击“连接到数据”，然后在“数据”窗格中，单击或点击“Common Data Service”连接。

1. 在搜索框中，键入或粘贴帐户的前几个字母以筛选实体列表，选择“帐户”复选框，然后单击或点击“连接”。

    ![指定帐户实体](./media/data-platform-create-app-scratch/cds-connect.png)

1. 通过单击或点击右上角的关闭图标，关闭“数据”窗格。

## <a name="add-a-list-screen"></a>添加列表屏幕

1. 在“开始”选项卡中，依次单击或点击“新屏幕”的向下箭头和“列表屏幕”。

    ![添加列表屏幕](./media/data-platform-create-app-scratch/list-screen.png)

1. 在左侧导航栏中，单击或点击“TemplateGalleryList1”进行选择，然后将“项”属性的值设为此公式：

    `SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))`

    此公式指定：

   - 库应显示“帐户”实体的数据。
   - 在用户单击或点击排序按钮切换排序顺序之前，数据应是按升序排序。
   - 如果用户在搜索栏中键入或粘贴一个或多个字符，则该列表仅显示名称包含用户指定字符的帐户。

     可以使用[这些函数和许多其他函数](formula-reference.md)指定应用的显示方式和行为方式。

     ![设置库项属性](./media/data-platform-create-app-scratch/gallery-items.png)

1. 将库的布局设置为仅显示每个帐户的名称，并将标题栏配置为显示“浏览”一词，如[自定义库](customize-layout-sharepoint.md)中所述。

    ![浏览屏幕](./media/data-platform-create-app-scratch/final-browse.png)

1. 在左侧的导航栏中，将鼠标悬停在“Screen1”上，单击或点击省略号图标 (...)，然后点击或点击“删除”。

1. 在左侧的导航栏中，将鼠标悬停在“Screen2”上，单击或点击省略号图标 (...)，然后点击或点击“重命名”。

1. 键入或粘贴“BrowseScreen”，然后将该屏幕中的库重命名为“BrowseGallery”。

    ![重命名浏览屏幕, 库](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>添加一个窗体屏幕

1. 重复前述流程的第一步，除一点不同：将添加“列表屏幕”改为添加“窗体屏幕”。

1. 将窗体的“数据源”属性设置为“帐户”并将其“项”属性设置为“BrowseGallery.Selected”，如右侧窗格的“高级选项卡”所示。

    ![设置窗体的“数据源”和“项”属性](./media/data-platform-create-app-scratch/form-datasource.png)

1. 在右侧窗格的“属性”选项卡中，单击或点击“帐户”以打开“数据”窗格，然后选择以下字段的复选框：

    - 帐户名
    - 地址 1：街道 1
    - 地址 1：城市
    - 地址 1：ZIP/邮政编码
    - 员工人数
    - 年收入

1. 将标题栏的“文本”属性设置为显示“创建/编辑”。

    屏幕将体现所做的更改。

    ![设置窗体的“数据源”和“项”属性](./media/data-platform-create-app-scratch/field-list.png)

1. 将此屏幕重命名为“FormScreen”。

## <a name="configure-icons"></a>配置图标

1. 在“BrowseScreen上”，单击或点击屏幕顶部附近的环形图标，然后将其“OnSelect”属性设置为此公式：

    `Refresh(Accounts)`

    ![“刷新”图标](./media/data-platform-create-app-scratch/refresh-icon.png)

1. 单击或点击加号图标，并将其“OnSelect”属性设置为此公式：

    `NewForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![“添加”图标](./media/data-platform-create-app-scratch/plus-icon.png)

1. 单击或点击第一个向右箭头，并将其“OnSelect”属性设置为此公式：

    `EditForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![“下一步”图标](./media/data-platform-create-app-scratch/next-icon.png)

1. 在“FormScreen”上，单击或点击取消图标，然后将其“OnSelect”属性设置为此公式：

    `ResetForm(EditForm1);Navigate(BrowseScreen, ScreenTransition.None)`

    ![“取消”图标](./media/data-platform-create-app-scratch/cancel-icon.png)

1. 单击或点击选中标记图标，并将其“OnSelect”属性设置为此公式：

    `SubmitForm(EditForm1); Navigate(BrowseScreen, ScreenTransition.None)`

    ![“选中标记”图标](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. 在“插入”选项卡上，单击或点击“图标”，然后单击或点击“垃圾桶”图标。

1. 将“垃圾桶”图标的“颜色”属性设置为“白色”，并将其“OnSelect”属性设置为此公式：

    `Remove(Accounts, BrowseGallery.Selected); Navigate(BrowseScreen, ScreenTransition.None)`

    ![“垃圾桶”图标](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>测试应用程序

1. 在左侧导航栏中，选择“BrowseScreen”，然后按 F5（或者单击或点击右上角附近的“播放”图标）打开预览。

    ![打开预览](./media/data-platform-create-app-scratch/open-preview.png)

1. 在列表的升序和降序排序之间进行切换，按每个帐户名称中的特定字符筛选列表。

1. 添加帐户，编辑所添加的帐户，开始更新帐户但取消所做的更改，然后删除该帐户。

## <a name="next-steps"></a>后续步骤

[打开一个或多个示例应用](open-and-run-a-sample-app.md)，并浏览可以创建的不同应用类型。