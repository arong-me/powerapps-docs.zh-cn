---
title: 自定义画布应用中的窗体 | Microsoft Docs
description: 在 PowerApps 中，指定画布应用窗体中要显示哪些数据、以何种顺序显示以及在哪些控件中显示。
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1a6465a00f135489d594bad75b8a25942e05dd25
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560537"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>自定义 PowerApps 中的画布应用窗体

在画布应用中，自定义“显示窗体”控件和“编辑窗体”控件，以便它们以最直观的顺序显示最重要的数据，帮助用户轻松了解和更新数据。

每个窗体包含一个或多个卡，其中每个卡均可显示数据源中特定列的数据。 按照本主题中的步骤操作，可以指定在窗体中显示的卡并在窗体中上下移动卡。

如果您对画布 pps 不熟悉，请参阅[画布应用有哪些？](getting-started.md)。

## <a name="prerequisites"></a>先决条件

从 Common Data Service [生成应用](data-platform-create-app.md)，然后在该应用中[自定义库](customize-layout-sharepoint.md)。

## <a name="show-and-hide-cards"></a>显示和隐藏卡

1. 登录到[PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后打开的应用程序生成并自定义。

1. 在左侧的导航栏中，键入或粘贴**D**在搜索栏中，以筛选列表的元素，然后选择**DetailForm1**。

    > [!div class="mx-imgBorder"]
    > ![选择详细信息屏幕](./media/customize-forms-sharepoint/select-detailform.png)

1. 在右侧窗格的“属性”选项卡上，选择“编辑字段”以打开“字段”窗格。

    > [!div class="mx-imgBorder"]
    > ![打开字段窗格](./media/customize-forms-sharepoint/edit-fields.png)

1. 隐藏字段，如**描述**，通过将鼠标悬停其上，选择省略号 （...），然后选择**删除**。

    > [!div class="mx-imgBorder"]
    > ![字段的列表](./media/customize-forms-sharepoint/hide-fields.png)

1. 通过选择显示字段**添加字段**、 键入或粘贴搜索框中，选择该字段的复选框，然后选中字段的名称的第几个字母**添加**。

    > [!div class="mx-imgBorder"]
    > ![字段的列表](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>对卡重新排序

1. 在中**字段**窗格中，拖动**帐户名称**字段的字段列表的顶部。

    中的卡片**DetailForm1**反映更改。

    > [!div class="mx-imgBorder"]
    > ![重新排序的卡](./media/customize-forms-sharepoint/reordered-card.png)

1. （可选）为此序列重新排列其他卡：

    - 帐户名
    - 员工人数
    - 年收入
    - 主要电话
    - 地址 1：街道 1
    - 地址 1：街道 2
    - 地址 1：城市
    - 地址 1：ZIP/邮政编码

1. 在左侧的导航栏中，键入或粘贴**Ed**在搜索栏中，并选择**EditForm1**以将其选中。

1. 重复上一过程和此过程中的步骤，以便 EditForm1 中的字段与 DetailForm1 中的字段相匹配。

## <a name="run-the-app"></a>运行应用

1. 在左侧的导航栏中，键入或粘贴**Br**在搜索栏中，并选择**BrowseScreen1**以将其选中。

1. 按 F5（或选择右上角附近的“**预览**”图标）打开预览模式。

    > [!div class="mx-imgBorder"]
    > ![预览图标](./media/customize-forms-sharepoint/open-preview.png)

1. 在右上角中，选择加号图标以添加中的记录**EditScreen1**。

    > [!div class="mx-imgBorder"]
    > ![添加记录](./media/customize-forms-sharepoint/add-record.png)

1. 添加任何数据，然后在右上角登录以保存所做的更改并返回到选择复选标记图标**BrowseScreen1**。

    > [!div class="mx-imgBorder"]
    > ![保存记录](./media/customize-forms-sharepoint/save-record.png)

1. 选择箭头，显示刚刚创建的项的详细信息中的项的相关**DetailScreen1**。

    > [!div class="mx-imgBorder"]
    > ![向右箭头](./media/customize-forms-sharepoint/right-arrow.png)

1. 在右上角中，选择要更新中的记录的编辑图标**EditScreen1**。

    > [!div class="mx-imgBorder"]
    > ![编辑记录](./media/customize-forms-sharepoint/edit-record.png)

1. 更改一个或多个字段中的信息，然后在右上角登录以保存所做的更改并返回到选择复选标记**DetailScreen1**。

    > [!div class="mx-imgBorder"]
    > ![保存更改](./media/customize-forms-sharepoint/save-record.png)

1. 右上角附近选择回收站图标，删除刚刚更新的记录并返回到**BrowseScreen1**。

    > [!div class="mx-imgBorder"]
    > ![删除记录](./media/customize-forms-sharepoint/delete-record.png)

1. 通过按 esc 键 （或通过选择窗口左上角附近的关闭图标） 关闭预览模式。

## <a name="next-steps"></a>后续步骤

- [保存并发布](save-publish-app.md)应用。
- 在应用中[自定义卡](customize-card.md)。