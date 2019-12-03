---
title: 自定义画布应用中的窗体 | Microsoft Docs
description: 在 Power Apps 中，指定要在画布应用窗体中显示的数据，其中显示这些数据的顺序以及控件。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6732dabea803cd7680ef618e4e8d1c4e88f7afe5
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678617"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>自定义 PowerApps 中的画布应用窗体

在画布应用中，自定义“显示窗体”控件和“编辑窗体”控件，以便它们以最直观的顺序显示最重要的数据，帮助用户轻松了解和更新数据。

每个窗体包含一个或多个卡，其中每个卡均可显示数据源中特定列的数据。 按照本主题中的步骤操作，可以指定在窗体中显示的卡并在窗体中上下移动卡。

如果你不熟悉 canvas-pps，请参阅[什么是画布应用？](getting-started.md)。

## <a name="prerequisites"></a>必备组件

从 Common Data Service [生成应用](data-platform-create-app.md)，然后在该应用中[自定义库](customize-layout-sharepoint.md)。

## <a name="show-and-hide-cards"></a>显示和隐藏卡

1. 登录到[PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后打开生成并自定义的应用。

1. 在左侧导航栏中，在搜索栏中键入或粘贴**D**以筛选元素列表，然后选择 " **DetailForm1**"。

    > [!div class="mx-imgBorder"]
    > !["选择详细信息" 屏幕](./media/customize-forms-sharepoint/select-detailform.png)

1. 在右侧窗格的“属性”选项卡上，选择“编辑字段”以打开“字段”窗格。

    > [!div class="mx-imgBorder"]
    > ![打开字段窗格](./media/customize-forms-sharepoint/edit-fields.png)

1. 通过将鼠标悬停在其上方，选择显示的省略号（...），然后选择 "**删除**"，隐藏字段，如 "**说明**"。

    > [!div class="mx-imgBorder"]
    > 字段 ![列表](./media/customize-forms-sharepoint/hide-fields.png)

1. 通过选择 "**添加字段**"，在搜索框中键入或粘贴字段名称的前几个字母，然后选择字段的复选框，然后选择 "**添加**"，以显示字段。

    > [!div class="mx-imgBorder"]
    > 字段 ![列表](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>对卡重新排序

1. 在 "**字段**" 窗格中，将 "**帐户名**" 字段拖到字段列表的顶部。

    **DetailForm1**中的卡片反映了更改。

    > [!div class="mx-imgBorder"]
    > ![重新排序卡](./media/customize-forms-sharepoint/reordered-card.png)

1. 可有可无将其他卡重新排序为此顺序：

    - 帐户名
    - 员工人数
    - 年收入
    - 主电话
    - 地址 1：街道 1
    - 地址1：街道2
    - 地址 1：城市
    - 地址 1：ZIP/邮政编码

1. 在左侧导航栏中，在搜索栏中键入或粘贴**Ed** ，然后选择 " **EditForm1** " 以将其选中。

1. 重复上一过程和此过程中的步骤，以便 EditForm1 中的字段与 DetailForm1 中的字段相匹配。

## <a name="run-the-app"></a>运行应用

1. 在左侧导航栏中，在搜索栏中键入或粘贴**Br** ，然后选择 " **BrowseScreen1** " 以将其选中。

1. 按 F5（或选择右上角附近的“**预览**”图标）打开预览模式。

    > [!div class="mx-imgBorder"]
    > ![预览 "图标](./media/customize-forms-sharepoint/open-preview.png)

1. 在右上角，选择加号图标以便在**EditScreen1**中添加记录。

    > [!div class="mx-imgBorder"]
    > ![添加记录](./media/customize-forms-sharepoint/add-record.png)

1. 添加所需的任何数据，然后选择右上角的复选标记图标以保存所做的更改并返回到**BrowseScreen1**。

    > [!div class="mx-imgBorder"]
    > ![保存记录](./media/customize-forms-sharepoint/save-record.png)

1. 选择刚创建的项的箭头，以显示有关**DetailScreen1**中该项的详细信息。

    > [!div class="mx-imgBorder"]
    > ![右箭头](./media/customize-forms-sharepoint/right-arrow.png)

1. 在右上角，选择 "编辑" 图标以更新**EditScreen1**中的记录。

    > [!div class="mx-imgBorder"]
    > ![编辑记录](./media/customize-forms-sharepoint/edit-record.png)

1. 更改一个或多个字段中的信息，然后选择右上角的复选标记以保存更改并返回到**DetailScreen1**。

    > [!div class="mx-imgBorder"]
    > ![保存更改](./media/customize-forms-sharepoint/save-record.png)

1. 在右上角附近，选择垃圾桶图标，删除刚刚更新的记录并返回到**BrowseScreen1**。

    > [!div class="mx-imgBorder"]
    > ![删除记录](./media/customize-forms-sharepoint/delete-record.png)

1. 按 Esc （或选择左上角附近的关闭图标）关闭预览模式。

## <a name="next-steps"></a>后续步骤

- [保存并发布](save-publish-app.md)应用。
- 在应用中[自定义卡](customize-card.md)。