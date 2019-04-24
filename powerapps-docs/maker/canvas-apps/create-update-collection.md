---
title: 创建和更新集合中的画布应用 |Microsoft Docs
description: 画布应用中创建集合、 将项添加到集合中，并移除其中的一个或所有项目
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/28/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6089063e2478c95bb5bfbc5926608d85552cea40
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61561480"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>创建和更新集合中的画布应用

使用集合来存储应用程序中的用户可以管理的数据。 集合是一组类似，例如产品列表中的产品的项。 有关不同类型的变量 （如集合） 的详细信息：[了解画布应用变量](working-with-variables.md)。

## <a name="prerequisites"></a>先决条件

- [注册](../signup-for-powerapps.md) PowerApps，然后使用注册所用的同一凭据[登录](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
- 在 PowerApps 中创建一个应用，或打开一个现有应用。
- 了解如何在 PowerApps 中 [配置控件](add-configure-controls.md)。

## <a name="create-a-multicolumn-collection"></a>创建多列的集合

1. 在 PowerApps Studio 中添加**文本输入**控件。

    ![插入文本输入的控件](./media/create-update-collection/add-textbox.png)

1. 通过在左侧的导航窗格中，选择其省略号重命名控件选择**重命名**，然后键入**ProductName**。

    ![重命名控件](./media/create-update-collection/rename-textbox.png)

1. 添加**下拉列表**控件。

    ![添加下拉列表](./media/create-update-collection/add-dropdown.png)

1. 重命名**下拉列表**控制**颜色**，并确保选中**项**属性列表中选择属性。

    ![项属性](./media/create-update-collection/items-property.png)

1. 在编辑栏中，将替换**DropDownSample**使用以下表达式：

    `["Red","Green","Blue"]`

1. 添加**按钮**控件，将其**文本**属性设置为 **"添加"**，并设置其**OnSelect**属性设为此公式：

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. 按 F5，键入一些文本**ProductName**，选择中的一个选项**颜色**，然后选择**添加**。

    ![应用程序的预览](./media/create-update-collection/preview-add.png)

1. 重复上述步骤至少两次，然后按 Esc。

1. 上**文件**菜单中，选择**集合**以说明您创建的集合。

    ![显示集合](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>显示集合

1. 添加垂直**库**控件。

    ![添加垂直库](./media/create-update-collection/add-gallery.png)

1. 设置库的**项**属性设置为**ProductList**。

1. 在中**数据**窗格中，将副标题字段设置为**颜色**，并将标题字段设置为**产品**。

    ![设置库的 Items 属性，并更改其所显示的字段](./media/create-update-collection/configure-gallery.png)

1. 关闭**数据**窗格中，选择库，然后设置**布局**字段**标题和副标题**。

    ![设置库的 Items 属性，并更改其所显示的字段](./media/create-update-collection/change-layout.png)

    你的屏幕类似于以下示例：

    ![第一个屏幕示例](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>删除一个或所有项

1. 通过单击或点击库底部附近，然后单击或点击左上角附近的铅笔图标选择库模板。

    ![选择库模板](./media/create-update-collection/select-template.png)

1. 添加**垃圾桶**向库模板的图标。

    ![添加垃圾桶图标](./media/create-update-collection/trash-icon.png)

1. 设置图标**OnSelect**属性设为此公式：

    `Remove(ProductList, ThisItem)`

1. 外部库中，添加一个按钮，设置其**文本**属性设置为 **"清除"**，并设置其**OnSelect**属性设为此公式：

    `Clear(ProductList)`

1. 按住 Alt 键，同时选择**垃圾桶**要从集合中删除该项目或选择的项的图标**清除**按钮以从集合中移除所有项。

## <a name="put-a-sharepoint-list-into-a-collection"></a>将 SharePoint 列表放入集合

1. [创建到 SharePoint 列表的连接](connections/connection-sharepoint-online.md#create-a-connection).

1. 添加一个按钮，并将其 **[OnSelect](controls/properties-core.md)** 属性设置为此函数，将 ListName 替换为 SharePoint 列表的名称：<br>

    `Collect(MySPCollection, ListName)`

    此函数创建一个名为 MySPCollection 的集合，其中包含与 SharePoint 列表相同的数据。

1. 按住 Alt 键，并选择按钮。

1. （可选）若要预览你所创建的集合，请选择**集合**上**文件**菜单。

有关如何在库中显示数据 （如日期、 选择和人员） 在 SharePoint 列表中的信息：[显示库中的列表列](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery)。 有关如何在 （具有下拉列表、 日期选取器和人员选取器） 的窗体中显示数据的信息：[编辑窗体和显示窗体控件](controls/control-form-detail.md)。

## <a name="next-steps"></a>后续步骤

- 审阅[参考主题](functions/function-clear-collect-clearcollect.md)有关**收集**函数。
- 了解如何通过使用形状集合中的数据[AddColumns、 DropColumns、 RenameColumns 和 ShowColumns](functions/function-table-shaping.md)函数。
