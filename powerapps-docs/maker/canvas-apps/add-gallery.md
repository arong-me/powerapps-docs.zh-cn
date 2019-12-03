---
title: 显示画布应用中项的列表 | Microsoft Docs
description: 使用库显示画布应用中项的列表，并通过指定条件来筛选该列表。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/28/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fd48455f24cd07a09ce3a7cdb44b2fa6da2a0166
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679238"
---
# <a name="show-a-list-of-items-in-powerapps"></a>显示 PowerApps 中项的列表

通过向画布应用添加[库](controls/control-gallery.md)控件，显示任意数据源中项的列表。 本主题使用 Excel 作为数据源。 筛选该列表，方法是：将库控件配置为仅显示那些与[文本输入](controls/control-text-input.md)控件中的筛选器条件匹配的项。

## <a name="prerequisites"></a>必备组件

- 了解如何在 PowerApps 中[添加和配置控件](add-configure-controls.md)。

- 设置示例数据：
    1. 下载[此 Excel 文件](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)，其中包含本教程的示例数据。

    2. 将 Excel 文件上传到[云存储帐户](connections/cloud-storage-blob-connections.md)（如 OneDrive for Business）中。

- 打开空白应用：
    1. [登录 PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    1. 在“生成自己的应用”下，选择“从空白开始创建画布应用”。

    1. 为应用指定名称，选择“手机”，然后选择“创建”。

    1. 如果出现 "**欢迎使用 Power Apps Studio** " 对话框，请选择 "**跳过**"。

    1. 与 Excel 文件中的“FlooringEstimates”表[建立连接](add-data-connection.md)。

## <a name="add-a-gallery-to-a-blank-screen"></a>将库添加到空白屏幕

1. 在 "**插入**" 选项卡上，选择 "**库**"，然后选择 "**垂直**"。

    ![添加垂直库](./media/add-gallery/gallery-dropdown.png)

1. 在右侧窗格的 "**属性**" 选项卡上，打开 "**项**" 列表，然后选择 "**地板估计**"。

    ![地板估计](./media/add-gallery/select-layout.png)

1. 可有可无在 "**布局**" 列表中，选择一个不同的选项。

## <a name="add-a-gallery-in-a-screen"></a>在屏幕中添加库

1. 在 "**主页**" 选项卡上，选择 "**新屏幕** > **列表屏幕**"。

    此时会显示一个包含**库**控件和其他控件（如搜索栏）的屏幕。

1. 将库的 **Items** 属性设置为 `FlooringEstimates`。

    此时，库控件显示示例数据。

    ![显示数据](./media/add-gallery/show-data-default.png)

## <a name="add-a-control-to-the-gallery-control"></a>将控件添加到库控件
在进行任何其他自定义之前，请确保**库**控件的布局与你需要的内容最匹配。 然后，你可以进一步修改**库**模板，该模板确定**库**控件中的所有数据的显示方式。

1. 单击或点击**库**控件底部附近，然后选择左上角的铅笔图标，从而选择模板。

    ![编辑库模板](./media/add-gallery/edit-item.png)

2. 在模板仍然处于选中状态的情况下，添加[标签](controls/control-text-box.md)控件，然后移动此控件并重设其大小，使之与模板中的其他控件不重叠。

    ![添加标签](./media/add-gallery/add-text-box.png)

3. 选择库，然后在右侧窗格的 "**属性**" 选项卡上选择 "**字段**" 旁边的 "**编辑**"。

4. 选择在此过程前面部分添加的标签，然后打开“数据”窗格中突出显示的列表。

    ![打开下拉列表](./media/add-gallery/open-dropdown.png)

5. 在此列表中，单击或点击“价格”。

    此时，库控件显示示例新值。

    ![最终库](./media/add-gallery/final-gallery.png)

## <a name="filter-and-sort-a-gallery"></a>对库进行筛选和排序
库控件的[“Items”](controls/properties-core.md) 属性决定了其所显示的项。 在此过程中，您将配置该属性，以便它还根据筛选条件和顺序确定显示的记录。

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

1. 双击搜索框，然后在其中键入产品名称的一部分或全部。

    仅显示符合筛选条件的项。

1. 按 Alt 键的同时选择排序图标一次或多次，以切换排序顺序。

    记录根据产品名称在升序和降序字母顺序之间切换。

## <a name="highlight-the-selected-item"></a>突出显示选定项
将**库**控件的 " **TemplateFill** " 属性设置为与此示例类似的公式，但如果需要，可以指定不同的颜色：

If(ThisItem.IsSelected, LightCyan, White)

## <a name="change-the-default-selection"></a>更改默认选择
将库控件的“Default”属性设置为要默认选择的记录。 例如，可以在**FlooringEstimates**数据源中指定第五项：

Last(FirstN(FlooringEstimates, 5))

在以下示例中，指定“FlooringEstimates”数据源中“Hardwood”类别的第一项：

First(Filter(FlooringEstimates, Category = "Hardwood"))

## <a name="next-steps"></a>后续步骤
了解如何使用[窗体](working-with-forms.md)和[公式](working-with-formulas.md)。
