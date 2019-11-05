---
title: 教程 - 在生成应用中自定义库 | Microsoft Docs
description: 本教程将介绍自定义显示在库中的数据，以及在 PowerApps 中自动生成的应用的其他元素。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: tutorial
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6b3a33f327aab7e4f02c954dbd31c412e35dd661
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73539177"
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>教程：在 PowerApps 中自定义库

本教程将自定义一个记录列表（称为一个库），以及对已在 Microsoft PowerApps 中自动生成的应用进行其他更改。 即使不进行这些更改，用户也可以管理应用中的数据，但是，如果对其进行自定义来满足组织需要，则可以更加轻松使用该应用。

例如，本教程中的库默认情况下与此图形匹配。 电子邮件地址比其他数据类型更加突出，用户可基于地址中的文本对库进行排序和筛选：

![默认库](./media/customize-layout-sharepoint/gallery-before.png)

但是，相较于电子邮件地址，用户可能会更加关注帐户名，因此需要重新配置库，以便基于组织的关键数据来实现突出显示、排序和筛选。 此外，需要更改默认屏幕的标题，使其与应用中的其他屏幕区分开来。

![最终库](./media/customize-layout-sharepoint/gallery-after.png)

还需要添加滚动条，以便没有触摸屏或鼠标滚轮的用户可以浏览整个库。

> [!div class="checklist"]
> * 更改库布局
> * 更改显示在库中的数据类型
> * 更改用户排序和搜索数据所依据的列
> * 更改屏幕标题
> * 显示滚动条

本教程从一个由特定数据源生成的应用开始。 但是，相同的概念适用于在 PowerApps 中生成（无论从 SharePoint 列表、Excel 表还是某些其他数据源生成）的任何应用。

如果没有注册 PowerApps，请在开始使用之前先[免费注册](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

## <a name="prerequisites"></a>必备组件

从 Common Data Service 的 "**帐户**" 实体[生成应用](data-platform-create-app.md)。

## <a name="open-the-generated-app"></a>打开生成的应用

1. 登录 [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后选择左边缘附近的“应用”。

1. 找到你生成的应用，选择其省略号图标 (...)，然后选择“编辑”。

    ![打开应用进行编辑](./media/customize-layout-sharepoint/open-app.png)

1. 如果出现“欢迎使用 PowerApps Studio”对话框，则单击“跳过”。

## <a name="change-the-layout"></a>更改布局

1. 在左侧导航窗格中，选择“BrowseGallery1”。

    选择库后，会有带句柄的选择框环绕它。

    ![选择库](media/customize-layout-sharepoint/select-gallery-1.png)

1. 在右侧窗格的 "**属性**" 选项卡上，打开 "**布局**" 下的选项列表，然后选择只显示标题的选项。

    ![选择仅限标题的布局](./media/customize-layout-sharepoint/choose-layout.png)

1. 在 "**字段**" 旁，选择 "**编辑**"，然后选择 "标题" 框的向下箭头。

    此控件的名称以数字结尾，如“标题 1”，基于已执行的其他操作，该数字可能有所不同。

1. 在选项列表中，选择 "**帐户名称**"，然后关闭 "**数据**" 窗格。

    库显示每个帐户的名称。

    ![最终库](./media/customize-layout-sharepoint/final-gallery.png)

## <a name="change-sort-and-search-columns"></a>更改排序和搜索列

1. 按前一部分所述选择库。

    ![选择库](./media/customize-layout-sharepoint/select-gallery-title.png)

1. 确认左上角附近的属性列表显示“Items”。

    ![项属性](./media/customize-layout-sharepoint/items-property.png)

    此属性值将显示在公式栏中。 设置此属性不仅指定库的数据源，还将指定用户排序和搜索数据所依据的列。

1. 复制此公式，然后将其粘贴在公式栏中。

    ```SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, Descending, Ascending))```

    通过使用此公式，请确保：

    * 如果用户在搜索栏中键入一个或多个字符，则库将仅显示那些包含用户所键入文本的帐户名称。
    * 如果用户选择排序图标，库会按照帐户名称的字母顺序以升序或降序排序，具体取决于用户选择图标的次数。

     有关这些函数和其他函数的详细信息，请参阅[公式参考](formula-reference.md)。

### <a name="test-sorting-and-searching"></a>测试排序和搜索

1. 按 F5 键（或选择右上角附近的播放按钮）打开“预览”模式。

    ![打开预览模式](./media/customize-layout-sharepoint/open-preview.png)

1. 在浏览屏幕的右上角附近，一次或多次选择排序图标，在升序和降序之间更改字母排序顺序。

    ![测试排序图标](./media/customize-layout-sharepoint/sort-button.png)

1. 在搜索框中，键入“k”以仅显示那些包含所键入字母的帐户名称。

    ![测试搜索栏](./media/customize-layout-sharepoint/test-filter.png)

1. 删除搜索栏的所有文本，然后按 Esc 键（或者选择右上角附近的关闭图标）即可关闭“预览”模式。

## <a name="change-the-screen-title"></a>更改屏幕标题

1. 通过单击或点击来选择屏幕标题。

    ![选择屏幕标题](./media/customize-layout-sharepoint/select-title.png)

1. 确保属性列表显示“文本”，然后在公式栏中，将“帐户”替换为“浏览”（用双引号括住）。

    ![更新屏幕标题](./media/customize-layout-sharepoint/change-screen-title.png)

    屏幕将体现所做的更改。

    ![新建屏幕标题](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scrollbar"></a>显示滚动条

如果用户没有触摸屏或鼠标滚轮，可将库配置为用户在其上悬停鼠标时显示滚动条。 那样，即使屏幕不能一次性全部显示，用户依然可以显示所有帐户。

1. 按第一个步骤所述选择库。

    ![选择库](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. 将库的 "**显示滚动条**" 属性设置为 " **true**"。

## <a name="next-steps"></a>后续步骤

本教程中已自定义库，并对默认屏幕进行了其他更改，以便在生成应用中浏览记录。 还可以自定义用于显示详细信息以及创建或更新帐户的默认屏幕。 因为浏览屏幕包含一个库，应用的其他两个屏幕将包含窗体。 例如，可以更改窗体显示的数据类型和顺序。

> [!div class="nextstepaction"]
> [自定义窗体](customize-forms-sharepoint.md)
