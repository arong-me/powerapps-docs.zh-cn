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
ms.openlocfilehash: bb6f8edb35bd6f19bff06516f6fb9d22de1320a0
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42852660"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>自定义 PowerApps 中的画布应用窗体

在画布应用中，自定义“显示窗体”控件和“编辑窗体”控件，以便它们以最直观的顺序显示最重要的数据，帮助用户轻松了解和更新数据。

每个窗体包含一个或多个卡，其中每个卡均可显示数据源中特定列的数据。 按照本主题中的步骤操作，可以指定在窗体中显示的卡并在窗体中上下移动卡。

如果不熟悉 PowerApps，请参阅 [PowerApps 简介](getting-started.md)。

## <a name="prerequisites"></a>先决条件

从 Common Data Service [生成应用](data-platform-create-app.md)，然后在该应用中[自定义库](customize-layout-sharepoint.md)。

## <a name="show-and-hide-cards"></a>显示和隐藏卡

1. 登录 [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    ![PowerApps 站点的主页](./media/customize-forms-sharepoint/sign-in.png)


1. 打开生成并自定义的应用。

1. 在左侧导航栏中，在搜索栏中键入或粘贴 D 以筛选元素列表，然后单击或点击 DetailForm1 以将其选中。

    ![选择详细信息屏幕](./media/customize-forms-sharepoint/select-detailform.png)

1. 在右侧窗格中，单击或点击“帐户”以显示“数据”窗格。

    ![显示“数据”窗格](./media/customize-forms-sharepoint/show-data-pane.png)

1. 在“数据”窗格中，取消选中“主要联系人”、“描述”和“地址 1: 街道 2”复选框以隐藏这些字段。

    ![字段列表](./media/customize-forms-sharepoint/hide-fields.png)

1.  在“数据”窗格中，选中“地址 1: ZIP/邮政编码”复选框以显示这些字段。

    ![字段列表](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>对卡重新排序
1. 在“数据”窗格中，将“帐户名”字段拖到字段列表顶部。

    ![移动卡](./media/customize-forms-sharepoint/move-card.png)

    DetailForm1 中的卡反映了相同更改。

    ![重新排序后的卡](./media/customize-forms-sharepoint/reordered-card.png)

1. 将其他卡重新排序为以下顺序：

    - 帐户名
    - 地址 1：街道 1
    - 地址 1：城市
    - 地址 1：ZIP/邮政编码
    - 员工人数
    - 年收入

1. 在左侧导航栏中，在搜索栏中键入或粘贴 Ed，然后单击或点击 EditForm1 以将其选中。

1. 重复上一过程和此过程中的步骤，以便 EditForm1 中的字段与 DetailForm1 中的字段相匹配。

## <a name="run-the-app"></a>运行应用
1. 在左侧导航栏中，键入或粘贴 Br 以筛选列表，然后单击或点击 BrowseScreen1 以将其选中。

2. 按 F5（或选择右上角附近的“**预览**”图标）打开预览模式。

    ![预览图标](./media/customize-forms-sharepoint/open-preview.png)

3. 在右上角，单击或点击加号图标，在“**EditScreen1**中添加一条记录。

    ![添加记录](./media/customize-forms-sharepoint/add-record.png)

4. 添加任何所需的数据，然后单击或点击右上角的选中标记图标，以保存更改并返回到 BrowseScreen1。

    ![保存记录](./media/customize-forms-sharepoint/save-record.png)

5. 单击或点击刚刚创建的项的箭头，可在 **DetailScreen1** 中显示有关该项的详细信息。  

    ![右箭头](./media/customize-forms-sharepoint/right-arrow.png)

6. 在右上角，单击或点击加号图标，更新 **EditScreen1** 中的记录。

    ![编辑记录](./media/customize-forms-sharepoint/edit-record.png)

7. 更改一个或多个字段中的信息，然后单击或点击右上角的复选标记，保存对 SharePoint 列表所做的更改并返回到“DetailScreen1”。  

    ![保存更改](./media/customize-forms-sharepoint/save-record.png)

8. 单击或点击右上角附近的回收站图标，删除刚刚更新的记录并返回到“BrowseScreen1”。

    ![删除记录](./media/customize-forms-sharepoint/delete-record.png)

9. 按 Esc（或通过单击或点击左上角附近的关闭图标）关闭预览模式。

## <a name="next-steps"></a>后续步骤
- [保存并发布](save-publish-app.md)应用。
- 在应用中[自定义卡](customize-card.md)。
