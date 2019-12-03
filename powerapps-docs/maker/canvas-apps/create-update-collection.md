---
title: 在画布应用中创建和更新集合 |Microsoft Docs
description: 在画布应用中创建集合，将项添加到集合中，并从该集合中删除一个或所有项
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/28/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 47233d4ead10ab01fe57c1f0573a4123894f9e58
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678663"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>在画布应用中创建和更新集合

使用集合来存储用户可以在应用中管理的数据。 集合是一组类似的项，例如产品列表中的产品。 有关不同类型的变量（例如集合）的详细信息，请[了解画布应用变量](working-with-variables.md)。

## <a name="prerequisites"></a>必备组件

- [注册](../signup-for-powerapps.md)Power Apps，并[提供注册所](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)用的相同凭据。
- 在 PowerApps 中创建一个应用，或打开一个现有应用。
- 了解如何在 PowerApps 中 [配置控件](add-configure-controls.md)。

## <a name="create-a-multicolumn-collection"></a>创建多列集合

1. 在 Power Apps Studio 中，添加**文本输入**控件。

    ![插入文本输入控件](./media/create-update-collection/add-textbox.png)

1. 通过选择左侧导航窗格中的省略号，选择 "**重命名**"，然后键入 " **ProductName**" 来重命名该控件。

    ![重命名控件](./media/create-update-collection/rename-textbox.png)

1. 添加**下拉**控件。

    ![添加下拉列表](./media/create-update-collection/add-dropdown.png)

1. 重命名**下拉**控件的**颜色**，并确保在属性列表中选择 " **Items** " 属性。

    ![项属性](./media/create-update-collection/items-property.png)

1. 在编辑栏中，将**DropDownSample**替换为以下表达式：

    `["Red","Green","Blue"]`

1. 添加一个**按钮**控件，将其**Text**属性设置为 **"Add"** ，并将其**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. 按 F5，在 " **ProductName**" 中键入一些文本，在 "**颜色**" 中选择一个选项，然后选择 "**添加**"。

    ![应用预览](./media/create-update-collection/preview-add.png)

1. 再重复前面的步骤至少两次，然后按 Esc。

1. 在 "**文件**" 菜单上，选择 "**集合**" 以显示你创建的集合。

    ![显示集合](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>显示集合

1. 添加垂直**库**控件。

    ![添加垂直库](./media/create-update-collection/add-gallery.png)

1. 将库的**Items**属性设置为**ProductList**。

1. 在 "**数据**" 窗格中，将 "副标题" 字段设置为 "**颜色**"，并将 "标题" 字段设置为 "**产品**"

    ![设置库的 Items 属性，并更改它所显示的字段](./media/create-update-collection/configure-gallery.png)

1. 关闭 "**数据**" 窗格，选择库，然后将 "**布局**" 字段设置为 "**标题" 和 "副标题**"。

    ![设置库的 Items 属性，并更改它所显示的字段](./media/create-update-collection/change-layout.png)

    屏幕类似于以下示例：

    ![第一个屏幕示例](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>删除一个或所有项

1. 通过单击或点击库底部附近，然后单击或点击左上角附近的铅笔图标，选择库模板。

    ![选择库模板](./media/create-update-collection/select-template.png)

1. 将**垃圾桶**图标添加到库模板。

    ![添加垃圾桶图标](./media/create-update-collection/trash-icon.png)

1. 将图标的**OnSelect**属性设置为以下公式：

    `Remove(ProductList, ThisItem)`

1. 在库外，添加一个按钮，将其**Text**属性设置为 **"Clear"** ，并将其**OnSelect**属性设置为以下公式：

    `Clear(ProductList)`

1. 按下 Alt 键时，为项选择 "**垃圾桶**" 图标以便从集合中删除该项，或选择 "**清除**" 按钮以从集合中删除所有项。

## <a name="put-a-sharepoint-list-into-a-collection"></a>将 SharePoint 列表放入集合

1. [创建到 SharePoint 列表的连接](connections/connection-sharepoint-online.md#create-a-connection).

1. 添加一个按钮，并将其 **[OnSelect](controls/properties-core.md)** 属性设置为此函数，将 ListName 替换为 SharePoint 列表的名称：<br>

    `Collect(MySPCollection, ListName)`

    此函数创建一个名为 MySPCollection 的集合，其中包含与 SharePoint 列表相同的数据。

1. 按住 Alt 键，并选择按钮。

1. 可有可无若要预览所创建的集合，请在 "**文件**" 菜单上选择 "**集合**"。

有关如何在库中显示 SharePoint 列表（如日期、选项和人员）的数据的信息，请查看库中的[列表列](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery)。 有关如何在窗体中显示数据的信息（使用下拉列表、日期选取器和人员选取器）：[编辑窗体和显示窗体控件](controls/control-form-detail.md)。

## <a name="next-steps"></a>后续步骤

- 查看有关**收集**函数的[参考主题](functions/function-clear-collect-clearcollect.md)。
- 了解如何使用[AddColumns、DropColumns、RenameColumns 和 ShowColumns](functions/function-table-shaping.md)函数在集合中绘制数据。
