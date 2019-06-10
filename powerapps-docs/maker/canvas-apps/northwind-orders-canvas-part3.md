---
title: 创建画布应用中的详细信息库 |Microsoft Docs
description: 创建用于管理数据的 Northwind Traders 的画布应用中的详细信息库
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
ms.openlocfilehash: 9549b8f389cf696cf3fc8e4659da6b418383ac6e
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66760950"
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>创建画布应用中的详细信息库

按照分步说明来创建用于管理在 Northwind Trader 数据库中的虚拟数据的画布应用中的详细信息库。 本主题是介绍如何在 Common Data Service 中的关系数据上构建企业应用程序的一系列的一部分。 为了获得最佳结果，将介绍此序列中的以下主题：

1. [创建顺序库](northwind-orders-canvas-part1.md)。
1. [创建摘要的窗体](northwind-orders-canvas-part2.md)。
1. 创建详细信息库 (**本主题**)。

> [!div class="mx-imgBorder"]
> ![屏幕区域的定义](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>先决条件

在开始本主题之前，必须安装数据库，如本主题中前面所述。 您必须再创建顺序库和摘要的窗体或打开**Northwind 订单 （画布）-第 3 部分开始**已包含库和该窗体的应用程序。

## <a name="create-another-title-bar"></a>创建另一个标题栏

1. 在屏幕的顶部，选择[**标签**](controls/control-text-box.md)作为标题栏控件通过按 Ctrl + C 复制它，然后将其粘贴通过按 Ctrl:

    > [!div class="mx-imgBorder"]
    > ![复制并粘贴标题栏](media/northwind-orders-canvas-part3/details-01.png)

1. 调整大小和移动副本，以使其只需在汇总窗体下显示。

1. 从这些方式中的任一副本中删除文本：

    - 双击以选择它的文本，然后按 Delete。
    - 设置的标签**文本**属性设置为空字符串 ( **""** )。

    > [!div class="mx-imgBorder"]
    > ![删除标题栏复制中的文本](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>添加库

1. 插入[**库**](controls/control-gallery.md)与控制**垂直空白库**布局：

    > [!div class="mx-imgBorder"]
    > ![添加空白垂直库](media/northwind-orders-canvas-part3/details-03.png)

    新的库，它将在显示订单详细信息，将显示在左上角中：

    > [!div class="mx-imgBorder"]
    > ![订单详细信息库的默认位置](media/northwind-orders-canvas-part3/details-04.png)

1. 关闭**数据**窗格中，然后调整大小并移动到右下角，新的标题栏下方的库详细信息：

    > [!div class="mx-imgBorder"]
    > ![最终的订单详细信息库位置](media/northwind-orders-canvas-part3/details-05.png)

1. 设置**项**属性的详细信息库为以下公式：

    ```powerapps-dot
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![设置项属性的详细信息库](media/northwind-orders-canvas-part3/details-06.png)

    如果出现一个错误，请确认订单库名为**Gallery1** (在**树视图**窗格的左边缘附近)。 如果库具有不同的名称，其重命名**Gallery1**。

    只需链接两个库。 所选内容时用户选择顺序库中的订单，标识中的记录**订单**实体。 如果订单包含一个或多个行项中的记录**订单**实体链接到中的一个或多个记录**订单详细信息**实体，并且这些记录中的数据显示在详细信息库。 此行为将反映已为你之间创建一个对多关系**订单**并**订单详细信息**实体。 指定的公式"指导"该关系使用点表示法：

    > [!div class="mx-imgBorder"]
    > ![Orders 实体和订单详细信息实体之间的一个对多关系](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>显示产品名称

1. 在详细信息库中，选择**从插入选项卡添加项**选择库模板：

    > [!div class="mx-imgBorder"]
    > ![选择库详细信息的模板](media/northwind-orders-canvas-part3/details-07.png)

    确保已选择库模板而不是库本身。 边界框应略有内部库的边界和可能短于库的高度。 此模板中插入控件，因为它们会重复库中每一项。

1. 上**插入**选项卡上，插入到库详细信息的标签。

    标签应出现在库;如果没有，重试，但请务必选择库模板，然后插入标签。

    > [!div class="mx-imgBorder"]
    > ![将标签添加到库详细信息](media/northwind-orders-canvas-part3/details-08.png)

1. 设置新标签**文本**属性设为此公式：

    ```powerapps-dot
    ThisItem.Product.'Product Name'
    ```

    如果没有文本显示，请选择箭头**顺序 0901年**顺序库底部附近。

1. 设标签的大小，以便将显示完整的文本：

    > [!div class="mx-imgBorder"]
    > ![在订单详细信息中显示产品名称](media/northwind-orders-canvas-part3/details-09.png)

    此表达式中的记录将指导**订单详细信息**实体。 该记录会保留在**ThisItem**转移到**订购产品**通过多对一关系的实体：

    > [!div class="mx-imgBorder"]
    > ![订单详细信息实体和顺序 Product 实体的多对一关系](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    **产品名称**提取字段 （和即将使用其他字段）：

    > [!div class="mx-imgBorder"]
    > ![订购产品实体中的字段](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>显示产品图像

1. 上**插入**选项卡上，插入[**图像**](controls/control-image.md)到详细信息库控件：

    > [!div class="mx-imgBorder"]
    > ![插入图像控件](media/northwind-orders-canvas-part3/details-10.png)

1. 调整大小和移动图像和标签以并排放置。

    > [!TIP]
    > 进行精细控制的大小和控件的位置，开始调整大小或将其移动而无需按 Alt 键，然后继续或按住 Alt 键，同时移动控件或调整：

    > [!div class="mx-imgBorder"]
    > ![移动图像控件](media/northwind-orders-canvas-part3/details-11.png)

1. 设置图像的**图像**属性设为此公式：

    ```powerapps-dot
    ThisItem.Product.Picture
    ```

    同样，该表达式引用一个与此相关联的产品的订单详细信息和提取**图片**要显示字段。

    > [!div class="mx-imgBorder"]
    > ![显示产品图像](media/northwind-orders-canvas-part3/details-12.png)

1. 减少的库的模板，因此该超过一个高度**Order Detail**记录出现一次：

    > [!div class="mx-imgBorder"]
    > ![缩短库的模板](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>显示产品数量和成本

1. 上**插入**选项卡上，插入另一个标签到详细信息库，然后重设大小并移动新标签，右侧的产品信息。

1. 设置新标签**文本**属性设置为此表达式：

    ```powerapps-dot
    ThisItem.Quantity
    ```

    此公式中提取信息直接从**订单详细信息**实体 （所需的任何关系）。

    > [!div class="mx-imgBorder"]
    > ![显示产品数量](media/northwind-orders-canvas-part3/details-13b.png) 

1. 上**主页**选项卡上，更改到此控件的对齐方式**右**:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/details-14.png)

1. 上**插入**选项卡上，插入另一个标签到详细信息库，然后重设大小并将标签移动到数量标签的右侧。

1. 设置新标签**文本**属性设为此公式：

    ```powerapps-dot
    Text( ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    如果不包含语言标记 ( **[$-EN-US]** )，它将根据你的语言和区域添加。 如果使用不同的语言标记，你需要删除 **$** 紧靠右方括号 ( **]** )，然后在该位置添加货币符号。

    > [!div class="mx-imgBorder"]
    > ![显示单位价格](media/northwind-orders-canvas-part3/details-15.png)

1. 上**主页**选项卡上，更改到此控件的对齐方式**右**:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/details-16.png)

1. 上**插入**选项卡上，将另一个标签控件插入到详细信息库，然后重设大小并移动的单位价格右侧新标签。

1. 设置新标签**文本**属性设为此公式：

    ```powerapps-dot
    Text( ThisItem.Quantity * ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    同样，如果不包含语言标记 ( **[$-EN-US]** )，它将根据你的语言和区域添加。 如果标记不同，您将想要使用你自己的货币符号而不是 **$** 紧靠右方括号 ( **]** )。

    > [!div class="mx-imgBorder"]
    > ![显示扩展的价格](media/northwind-orders-canvas-part3/details-17.png)

1. 上**主页**选项卡上，更改到此控件的对齐方式**右**:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/details-18.png)

    现在，已完成将控件添加到库详细信息。

1. 在中**树视图**窗格中，选择**Screen1**以确保详细信息库不再处于选中状态。

## <a name="add-text-to-the-new-title-bar"></a>将文本添加到新的标题栏

1. 上**插入**选项卡上，插入到屏幕的另一个标签：

    > [!div class="mx-imgBorder"]
    > ![插入标签](media/northwind-orders-canvas-part3/details-19.png)

1. 重设大小和中的第二个的标题栏，移动上面的产品照片的新标签，然后在将文本的颜色更改为白色**主页**选项卡。

1. 双击该标签的文本，然后键入**产品**:

    > [!div class="mx-imgBorder"]
    > ![将标签文本更改为产品](media/northwind-orders-canvas-part3/details-20.png)

1. 复制和粘贴产品标签，然后重设大小和移动 quantity 列的上方的副本。

1. 双击新标签的文本，然后键入**数量**:

    > [!div class="mx-imgBorder"]
    > ![更改为 Quantity 的标签文本](media/northwind-orders-canvas-part3/details-21.png)

1. 复制和粘贴 quantity 标签，然后重设大小和移动复制单元价格列的上方。

1. 双击新标签的文本，然后键入**单价**:

    > [!div class="mx-imgBorder"]
    > ![将标签文本更改为单位价格](media/northwind-orders-canvas-part3/details-22.png)

1. 复制和粘贴的单位价格标签，然后重设大小和移动扩展价格列的上方的副本。

1. 双击新标签的文本，然后键入**扩展**:

    > [!div class="mx-imgBorder"]
    > ![将标签文本更改为扩展](media/northwind-orders-canvas-part3/details-23.png)

## <a name="display-order-totals"></a>显示订单总计

1. 减少详细信息库以便为在屏幕底部的订单总额腾出的高度：

    > [!div class="mx-imgBorder"]
    > ![缩短订单详细信息库](media/northwind-orders-canvas-part3/sum-01.png)

1. 复制并粘贴屏幕中间，标题栏，然后将副本移动到屏幕的底部：

    > [!div class="mx-imgBorder"]
    > ![复制标题栏中，并将副本移到下边缘](media/northwind-orders-canvas-part3/sum-02.png)

1. 复制并粘贴从中间的标题栏中，产品标签，然后将副本移动到底部的标题栏的左侧**数量**列。

1. 双击新标签的文本，然后键入以下文本：<br>**订单总计：**

    > [!div class="mx-imgBorder"]
    > ![添加订单合计的标签](media/northwind-orders-canvas-part3/sum-03.png)

1. 复制并粘贴订单合计标签，然后重设大小然后将副本移到订单合计标签的右侧。

1. 设置新标签**文本**属性设为此公式：

    ```powerapps-dot
    Sum( Gallery1.Selected.'Order Details', Quantity )
    ```

    此公式显示委派警告，但您可以忽略它，因为没有单个订单将包含超过 500 个产品。

1. 上**主页**选项卡上，将新标签的文本对齐方式设置为**右**:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/sum-04.png)

1. 复制和粘贴此标签控件，然后重设大小和移动下的副本**扩展**列。

1. 设置的副本**文本**属性设为此公式：

    ```powerapps-dot
    Text( Sum( Gallery1.Selected.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    此公式显示委派警告，但您可以忽略它，因为没有单个订单将包含超过 500 个产品。

    > [!div class="mx-imgBorder"]
    > ![显示订单的总成本](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>添加新的详细信息的空间

在任何库中，您可以显示的数据但不能更新或添加记录。 在详细信息库下，你将添加用户可在其中配置中的记录的区域**订单详细信息**实体和插入到订单记录。

1. 减少详细信息库足够，以便为在库下的单个项编辑空间腾出的高度。

    在此空间，你将添加控件，以便用户可以添加订单详细信息：

    > [!div class="mx-imgBorder"]
    > ![缩短详细库](media/northwind-orders-canvas-part3/add-details-01.png)

1. 上**插入**选项卡上，插入一个标签，然后重设大小并将其移到详细信息库下。

    > [!div class="mx-imgBorder"]
    > ![插入一个标签](media/northwind-orders-canvas-part3/add-details-02.png)

1. 双击新标签的文本，然后按 Delete。

1. 上**主页**选项卡上，设置新标签**填充**颜色**LightBlue**:

    > [!div class="mx-imgBorder"]
    > ![将标签的填充更改为浅蓝色](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="add-the-order-details-data-source"></a>添加订单详细信息数据源

1. 上**视图**选项卡上，选择**数据源**，然后选择**添加数据源**中**数据**窗格：

    > [!div class="mx-imgBorder"]
    > ![添加数据源](media/northwind-orders-canvas-part3/add-details-04.png)

1. 选择**Common Data Service**:

    > [!div class="mx-imgBorder"]
    > ![选择 Common Data Service](media/northwind-orders-canvas-part3/add-details-05.png)

1. 在顶部**数据**窗格中，键入**顺序**在搜索框中，选择**订单详细信息**复选框，然后再选择**Connect**在窗格的底部：

    > [!div class="mx-imgBorder"]
    > ![指定顺序的详细信息实体](media/northwind-orders-canvas-part3/add-details-06.png)

    您刚才已添加到应用的另一个数据源：

    > [!div class="mx-imgBorder"]
    > ![数据源的列表](media/northwind-orders-canvas-part3/add-details-07.png)

    您必须添加此数据源，因为尽管应用程序可以读取通过一个对多关系，但应用无法尚未写回更改。 应用程序必须进行直接与相关实体的更改。

1. 关闭**数据**窗格。

## <a name="select-a-product"></a>选择产品

1. 上**插入**选项卡上，选择**控件** > **组合框**:

    > [!div class="mx-imgBorder"]
    > ![插入组合框](media/northwind-orders-canvas-part3/add-details-08.png)

    [**组合框**](controls/control-combo-box.md)控件显示在左上角。

1. 设置组合框**项**属性设为此公式：

    ```powerapps-dot
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置组合框的项属性](media/northwind-orders-canvas-part3/add-details-09.png)

    [**选择**](functions/function-choices.md)函数返回的所有可能值的表**产品**字段中**订单详细信息**实体。 因此，此字段才在多对一关系中，查找**选项**返回中的所有记录**订购产品**实体。

    > [!NOTE]
    > 此外可以使用**选择**选项集以返回所有选项的表。 步骤没有提过这种方法，但已添加显示组合框时，会使用它**订单状态**在汇总窗体中。

1. 在中**数据**窗格中，打开**主要文本**列表，并选择**nwind_productname**。 

1. 打开**SearchField**列表，并选择**nwind_productname**。

    您指定的逻辑名称，因为**数据**窗格尚不支持显示名称在此情况下：

    > [!div class="mx-imgBorder"]
    > ![设置组合框的主要文本](media/northwind-orders-canvas-part3/add-details-10.png)

1. 关闭**数据**窗格。

1. 在中**属性**右边缘附近选项卡，向下滚动，将关闭**允许多个所选内容**，并确保**允许搜索**处于开启状态：

    > [!div class="mx-imgBorder"]
    > ![禁用多个所选内容并启用搜索](media/northwind-orders-canvas-part3/add-details-12.png)

1. 调整大小并将组合框移到浅蓝色区域，在详细信息库中的产品名称列下，只需：

    > [!div class="mx-imgBorder"]
    > ![将组合框](media/northwind-orders-canvas-part3/add-details-13.png)

    在此组合框中，用户将指定的记录中**产品**实体**订单详细信息**该应用会创建的记录。

1. 在按住 Alt 键，选择组合框的向下箭头。

    > [!TIP]
    > 通过按住 Alt 键，您可以与控件进行交互在 PowerApps Studio 中而无需打开预览模式。

1. 在显示的产品列表中，选择一个产品：

    > [!div class="mx-imgBorder"]
    > ![在组合框中选择一个产品](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>添加产品图像

1. 上**插入**选项卡上，选择**媒体** > **映像**:

    > [!div class="mx-imgBorder"]
    > ![插入图像控件](media/northwind-orders-canvas-part3/add-details-15.png)

    [**映像**](controls/control-image.md)控件将显示在左上角中：

    > [!div class="mx-imgBorder"]
    > ![图像控件的默认位置](media/northwind-orders-canvas-part3/add-details-16.png)

1. 调整大小并将映像移动到其他产品的图像下和组合框旁的浅蓝色区域。

1. 设置**图像**的映像的属性：

    ```powerapps-dot
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图像的 Image 属性](media/northwind-orders-canvas-part3/add-details-17.png)

    使用相同的方法作为您用来在汇总窗体中显示雇员照片。 **Selected**组合框的属性将返回用户选择，包括任何产品的整个记录**图片**字段。

## <a name="add-a-quantity-box"></a>添加一个数量框

1. 上**插入**选项卡上，选择**文本** > **文本输入**:

    > [!div class="mx-imgBorder"]
    > ![添加文本输入框](media/northwind-orders-canvas-part3/add-details-18.png)

    [**文本输入**](controls/control-text-input.md)控件将显示在左上角中：

    > [!div class="mx-imgBorder"]
    > ![文本输入框的默认位置](media/northwind-orders-canvas-part3/add-details-19.png)

1. 调整大小并将文本输入框移到下详细信息库中的 quantity 列的组合框的右侧：

    > [!div class="mx-imgBorder"]
    > ![调整大小和移动文本输入框](media/northwind-orders-canvas-part3/add-details-20.png)

    通过使用此文本输入框，用户将指定**Quantity**字段**订单详细信息**记录。

1. 设置**默认**到此控件的属性 **""** :

    > [!div class="mx-imgBorder"]
    > ![设置 * * 默认 * * 属性的文本输入框](media/northwind-orders-canvas-part3/add-details-21.png)

1. 上**主页**选项卡上，设置到此控件的文本对齐方式**右**:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>显示的单元和扩展的价格

1. 上**插入**选项卡上，插入**标签**控件。

    标签出现在屏幕的左上角中：

    > [!div class="mx-imgBorder"]
    > ![插入一个标签](media/northwind-orders-canvas-part3/add-details-23.png)

1. 重设大小和移动该标签，右侧的文本输入控件，以及设置的标签**文本**属性设为此公式：

    ```powerapps-dot
    Text( ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置标签的 Text 属性](media/northwind-orders-canvas-part3/add-details-24.png)

    此控件显示**标价**从**订购产品**实体。 此值将确定**单价**字段中**订单详细信息**记录。

    > [!NOTE]
    > 对于此方案，此值为只读的但其他情况下可能要求应用用户对其进行修改。 在这种情况下，使用**文本输入**控件，并设置其**默认**属性设置为**标价**。

1. 上**主页**选项卡上，设置为列表价格标签的文本对齐方式**右**:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/add-details-25.png)

1. 复制并粘贴列表价格标签，然后重设大小然后将副本移到列表价格标签的右侧。

1. 设置新标签**文本**属性设为此公式：

    ```powerapps-dot
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置新标签的 Text 属性](media/northwind-orders-canvas-part3/add-details-27.png)

    此控件显示的扩展的价格基于指定的应用程序用户的数量和应用程序用户所选的产品标价。 它是应用用户仅用于提供信息。

1. 双击数量，该文本输入控件，然后键入一个数字。

    **扩展**价格标签重新计算，以显示新值：

    > [!div class="mx-imgBorder"]
    > ![指定数量，并显示扩展的价格](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>添加一个添加图标

1. 上**插入**选项卡上，选择**图标** > **添加**:

    > [!div class="mx-imgBorder"]
    > ![插入添加图标](media/northwind-orders-canvas-part3/add-details-29.png)

    图标将显示在屏幕的左上角。

    > [!div class="mx-imgBorder"]
    > ![添加图标的默认位置](media/northwind-orders-canvas-part3/add-details-30.png)

1. 重设大小和移动到的右边缘的浅蓝色区域中，此图标，然后设置图标**OnSelect**属性设为此公式：

    ```powerapps-dot
    Patch( 'Order Details',
        Defaults('Order Details'),
        {
            Order: Gallery1.Selected,
            Product: ComboBox1.Selected,
            Quantity: Value(TextInput1.Text),
            'Unit Price': ComboBox1.Selected.'List Price'
        }
    );
    Refresh( Orders );
    Reset( ComboBox1 );
    Reset( TextInput1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图标的 OnSelect 属性](media/northwind-orders-canvas-part3/add-details-31.png)

    一般情况下， [**修补**](functions/function-patch.md)函数更新，并创建记录，并在此公式中的特定参数确定将使该函数的具体更改。

    - 第一个参数指定的数据源 (在这种情况下，**订单详细信息**实体) 中或创建记录的更新函数将。
    - 第二个参数指定该函数将创建具有默认值的记录**订单详细信息**实体除非第三个参数中指定。
    - 第三个参数指定新的记录中的四个列将包含来自用户的值。

      - **顺序**列将包含用户所选订单库中的订单数。
      - **产品**列将包含产品中的显示产品组合框中选定的用户的名称。
      - **数量**列将包含用户指定的文本输入框中的值。
      - **单价**列将包含在用户选择了为此订单详细信息的产品标价。

    > [!NOTE]
    > 你可以构建使用任何列中的数据的公式 (在**订购产品**实体) 的任何产品应用用户显示产品的组合框中选择。 当用户选择中的记录**订购产品**实体，不仅产品的名称在该组合框中会显示，但该产品的单价中还将显示一个标签。 画布应用中的每个查找值引用整条记录，而不仅仅是主键。

    **刷新**函数确保**订单**实体反映您刚才已添加到的记录**Order Details**实体。 **重置**函数清除产品、 数量和单价的数据，以便用户可以更轻松地创建的相同顺序的另一个订单详细信息。

1. 按 F5，然后依次**添加**图标。

    顺序反映了你指定的信息：

    > [!div class="mx-imgBorder"]
    > ![动画的添加订单详细信息](media/northwind-orders-canvas-part3/add-details.gif)

1. （可选）将另一个项添加到订单。

1. 按 Esc 关闭预览模式。

## <a name="remove-an-order-detail"></a>删除订单详细信息

1. 在屏幕的中心，选择详细信息库的模板：

    > [!div class="mx-imgBorder"]
    > ![选择库模板](media/northwind-orders-canvas-part3/remove-details-01.png)

1. 上**插入**选项卡上，选择**图标** > **回收站**:

    > [!div class="mx-imgBorder"]
    > ![插入垃圾桶图标](media/northwind-orders-canvas-part3/remove-details-02.png)

    垃圾桶图标显示在左上角的库模板的。

    > [!div class="mx-imgBorder"]
    > ![图标的默认位置](media/northwind-orders-canvas-part3/remove-details-03.png)

1. 重设大小和移动详细库模板后，右侧的垃圾桶图标，以及设置的图标**OnSelect**属性设为此公式：

    ```powerapps-dot
    Remove( 'Order Details', ThisItem ); Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图标的 OnSelect 属性](media/northwind-orders-canvas-part3/remove-details-04.png)

    在撰写本文时，不能删除一条记录直接从一种关系，因此[**删除**](functions/function-remove-removeif.md)函数直接从相关实体中删除一条记录。 **ThisItem**指定要删除的记录从垃圾桶图标的显示位置的详细信息库中的同一记录。

    同样，该操作使用缓存的数据，因此**刷新**函数将通知**订单**该应用具有更改其相关实体之一中的实体。

1. 按 F5 打开预览模式，然后选择每个旁边的垃圾桶图标**订单详细信息**记录你想要删除的顺序。

1. 尝试添加和删除各种订单从您的订单的详细信息：

    > [!div class="mx-imgBorder"]
    > ![添加和删除订单详细信息的动画](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>总结

概括来说，您添加了另一个库，以显示订单详细信息和控件添加和删除应用程序中的订单详细信息。 使用这些元素：

- 第二个库控件中，链接到订单库通过对多关系：**Gallery2.Items** = `Gallery1.Selected.'Order Details'`
- 从多对一的关系**订单详细信息**实体与**订购产品**实体：`ThisItem.Product.'Product Name'`和 `ThisItem.Product.Picture`
- **选择**函数以获取产品列表： `Choices( 'Order Details'.Product' )`
- **Selected**组合框以完成对一多属性相关的记录：`ComboBox1.Selected.Picture`和 `ComboBox1.Selected.'List Price'`
- **修补程序**函数来创建**订单详细信息**记录： `Patch( 'Order Details', Defaults( 'Order Details' ), ... )`
- **删除**函数来删除**订单详细信息**记录： `Remove( 'Order Details', ThisItem )`

这一系列的主题已被使用 Common Data Service 关系的快速演练和选项设置中的画布应用出于教育目的。 在发布任何应用到生产环境之前，应考虑字段验证、 错误处理和许多其他因素。
