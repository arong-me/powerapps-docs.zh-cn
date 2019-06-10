---
title: 创建画布应用中的顺序库 |Microsoft Docs
description: 创建顺序库中用于管理数据的 Northwind Traders 的画布应用
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 94d6c104cb888bb13f3724231d7891d622f5377b
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66760996"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>创建画布应用中的顺序库

按照分步说明来创建顺序库用于管理在 Northwind Trader 数据库中的虚拟数据的画布应用中。 本主题是介绍如何在 Common Data Service 中的关系数据上构建企业应用程序的一系列的一部分。 为了获得最佳结果，将介绍此序列中的以下主题：

1. 创建顺序库 (**本主题**)。
1. [创建摘要的窗体](northwind-orders-canvas-part2.md)。
1. [创建详细信息库](northwind-orders-canvas-part3.md)。

> [!div class="mx-imgBorder"]
> ![屏幕区域的定义](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>先决条件

- [安装的 Northwind Trader 数据库和应用](northwind-install.md)。
- 通读[概述的画布应用](northwind-orders-canvas-overview.md)为 Northwind Traders。

## <a name="create-a-blank-app"></a>创建空白应用

1. [登录到 PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后创建一个空白的平板电脑应用。

    > [!div class="mx-imgBorder"]
    > ![从空白磁贴的画布应用](media/northwind-orders-canvas-part1/start-01.png)

1. 任何应用命名，请然后选择**创建**。

    > [!div class="mx-imgBorder"]
    > ![空白对话框中的画布应用](media/northwind-orders-canvas-part1/start-02.png)

    将会打开 PowerApps Studio，以便可以将数据源和控件添加到您的应用程序：

    > [!div class="mx-imgBorder"]
    > ![PowerApps Studio](media/northwind-orders-canvas-part1/start-03.png)

1. 启用[实验性功能](working-with-experimental.md)显示直接在公式栏中的公式的结果。

    1. 上**文件**菜单中，选择**应用程序设置**，然后选择**高级设置**。
    1. 滚动到的功能，列表的底部，然后开启**启用公式栏结果视图**:

        > [!div class="mx-imgBorder"]
        > ![实验性功能的列表](media/northwind-orders-canvas-part1/start-04.png)

1. 在左上角中，选择后退箭头返回到空白画布。

## <a name="add-the-data"></a>添加数据

1. 上**视图**选项卡上，选择**数据源**，然后选择**添加数据源**中**数据**窗格：

    > [!div class="mx-imgBorder"]
    > ![选择查看数据源、 添加数据源](media/northwind-orders-canvas-part1/datasource-01.png)

1. 选择**Common Data Service**。

    如果**Common Data Service**未显示在列表中的连接，选择**新的连接**，然后将其添加。

    > [!div class="mx-imgBorder"]
    > ![连接的列表](media/northwind-orders-canvas-part1/datasource-02.png)

1. 下**选择实体**，类型**订单**，选择**订单**复选框，然后选择**Connect**:

    > [!div class="mx-imgBorder"]
    > ![实体的列表](media/northwind-orders-canvas-part1/datasource-03.png)

    已添加**订单**到您的应用程序的数据源：

    > [!div class="mx-imgBorder"]
    > ![数据窗格](media/northwind-orders-canvas-part1/datasource-04.png)

    **订单**实体包含各种类型的多个字段：

    > [!div class="mx-imgBorder"]
    > ![订单实体中的字段的列表](media/northwind-orders-canvas-part1/datasource-05.png)

    每个字段有**显示名称**和一个**名称**，有时称为逻辑名称。 这两个名称引用相同的操作。 一般情况下，将使用的显示名称，如果生成应用，但某些情况下需要较为隐秘**名称**、 一个过程中所述。

1. 在 PowerApps Studio 中关闭**数据**窗格中选择在其右上角的关闭图标 (x)。

## <a name="create-the-order-gallery"></a>创建顺序库

1. 上**插入**选项卡上，选择**库** > **垂直空白库**添加[**库**](controls/control-gallery.md)控件，它将在显示订单。

    > [!div class="mx-imgBorder"]
    > ![Insert、 库中，垂直空白库](media/northwind-orders-canvas-part1/orders-01.png)

1. 在编辑栏设置库的**项**属性设为此公式：

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    [**排序**](functions/function-sort.md)函数对列表排序，以便首先出现的最新的顺序 （它具有最高的订单号）。

    > [!div class="mx-imgBorder"]
    > ![设置库的 Items 属性](media/northwind-orders-canvas-part1/orders-02.png)

1. 在中**属性**附近的右边缘，打开选项卡**布局**列表：

    > [!div class="mx-imgBorder"]
    > ![布局选项的列表](media/northwind-orders-canvas-part1/orders-03.png)

1. 在选项列表中，选择**标题和副标题**:

    > [!div class="mx-imgBorder"]
    > ![选择布局](media/northwind-orders-canvas-part1/orders-04.png)

    两个[**标签**](controls/control-text-box.md)库的模板中添加控件。 默认情况下，这些控件显示的两个列**订单**实体，接下来，您将更改。 库模板的垂直复制以在实体中的每个记录。

1. 如果已关闭**数据**窗格中，选择**编辑**(下一步**字段**) 中**属性**右边缘附近的选项卡。

1. 在中**数据**窗格中，选择**Title1** （或库的模板中选择上部标签）。

1. 在编辑栏中，将设置的标签**文本**属性设置为此表达式：

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > ![设置标题标签的 Text 属性](media/northwind-orders-canvas-part1/orders-06.png)

    每个库项的顶部显示的订单号。 在库模板后， **ThisItem**授予访问权限中的所有字段**顺序**实体。

1. 在中**数据**窗格中，选择**Subtitle1** （或库的模板中选择较低的标签）：

    > [!div class="mx-imgBorder"]
    > ![选择副标题标签](media/northwind-orders-canvas-part1/orders-07.png)

1. 在编辑栏中，将设置的标签**文本**属性设置为此表达式：

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > ![将对白字幕标签的 Text 属性设置](media/northwind-orders-canvas-part1/orders-08.png)

    键入下面的公式后，它可能暂时显示红色的波浪线错误。 如果选择公式栏之外的任何内容，然后将光标返回到编辑栏，应清除错误。 如果错误仍然存在，或者看不到一个值，则选择**视图**选项卡上，选择**数据源**，然后刷新**订单**通过选择省略号 （...） 到实体数据源名称。

    当指定**ThisItem.Customer**，，您在利用之间的多对一关系**订单**并**客户**实体和检索客户记录与每个订单关联。 要从客户记录提取中的数据**公司**列以供显示。

    可以显示从所有关系**订单**实体与其他实体，包括**客户**实体：

    > [!div class="mx-imgBorder"]
    > ![关系的列表](media/northwind-orders-canvas-part1/orders-09.png)

1. 关闭**数据**窗格中选择在其右上角的关闭图标 (x)。

## <a name="show-each-orders-status"></a>显示每个订单的状态

在此过程中，将在标签的库中添加空间，将其配置为在基于的数据在不同的颜色显示每个订单的状态。

1. 在库的模板中，减少的第一个标签，宽度**Title1**:

    > [!div class="mx-imgBorder"]
    > ![库的模板中的标题 1](media/northwind-orders-canvas-part1/status-01.png)

1. 重复使用第二个标签，在上一步**Subtitle1**:

    > [!div class="mx-imgBorder"]
    > ![库的模板中的 Subtitle1](media/northwind-orders-canvas-part1/status-02.png)

1. 使用库模板 （或模板中的控件），它选择，选择**标签**上**插入**选项卡：

    > [!div class="mx-imgBorder"]
    > ![添加一个标签](media/northwind-orders-canvas-part1/status-03.png)

1. 将新标签移动到右侧**Title1**标签：

    > [!div class="mx-imgBorder"]
    > ![移动和调整标签](media/northwind-orders-canvas-part1/status-04.png)

1. 设置**文本**属性为此表达式的新标签：

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![设置文本属性](media/northwind-orders-canvas-part1/status-05.png)

    在中**订单**实体，**订单状态**字段保存从值**订单状态**选项集。 选项集是类似于其他编程工具中的枚举。 因此，用户可以指定只有这些组中的选项，在数据库中，定义每个组的选项。 **订单状态**选项集也是全局而非本地，因此可以在其他实体中使用它：

    > [!div class="mx-imgBorder"]
    > ![状态选项集进行排序](media/northwind-orders-canvas-part1/status-06.png)

    每个选项在一组中有如果显示在标签中显示的名称。 可以本地化这些名称，并应用识别相同的选项，英语用户选择是否**Apple**，法语用户选择**Pomme**，或西班牙语用户选择**Manzana**. 出于此原因，不能创建的公式，依赖于硬编码字符串有关的选项，如本主题中所示更高版本。

    在公式中，必须括住**订单状态**与单一引号，因为它包含一个空格。 但是，该名称的功能相同方式与任何其他名称在 PowerApps 中，如**客户**或**公司**，does。

1. 上**主页**选项卡上，增加到 20 点，状态标签的字体大小和右对齐的文本：

    > [!div class="mx-imgBorder"]
    > ![更改字体大小和对齐方式](media/northwind-orders-canvas-part1/status-07.png)

1. 在编辑栏中，将**颜色**属性的状态标签为以下公式：

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![状态标签的颜色属性设置](media/northwind-orders-canvas-part1/status-08.png)

    PowerApps 可阻止您创建依赖于硬编码的字符串中一组每个选项，因为此类公式可能产生不良结果，如果选项名称已本地化的公式。 相反，**交换机**函数确定基于根据用户的设置的标签中显示的任何字符串的颜色。

    通过此公式中的位置，不同的状态值出现在不同的颜色，如前面的图形所示。

## <a name="display-each-orders-total"></a>显示每个订单的总计

1. 在库中，这是库的模板选择的第一项：

    > [!div class="mx-imgBorder"]
    > ![选择库模板](media/northwind-orders-canvas-part1/aggregate-01.png)

1. 上**插入**选项卡上，选择**标签**以添加另一个标签：

    > [!div class="mx-imgBorder"]
    > ![添加一个标签](media/northwind-orders-canvas-part1/aggregate-02.png)

1. 移动新标签，以使其显示在状态标签下：

    > [!div class="mx-imgBorder"]
    > ![调整大小和移动的新标签](media/northwind-orders-canvas-part1/aggregate-03.png)

1. 在编辑栏中，将设置新的标签**文本**属性设为此公式：

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![公式用于计算订单的总成本](media/northwind-orders-canvas-part1/aggregate-04.png)

    在此公式中， [**总和**](functions/function-aggregates.md)函数将中的记录**订单详细信息**与中的每个记录相关联的实体**顺序**通过一个对多关系的实体。 这些明细项目构成每个订单，并将使用相同的一对多关系来显示和编辑屏幕的右下角区域中的行项。

    此公式显示了出现蓝色下划线和一个[委派警告](delegation-overview.md)因为 Common Data Service 不支持复杂的聚合函数 （例如，乘法运算的总和） 的委派。 因为没有在此示例中的顺序将包含 500 多个行项，则可以忽略此信息。 如果需要不同的应用，则可以增加该限制**应用设置**。

    [**文本**](functions/function-text.md)函数在此公式中添加货币符号，并使用千位分隔符和十进制分隔符将结果格式化。 顾名思义，公式中包含的语言标记适用于美国英语 ( **[$-EN-US]** ) 和美元符号 ( **$** )。 如果删除的语言标记，将替换基于您的语言设置和标签会显示该标记的适当格式。 如果将美元符号，标签会显示基于用户的设置的相应货币符号。 但是，可以强制其他符号显示的美元符号替换为自己喜欢的。

1. 上**主页**选项卡，将最新的标签的字体大小更改为 20 磅，其文本右对齐：

    > [!div class="mx-imgBorder"]
    > ![更改字体大小和标签的对齐方式](media/northwind-orders-canvas-part1/aggregate-05.png)

1. 将库移动到屏幕的左边缘，降低库的宽度，以关闭一些空间。

1. 增加库的高度，这样就几乎高度都是屏幕上，但留出一些顶部的标题栏，你将在下一主题开始添加：

    > [!div class="mx-imgBorder"]
    > ![移动和调整库的大小](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>摘要

概括来说，你开始通过添加包含这些元素的顺序库生成单屏幕画布应用：

- 要显示的订单号的表达式： `"Orders " & ThisItem.OrderNumber`
- 多对一关系中的字段： `ThisItem.Customer.Company`
- 显示选项的名称中一组的标签： `ThisItem.'Order Status'`
- 更改基于一组中的哪个选项，标签显示格式标签： `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- 一个对多关系是复杂的聚合函数： `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>下一主题

在下一主题将添加[**编辑窗体**](controls/control-form-detail.md)控件来显示和编辑刚创建的库中选择的任何排序用户的摘要。

> [!div class="nextstepaction"]
> [创建摘要窗体](northwind-orders-canvas-part2.md)