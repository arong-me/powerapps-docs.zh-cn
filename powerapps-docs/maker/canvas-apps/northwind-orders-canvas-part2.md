---
title: 在画布应用中创建摘要窗体 |Microsoft Docs
description: 在画布应用中创建摘要窗体，以管理 Northwind 商贸的数据
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d151249caebdb2a6f142943074a409bc626ff662
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "71995857"
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>在画布应用中创建摘要窗体

按照分步说明在画布应用中创建一个用于管理 Northwind 商贸数据库中虚拟数据的摘要窗体。 本主题是一系列文章的一部分，说明如何在 Common Data Service 中构建业务应用程序的关系数据。 为了获得最佳结果，请在此序列中浏览这些主题：

1. [创建订单库](northwind-orders-canvas-part1.md)。
2. 创建摘要窗体（**本主题**）。
3. [创建详细信息库](northwind-orders-canvas-part3.md)。

> [!div class="mx-imgBorder"]
> ![屏幕区域的定义](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>必备组件

1. [安装 Northwind 商贸数据库和应用](northwind-install.md)。
1. 查看 Northwind 商贸的[画布应用的概述](northwind-orders-canvas-overview.md)。
1. 自行[创建订单库](northwind-orders-canvas-part1.md)，或打开 " **Northwind 订单（画布）-开始第2部分**" 应用，该应用已包含该库。

## <a name="add-a-title-bar"></a>添加标题栏

在应用程序的顶部，创建一个标题栏，其中包含本主题末尾的操作按钮。

1. 在 "**树视图**" 窗格中，选择 " **Screen1** "，以确保不会意外地将控件添加到订单库：

    > [!div class="mx-imgBorder"]
    > ![在树视图窗格中选择 "Screen1"](media/northwind-orders-canvas-part2/titlebar-01.png)

1. 在 "**插入**" 选项卡上，选择 "**标签**" 以插入[**标签**](controls/control-text-box.md)控件：

    > [!div class="mx-imgBorder"]
    > ![插入标签](media/northwind-orders-canvas-part2/titlebar-02.png)

    新标签只应在库上出现一次。 如果它出现在库的每个项中，则删除该标签的第一个实例，确保选中该屏幕（如前一步骤所述），然后再次插入标签。

1. 移动新标签并调整其大小，使其位于屏幕顶部：

    > [!div class="mx-imgBorder"]
    > ![移动标签并调整其大小](media/northwind-orders-canvas-part2/titlebar-03.png)

1. 双击标签文本，然后键入**Northwind Orders**。

    作为替代方法，请修改公式栏中的**Text**属性以获得相同的结果：

    > [!div class="mx-imgBorder"]
    > ![更改标题栏中的文本](media/northwind-orders-canvas-part2/titlebar-04.png)

1. 在 "**主页**" 选项卡上，设置标签的格式：
    - 将字体大小增加为24磅。
    - 使文本为粗体。
    - 使文本为白色。
    - 使文本居中。
    - 将深蓝填充添加到背景。

    > [!div class="mx-imgBorder"]
    > !["主页" 选项卡上的格式设置选项](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>添加编辑窗体控件

在本部分中，你将添加控件以显示用户在库中选择的任何订单的摘要。

1. 在 "**插入**" 选项卡上，插入 "[**编辑窗体**](controls/control-form-detail.md)" 控件：

    > [!div class="mx-imgBorder"]
    > ![添加 "编辑窗体" 控件](media/northwind-orders-canvas-part2/form-01.png)

    默认情况下，窗体显示在左上角，其他控件可能会导致难以查找：

    > [!div class="mx-imgBorder"]
    > ![在默认位置编辑窗体控件](media/northwind-orders-canvas-part2/form-02.png)

1. 移动窗体并调整其大小以覆盖标题栏下面屏幕的右上角：

    > [!div class="mx-imgBorder"]
    > ![移动 "编辑窗体" 控件并调整其大小](media/northwind-orders-canvas-part2/form-03.png)

1. 在编辑栏中，将窗体的**DataSource**属性设置为以下值：

    ```powerapps-dot
    Orders
    ```

    > [!div class="mx-imgBorder"]
    > ![设置编辑窗体控件的 DataSource 属性](media/northwind-orders-canvas-part2/form-04.png)

    您可以在右侧边缘附近的 "**属性**" 选项卡中设置相同的属性，但该方法会将您不需要的字段添加到窗体中。 如果使用公式栏，则窗体将保留为空。

## <a name="add-and-arrange-fields"></a>添加并排列字段

1. 在右侧边缘附近的 "**属性**" 选项卡中，选择 "**编辑字段**"，打开 "**字段**" 窗格：

    > [!div class="mx-imgBorder"]
    > ![打开 "字段" 窗格](media/northwind-orders-canvas-part2/form-05.png)

1. 在 "**字段**" 窗格中，选择 "**添加字段**"，然后选中 "**客户**" 和 "**员工**" 字段的复选框。

    > [!div class="mx-imgBorder"]
    > ![将 "Customer" 和 "Employee" 字段添加到 "编辑窗体" 控件](media/northwind-orders-canvas-part2/form-06.png)

1. 向下滚动，直到显示这些字段，然后选中其复选框：

    - **备注**
    - **订单日期**
    - **订单号**
    - **订单状态**
    - **支付日期**

    > [!div class="mx-imgBorder"]
    > ![将其他五个字段添加到 "编辑窗体" 控件](media/northwind-orders-canvas-part2/form-07.png)

1. 在 "**字段**" 窗格的底部，选择 "**添加**"，然后关闭 "**字段**" 窗格。

    该窗体显示七个字段：

    > [!div class="mx-imgBorder"]
    > ![编辑窗体控件显示七个字段](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > 如果任何字段显示红色错误图标，则表示从源中提取数据时可能出现问题。 若要解决此错误，请刷新数据：
    >
    > 1. 在“视图”选项卡上，选择“数据源”。
    > 1. 在 "**数据**" 窗格中，选择 "**数据源**"。
    > 1. 选择 "**订单**" 旁边的省略号（...），选择 "**刷新**"，然后关闭 "**数据**" 窗格。
    >
    > 如果客户或雇员名称的组合框仍显示错误，请通过选择并打开 "**数据**" 窗格来检查每个框的**主文本**和**SearchField** 。 对于 customer box，应将两个字段都设置为**nwind_company**。 对于 employee 框，这两个字段应设置为**nwind_lastname**。

1. 选择该窗体后，在右侧边缘附近的 "**属性**" 选项卡中，将窗体中的列数从3更改为12。

    此步骤可在排列字段时增加灵活性：

    > [!div class="mx-imgBorder"]
    > ![更改编辑窗体控件中的列数](media/northwind-orders-canvas-part2/form-08b.png)

    许多 UI 设计依赖于12个列的布局，因为它们可以平均容纳1、2、3、4、6和12个控件的行。 在本主题中，您将创建包含1个、2个或4个控件的行。

1. 拖动字段的句柄并调整其大小，就像对任何其他控件一样，每一行都按指定顺序包含这些数据卡：

    - 第一行：**订单号**、**订单状态**、**订单日期**和**支付日期**
    - 第二行：**客户**和**员工**
    - 第三行：**说明**

    > [!NOTE]
    > 你可能会发现，在排列**便笺**、**客户**和**员工**数据卡之前，可以更轻松地对其进行放宽。

    > [!div class="mx-imgBorder"]
    > ![移动字段并调整其大小](media/northwind-orders-canvas-part2/form-rearrange.gif)

    有关如何排列窗体中的字段的详细信息：[了解画布应用的数据窗体布局](working-with-form-layout.md)。

## <a name="hide-time-controls"></a>隐藏时间控件

在此示例中，无需日期字段的时间部分，因为该粒度级别可能会打乱用户的注意力。 如果删除这些控件，则可能会导致依赖于这些控件的公式更新日期值或确定另一个控件在数据卡中的位置时出现问题。 相反，您将通过设置 " **Visible** " 属性来隐藏时间控件。

1. 在 "**树视图**" 窗格中，选择 "**订单日期**" 数据卡。

    此卡的名称可能不同，但包含**订单日期**。

1. 按住 Shift 键的同时，在 "**订单日期**" 数据卡中选择 "小时"、"分钟" 和 "冒号分隔符" 控件。

    > [!div class="mx-imgBorder"]
    > ![在 "订单日期" 卡中选择时间控制](media/northwind-orders-canvas-part2/form-09.png)

1. 将控件的**Visible**属性设置为**false**。

    所有选定控件都将从窗体中消失：

    > [!div class="mx-imgBorder"]
    > ![将 Visible 属性设置为 false。](media/northwind-orders-canvas-part2/form-10.png)

1. 调整 "[**日期选取器**](controls/control-date-picker.md)" 控件的大小以显示完整的日期：

    > [!div class="mx-imgBorder"]
    > ![调整日期选取器控件的大小](media/northwind-orders-canvas-part2/form-11.png)

    接下来，对 "**付费日期**" 字段重复执行最后几个步骤。

1. 在 "**树视图**" 窗格中，选择 "**付费日期**" 数据卡中的时间控件：

    > [!div class="mx-imgBorder"]
    > ![在付费日期卡中选择时间控制](media/northwind-orders-canvas-part2/form-12.png)

1. 将所选控件的**Visible**属性设置为**false**：

    > [!div class="mx-imgBorder"]
    > ![将 Visible 属性设置为 false。](media/northwind-orders-canvas-part2/form-13.png)

1. 在 "**付费卡日期**" 中调整日期选取器的大小：

    > [!div class="mx-imgBorder"]
    > ![调整日期选取器控件的大小](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>连接订单库

1. 在 "**树视图**" 窗格中，折叠窗体以便更轻松地找到订单库的名称，然后在必要时将其重命名为**gallery1.selected**。

1. 将摘要窗体的**Item**属性设置为以下表达式：

    ```powerapps-dot
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > ![设置窗体的项目属性](media/northwind-orders-canvas-part2/form-15.png)

    此窗体显示应用用户在列表中选择的任意订单的摘要。

    > [!div class="mx-imgBorder"]
    > ![在列表中选择订单，以将其概述显示为表单](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>更换数据卡

**订单号**是 Common Data Service 在创建记录时自动分配的标识符。 默认情况下，此字段具有 "[**文本输入**](controls/control-text-input.md)" 控件，但您会将其替换为标签，以便用户无法编辑此字段。

1. 选择窗体，在右边缘附近的 "**属性**" 选项卡中选择 "**编辑字段**"，然后选择 "**订单号**" 字段：

    > [!div class="mx-imgBorder"]
    > ![选择订单号字段](media/northwind-orders-canvas-part2/alt-01.png)

1. 打开 "**控件类型**" 列表：

    > [!div class="mx-imgBorder"]
    > ![打开 "控件类型" 列表](media/northwind-orders-canvas-part2/alt-02.png)

1. 选择 "**查看文本**" 数据卡：

    > [!div class="mx-imgBorder"]
    > ![选择 "查看文本" "数据卡"](media/northwind-orders-canvas-part2/alt-02b.png)

1. 关闭 "**字段**" 窗格。

    用户不能再更改订单号：

    > [!div class="mx-imgBorder"]
    > ![订单号为只读](media/northwind-orders-canvas-part2/alt-03.png)

1. 在 "**主页**" 选项卡上，将订单号的字号更改为20磅，以便更易于查找字段：

    > [!div class="mx-imgBorder"]
    > ![更改订单号的字号](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>使用多对一关系

**Orders**实体与**Employees**实体具有多对一的关系：每个员工可以创建许多订单，但每个订单只能分配给一个员工。 当用户在[**组合框**](controls/control-combo-box.md)控件中选择员工时，其 **所选**属性将从**Employees**实体提供该员工的整个记录。 因此，您可以将[**图像**](controls/control-image.md)控件配置为显示用户在组合框中选择的任何员工的照片。

1. 选择**员工**数据卡：

    > [!div class="mx-imgBorder"]
    > ![选择 "员工" 数据卡](media/northwind-orders-canvas-part2/employee-01.png)

1. 在右侧边缘附近的 "**高级**" 选项卡中，对数据卡进行解锁，以便编辑以前为只读公式：

    > [!div class="mx-imgBorder"]
    > ![解锁员工数据卡](media/northwind-orders-canvas-part2/employee-02.png)

1. 在数据卡中，缩小组合框的宽度以为员工图片腾出空间：

    > [!div class="mx-imgBorder"]
    > ![调整组合框控件的大小](media/northwind-orders-canvas-part2/employee-03b.png)

1. 在 "**插入**" 选项卡上，选择 " **Media**  > "**图像**：

    > [!div class="mx-imgBorder"]
    > ![插入图像](media/northwind-orders-canvas-part2/employee-04.png)

    此时会在数据卡中显示图像，这会扩展以容纳该图像：

    > [!div class="mx-imgBorder"]
    > ![包含图像控制的员工数据卡](media/northwind-orders-canvas-part2/employee-05.png)

1. 调整图像大小，并将其移动到组合框的右侧：

    > [!div class="mx-imgBorder"]
    > ![移动图像控件并调整其大小](media/northwind-orders-canvas-part2/employee-06.png)

1. 将图像的**image**属性设置为此公式，如有必要，将 DataCardValue 的末尾替换为数字：

    ```powerapps-dot
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图像的 Image 属性](media/northwind-orders-canvas-part2/employee-07.png)

    此时将显示所选员工的照片。

1. 按住 Alt 键的同时，在组合框中选择不同的员工，确认图片也发生了变化。

    > [!div class="mx-imgBorder"]
    > ![选择一个雇员来显示该雇员的照片](media/northwind-orders-canvas-part2/employee-select.gif)

## <a name="add-a-save-icon"></a>添加保存图标

1. 在 "**树视图**" 窗格中，选择 " **Screen1**"，然后选择 "**插入** > **图标** > **检查**：

    > [!div class="mx-imgBorder"]
    > ![插入勾号图标](media/northwind-orders-canvas-part2/save-01.png)

    默认情况下，默认情况下，此[**复选**](controls/control-shapes-icons.md)框显示在左上角，其他控件可能会使该图标难以查找：

    > [!div class="mx-imgBorder"]
    > ![图标位于默认位置](media/northwind-orders-canvas-part2/save-02.png)

1. 在 "**主页**" 选项卡上，将图标的 "**颜色**" 属性更改为白色，并调整图标大小，并将其移动到标题栏的右边缘附近：

    > [!div class="mx-imgBorder"]
    > ![配置保存图标的颜色、大小和位置](media/northwind-orders-canvas-part2/save-03.png)

1. 在 "**树视图**" 窗格中，确认窗体的名称为 " **Form1**"，然后将图标的 " **OnSelect** " 属性设置为以下公式：

    ```powerapps-dot
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置保存图标的 OnSelect 属性](media/northwind-orders-canvas-part2/save-04.png)

    当用户选择此图标时， [**SubmitForm**](functions/function-form.md)函数将收集窗体中的任何更改后的值，并将其提交到数据源。 提交数据时，屏幕3月的第3点点之间的点号，并且在该过程完成后，订单库会反映这些更改。

1. 将图标的**DisplayMode**属性设置为以下公式：

    ```powerapps-dot
    If( Form1.Unsaved, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图标的 DisplayMode 属性](media/northwind-orders-canvas-part2/save-05.png)

    如果窗体中的所有更改都已保存，则图标将被禁用并显示在**DisabledColor**中，接下来将设置。

1. 将图标的**DisabledColor**属性设置为以下值：

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![设置图标的 DisabledColor 属性](media/northwind-orders-canvas-part2/save-06.png)

    用户可以通过选中复选图标来保存对订单所做的更改，然后在用户进行其他更改之前禁用并灰显。

    > [!div class="mx-imgBorder"]
    > ![保存更改](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>添加 "取消" 图标

1. 在 "**插入**" 选项卡上，选择 " > **取消**"**图标**：

    > [!div class="mx-imgBorder"]
    > ![添加取消图标](media/northwind-orders-canvas-part2/save-07.png)

    默认情况下，该图标显示在左上角，其他控件可能会使该图标难以查找：

    > [!div class="mx-imgBorder"]
    > 默认位置 !["取消" 图标](media/northwind-orders-canvas-part2/save-08.png)

1. 在 "**主页**" 选项卡上，将图标的 "**颜色**" 属性更改为白色，调整图标的大小，然后将其移到复选图标的左侧：

    > [!div class="mx-imgBorder"]
    > ![更改 "取消" 图标的颜色、大小和位置](media/northwind-orders-canvas-part2/save-09.png)

1. 将 "取消" 图标的 " **OnSelect** " 属性设置为以下公式：

    ```powerapps-dot
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置 "取消" 图标的 OnSelect 属性](media/northwind-orders-canvas-part2/save-10.png)

    [**ResetForm**](functions/function-form.md)函数将放弃窗体中的所有更改，这会将其返回到其原始状态。

1. 将 "取消" 图标的 " **DisplayMode** " 属性设置为以下公式：

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置 "取消" 图标的 DisplayMode 属性](media/northwind-orders-canvas-part2/save-11.png)

    此公式略有不同于选中图标的公式。 如果所有更改均已保存或窗体处于**新**模式，则 "取消" 图标处于禁用状态，你将在下一步启用此功能。 在这种情况下， **ResetForm**将放弃新记录。

1. 将 "取消" 图标的**DisabledColor**属性设置为以下值：

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![设置 "取消" 图标的 DisabledColor 属性](media/northwind-orders-canvas-part2/save-12.png)

    用户可以取消对订单所做的更改，如果已保存所有更改，则 "检查" 和 "取消" 图标将处于禁用状态并灰显：

    > [!div class="mx-imgBorder"]
    > ![保存和取消更改](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>添加添加图标

1. 在 "**插入**" 选项卡上，选择  > **添加**的**图标**。

    > [!div class="mx-imgBorder"]
    > ![插入添加图标](media/northwind-orders-canvas-part2/save-13.png)

    默认情况下，"**添加**" 图标默认显示在左上角，其他控件可能会导致难以查找：

    > [!div class="mx-imgBorder"]
    > "添加" 图标 ![默认位置](media/northwind-orders-canvas-part2/save-14.png)

1. 在 "**主页**" 选项卡上，将 "添加" 图标的 "**颜色**" 属性设置为白色，调整图标大小，并将其移到 "取消" 图标的左侧：

    > [!div class="mx-imgBorder"]
    > ![更改 "添加" 图标的颜色、大小和位置](media/northwind-orders-canvas-part2/save-15.png)

1. 将 "添加" 图标的 " **OnSelect** " 属性设置为以下公式：

    ```powerapps-dot
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置 "添加" 图标的 OnSelect 属性](media/northwind-orders-canvas-part2/save-15b.png)

    [**NewForm**](functions/function-form.md)函数在窗体中显示空白记录。  

1. 将 "添加" 图标的 " **DisplayMode** " 属性设置为以下公式：

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置 "添加" 图标的 DisplayMode 属性](media/northwind-orders-canvas-part2/save-16.png)

    此公式在以下条件下禁用添加图标：

    - 用户进行了更改，但未保存或取消它们，这与 "检查" 和 "取消" 图标的行为相反。
    - 用户选择 "添加" 图标但不进行任何更改。

1. 将 "添加" 图标的 " **DisabledColor** " 属性设置为以下值：

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![设置 "添加" 图标的 DisabledColor 属性](media/northwind-orders-canvas-part2/save-17.png)

    如果用户未进行任何更改，则可以创建订单，或者保存或取消其所做的任何更改。 （如果用户选择此图标，则他们不能再次选择此图标，直到他们做出一项或多项更改，然后保存或取消这些更改）：

    > [!div class="mx-imgBorder"]
    > ![创建订单](media/northwind-orders-canvas-part2/save-new.gif)

> [!NOTE]
> 如果你创建并保存了订单，则可能需要在订单库中向下滚动以显示你的新订单。 由于尚未添加任何订单详细信息，因此不会产生总价格。

## <a name="add-a-trash-icon"></a>添加垃圾桶图标

1. 在 "**插入**" 选项卡上，选择 " > **垃圾桶**"**图标**。

    > [!div class="mx-imgBorder"]
    > ![插入垃圾桶图标](media/northwind-orders-canvas-part2/save-18.png)

    默认情况下，"**垃圾桶**" 图标默认显示在左上角，其他控件可能会导致难以查找：

    > [!div class="mx-imgBorder"]
    > 垃圾桶图标 ![默认位置](media/northwind-orders-canvas-part2/save-19.png)

1. 在 "**主页**" 选项卡上，将 "垃圾桶" 图标的 "**颜色**" 属性更改为白色，调整图标大小，并将其移到 "添加" 图标的左侧：

    > [!div class="mx-imgBorder"]
    > ![更改垃圾桶图标的颜色、大小和位置](media/northwind-orders-canvas-part2/save-20.png)

1. 将垃圾桶图标的**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Remove( Orders, Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置垃圾桶图标的 OnSelect 属性](media/northwind-orders-canvas-part2/save-21.png)

    [**Remove**](functions/function-remove-removeif.md)函数从数据源中删除记录。 在此公式中，函数将删除订单库中选择的记录。 垃圾桶图标显示在摘要窗体（而不是订单库）附近，因为该窗体显示了有关记录的更多详细信息，因此用户可以更轻松地标识公式将删除的记录。

1. 将垃圾桶图标的**DisplayMode**属性设置为以下公式：

    ```powerapps-dot
    If( Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![设置垃圾桶图标的 DisplayMode 属性](media/northwind-orders-canvas-part2/save-22.png)

    如果用户正在创建记录，则此公式禁用垃圾桶图标。 在用户保存记录之前， **Remove**函数没有要删除的记录。

1. 将垃圾桶图标的**DisabledColor**属性设置为以下值：

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![设置垃圾桶图标的 DisabledColor 属性](media/northwind-orders-canvas-part2/save-23.png)

    用户可以删除订单。

    > [!div class="mx-imgBorder"]
    > ![删除订单](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>摘要

概括而言，你添加了一个窗体，用户可以在其中显示和编辑每个订单的摘要，并使用以下元素：

- 显示 "**订单**" 实体中的数据的窗体： node.js **=** `Orders`
- 窗体和订单库之间的连接： **Form1. Item =** `Gallery1.Selected`
- **订单号**字段的替代控件：**查看文本**
- 多对一关系，用于在**员工**数据卡中显示员工的照片： `DataCardValue1.Selected.Picture`
- 用于保存对订单的更改的图标： `SubmitForm( Form1 )`
- 用于取消对订单的更改的图标： `ResetForm( Form1 )`
- 用于创建订单的图标： `NewForm( Form1 )`
- 用于删除订单的图标： `Remove( Orders, Gallery1.Selected )`

## <a name="next-step"></a>下一步

在下一主题中，你将添加另一个库以显示每个订单中的产品，你将使用[**Patch**](functions/function-patch.md)函数更改这些详细信息。

> [!div class="nextstepaction"]
> [创建详细信息库](northwind-orders-canvas-part3.md)
