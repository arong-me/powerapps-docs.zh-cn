---
title: 在画布应用中创建订单库 |Microsoft Docs
description: 在画布应用中创建订单库，以管理 Northwind 商贸的数据
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 06c3a02d1ea3943f64661334ca419f6f205e8b7e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675817"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>在画布应用中创建订单库

按照分步说明在画布应用中创建订单库，以便在 Northwind 商贸数据库中管理虚拟数据。 本主题是一系列文章的一部分，说明如何在 Common Data Service 中构建业务应用程序的关系数据。 为了获得最佳结果，请在此序列中浏览这些主题：

1. 创建订单库（**本主题**）。
1. [创建摘要窗体](northwind-orders-canvas-part2.md)。
1. [创建详细信息库](northwind-orders-canvas-part3.md)。

> [!div class="mx-imgBorder"]
> ![屏幕区域的定义](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>必备组件

- [安装 Northwind 商贸数据库和应用](northwind-install.md)。
- 通读 Northwind 商贸的[画布应用概述](northwind-orders-canvas-overview.md)。

## <a name="create-a-blank-app"></a>创建空白应用

1. [登录到 PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后创建一个空的平板电脑应用。

    > [!div class="mx-imgBorder"]
    > 空白磁贴中的 ![画布应用](media/northwind-orders-canvas-part1/start-01.png)

1. 任意命名你的应用，然后选择 "**创建**"。

    > [!div class="mx-imgBorder"]
    > "从空白 ![画布应用" 对话框](media/northwind-orders-canvas-part1/start-02.png)

    打开 Power Apps Studio 后，可以将数据源和控件添加到应用：

    > [!div class="mx-imgBorder"]
    > ![Power Apps Studio](media/northwind-orders-canvas-part1/start-03.png)

## <a name="add-the-data"></a>添加数据

1. 在 "**视图**" 选项卡上，选择 "**数据源**"：

    > [!div class="mx-imgBorder"]
    > ![选择视图、数据源、添加数据源](media/northwind-orders-canvas-part1/datasource-01.png)

1. 在搜索框中键入**orders** ：

    > [!div class="mx-imgBorder"]
    > ![连接列表](media/northwind-orders-canvas-part1/datasource-02.png)

1. 选择要在应用中使用的**订单**数据源：

    > [!div class="mx-imgBorder"]
    > 实体 ![列表](media/northwind-orders-canvas-part1/datasource-03.png)

    **Orders**实体包含各种类型的多个字段：

    > [!div class="mx-imgBorder"]
    > "订单" 实体中的字段 ![列表](media/northwind-orders-canvas-part1/datasource-05.png)

    每个字段都有一个**显示名称**和一个**名称**，该名称有时称为逻辑名称。 这两个名称引用相同的内容。 通常情况下，在生成应用时将使用显示名称，但某些情况下需要的**名称**越多，如过程中所述。

1. 由于我们将使用屏幕和控件，接下来，在 Power Apps Studio 中，通过按三个堆积正方形图标切换回左侧的**树视图**。 您可以通过按圆柱体图标随时返回到**数据源**。

## <a name="create-the-order-gallery"></a>创建订单库

1. 在 "**插入**" 选项卡上，选择 "**库** > **空白垂直**" 以添加[**库**](controls/control-gallery.md)控件，该控件将显示订单。

    > [!div class="mx-imgBorder"]
    > ![插入、库、空白垂直](media/northwind-orders-canvas-part1/orders-01.png)

    控件将被放置在画布上，并将显示 "飞出" 对话框，询问要连接到哪些数据源。  


    > [!div class="mx-imgBorder"]
    > ![库的 Set Items 属性](media/northwind-orders-canvas-part1/orders-02.png)

1. 我们可以将它直接连接到此处的**订单**，但我们想要控制库的排序顺序。  忽略飞出对话框，并在编辑栏中将库的**Items**属性设置为以下公式：

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    Sort 函数对该列表[**进行排序**](functions/function-sort.md)，以便先显示最新的订单（具有最高的订单号）。

    > [!div class="mx-imgBorder"]
    > ![库的 Set Items 属性](media/northwind-orders-canvas-part1/orders-02b.png)

1. 几分钟后，结果视图将显示在编辑栏的下方。  向下下拉箭头以查看公式的结果。  向右滚动以查看 "**订单号**" 列，并确保按所需的方式对其进行排序（从高到低）。  

    > [!div class="mx-imgBorder"]
    > ![库的 Set Items 属性](media/northwind-orders-canvas-part1/orders-02c.png)

1. 在右侧边缘附近的 "**属性**" 选项卡中，打开 "**布局**" 列表：

    > [!div class="mx-imgBorder"]
    > ![布局选项的列表](media/northwind-orders-canvas-part1/orders-03.png)

1. 在选项列表中，选择 "**标题和副标题**"：

    > [!div class="mx-imgBorder"]
    > ![选择布局](media/northwind-orders-canvas-part1/orders-04.png)

    将两个[**标签**](controls/control-text-box.md)控件添加到库的模板中。 默认情况下，这些控件显示 " **Orders** " 实体的两个列，接下来将更改这些列。 将为实体中的每个记录垂直复制库的模板。

1. 在右侧边缘附近的 "**属性**" 选项卡中，选择 "**编辑**" （**字段**旁边）。

    > [!div class="mx-imgBorder"]
    > ![选择布局](media/northwind-orders-canvas-part1/orders-04b.png)

1. 在 "**数据**" 窗格中，选择 " **Title1** " （或选择库模板中的上部标签）。

1. 在编辑栏中，将标签的 " **Text** " 属性设置为以下表达式：

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > ![设置标题标签的 Text 属性](media/northwind-orders-canvas-part1/orders-06.png)

    订单号将显示在每个库项的顶部。 在库模板中， **ThisItem**向**Order**实体中的所有字段授予访问权限。

1. 在 "**数据**" 窗格中，选择 " **Subtitle1** " （或选择库模板中的下部标签）：

    > [!div class="mx-imgBorder"]
    > ![选择副标题标签](media/northwind-orders-canvas-part1/orders-07.png)

1. 在编辑栏中，将标签的 " **Text** " 属性设置为以下表达式：

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > ![设置副标题标签的 Text 属性](media/northwind-orders-canvas-part1/orders-08.png)

    输入此公式后，可能会有一段时间显示红色波浪错误。 如果您在公式栏之外选择了任何内容，然后将光标返回到公式栏中，则会清除该错误。 如果错误仍然存在或未显示值，请选择 "**视图**" 选项卡，选择 "**数据源**"，然后通过选择 "数据源名称" 右侧的省略号（...）来刷新 "**订单**" 实体。

    指定**ThisItem**时，将利用**Orders**和**Customers**实体之间的多对一关系，并检索与每个订单关联的客户记录。 从客户记录中，您要在 "**公司**" 列中提取数据以供显示。

    您可以显示 "**订单**" 实体与 "**客户**" 实体之间的所有关系：

    > [!div class="mx-imgBorder"]
    > ![关系列表](media/northwind-orders-canvas-part1/orders-09.png)

1. 通过选择右上角的 "关闭" 图标（x）来关闭 "**数据**" 窗格。

## <a name="show-each-orders-status"></a>显示每个订单的状态

在此过程中，您将在库中为标签添加空间，并将其配置为根据数据以不同的颜色显示每个订单的状态。

1. 在库的模板中，缩小第一个标签的宽度， **Title1**：

    > [!div class="mx-imgBorder"]
    > ![库模板中的 Title1](media/northwind-orders-canvas-part1/status-01.png)

1. 对第二个标签**Subtitle1**重复上述步骤：

    > [!div class="mx-imgBorder"]
    > ![库模板中的 Subtitle1](media/northwind-orders-canvas-part1/status-02.png)

1. 在选定库模板（或模板中的控件）的情况下，选择 "**插入**" 选项卡上的 "**标签**"：

    > [!div class="mx-imgBorder"]
    > ![添加标签](media/northwind-orders-canvas-part1/status-03.png)

1. 将新标签移动到 " **Title1** " 标签的右侧：

    > [!div class="mx-imgBorder"]
    > ![移动标签并调整其大小](media/northwind-orders-canvas-part1/status-04.png)

1. 将新标签的 " **Text** " 属性设置为此表达式：

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![设置 "Text" 属性](media/northwind-orders-canvas-part1/status-05.png)

    在 "**订单**" 实体中，"**订单状态**" 字段保留 "**订单状态**" 选项集的值。 选项集类似于其他编程工具中的枚举。 每组选项都是在数据库中定义的，因此用户只能指定集中的那些选项。 "**订单状态**" 选项集也是全局的，而不是本地的，因此可以在其他实体中使用它：

    > [!div class="mx-imgBorder"]
    > ![订单状态选项集](media/northwind-orders-canvas-part1/status-06.png)

    如果在标签中显示某个集合中的每个选项，则会显示该名称。 可以对这些名称进行本地化，应用可识别相同的选项，无论是英语用户选择**Apple**、法语用户还是选择**Pomme**，还是西班牙语用户选择**Manzana**。 因此，不能创建依赖于某个选项的硬编码字符串的公式，如本主题后面所示。

    在公式中，必须将**订单状态**括在单引号中，因为它包含空格。 但是，此名称的工作方式与 Power Apps 中的任何其他名称（如**Customer**或**Company**）的工作方式相同。

1. 在 "**主页**" 选项卡上，将状态标签的字体大小增加到20个点，然后右对齐文本：

    > [!div class="mx-imgBorder"]
    > ![更改字号和对齐方式](media/northwind-orders-canvas-part1/status-07.png)

1. 在编辑栏中，将状态标签的 "**颜色**" 属性设置为以下公式：

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置状态标签的 "颜色" 属性](media/northwind-orders-canvas-part1/status-08.png)

    Power Apps 使你无法创建一个公式，该公式依赖于集中每个选项的硬编码字符串，因为当选项名称已本地化时，此类公式可能会产生不正确的结果。 相反， **Switch**函数基于用户的设置来确定标签中显示的任何字符串的颜色。

    设置此公式后，不同的状态值以不同的颜色显示，如上图所示。

## <a name="display-each-orders-total"></a>显示每个订单的总数

1. 选择库中的第一项，即库的模板：

    > [!div class="mx-imgBorder"]
    > ![选择库模板](media/northwind-orders-canvas-part1/aggregate-01.png)

1. 在 "**插入**" 选项卡上，选择 "**标签**" 添加另一个标签：

    > [!div class="mx-imgBorder"]
    > ![添加标签](media/northwind-orders-canvas-part1/aggregate-02.png)

1. 移动新标签，使其显示在 "状态" 标签下：

    > [!div class="mx-imgBorder"]
    > ![重设大小并移动新标签](media/northwind-orders-canvas-part1/aggregate-03.png)

1. 在编辑栏中，将 "新建标签" 的 "**文本**" 属性设置为以下公式：

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > 用于计算订单的总成本的 ![公式](media/northwind-orders-canvas-part1/aggregate-04.png)

    在此公式中， [**Sum**](functions/function-aggregates.md)函数通过一对多关系在**订单详细信息**实体中添加与**订单**实体中每条记录关联的记录。 这些行项构成每个订单，您将使用同一一对多关系来显示和编辑屏幕右下方区域中的行项。

    此公式显示蓝色下划线和[委托警告](delegation-overview.md)，因为 Common Data Service 不支持对复杂聚合函数（例如，乘法）的委托。 您可以忽略此信息，因为此示例中的任何订单都不包含500行以上的项。 如果需要其他应用，可以在**应用设置**中增加该限制。

    此公式中的[**文本**](functions/function-text.md)函数添加货币符号，并使用千位分隔符和小数分隔符设置结果格式。 根据编写，该公式包括美国英语的语言标记（ **[$-en-us]** ）和一个美元符号（ **$** ）。 如果删除 language 标记，则会将其替换为基于您的语言设置的一个标记，标签将显示该标记的相应格式。 如果保留美元符号，则标签将根据用户的设置显示相应的货币符号。 但是，您可以通过将美元符号替换为您喜欢的符号来强制显示不同的符号。

1. 在 "**主页**" 选项卡上，将最新标签的字体大小更改为20磅，并将其文本右对齐：

    > [!div class="mx-imgBorder"]
    > ![更改标签的字号和对齐方式](media/northwind-orders-canvas-part1/aggregate-05.png)

1. 将库移动到屏幕的左边缘，并缩小库的宽度以关闭一些空间。

1. 增加库的高度，使其与屏幕几乎一样高，但将标题栏的顶部留下一点空间，并将其添加到下一主题开头：

    > [!div class="mx-imgBorder"]
    > ![移动库并调整其大小](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>摘要

概括而言，你开始通过添加订单库来生成一个屏幕画布应用，其中包括以下元素：

- 用于显示订单号的表达式： `"Orders " & ThisItem.OrderNumber`
- 多对一关系中的字段： `ThisItem.Customer.Company`
- 显示某一集中选项的名称的标签： `ThisItem.'Order Status'`
- 根据标签中显示的选项更改格式的标签： `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- 对一对多关系的复杂聚合函数： `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>下一主题

在下一主题中，你将添加 "[**编辑窗体**](controls/control-form-detail.md)" 控件，以显示和编辑用户在刚创建的库中选择的任意订单的摘要。

> [!div class="nextstepaction"]
> [创建摘要窗体](northwind-orders-canvas-part2.md)
