---
title: 从头开始创建 Excel 应用 | Microsoft Docs
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/23/2018
ms.author: anneta
ms.openlocfilehash: 267480158d7e44afd06962779b98c0468436841a
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39022599"
---
# <a name="create-an-excel-app-from-scratch"></a>从头开始创建 Excel 应用
基于 Excel 数据从头开始创建你自己的应用，将其格式化为表格，然后从其他源添加数据（如果需要）。 按照本教程中的步骤进行操作，可以创建包含两个屏幕的应用。 在一个屏幕上，用户可以浏览一组记录。 在另一个屏幕上，用户可以创建记录、更新记录中的一个或多个字段，或删除整条记录。 与[自动生成应用](get-started-create-from-data.md)相比，此方法耗费的时间要多得多，但有经验的应用创作者可以使用它根据需要生成最佳应用。

## <a name="prerequisites"></a>先决条件
要完全按照本教程中的步骤执行，请首先使用此示例数据创建 Excel 文件。

1. 复制此数据，并将其粘贴到 Excel 文件中。

    | StartDay | StartTime | 志愿者 | 备份 |
    | --- | --- | --- | --- |
    | 星期六 |上午 10:00-中午 |Vasquez |Kumashiro |
    | 星期六 |中午-下午 2:00 |Ice |Singhal |
    | 星期六 |下午 2:00-4:00 |Myk |Mueller |
    | 星期日 |上午 10:00-中午 |Li |Adams |
    | 星期日 |上午 10:00-中午 |Singh |Morgan |
    | 星期日 |上午 10:00-中午 |Batye |Nguyen |

2. 将该数据格式化为名为 **Schedule** 的表，以便 PowerApps 能够分析信息。

    有关详细信息，请参阅[在 Excel 中设置表格格式](how-to-excel-tips.md)。

3. 将文件以“eventsignup.xls”名称保存并关闭，然后将其上传到[云存储帐户](connections/cloud-storage-blob-connections.md)，例如 OneDrive。

> [!IMPORTANT]
> 可以使用自己的 Excel 文件，而仅通过此教程学习基本概念。 但是，Excel 文件中的数据必须设置为表格格式。 有关详细信息，请参阅[在 Excel 中设置表格格式](how-to-excel-tips.md)。

## <a name="open-a-blank-app"></a>打开一个空白应用
1. 登录 [PowerApps](http://web.powerapps.com)。

    ![PowerApps 主页](./media/get-started-create-from-blank/sign-in.png)

    可以从头开始为手机或其他设备（如平板电脑）设计应用。 本主题重点介绍设计适用于手机的应用。

1. 在“生成类似应用”下，悬停在“从空白开始”磁贴上，选择手机图标，然后选择“生成此应用”。

    ![空白应用磁贴](./media/get-started-create-from-blank/blank-app.png)

    PowerApps Studio 创建适用于手机的空白应用。

1. 如果打开“欢迎使用 PowerApps Studio”对话框，则选择“跳过”。

## <a name="connect-to-data"></a>连接到数据
1. 在屏幕中间，选择“连接到数据”。

1. 在“数据”窗格中，选择云存储帐户的连接（如果显示）。 否则，请按照下列步骤添加连接：

    1. 依次选择“新连接”、云存储帐户磁贴和“创建”。
    2. 如果系统提示，则为该帐户提供凭据。

1. 在“选择 Excel 文件”下，键入或粘贴 eventsignup 的第一个字母以筛选列表，然后选择已上传的文件。

1. 在“选择表”下，勾选“计划”复选框，然后选择“连接”。

## <a name="create-the-view-screen"></a>创建视图屏幕

1. 在“主页”选项卡上，选择“新屏幕”旁的向下箭头打开屏幕类型列表，然后选择“列表屏幕”。

    ![添加列表屏幕](./media/get-started-create-from-blank/add-list-screen.png)

    包含多个默认控件（如搜索框和“[库](controls/control-gallery.md)”控件）的屏幕已添加。 库覆盖搜索框下的整个屏幕。

2. 通过单击或点击其中心附近来选择库。

    带句柄的选择框会环绕该库。

    ![添加列表屏幕](./media/get-started-create-from-blank/select-gallery.png)

3. 在右侧窗格中，选择“CustomGallerySample”以打开“数据”窗格。

    ![打开“数据”窗格](./media/get-started-create-from-blank/custom-gallery-sample.png)

4. 在“数据源”下，选择向下箭头以打开应用程序的数据源列表，然后选择“计划”。

    ![选择数据源](./media/get-started-create-from-blank/select-schedule.png)

5. 在“布局”下，选择向下箭头以打开布局列表，然后选择“标题、副标题和正文”。

    ![选择布局](./media/get-started-create-from-blank/select-layout.png)

6. 在“标题 2”下，将“备份”中显示的列更改为“志愿者”。

     ![更改标签中的列](./media/get-started-create-from-blank/change-title2.png)

7. 选择右上角的关闭图标，关闭“数据”窗格。

    库会显示每个志愿者的姓名以及志愿者排班的日期和时间。

    ![库中未排序的“计划”数据](./media/get-started-create-from-blank/show-data-unsorted.png)

8. 选择库，并确认属性列表显示 [Items](controls/properties-core.md)。

    如公式栏所示，该属性的值为“计划”。

    ![库中未排序的“计划”数据](./media/get-started-create-from-blank/set-property.png)

9. 通过复制此公式并将其粘贴到公式栏中来更改“Items”属性的值：

    SortByColumns(Search(Schedule, TextSearchBox1.Text, "Volunteer"), "Volunteer", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))

    库会按志愿者姓名的字母顺序显示数据。

    ![库中已排序的“计划”数据](./media/get-started-create-from-blank/show-data-sorted.png)

    用户可以根据该公式中的 SortByColumns 和 Search 函数，按志愿者姓名排序和筛选库。

   - 如果用户在搜索框中键入至少一个字母，则库将仅显示“志愿者”字段中包含用户键入文本的那些记录。
   - 如果用户选择排序按钮，库将基于“志愿者”字段，按升序或降序顺序显示记录（具体取决于用户选择按钮的次数）。

     有关这些函数和其他函数的详细信息，请参阅[公式参考](formula-reference.md)。

10. 在搜索框中键入“i”，通过单击或点击来选择排序按钮，然后再次选择它（或者额外奇数次）。

     库将显示以下结果。

     ![对库进行排序和筛选](./media/get-started-create-from-blank/sort-filter.png)

11. 清除搜索框中的所有文本。

12. 在屏幕顶部，选择[标签](controls/control-text-box.md)控件，然后将“[Title]”替换为“查看记录”。

     ![更改标题栏](./media/get-started-create-from-blank/change-title-bar.png)

## <a name="create-the-change-screen"></a>创建更改屏幕
1. 在“主页”选项卡上，选择“新屏幕”旁的向下箭头，然后选择“窗体屏幕”。

     ![添加窗体屏幕](./media/get-started-create-from-blank/add-form-screen.png)

1. 在刚添加的屏幕中，选择“连接到数据”以打开“数据”窗格，然后将数据源设置为“计划”。

1. 在“字段”下，选中所有复选框以在窗体中显示所有字段。

     ![显示字段](./media/get-started-create-from-blank/show-fields.png)

1. 向上拖动“志愿者”字段，以便它显示在字段列表顶部。

     ![将字段重新排序](./media/get-started-create-from-blank/reorder-fields.png)

1. 选择窗体，通过在公式栏中键入或粘贴将其“Item”属性设置为此表达式：<br>**BrowseGallery1.Selected**

1. 在屏幕顶部，选择[标签](controls/control-text-box.md)控件，然后将“[Title]”替换为“更改记录”。

    ![更改标题栏](./media/get-started-create-from-blank/change-title-bar2.png)

## <a name="delete-and-rename-screens"></a>删除并重命名屏幕
1. 在左侧导航栏中，选择“屏幕 1”的省略号 (...)，然后选择“删除”。

    ![删除屏幕](./media/get-started-create-from-blank/delete-screen.png)

1. 选择“屏幕 2”的省略号 (...)，选择“重命名”，然后键入或粘贴“ViewScreen”。

1. 选择“屏幕 3”的省略号 (...)，选择“重命名”，然后键入或粘贴“ChangeScreen”。

## <a name="configure-icons-on-the-view-screen"></a>在视图屏幕上配置图标
1. 在“ViewScreen”顶部附近，选择圆形箭头图标。

    ![添加记录](./media/get-started-create-from-blank/refresh-icon.png)

1. 将此图标的“OnSelect”属性设置为此公式：<br>Refresh(Schedule)

    当用户选择此图标，来自“计划”的数据会从 Excel 文件进行刷新。

    有关此函数和其他函数的详细信息，请参阅[公式参考](formula-reference.md)。

1. 在“ViewScreen”的右上角，选择加号图标。

    ![添加记录](./media/get-started-create-from-blank/add-record.png)

1. 将此图标的“OnSelect”属性设置为此公式：<br>NewForm(EditForm1);Navigate(ChangeScreen,ScreenTransition.None)

    用户选择图标时，将显示“ChangeScreen”且每个字段均为空，这样用户可以更轻松地创建记录。

1. 选择右箭头，获取库中的第一个记录。

    ![选择箭头](./media/get-started-create-from-blank/select-arrow.png)

1. 将该箭头的 OnSelect 属性设置为此公式：<br>EditForm(EditForm1); Navigate(ChangeScreen, ScreenTransition.None)

    当用户选择此图标时，将显示“ChangeScreen”，其中每个字段显示所选记录的数据，以便用户可以更轻松地编辑或删除记录。

## <a name="configure-icons-on-the-change-screen"></a>在更改屏幕上配置图标
1. 在“ChangeScreen”上，选择左上角的“x”图标。

    ![“取消”图标](./media/get-started-create-from-blank/cancel-icon.png)

1. 将此图标的“OnSelect”属性设置为此公式：<br>ResetForm(EditForm1);Navigate(ViewScreen, ScreenTransition.None)

    当用户选择此图标时，将放弃用户在此屏幕中所做的任何更改，并会打开视图屏幕。

1. 在右上角，选择复选标记图标。

    ![“选中标记”图标](./media/get-started-create-from-blank/checkmark-icon.png)

1. 将该复选标记的“OnSelect”属性设置为此公式：<br>SubmitForm(EditForm1); Navigate(ViewScreen, ScreenTransition.None)

    当用户选择此图标时，将保存用户在此屏幕中所做的任何更改，并会打开视图屏幕。

1. 在“插入”选项卡上，选择“图标”，然后选择“垃圾桶”图标。

1. 将新图标的“Color”属性设置为“White”，并移动新图标，以便显示在复选标记图标旁。

    ![“垃圾桶”图标](./media/get-started-create-from-blank/trash-icon.png)

1. 将此垃圾桶图标的“OnSelect”属性设置为此公式：<br>Remove(Schedule, BrowseGallery1.Selected); Navigate(ViewScreen, ScreenTransition.None)

    当用户选择此图标，会从数据源删除所选记录，且视图屏幕将打开。

## <a name="test-the-app"></a>测试应用程序
1. 选择“ViewScreen”，然后按 F5（或选择右上角附近的“预览”图标）打开“预览”。

    ![打开预览模式](./media/get-started-create-from-blank/open-preview.png)

1. 添加记录。

1. 更新添加的记录，然后保存所做的更改。

1. 更新添加的记录，然后取消所做的更改。

1. 删除添加的记录。

1. 按 Esc（或选择右上角的关闭图标）关闭“预览”模式。

## <a name="next-steps"></a>后续步骤
* 按 Ctrl-S 在云中保存应用，以便从其他设备运行该应用。
* [共享应用](share-app.md)，便于其他人运行该应用。
* 详细了解[函数](working-with-formulas.md)（如 Patch），可以用于管理数据，而无需创建标准窗体。
