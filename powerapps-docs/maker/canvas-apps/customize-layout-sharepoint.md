---
title: 库自定义教程 | Microsoft Docs
description: 本教程介绍如何自定义 PowerApps 中生成的应用的默认浏览屏幕（包括库）。
services: ''
suite: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/11/2018
ms.author: anneta
ms.openlocfilehash: 30ec6be11b40e01dddfe09cf0ac8af0ed3a8a437
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>教程：在 PowerApps 中自定义库
本教程介绍如何自定义 PowerApps 中生成的应用的默认浏览屏幕（包括库）。 管理数据时可以只使用默认应用而不对其进行自定义，但如果做出以下更改，应用会变得更强大、更易于使用：

> [!div class="checklist"]
> * 更改布局
> * 更改显示的数据
> * 设置用于筛选和排序的列
> * 测试筛选和排序
> * 更改标题
> * 显示滚动条

本教程一开始将使用通过 [Common Data Service for Apps](../common-data-service/data-platform-intro.md) 生成的应用，其中涉及的概念同样适用于通过 SharePoint、Excel 和其他数据源生成的应用。 

如果没有适用于 PowerApps 的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="prerequisites"></a>先决条件
在开始本教程之前，请先从 Common Data Service for Apps [生成应用](data-platform-create-app.md)。

## <a name="open-the-generated-app"></a>打开生成的应用
1. 登录 [PowerApps](https://web.powerapps.com)，然后单击或点击左边缘附近的“应用”。

    ![PowerApps 主页](./media/customize-layout-sharepoint/sign-in.png)

1. 查找生成的应用，然后单击或点击右边缘附近的省略号图标 (...)。

    ![应用列表](./media/customize-layout-sharepoint/open-for-edit.png)

1. 在出现的菜单中，单击或点击用于编辑应用的选项。 

## <a name="customize-the-gallery"></a>自定义库
1. 在浏览屏幕上，单击或点击任意项（帐户列表第一项除外）。

    此步骤选择用于显示帐户列表的“库”控件。

    ![所选的库](./media/customize-layout-sharepoint/select-gallery.png)

1. 在右侧窗格中，单击或点击“数据”标签右侧的“帐户”。

    ![打开“数据”窗格](./media/customize-layout-sharepoint/open-data-pane.png)

1. 在“数据”窗格中，单击或点击向下箭头，打开“布局”下的选项列表。

    ![显示布局选项](./media/customize-layout-sharepoint/show-layouts.png)

1. 在选项列表中，单击或点击仅显示一个标题的选项。

    ![选择仅限标题的布局](./media/customize-layout-sharepoint/choose-layout.png)

1. 在“数据”窗格中，单击或点击向下箭头，打开标题的选项列表。

    ![选择仅限标题的布局](./media/customize-layout-sharepoint/show-title-options.png)

1. 在选项列表中，单击或点击“名称”，在“库”控件中显示数据。

    ![最终库](./media/customize-layout-sharepoint/final-gallery.png)


## <a name="set-the-sort-and-search-columns"></a>设置排序和搜索列
1. 按前一部分所述选择“库”控件。

    ![选择库](./media/customize-layout-sharepoint/select-gallery-title.png)

2. 确保左上角附近的属性列表显示**项**。

    ![项属性](./media/customize-layout-sharepoint/items-property.png)

    此属性的值显示在编辑栏中，不仅确定库的数据源，还确定筛选列和排序列。

1. 在编辑栏中，将“emailaddress1”的两个实例替换为“名称”，并且保留每个实例的双引号。

    公式应与此示例相匹配：

    ![项属性的公式](./media/customize-layout-sharepoint/items-value.png)

    “名称”的第一个实例指定用户可以将列表筛选为仅显示某些记录，这些记录的帐户名包含用户在搜索栏中键入的文本。 “名称”的第二个实例指定用户可以按帐户名的字母顺序对列表进行排序。 有关这些函数和其他函数的详细信息，请参阅[公式参考](formula-reference.md)。

## <a name="test-sorting-and-searching"></a>测试排序和搜索
1. 按 F5（或者单击或点击靠近右上角的播放按钮）即可打开预览模式。

    ![打开预览模式](./media/customize-layout-sharepoint/open-preview.png)

1. 在浏览屏幕的右上角附近，一次或多次单击或点击排序图标，在升序和降序之间更改字母排序顺序。

    ![测试排序图标](./media/customize-layout-sharepoint/sort-button.png)

1. 在搜索框中，键入“k”，可仅显示名称中包含键入的字母的帐户。

    ![测试搜索栏](./media/customize-layout-sharepoint/test-filter.png)

1. 删除搜索栏的所有文本，然后按 Esc 键（或者单击或点击 PowerApps 标题栏 *下方* 的关闭图标）即可关闭预览模式。

## <a name="change-the-title-of-the-screen"></a>更改屏幕标题
1. 单击或点击屏幕标题以将其选中。

    ![选择屏幕标题](./media/customize-layout-sharepoint/select-title.png)

1. 确保属性列表显示“文本”，然后在编辑栏中键入“浏览”，并用双引号括住。

    ![更新屏幕标题](./media/customize-layout-sharepoint/change-screen-title.png)

    屏幕将体现所做的更改。

    ![新建屏幕标题](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scroll-bar"></a>显示滚动条
如果用户不具有触摸屏或鼠标滚轮，可将“库”控件配置为用户在其上悬停鼠标时显示滚动条。 那样，即使屏幕不能一次性全部显示，用户依然可以显示所有帐户。

1. 按第一个步骤所述选择“库”控件。

    ![选择库](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. 在“库”选项卡上，单击或点击“显示滚动条”，并确认该属性的值已更改为“true”。 

    ![显示滚动条](./media/customize-layout-sharepoint/show-scrollbar.png)

## <a name="next-steps"></a>后续步骤
本教程中自定义了“库”控件以及生成的应用的默认浏览屏幕标题。 还可以自定义用于显示详细信息以及创建或更新帐户的默认屏幕。 这些屏幕包含“显示窗体”控件和“编辑窗体”控件，并可更改（例如）显示的数据类型和显示的顺序。

> [!div class="nextstepaction"]
> [自定义窗体](customize-forms-sharepoint.md)