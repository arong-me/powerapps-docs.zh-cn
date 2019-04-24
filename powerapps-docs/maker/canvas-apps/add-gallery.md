---
title: 显示画布应用中项的列表 | Microsoft Docs
description: 使用库显示画布应用中项的列表，并通过指定条件来筛选该列表。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/28/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f45948bc16f036669a09ed2c566c60440d24a797
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61527958"
---
# <a name="show-a-list-of-items-in-powerapps"></a>显示 PowerApps 中项的列表

通过向画布应用添加[库](controls/control-gallery.md)控件，显示任意数据源中项的列表。 本主题使用 Excel 作为数据源。 筛选该列表，方法是：将库控件配置为仅显示那些与[文本输入](controls/control-text-input.md)控件中的筛选器条件匹配的项。

## <a name="prerequisites"></a>先决条件

- 了解如何在 PowerApps 中[添加和配置控件](add-configure-controls.md)。

- 设置示例数据：
    1. 下载[此 Excel 文件](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)，其中包含本教程的示例数据。

    2. 将 Excel 文件上传到[云存储帐户](connections/cloud-storage-blob-connections.md)（如 OneDrive for Business）中。

- 打开一个空白应用程序：
    1. [登录 PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    1. 在“生成自己的应用”下，选择“从空白开始创建画布应用”。

    1. 为应用指定名称，选择“手机”，然后选择“创建”。

    1. 如果出现“欢迎使用 PowerApps Studio”对话框，则单击“跳过”。

    1. 与 Excel 文件中的“FlooringEstimates”表[建立连接](add-data-connection.md)。

## <a name="add-a-gallery-to-a-blank-screen"></a>将库添加到空白屏幕

1. 上**插入**选项卡上，选择**库**，然后选择**垂直**。

    ![添加垂直库](./media/add-gallery/gallery-dropdown.png)

1. 上**属性**选项卡的右侧窗格中，打开**项**列表，并选择**地面材料估算**。

    ![地面材料估算](./media/add-gallery/select-layout.png)

1. （可选）在中**布局**列表中，选择一个不同的选项。

## <a name="add-a-gallery-in-a-screen"></a>在屏幕中添加一个库

1. 上**主页**选项卡上，选择**新屏幕** > **列表屏幕**。

    包含一个屏幕**库**控件和其他控件，如搜索栏中，将出现。

1. 将库的 **Items** 属性设置为 `FlooringEstimates`。

    此时，库控件显示示例数据。

    ![显示数据](./media/add-gallery/show-data-default.png)

## <a name="add-a-control-to-the-gallery-control"></a>将控件添加到库控件
在执行任何其他自定义之前，确保的布局你**库**控件最匹配所需。 在这里，您可以进一步修改**库**模板，用于确定如何中的所有数据**库**显示控件。

1. 通过单击或点击底部附近选择的模板**库**控件，然后选择其左上角的铅笔图标。

    ![编辑库模板](./media/add-gallery/edit-item.png)

2. 在模板仍然处于选中状态的情况下，添加[标签](controls/control-text-box.md)控件，然后移动此控件并重设其大小，使之与模板中的其他控件不重叠。

    ![添加标签](./media/add-gallery/add-text-box.png)

3. 选择库，然后选择**编辑**旁边**字段**上**属性**的右侧窗格的选项卡。

4. 选择在此过程前面部分添加的标签，然后打开“数据”窗格中突出显示的列表。

    ![打开下拉列表](./media/add-gallery/open-dropdown.png)

5. 在此列表中，单击或点击“价格”。

    此时，库控件显示示例新值。

    ![最终库](./media/add-gallery/final-gallery.png)

## <a name="filter-and-sort-a-gallery"></a>筛选器和排序库
库控件的[“Items”](controls/properties-core.md) 属性决定了其所显示的项。 在此过程中，你将配置该属性，以便它还确定基于筛选条件，按什么顺序显示的记录。

![搜索框和排序图标](./media/add-gallery/text-search-box.png)

1. 将库控件的[“Items”](controls/properties-core.md)属性设置为以下公式：

    ```powerapps-dot
    Sort
        (If
            (IsBlank(TextSearchBox1.Text),
            FlooringEstimates,
            Filter(
                FlooringEstimates,
                TextSearchBox1.Text in Text(Name)
            )
        ),
        Name,
        If(
            SortDescending1,
            SortOrder.Descending,
            SortOrder.Ascending
        )
    )
    ```

    若要详细了解此公式中的函数，请参阅[公式参考](formula-reference.md)。

1. 双击搜索框，然后在其中键入部分或全部产品名称。

    仅满足筛选条件的这些项显示。

1. 在按住 Alt 键，选择排序图标一次多多次切换排序顺序。

    记录升序和降序基于产品名称的字母顺序之间切换。

## <a name="highlight-the-selected-item"></a>突出显示选定项
设置**库**控件的**TemplateFill**属性的公式类似于此示例中，但您可以指定不同的颜色，如果你想：

If(ThisItem.IsSelected, LightCyan, White)

## <a name="change-the-default-selection"></a>更改默认选择
将库控件的“Default”属性设置为要默认选择的记录。 例如，可以指定中的第五个项**FlooringEstimates**数据源：

Last(FirstN(FlooringEstimates, 5))

在以下示例中，指定“FlooringEstimates”数据源中“Hardwood”类别的第一项：

First(Filter(FlooringEstimates, Category = "Hardwood"))

## <a name="next-steps"></a>后续步骤
了解如何使用[窗体](working-with-forms.md)和[公式](working-with-formulas.md)。
