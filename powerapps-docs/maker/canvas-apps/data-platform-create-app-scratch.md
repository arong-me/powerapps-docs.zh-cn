---
title: 使用 Common Data Service 从头开始创建画布应用 | Microsoft Docs
description: 在 PowerApps 中，创建在 Common Data Service 中添加、更新和删除记录的画布应用。
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/21/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 482a5a91c241aa9fd8c85dfb970cf692cd2ab1a3
ms.sourcegitcommit: 38270060d2d0b784fe065164e6112c011b26e17c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2019
ms.locfileid: "68830455"
---
# <a name="create-a-canvas-app-from-scratch-using-common-data-service"></a>使用 Common Data Service 从头开始创建画布应用

生成画布应用，以使用（内置的）标准实体和/或（组织创建的）自定义实体来管理 Common Data Service 中存储的数据。

使用 Common Data Service 生成应用时，无需从 PowerApps 建立连接，而处理 SharePoint、Dynamics 365 或 Salesforce 等数据源时则需要这样做。 只需指定想要在应用中显示或管理的实体。

## <a name="prerequisites"></a>先决条件

- 在从头开始创建应用之前，请通过[生成应用](data-platform-create-app.md)并自定义应用的[库](customize-layout-sharepoint.md)、[窗体](customize-forms-sharepoint.md)和[卡](customize-card.md)来熟悉 PowerApps 基础知识。
- [切换到一个环境](working-with-environments.md)，该环境中已创建带有示例数据的数据库。 如果有合适的许可证，则可以[创建环境](../../administrator/create-environment.md)以满足此需要。
- 若要创建应用，须具有[环境创建者](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles)安全角色。

## <a name="open-a-blank-app"></a>打开一个空白应用

1. 登录 [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. 在“生成自己的应用”下，选择“从空白开始创建画布应用”。

    ![空白应用磁贴](./media/data-platform-create-app-scratch/blank-app.png)

1. 为应用指定名称，选择“手机”，然后选择“创建”。

    可以为平板电脑从头开始构建应用，但此主题介绍的是为手机构建应用。

## <a name="specify-an-entity"></a>指定实体

1. 在屏幕中间，选择“连接到数据”。

1. 在“数据”窗格中，选择“Common Data Service”，选择“帐户”复选框，然后选择“连接”。

1. 选择右上角的关闭图标，关闭“数据”窗格。

## <a name="add-a-list-screen"></a>添加列表屏幕

1. 在“主页”选项卡上，选择“新屏幕”的向下箭头，然后选择“列表”。

    ![添加列表屏幕](./media/data-platform-create-app-scratch/list-screen.png)

1. 在左侧导航栏中，选择“BrowseGallery1”，然后将“项”属性的值设置为此公式：

    `SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))`

    此公式指定：

   - 库应显示“帐户”实体的数据。
   - 在用户选择排序按钮切换排序顺序之前，数据应是按升序排序。
   - 如果用户在搜索栏 (TextSearchBox1) 中键入或粘贴一个或多个字符，则该列表仅显示名称包含用户指定字符的帐户。

     可以使用[这些函数和许多其他函数](formula-reference.md)指定应用的显示方式和行为方式。

     ![设置库项属性](./media/data-platform-create-app-scratch/gallery-items.png)

1. 将库的布局设置为仅显示每个帐户的名称，并将标题栏配置为显示“浏览”一词，如[自定义库](customize-layout-sharepoint.md)中所述。

    ![浏览屏幕](./media/data-platform-create-app-scratch/final-browse.png)

1. 在左侧导航栏中，将鼠标悬停在“Screen1”上方，选择省略号 (...)，然后选择“删除”。

1. 在左侧导航栏中，将鼠标悬停在“Screen2”上方，选择省略号 (...)，然后选择“重命名”。

1. 键入或粘贴“BrowseScreen”，然后将该屏幕中的库重命名为“BrowseGallery”。

    ![重命名浏览屏幕, 库](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>添加一个窗体屏幕

1. 重复前述流程的第一步，除一点不同：将添加“列表屏幕”改为添加“窗体屏幕”。

1. 将窗体的“数据源”属性设置为“帐户”并将其“项”属性设置为“BrowseGallery.Selected”，如右侧窗格的“高级选项卡”所示。

    ![设置窗体的“数据源”和“项”属性](./media/data-platform-create-app-scratch/form-datasource.png)

1. 在右侧窗格的 "**属性**" 选项卡上, 选择 "**编辑字段**", 打开 "**字段**" 窗格。

1. 选择“添加字段”，然后选择这些字段对应的复选框：

    - **帐户名**
    - **地址 1：街道 1**
    - **地址 1：城市**
    - **地址 1：邮政编码**
    - **员工人数**
    - **年收入**

    > [!NOTE]
    > 在这种情况下, 您可以通过选择 "**新建字段**" 创建自定义字段, 提供所需的信息, 然后选择 "**完成**"。 详细信息：[创建字段](../common-data-service/create-edit-field-portal.md#create-a-field)。<br><br>![](media/data-platform-create-app-scratch/choose-or-add-fields.png "选择并添加字段")

1. 选择“添加”。

1. 将标题栏的“文本”属性设置为显示“创建/编辑”。

    屏幕将体现所做的更改。

    ![设置窗体的“数据源”和“项”属性](./media/data-platform-create-app-scratch/field-list.png)

1. 将此屏幕重命名为“FormScreen”。

## <a name="configure-icons"></a>配置图标

1. 在“BrowseScreen”上，将屏幕顶部附近的圆形图标的属性“OnSelect”设置为此公式：

    `Refresh(Accounts)`

    ![“刷新”图标](./media/data-platform-create-app-scratch/refresh-icon.png)

1. 将“加号”图标的“OnSelect”属性设置为此公式：

    `NewForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![“添加”图标](./media/data-platform-create-app-scratch/plus-icon.png)

1. 将指向右侧的第一个箭头的“OnSelect”属性设置为此公式：

    `EditForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![“下一步”图标](./media/data-platform-create-app-scratch/next-icon.png)

1. 在“FormScreen”上，将“取消”图标的“OnSelect”属性设置为此公式：

    `ResetForm(EditForm1);Navigate(BrowseScreen, ScreenTransition.None)`

    ![“取消”图标](./media/data-platform-create-app-scratch/cancel-icon.png)

1. 将选中标记的 OnSelect 属性设置为此公式：

    `SubmitForm(EditForm1); Navigate(BrowseScreen, ScreenTransition.None)`

    ![“选中标记”图标](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. 在“插入”选项卡上，选择“图标”，然后选择“垃圾桶”图标。

1. 将“垃圾桶”图标的“颜色”属性设置为“白色”，并将其“OnSelect”属性设置为此公式：

    `Remove(Accounts, BrowseGallery.Selected); Navigate(BrowseScreen, ScreenTransition.None)`

    ![“垃圾桶”图标](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>测试应用程序

1. 在左侧导航栏中，选择“BrowseScreen”，然后按 F5（或者选择右上角附近的“播放”图标）打开预览。

    ![打开预览](./media/data-platform-create-app-scratch/open-preview.png)

1. 在列表的升序和降序排序之间进行切换，按帐户名称中的一个或多个字符筛选列表。

1. 添加帐户，编辑所添加的帐户，开始更新帐户但取消所做的更改，然后删除该帐户。

## <a name="next-steps"></a>后续步骤

- [将此应用链接到解决方案](add-app-solution.md)以便能够将其部署到其他环境或在 AppSource 上发布此应用等等。
- [打开一个或多个示例应用](open-and-run-a-sample-app.md)，并浏览可以创建的不同应用类型。
