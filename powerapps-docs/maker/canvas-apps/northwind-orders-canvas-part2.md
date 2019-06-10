---
title: 在画布应用中创建摘要表单 |Microsoft Docs
description: 用于管理数据的 Northwind Traders 的画布应用中创建的摘要的窗体
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
ms.openlocfilehash: 5c40cb030241d142a2ee2a68d32f7fb839a350ff
ms.sourcegitcommit: 55bc11ac6a964f22301c9fdadb06ee34e1399f83
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66806732"
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>在画布应用中创建摘要表单

按照分步说明来创建摘要的窗体中用于管理在 Northwind Trader 数据库中的虚拟数据的画布应用。 本主题是介绍如何在 Common Data Service 中的关系数据上构建企业应用程序的一系列的一部分。 为了获得最佳结果，将介绍此序列中的以下主题：

1. [创建顺序库](northwind-orders-canvas-part1.md)。
2. 创建摘要的窗体 (**本主题**)。
3. [创建详细信息库](northwind-orders-canvas-part3.md)。

> [!div class="mx-imgBorder"]
> ![屏幕区域的定义](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>先决条件

1. [安装的 Northwind Trader 数据库和应用](northwind-install.md)。
1. 审阅[概述的画布应用](northwind-orders-canvas-overview.md)为 Northwind Traders。
1. [创建顺序库](northwind-orders-canvas-part1.md)自己或开放**Northwind 订单 （画布）-第 2 部分开始**已包含库的应用程序。

## <a name="add-a-title-bar"></a>添加标题栏

跨应用程序的顶部，创建将由本主题末尾保留操作按钮标题栏。

1. 在中**树视图**窗格中，选择**Screen1**以确保不会意外地添加控件到顺序库：

    > [!div class="mx-imgBorder"]
    > ![在树视图窗格中选择 Screen1](media/northwind-orders-canvas-part2/titlebar-01.png)

1. 上**插入**选项卡上，选择**标签**插入[**标签**](controls/control-text-box.md)控件：

    > [!div class="mx-imgBorder"]
    > ![插入一个标签](media/northwind-orders-canvas-part2/titlebar-02.png)

    新标签应仅出现一次，库上面。 如果它出现在每个库项中，删除标签的第一个实例，确保屏幕已选择 （如在上一步中所述），然后重新插入该标签。

1. 移动和调整大小的新标签跨屏幕的顶部：

    > [!div class="mx-imgBorder"]
    > ![移动和调整大小的标签](media/northwind-orders-canvas-part2/titlebar-03.png)

1. 双击该标签的文本，然后键入**Northwind 订单**。

    或者，修改**文本**来实现相同的结果在编辑栏中的属性：

    > [!div class="mx-imgBorder"]
    > ![更改标题栏中的文本](media/northwind-orders-canvas-part2/titlebar-04.png)

1. 上**主页**选项卡上，设置标签的格式：
    - 增加字体大小为 24 磅。
    - 加粗文本。
    - 使白色文本。
    - 文本居中。
    - 添加到后台，深蓝色填充。

    > [!div class="mx-imgBorder"]
    > ![在主页选项卡上的格式设置选项](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>添加一个编辑窗体控件

在本部分中，将添加控件来显示用户在库中选择任何订单的摘要。

1. 上**插入**选项卡上，插入[**编辑窗体**](controls/control-form-detail.md)控件：

    > [!div class="mx-imgBorder"]
    > ![添加一个编辑窗体控件](media/northwind-orders-canvas-part2/form-01.png)

    默认情况下，窗体显示在左上角中，其中的其他控件可能会难以查找：

    > [!div class="mx-imgBorder"]
    > ![编辑窗体控件在默认位置](media/northwind-orders-canvas-part2/form-02.png)

1. 移动和调整要介绍的标题栏下方屏幕的右上角的窗体：

    > [!div class="mx-imgBorder"]
    > ![移动和调整编辑窗体控件](media/northwind-orders-canvas-part2/form-03.png)

1. 在编辑栏中，将**数据源**窗体为此值的属性：

    ```powerapps-dot
    Orders
    ```

    > [!div class="mx-imgBorder"]
    > ![编辑窗体控件的数据源属性设置](media/northwind-orders-canvas-part2/form-04.png)

    可以设置相同的属性**属性**选项卡右侧边缘附近，但该方法将不需要的字段添加到窗体。 如果您使用公式栏，在窗体保持为空。

## <a name="add-and-arrange-fields"></a>添加和排列字段

1. 在中**属性**右边缘附近，选择的选项卡**编辑字段**以打开**字段**窗格：

    > [!div class="mx-imgBorder"]
    > ![打开字段窗格](media/northwind-orders-canvas-part2/form-05.png)

1. 在中**字段**窗格中，选择**添加字段**，然后选择对应的复选框**客户**并**员工**字段。

    > [!div class="mx-imgBorder"]
    > ![将客户和员工字段添加到编辑窗体控件](media/northwind-orders-canvas-part2/form-06.png)

1. 向下滚动，直到这些字段显示，然后选择其复选框：

    - **备注**
    - **订单日期**
    - **订单号**
    - **订单状态**
    - **付费的日期**

    > [!div class="mx-imgBorder"]
    > ![将更多的五个字段添加到编辑窗体控件](media/northwind-orders-canvas-part2/form-07.png)

1. 在底部**字段**窗格中，选择**添加**，然后关闭**字段**窗格。

    在窗体显示了七个字段：

    > [!div class="mx-imgBorder"]
    > ![编辑窗体控件将显示七个字段](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > 如果任何字段显示红色错误图标，从源提取数据时，可能有出现问题。 若要解决此错误，刷新数据：
    >
    > 1. 在“视图”选项卡上，选择“数据源”   。
    > 1. 在中**数据**窗格中，选择**数据源**。
    > 1. 下一步**订单**，依次选择省略号 （...）**刷新**，然后关闭**数据**窗格。
    >
    > 如果客户或员工名称组合框仍将显示错误，请检查**主要文本**并**SearchField**的每个框中选择它，然后打开**数据**窗格。 对于客户框中，这两个字段应设置为**nwind_company**。 对于雇员框中，这两个字段应设置为**nwind_lastname**。

1. 选择此窗体，将更改窗体中的列数从 3 为 12 英寸**属性**右边缘附近的选项卡。

    此步骤将添加大的灵活性，因为将字段排列：

    > [!div class="mx-imgBorder"]
    > ![然后更改编辑窗体控件中的列数](media/northwind-orders-canvas-part2/form-08b.png)

    许多 UI 设计依赖 12 列布局，因为它们可以均匀地适应行 1、 2、 3、 4、 6 和 12 控件。 在本主题中，你将创建包含 1、 2 或 4 个控件的行。

1. 移动和调整字段大小通过拖动其句柄，就像任何其他控件，以便每一行都包含这些数据卡中指定的顺序：

    - 第一行：**订单号**，**订单状态**，**订单日期**，并**付费日期**
    - 第二行：**客户**和**员工**
    - 第三行：**备注**

    > [!NOTE]
    > 你可能会发现可以更轻松地扩大**说明**，**客户**，并**员工**数据卡之前对其进行排列。

    > [!div class="mx-imgBorder"]
    > ![移动和调整字段大小](media/northwind-orders-canvas-part2/form-rearrange.gif)

    有关如何排列窗体中的字段的详细信息：[了解数据窗体布局的画布应用](working-with-form-layout.md)。

## <a name="hide-time-controls"></a>隐藏时间控件

在此示例中，不需要的日期字段的时间部分，因为该级别的粒度可以使用户变得混乱。 如果您删除它们，您可能依赖于这些控件来更新日期值或确定数据卡中的另一个控件位置的公式中导致问题。 相反，将隐藏的时间控件通过设置其**Visible**属性。

1. 在中**树视图**窗格中，选择**订单日期**数据卡。

    卡片可能包含不同的名称，但是，它包含**订单日期**。

1. 按住 Shift 键，同时选择中的小时、 分钟和冒号分隔符控件**订单日期**数据卡。

    > [!div class="mx-imgBorder"]
    > ![在订单日期卡中选择的时间控件](media/northwind-orders-canvas-part2/form-09.png)

1. 设置控件的**Visible**属性设置为**false**。

    所有选定的控件从窗体中消失：

    > [!div class="mx-imgBorder"]
    > ![将 Visible 属性设置为 false。](media/northwind-orders-canvas-part2/form-10.png)

1. 重设大小[**日期选取器**](controls/control-date-picker.md)控件以显示完整的日期：

    > [!div class="mx-imgBorder"]
    > ![调整日期选取器控件的大小](media/northwind-orders-canvas-part2/form-11.png)

    接下来，你要重复的最后几个步骤**付费日期**字段。

1. 在中**树视图**窗格中，选择时间控制在**付费日期**数据卡：

    > [!div class="mx-imgBorder"]
    > ![在付费日期卡中选择时间控件](media/northwind-orders-canvas-part2/form-12.png)

1. 设置所选的控件的**Visible**属性设置为**false**:

    > [!div class="mx-imgBorder"]
    > ![将 Visible 属性设置为 false。](media/northwind-orders-canvas-part2/form-13.png)

1. 重设大小中的日期选取器**带薪日期**卡：

    > [!div class="mx-imgBorder"]
    > ![调整日期选取器控件的大小](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>连接顺序库

1. 在中**树视图**窗格中，折叠窗体以更轻松地查找顺序库的名称，然后，如有必要，重命名到**Gallery1**。

1. 设置摘要的窗体**项**属性设置为此表达式：

    ```powerapps-dot
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > ![设置窗体的项属性](media/northwind-orders-canvas-part2/form-15.png)

    窗体将显示在列表中选择应用程序用户按特定顺序的摘要。

    > [!div class="mx-imgBorder"]
    > ![若要在窗体中显示其概述在列表中选择订单](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>替换数据卡

**订单号**是 Common Data Service 会自动分配时创建一条记录的标识符。 此字段的长度[**文本输入**](controls/control-text-input.md)控件默认情况下，但您会将其替换为一个标签，以便用户无法编辑此字段。

1. 选择窗体中，选择**编辑字段**中**属性**右边缘附近选项卡，然后选择**订单号**字段：

    > [!div class="mx-imgBorder"]
    > ![选择订单编号字段](media/northwind-orders-canvas-part2/alt-01.png)

1. 打开**控件类型**列表：

    > [!div class="mx-imgBorder"]
    > ![打开 * * 控制类型 * * 列表](media/northwind-orders-canvas-part2/alt-02.png)

1. 选择**查看文本**数据卡：

    > [!div class="mx-imgBorder"]
    > ![选择 * * 视图文本 * * 数据卡](media/northwind-orders-canvas-part2/alt-02b.png)

1. 关闭**字段**窗格。

    用户无法再更改的订单号：

    > [!div class="mx-imgBorder"]
    > ![订单号是只读的](media/northwind-orders-canvas-part2/alt-03.png)

1. 上**主页**选项卡上，将订单号的字体大小更改为 20 点，以便该字段是更轻松地找到：

    > [!div class="mx-imgBorder"]
    > ![将订单号的字体大小更改](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>使用多对一关系

**订单**实体具有多对一关系与**员工**实体： 每个员工可以创建很多订单，但每个订单可以分配给只能有一个员工。 当用户选择中的雇员[**组合框**](controls/control-combo-box.md)控件，其 **选定**属性提供了从该员工的整条记录**员工**实体。 因此，你可以配置[**映像**](controls/control-image.md)控件向用户显示任何员工的照片选择组合框中。

1. 选择**员工**数据卡：

    > [!div class="mx-imgBorder"]
    > ![选择员工数据卡](media/northwind-orders-canvas-part2/employee-01.png)

1. 在中**高级**右边缘附近的选项卡上，对数据卡解除锁定，以便可以编辑的是以前是只读的公式：

    > [!div class="mx-imgBorder"]
    > ![解锁员工数据卡](media/northwind-orders-canvas-part2/employee-02.png)

1. 在数据卡中，减少组合框，以留出空间中的员工图片的宽度：

    > [!div class="mx-imgBorder"]
    > ![调整组合框控件的大小](media/northwind-orders-canvas-part2/employee-03b.png)

1. 上**插入**选项卡上，选择**媒体** > **映像**:

    > [!div class="mx-imgBorder"]
    > ![插入图像](media/northwind-orders-canvas-part2/employee-04.png)

    图像显示在数据卡中，这将扩展以容纳它：

    > [!div class="mx-imgBorder"]
    > ![与图像控件的员工数据卡](media/northwind-orders-canvas-part2/employee-05.png)

1. 调整图像的大小并将其移到组合框的右侧：

    > [!div class="mx-imgBorder"]
    > ![移动和调整大小的图像控件](media/northwind-orders-canvas-part2/employee-06.png)

1. 设置**图像**为以下公式，如有必要替换 DataCardValue 末尾数字图像属性：

    ```powerapps-dot
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图像的 Image 属性](media/northwind-orders-canvas-part2/employee-07.png)

    将显示所选员工的图片。

1. 而按下 Alt 键，以确认在组合框中选择不同的员工图片也会更改。

    > [!div class="mx-imgBorder"]
    > ![选择要显示该雇员的图片的员工](media/northwind-orders-canvas-part2/employee-select.gif)

## <a name="add-a-save-icon"></a>添加保存图标

1. 在中**树视图**窗格中，选择**Screen1**，然后选择**插入** > **图标** >  **检查**:

    > [!div class="mx-imgBorder"]
    > ![插入复选标记图标](media/northwind-orders-canvas-part2/save-01.png)

    [**检查**](controls/control-shapes-icons.md)图标将出现在左上角默认情况下，其中的其他控件可能会使图标查找困难：

    > [!div class="mx-imgBorder"]
    > ![在默认位置中的图标](media/northwind-orders-canvas-part2/save-02.png)

1. 上**主页**选项卡上，更改**颜色**图标以白色、 调整大小图标，并将其移动的标题栏的右边缘附近的属性：

    > [!div class="mx-imgBorder"]
    > ![配置颜色、 大小和位置保存图标](media/northwind-orders-canvas-part2/save-03.png)

1. 在中**树视图**窗格中，确认窗体的名称是**Form1**，然后将设置的图标**OnSelect**属性设为此公式：

    ```powerapps-dot
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置存储图标的 OnSelect 属性](media/northwind-orders-canvas-part2/save-04.png)

    当用户选择图标[ **SubmitForm** ](functions/function-form.md)函数收集窗体中的任何已更改的值并将其提交到数据源。 在将数据提交，并顺序库反映所做的更改过程完成后，点年 3 月屏幕的顶部。

1. 设置图标**DisplayMode**属性设为此公式：

    ```powerapps-dot
    If( Form1.Unsaved, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图标的 DisplayMode 属性](media/northwind-orders-canvas-part2/save-05.png)

    如果已保存窗体中的所有更改，该图标已禁用且出现在**DisabledColor**，你将其设置下一步。

1. 设置图标**DisabledColor**属性设置为此值：

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图标的 DisabledColor 属性](media/northwind-orders-canvas-part2/save-06.png)

    用户可以将更改保存到订单中，通过选择勾选图标，然后禁用且灰显，直到用户进行另一项更改：

    > [!div class="mx-imgBorder"]
    > ![保存更改](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>添加一个取消图标

1. 上**插入**选项卡上，选择**图标** > **取消**:

    > [!div class="mx-imgBorder"]
    > ![添加取消按钮图标](media/northwind-orders-canvas-part2/save-07.png)

    图标出现在左上角默认情况下，其中的其他控件可能会使图标查找困难：

    > [!div class="mx-imgBorder"]
    > ![默认位置中的取消图标](media/northwind-orders-canvas-part2/save-08.png)

1. 上**主页**选项卡上，更改的图标**颜色**属性以白色、 调整大小的图标，并将其移到左侧的复选图标：

    > [!div class="mx-imgBorder"]
    > ![更改颜色、 大小和位置的取消图标](media/northwind-orders-canvas-part2/save-09.png)

1. 设置的取消图标**OnSelect**属性设为此公式：

    ```powerapps-dot
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![将取消图标的 OnSelect 属性设置](media/northwind-orders-canvas-part2/save-10.png)

    [ **ResetForm** ](functions/function-form.md)函数将放弃将其返回到其原始状态的窗体中的所有更改。

1. 设置的取消图标**DisplayMode**属性设为此公式：

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置取消图标的 DisplayMode 属性](media/northwind-orders-canvas-part2/save-11.png)

    此公式与一个用于检查图标略有不同。 如果已保存所有更改，或在窗体处于已禁用取消图标**新建**模式，则将启用下一步。 在这种情况下， **ResetForm**放弃新的记录。

1. 设置的取消图标**DisabledColor**属性设置为此值：

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![将取消图标 DisabledColor 属性设置](media/northwind-orders-canvas-part2/save-12.png)

    用户可取消更改到订单中，并检查和取消图标会禁用且灰显，如果已保存所有更改：

    > [!div class="mx-imgBorder"]
    > ![保存和取消更改](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>添加一个添加图标

1. 上**插入**选项卡上，选择**图标** > **添加**。

    > [!div class="mx-imgBorder"]
    > ![插入的添加图标](media/northwind-orders-canvas-part2/save-13.png)

    **添加**图标将出现在左上角默认情况下，其中的其他控件可能会难以查找：

    > [!div class="mx-imgBorder"]
    > ![添加图标的默认位置](media/northwind-orders-canvas-part2/save-14.png)

1. 上**主页**选项卡上，设置**颜色**属性的添加图标以白色、 调整大小的图标，并将其移到左侧的取消图标：

    > [!div class="mx-imgBorder"]
    > ![更改颜色、 大小和位置的添加图标](media/northwind-orders-canvas-part2/save-15.png)

1. 设置添加图标**OnSelect**属性设为此公式：

    ```powerapps-dot
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![将添加图标的 OnSelect 属性设置](media/northwind-orders-canvas-part2/save-15b.png)

    [ **NewForm** ](functions/function-form.md)函数在窗体中显示一个空记录。  

1. 设置添加图标**DisplayMode**属性设为此公式：

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置添加图标的 DisplayMode 属性](media/northwind-orders-canvas-part2/save-16.png)

    该公式可以禁用这些条件下的添加图标：

    - 用户所做的更改，但不会保存或取消它们，这是检查和取消图标从相反的行为。
    - 用户选择添加图标，但不进行任何更改。

1. 设置添加图标**DisabledColor**属性设置为此值：

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![将添加图标的 DisabledColor 属性设置](media/northwind-orders-canvas-part2/save-17.png)

    如果它们不进行任何更改，否则它们保存或取消它们已进行了任何更改，用户可以创建订单。 （如果用户选择此图标，它们不能选择它再次它们进行一个或多个更改，然后保存或取消这些更改之前）：

    > [!div class="mx-imgBorder"]
    > ![创建订单](media/northwind-orders-canvas-part2/save-new.gif)

> [!NOTE]
> 如果您创建并保存订单，可能需要向下滚动以显示新订单在订单库中。 它不会有总价格，因为还未添加任何订单详细信息。

## <a name="add-a-trash-icon"></a>添加一个垃圾桶图标

1. 上**插入**选项卡上，选择**图标** > **回收站**。

    > [!div class="mx-imgBorder"]
    > ![插入垃圾桶图标](media/northwind-orders-canvas-part2/save-18.png)

    **垃圾桶**图标将出现在左上角默认情况下，其中的其他控件可能会难以查找：

    > [!div class="mx-imgBorder"]
    > ![垃圾桶图标的默认位置](media/northwind-orders-canvas-part2/save-19.png)

1. 上**主页**选项卡上，更改回收站图标**颜色**属性以白色、 调整大小的图标，并将其移到左侧的添加图标：

    > [!div class="mx-imgBorder"]
    > ![更改颜色、 大小和位置的垃圾桶图标](media/northwind-orders-canvas-part2/save-20.png)

1. 设置垃圾桶图标**OnSelect**属性设为此公式：

    ```powerapps-dot
    Remove( Orders, Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > ![将此垃圾桶图标 OnSelect 属性设置](media/northwind-orders-canvas-part2/save-21.png)

    [**删除**](functions/function-remove-removeif.md)函数从数据源中删除一条记录。 在此公式中，该函数删除顺序库中选择的记录。 因为窗体将显示更多详细信息记录，因此用户可以更轻松地识别出该公式将删除的记录，垃圾桶图标显示附近摘要窗体 （不顺序库）。

1. 设置垃圾桶图标**DisplayMode**属性设为此公式：

    ```powerapps-dot
    If( Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![将此垃圾桶图标 DisplayMode 属性设置](media/northwind-orders-canvas-part2/save-22.png)

    如果用户为其创建一条记录，此公式将禁用回收站图标。 在用户保存该记录，直到**删除**函数具有要删除的记录。

1. 设置垃圾桶图标**DisabledColor**属性设置为此值：

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![将此垃圾桶图标 DisabledColor 属性设置](media/northwind-orders-canvas-part2/save-23.png)

    用户可以删除订单。

    > [!div class="mx-imgBorder"]
    > ![删除订单](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>摘要

概括来说，您添加窗体中的用户可以显示和编辑每个订单的摘要和使用这些元素：

- 显示数据的窗体**订单**实体：**Form1.DataSource =** `Orders`
- 在窗体和顺序库之间的连接：**Form1.Item =** `Gallery1.Selected`
- 备用控件**订单号**字段：**视图中的文本**
- 若要显示该雇员的图片中的多对一关系**员工**数据卡： `DataCardValue1.Selected.Picture`
- 若要将更改保存到订单图标： `SubmitForm( Form1 )`
- 若要取消更改到订单的图标： `ResetForm( Form1 )`
- 用于创建订单图标： `NewForm( Form1 )`
- 若要删除一个订单图标： `Remove( Orders, Gallery1.Selected )`

## <a name="next-step"></a>下一步

将在下一主题中，添加另一个库来显示每个订单中的产品并将通过使用更改这些详细信息[**修补**](functions/function-patch.md)函数。

> [!div class="nextstepaction"]
> [创建详细信息库](northwind-orders-canvas-part3.md)
