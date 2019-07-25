---
title: 在画布应用中创建详细信息库 |Microsoft Docs
description: 在画布应用中创建详细信息库以管理 Northwind 商贸的数据
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
ms.openlocfilehash: 36fc8c552dea9331ff5ffbaa2dca3bdac5508306
ms.sourcegitcommit: 39b32abb19ad9fae98ca986ded6974bcbbb3cea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68474632"
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>在画布应用中创建详细信息库

按照分步说明在画布应用中创建详细信息库, 以便在 Northwind 商贸数据库中管理虚拟数据。 本主题是一系列文章的一部分, 说明如何在 Common Data Service 中构建业务应用程序的关系数据。 为了获得最佳结果, 请在此序列中浏览这些主题:

1. [创建订单库](northwind-orders-canvas-part1.md)。
1. [创建摘要窗体](northwind-orders-canvas-part2.md)。
1. 创建详细信息库 (**本主题**)。

> [!div class="mx-imgBorder"]
> ![屏幕区域的定义](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>先决条件

在开始本主题之前, 必须按照本主题前面所述安装数据库。 然后, 您必须创建订单库和摘要窗体, 或者打开**Northwind Orders (Canvas)-Begin 第3部分**, 该应用程序已经包含该库和该窗体。

## <a name="create-another-title-bar"></a>创建另一个标题栏

1. 在屏幕顶部, 选择充当标题栏的 "[**标签**](controls/control-text-box.md)" 控件, 按 Ctrl + C 进行复制, 然后按 Ctrl + V 粘贴:

    > [!div class="mx-imgBorder"]
    > ![复制和粘贴标题栏](media/northwind-orders-canvas-part3/details-01.png)

1. 调整大小并移动复制, 使其显示在摘要窗体下。

1. 采用以下任一方式从副本中删除文本:

    - 双击文本将其选中, 然后按 Delete。
    - 将标签的 " **Text** " 属性设置为空字符串 ( **""** )。

    > [!div class="mx-imgBorder"]
    > ![从标题栏副本中删除文本](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>添加库

1. 插入具有**空白垂直**布局的[**库**](controls/control-gallery.md)控件:

    > [!div class="mx-imgBorder"]
    > ![添加空白垂直库](media/northwind-orders-canvas-part3/details-03.png)

    将显示订单详细信息的新库显示在左上角:

    > [!div class="mx-imgBorder"]
    > ![订单详细信息库的默认位置](media/northwind-orders-canvas-part3/details-04.png)

1. 关闭 "**数据**" 窗格, 然后将详细信息库调整到新标题栏下面的右下角:

    > [!div class="mx-imgBorder"]
    > ![订单详细信息库的最终位置](media/northwind-orders-canvas-part3/details-05.png)

1. 将详细信息库的**Items**属性设置为以下公式:

    ```powerapps-dot
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![设置详细信息库的 Items 属性](media/northwind-orders-canvas-part3/details-06.png)

    如果出现错误, 请确认订单库的名称为 " **gallery1.selected** " (位于左边缘附近的 "**树视图**" 窗格中)。 如果该库具有不同的名称, 请将其重命名为**gallery1.selected**。

    你刚刚链接了两个库。 当用户在订单库中选择一个订单时, 该选择标识 "**订单**" 实体中的一条记录。 如果该订单包含一个或多个行项, 则 "**订单**" 实体中的记录会链接到 "**订单详细信息**" 实体中的一个或多个记录, 详细信息库中将显示这些记录的数据。 此行为反映了在 "**订单**" 和 "**订单详细信息**" 实体之间为您创建的一对多关系。 您通过使用点表示法指定了关系的公式:

    > [!div class="mx-imgBorder"]
    > !["订单" 实体与 "订单详细信息" 实体之间的一对多关系](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>显示产品名称

1. 在详细信息库中,**从 "插入" 选项卡**中选择 "添加项" 以选择库模板:

    > [!div class="mx-imgBorder"]
    > ![选择详细信息库的模板](media/northwind-orders-canvas-part3/details-07.png)

    请确保已选择库模板而不是库本身。 边界框应略微位于库的边界内, 可能会短于库的高度。 将控件插入到此模板中时, 将对库中的每个项重复这些控件。

1. 在 "**插入**" 选项卡上的 "详细信息库" 中插入一个标签。

    此标签应显示在库中;如果不是, 请重试, 但请确保在插入标签之前选择库的模板。

    > [!div class="mx-imgBorder"]
    > ![向详细信息库添加标签](media/northwind-orders-canvas-part3/details-08.png)

1. 将新标签的 " **Text** " 属性设置为以下公式:

    ```powerapps-dot
    ThisItem.Product.'Product Name'
    ```

    如果未显示任何文本, 请选择订单库底部附近**订单 0901**的箭头。

1. 调整标签的大小, 以显示完整的文本:

    > [!div class="mx-imgBorder"]
    > ![按订单详细信息显示产品名称](media/northwind-orders-canvas-part3/details-09.png)

    此表达式将从 "**订单详细信息**" 实体中的记录进行审核。 记录通过多对一关系保存到**订单产品**实体的**ThisItem**中:

    > [!div class="mx-imgBorder"]
    > ![订单详细信息实体与订单产品实体之间的多对一关系](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    提取 "**产品名称**" 字段 (以及要使用的其他字段):

    > [!div class="mx-imgBorder"]
    > ![订单产品实体中的字段](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>显示产品映像

1. 在 "**插入**" 选项卡上的 "详细信息库" 中插入[**图像**](controls/control-image.md)控件:

    > [!div class="mx-imgBorder"]
    > ![插入图像控件](media/northwind-orders-canvas-part3/details-10.png)

1. 调整图像和标签的大小并将其并排移动。

    > [!TIP]
    > 若要对控件的大小和位置进行精细的控制, 请在按住 Alt 键的同时, 开始调整大小或移动控件, 然后在按住 Alt 键的同时继续调整控件大小或移动控件:

    > [!div class="mx-imgBorder"]
    > ![移动图像控件](media/northwind-orders-canvas-part3/details-11.png)

1. 将图像的**image**属性设置为以下公式:

    ```powerapps-dot
    ThisItem.Product.Picture
    ```

    同样, 该表达式引用与此订单详细信息关联的产品并提取要显示的**图片**字段。

    > [!div class="mx-imgBorder"]
    > ![显示产品映像](media/northwind-orders-canvas-part3/details-12.png)

1. 减小库模板的高度, 以便一次显示多个**订单详细信息**记录:

    > [!div class="mx-imgBorder"]
    > ![缩短库的模板](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>显示产品数量和成本

1. 在 "**插入**" 选项卡上, 将另一个标签插入到详细信息库中, 然后重设大小并将新标签移动到产品信息的右侧。

1. 将新标签的 " **Text** " 属性设置为以下表达式:

    ```powerapps-dot
    ThisItem.Quantity
    ```

    此公式直接从 "**订单详细信息**" 实体拉取信息 (无需任何关系)。

    > [!div class="mx-imgBorder"]
    > ![显示产品数量](media/northwind-orders-canvas-part3/details-13b.png) 

1. 在 "**主页**" 选项卡上, 将此控件的对齐方式更改为**右**对齐:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/details-14.png)

1. 在 "**插入**" 选项卡上的 "详细信息库" 中插入另一个标签, 然后调整大小并将标签移动到 "数量" 标签的右侧。

1. 将新标签的 " **Text** " 属性设置为以下公式:

    ```powerapps-dot
    Text( ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    如果不包含语言标记 ( **[$-en-us]** ), 则将根据语言和区域为你添加。 如果使用其他语言标记, 则需要删除右方括号 ( **]** ) **$** 后面的, 然后在该位置添加您自己的货币符号。

    > [!div class="mx-imgBorder"]
    > ![显示单价](media/northwind-orders-canvas-part3/details-15.png)

1. 在 "**主页**" 选项卡上, 将此控件的对齐方式更改为**右**对齐:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/details-16.png)

1. 在 "**插入**" 选项卡上, 将另一个 "标签" 控件插入到详细信息库中, 然后重设大小并将新标签移动到单位价格的右侧。

1. 将新标签的 " **Text** " 属性设置为以下公式:

    ```powerapps-dot
    Text( ThisItem.Quantity * ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    同样, 如果不包含语言标记 ( **[$-en-us]** ), 则将根据语言和区域为你添加。 如果标记不同, 则需要使用自己的货币符号, 而不 **$** 是右方括号 ( **]** ) 之后的。

    > [!div class="mx-imgBorder"]
    > ![显示扩展价格](media/northwind-orders-canvas-part3/details-17.png)

1. 在 "**主页**" 选项卡上, 将此控件的对齐方式更改为**右**对齐:

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/details-18.png)

    现在, 已完成将控件添加到详细信息库。

1. 在 "**树视图**" 窗格中, 选择 " **Screen1** " 以确保不再选中 "详细信息库"。

## <a name="add-text-to-the-new-title-bar"></a>向新标题栏添加文本

1. 在 "**插入**" 选项卡上, 在屏幕上插入另一个标签:

    > [!div class="mx-imgBorder"]
    > ![插入标签](media/northwind-orders-canvas-part3/details-19.png)

1. 调整新标签的大小并将其移到第二个标题栏中的产品图片上方, 然后在 "**主页**" 选项卡上将文本颜色更改为白色。

1. 双击标签的文本, 然后键入**Product**:

    > [!div class="mx-imgBorder"]
    > ![将标签文本更改为产品](media/northwind-orders-canvas-part3/details-20.png)

1. 复制并粘贴产品标签, 然后在 "数量" 列的上方调整大小并移动副本。

1. 双击新标签的文本, 然后键入 "**数量**":

    > [!div class="mx-imgBorder"]
    > ![将标签文本更改为数量](media/northwind-orders-canvas-part3/details-21.png)

1. 复制并粘贴 "数量" 标签, 然后调整其大小, 并将该副本移到 "单价" 列之上。

1. 双击新标签的文本, 然后键入**Unit Price**:

    > [!div class="mx-imgBorder"]
    > ![将标签文本更改为单价](media/northwind-orders-canvas-part3/details-22.png)

1. 复制并粘贴单位价格标签, 然后调整其大小, 并将其移动到扩展价格列以上。

1. 双击新标签的文本, 然后键入 "**扩展**":

    > [!div class="mx-imgBorder"]
    > ![将标签文本更改为扩展](media/northwind-orders-canvas-part3/details-23.png)

## <a name="display-order-totals"></a>显示订单总计

1. 减小详细信息库的高度, 以便为屏幕底部的订单总数腾出空间:

    > [!div class="mx-imgBorder"]
    > ![缩短订单-详细信息库](media/northwind-orders-canvas-part3/sum-01.png)

1. 将标题栏复制并粘贴到屏幕中间, 然后将其复制到屏幕底部:

    > [!div class="mx-imgBorder"]
    > ![复制标题栏, 并将复制到下边缘](media/northwind-orders-canvas-part3/sum-02.png)

1. 复制并粘贴中间标题栏中的 "产品" 标签, 然后将该副本移到 "**数量**" 列左侧的底部标题栏中。

1. 双击新标签的文本, 然后键入以下文本:<br>**订单总计:**

    > [!div class="mx-imgBorder"]
    > ![为订单总计添加标签](media/northwind-orders-canvas-part3/sum-03.png)

1. 复制并粘贴 "订单总计" 标签, 然后重设大小, 并将副本移动到 "订单总计" 标签的右边。

1. 将新标签的 " **Text** " 属性设置为以下公式:

    ```powerapps-dot
    Sum( Gallery1.Selected.'Order Details', Quantity )
    ```

    此公式显示委托警告, 但您可以忽略该警告, 因为没有单个订单包含的产品超过500。

1. 在 "**主页**" 选项卡上, 将新标签的文本对齐方式设置为 "**右**":

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/sum-04.png)

1. 复制并粘贴此 "标签" 控件, 然后在 "**扩展**" 列下调整或移动该副本。

1. 将复制的 " **Text** " 属性设置为以下公式:

    ```powerapps-dot
    Text( Sum( Gallery1.Selected.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    此公式显示委托警告, 但您可以忽略该警告, 因为没有单个订单包含的产品超过500。

    > [!div class="mx-imgBorder"]
    > ![显示订单总成本](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>为新详细信息添加空间

在任何库中, 你都可以显示数据, 但无法对其进行更新或添加记录。 在详细信息库下, 您将添加一个区域, 用户可在其中配置 "**订单详细信息**" 实体中的记录, 并将该记录插入到订单中。

1. 减小详细信息库的高度, 以便为该库下的单项编辑空间腾出空间。

    在此空间中, 你将添加控件, 以便用户可以添加订单详细信息:

    > [!div class="mx-imgBorder"]
    > ![缩短详细信息库](media/northwind-orders-canvas-part3/add-details-01.png)

1. 在 "**插入**" 选项卡上, 插入一个标签, 然后调整其大小, 然后将其移到详细信息库下。

    > [!div class="mx-imgBorder"]
    > ![插入标签](media/northwind-orders-canvas-part3/add-details-02.png)

1. 双击新标签的文本, 然后按 "删除"。

1. 在 "**主页**" 选项卡上, 将新标签的**填充**颜色设置为**LightBlue**:

    > [!div class="mx-imgBorder"]
    > ![将标签的填充更改为浅蓝色](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="add-the-order-details-data-source"></a>添加订单详细信息数据源

1. 在 "**视图**" 选项卡上, 选择 "**数据源**", 然后在 "**数据**" 窗格中选择 "**添加数据源**":

    > [!div class="mx-imgBorder"]
    > ![添加数据源](media/northwind-orders-canvas-part3/add-details-04.png)

1. 选择**Common Data Service**:

    > [!div class="mx-imgBorder"]
    > ![选择 Common Data Service](media/northwind-orders-canvas-part3/add-details-05.png)

1. 在 "**数据**" 窗格顶部的 "搜索" 框中键入 "**顺序**", 选中 "**订单详细信息**" 复选框, 然后在窗格底部选择 "**连接**":

    > [!div class="mx-imgBorder"]
    > ![指定订单详细信息实体](media/northwind-orders-canvas-part3/add-details-06.png)

    你刚向应用添加了另一个数据源:

    > [!div class="mx-imgBorder"]
    > ![数据源列表](media/northwind-orders-canvas-part3/add-details-07.png)

    您必须添加此数据源, 因为虽然应用程序可以通过一对多关系读取, 但是应用程序无法写回更改。 应用必须直接与相关实体进行更改。

1. 关闭 "**数据**" 窗格。

## <a name="select-a-product"></a>选择产品

1. 在 "**插入**" 选项卡上, 选择 "**控件** > "**组合框**:

    > [!div class="mx-imgBorder"]
    > ![插入组合框](media/northwind-orders-canvas-part3/add-details-08.png)

    [**组合框**](controls/control-combo-box.md)控件将显示在左上角。

1. 将组合框的**Items**属性设置为以下公式:

    ```powerapps-dot
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置组合框的 Items 属性](media/northwind-orders-canvas-part3/add-details-09.png)

    [**选项**](functions/function-choices.md)函数将为 "**订单详细信息**" 实体中的 "**产品**" 字段返回一个表。 此字段是多对一关系中的一个查找, 因此可**选择**返回**Order Products**实体中的所有记录。

    > [!NOTE]
    > 您还可以将**选项与选项**集结合使用, 以返回所有选项的表。 这些步骤未提到此方法, 但您在将显示**订单状态**的组合框添加到摘要窗体中时已使用了该方法。

1. 在 "**数据**" 窗格中, 打开 "**主文本**" 列表, 然后选择 " **nwind_productname**"。 

1. 打开 " **SearchField** " 列表, 然后选择 " **nwind_productname**"。

    指定逻辑名称, 因为在此示例中,**数据**窗格不支持显示名称:

    > [!div class="mx-imgBorder"]
    > ![设置组合框的主文本](media/northwind-orders-canvas-part3/add-details-10.png)

1. 关闭 "**数据**" 窗格。

1. 在右侧边缘附近的 "**属性**" 选项卡中, 向下滚动并关闭 "**允许多项选择**", 并确保已启用 "**允许搜索**":

    > [!div class="mx-imgBorder"]
    > ![禁用多重选择并启用搜索](media/northwind-orders-canvas-part3/add-details-12.png)

1. 调整组合框的大小并将其移动到浅蓝色区域, 只需在详细信息库中的产品名称列下面:

    > [!div class="mx-imgBorder"]
    > ![移动组合框](media/northwind-orders-canvas-part3/add-details-13.png)

    在此组合框中, 用户将为应用将创建的**订单详细信息**记录指定**Product**实体中的记录。

1. 按住 Alt 键的同时, 选择组合框的向下箭头。

    > [!TIP]
    > 按下 Alt 键, 无需打开预览模式, 即可与 PowerApps Studio 中的控件交互。

1. 在显示的产品列表中, 选择一个产品:

    > [!div class="mx-imgBorder"]
    > ![在组合框中选择一个产品](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>添加产品映像

1. 在 "**插入**" 选项卡上, 选择 "**媒体** > **图像**":

    > [!div class="mx-imgBorder"]
    > ![插入图像控件](media/northwind-orders-canvas-part3/add-details-15.png)

    [**图像**](controls/control-image.md)控件将出现在左上角:

    > [!div class="mx-imgBorder"]
    > ![图像控件的默认位置](media/northwind-orders-canvas-part3/add-details-16.png)

1. 调整图像的大小并将其移到 "其他产品" 图像下和组合框旁边的浅蓝色区域。

1. 将图像的**image**属性设置为:

    ```powerapps-dot
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图像的 Image 属性](media/northwind-orders-canvas-part3/add-details-17.png)

    你使用的是在摘要窗体中用来显示雇员照片的相同技巧。 组合框的**Selected**属性返回用户选择的任何产品的整个记录, 包括**图片**字段。

## <a name="add-a-quantity-box"></a>添加数量框

1. 在 "**插入**" 选项卡上, 选择 "**文本** > "**输入**:

    > [!div class="mx-imgBorder"]
    > ![添加文本输入框](media/northwind-orders-canvas-part3/add-details-18.png)

    [**文本输入**](controls/control-text-input.md)控件显示在左上角:

    > [!div class="mx-imgBorder"]
    > ![文本输入框的默认位置](media/northwind-orders-canvas-part3/add-details-19.png)

1. 在 "详细信息库" 中的 "数量" 列下调整组合框右侧的文本输入框并将其移动:

    > [!div class="mx-imgBorder"]
    > ![调整文本大小并移动文本输入框](media/northwind-orders-canvas-part3/add-details-20.png)

    使用此文本输入框, 用户将指定**订单详细信息**记录的**数量**字段。

1. 将此控件的**默认**属性设置为 **""** :

    > [!div class="mx-imgBorder"]
    > ![设置文本输入框的 * * 默认值 * * 属性](media/northwind-orders-canvas-part3/add-details-21.png)

1. 在 "**主页**" 选项卡上, 将此控件的文本对齐方式设置为 "**右**":

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>显示单位和扩展价格

1. 在 "**插入**" 选项卡上, 插入 "**标签**" 控件。

    标签显示在屏幕的左上角:

    > [!div class="mx-imgBorder"]
    > ![插入标签](media/northwind-orders-canvas-part3/add-details-23.png)

1. 调整大小并将标签移动到文本输入控件的右侧, 然后将标签的 " **text** " 属性设置为以下公式:

    ```powerapps-dot
    Text( ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置标签的 Text 属性](media/northwind-orders-canvas-part3/add-details-24.png)

    此控件显示 "**订单产品**" 实体的**定价**。 此值将确定**订单详细信息**记录中的 "**单价**" 字段。

    > [!NOTE]
    > 对于此方案, 此值是只读的, 但其他方案可能会调用应用程序用户来修改它。 在这种情况下, 请使用**文本输入**控件, 并将其**默认**属性设置为**标价。**

1. 在 "**主页**" 选项卡上, 将列表价格标签的文本对齐方式设置为 "**右**":

    > [!div class="mx-imgBorder"]
    > ![更改对齐方式](media/northwind-orders-canvas-part3/add-details-25.png)

1. 复制并粘贴标价标签, 然后调整其大小, 并将该副本移到标价标签的右边。

1. 将新标签的 " **Text** " 属性设置为以下公式:

    ```powerapps-dot
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置新标签的 Text 属性](media/northwind-orders-canvas-part3/add-details-27.png)

    此控件基于应用用户指定的数量以及应用用户选择的产品的定价显示扩展价格。 它纯粹是应用程序用户的信息。

1. 双击 "数量" 的文本输入控件, 然后键入一个数字。

    **扩展**价格标签将重新计算以显示新值:

    > [!div class="mx-imgBorder"]
    > ![指定数量并显示扩展价格](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>添加添加图标

1. 在 "**插入**" 选项卡上, 选择 "**图标** > " "**添加**":

    > [!div class="mx-imgBorder"]
    > ![插入添加图标](media/northwind-orders-canvas-part3/add-details-29.png)

    该图标将显示在屏幕的左上角。

    > [!div class="mx-imgBorder"]
    > !["添加" 图标的默认位置](media/northwind-orders-canvas-part3/add-details-30.png)

1. 调整此图标的大小并将其移动到浅蓝色区域的右边缘, 然后将图标的**OnSelect**属性设置为以下公式:

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

    通常, [**Patch**](functions/function-patch.md)函数会更新并创建记录, 而此公式中的特定参数会确定函数将进行的确切更改。

    - 第一个参数指定数据源 (在本例中为 "**订单详细信息**" 实体), 函数将在该数据源中更新或创建记录。
    - 第二个参数指定该函数将使用 "**订单详细信息**" 实体的默认值创建一个记录, 除非在第三个参数中另行指定。
    - 第三个参数指定新记录中的四列将包含用户的值。

      - **Order**列将包含用户在顺序库中选择的订单数。
      - **Product**列将包含用户在显示产品的组合框中选择的产品的名称。
      - "**数量**" 列将包含用户在文本输入框中指定的值。
      - "**单价**" 列将包含用户为此订单详细信息选择的产品的定价。

    > [!NOTE]
    > 对于应用用户在显示产品的组合框中选择的任何产品, 你可以使用 "**订单产品**" 实体中的任何列生成使用数据的公式。 当用户在 "**订单**" 实体中选择一条记录时, 不仅会在该组合框中显示产品的名称, 还会在标签中显示产品的单位价格。 画布应用中的每个查找值都引用整条记录, 而不只引用主键。

    **Refresh**函数可确保 "**订单**" 实体反映刚添加到 "**订单详细信息**" 实体中的记录。 **Reset**函数将清除产品、数量和单价数据, 以便用户可以更轻松地为同一订单创建另一个订单详细信息。

1. 按 F5, 然后选择 "**添加**" 图标。

    顺序反映了您指定的信息:

    > [!div class="mx-imgBorder"]
    > ![添加订单详细信息的动画](media/northwind-orders-canvas-part3/add-details.gif)

1. 可有可无将另一项添加到订单中。

1. 按 Esc 关闭预览模式。

## <a name="remove-an-order-detail"></a>删除订单详细信息

1. 在屏幕的中心, 选择详细信息库的模板:

    > [!div class="mx-imgBorder"]
    > ![选择库模板](media/northwind-orders-canvas-part3/remove-details-01.png)

1. 在 "**插入**" 选项卡上, 选择 "**图标** > **垃圾桶**":

    > [!div class="mx-imgBorder"]
    > ![插入垃圾桶图标](media/northwind-orders-canvas-part3/remove-details-02.png)

    "垃圾桶" 图标将显示在库模板的左上角。

    > [!div class="mx-imgBorder"]
    > ![图标的默认位置](media/northwind-orders-canvas-part3/remove-details-03.png)

1. 调整大小并将垃圾桶图标移到详细信息库模板的右侧, 并将图标的**OnSelect**属性设置为以下公式:

    ```powerapps-dot
    Remove( 'Order Details', ThisItem ); Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图标的 OnSelect 属性](media/northwind-orders-canvas-part3/remove-details-04.png)

    在撰写本文时, 您不能直接从关系中删除记录, 因此[**remove**](functions/function-remove-removeif.md)函数会直接从相关实体中删除记录。 **ThisItem**指定要删除的记录, 该记录来自 "详细信息库" 中显示的相同记录。

    该操作再次使用缓存的数据, 因此**Refresh**函数通知**Orders**实体应用已更改其相关实体之一。

1. 按 F5 打开预览模式, 然后选择要从订单中删除的每个 "**订单详细信息**" 记录旁边的 "垃圾桶" 图标。

1. 尝试添加和删除订单的各种订单详细信息:

    > [!div class="mx-imgBorder"]
    > ![添加和删除订单详细信息的动画](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>结束

总之, 你添加了另一个库来显示订单详细信息, 以及在应用程序中添加和删除订单详细信息的控件。 你使用了以下元素:

- 第二个库控件, 通过一对多关系链接到订单库:**Gallery2** = `Gallery1.Selected.'Order Details'`
- 从**订单详细信息**实体到**订单产品**实体的多对一关系: `ThisItem.Product.'Product Name'`和`ThisItem.Product.Picture`
- 用于获取产品列表的**选项**函数:`Choices( 'Order Details'.Product' )`
- 组合框的**所选**属性为完整的多对一相关记录: `ComboBox1.Selected.Picture`和`ComboBox1.Selected.'List Price'`
- 用于创建**订单详细信息**记录的**修补**函数:`Patch( 'Order Details', Defaults( 'Order Details' ), ... )`
- 删除**订单详细信息**记录的**Remove**函数:`Remove( 'Order Details', ThisItem )`

这一系列主题已是在画布应用中使用 Common Data Service 关系和选项集以便于教育目的的快速演练。 在将任何应用程序发布到生产环境之前, 应考虑字段验证、错误处理以及许多其他因素。
