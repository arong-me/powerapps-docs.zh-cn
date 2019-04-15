---
title: 显示、 编辑或在画布应用中添加一条记录 |Microsoft Docs
description: 使用画布应用窗体显示、编辑或添加数据源中的表记录。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/06/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e94aa48ed3fba1b4591e196e3b81d3fb0f76666f
ms.sourcegitcommit: 5c098a62f66a2f33418967fdce9363bd529e0fc1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58581015"
---
# <a name="show-edit-or-add-a-record-in-a-canvas-app"></a>显示、 编辑或在画布应用中添加一条记录

在画布应用中，添加和配置 **[显示](controls/control-form-detail.md)** 要记录中显示所有字段，您还可以添加和配置窗体控件 **[编辑](controls/control-form-detail.md)** 若要编辑记录中的任何字段、 添加记录，并将所做的更改保存回数据源的窗体控件。

## <a name="prerequisites"></a>先决条件

- 了解如何在 PowerApps 中[添加和配置控件](add-configure-controls.md)。
- 下载[此 Excel 文件](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)，其中包含本教程的示例数据。
- 将 Excel 文件上传到[云存储帐户](connections/cloud-storage-blob-connections.md)（如 OneDrive for Business）中。
- 创建或打开适用于手机，应用[添加连接](add-data-connection.md)到**FlooringEstimates** Excel 文件中的表。

    可以将窗体添加到平板电脑应用，但它不会匹配本主题，因为默认情况下，窗体将具有三列。

- 如果您打开一个现有的应用程序、[添加一个屏幕](add-screen-context-variables.md)到它。

## <a name="add-a-form-and-show-data"></a>添加窗体并显示数据
1. 在空白屏幕，添加 **[下拉列表](controls/control-drop-down.md)** 控制，并将其命名**ChooseProduct**。

    > [!NOTE]
   > 如果不确定如何添加控件、重命名控件或设置属性，请参阅[添加和配置控件](add-configure-controls.md)。

1. 上**属性**选项卡的右侧窗格中，设置**项**到`FlooringEstimates`并**值**到`Name`。

    ![设置窗体的项目属性](./media/add-form/items-property.png)

    此列表显示数据源中地面材料产品的名称。

1. 添加**编辑**窗体控件中，将其移**ChooseProduct**，，然后调整大小以覆盖大部分屏幕窗体。

    ![添加表单](./media/add-form/add-a-form.png)

    > [!NOTE]
   > 本主题介绍**编辑**窗体控件，但类似做法准则也适用于**显示**的窗体控件。

1. 设置窗体的 **[数据源](controls/control-form-detail.md)** 属性设置为**FlooringEstimates**并将其 **[项](controls/control-form-detail.md)** 属性此公式：

    `First(Filter(FlooringEstimates, Name=ChooseProduct.Selected.Value))`

   此公式指定，在配置完窗体后，显示用户在“ChooseProduct”中选择的记录。

1. 上**属性**选项卡的右侧窗格中，选择**编辑字段**。

    ![编辑字段](./media/add-form/edit-fields.png)

1. 在“字段”窗格中，选择“添加字段”，选中每个字段的复选框，然后选择“添加”。

    ![添加字段](./media/add-form/add-fields.png)

1. 选择省略号 （...） 下一步**添加字段**，选择**全部折叠**，然后将拖**名称**到列表的顶部。

    ![移动字段](./media/add-form/move-field.png)

    **编辑**窗体控件会反映出所做的更改。

    ![显示窗体](./media/add-form/show-form1.png)

## <a name="set-the-card-type-for-a-field"></a>设置字段的卡类型
1. 在中**字段**窗格中，展开**价格**字段通过选择向下箭头。

1. 打开**控件类型**列表，并选择**编辑滑块**。

    ![编辑滑块](./media/add-form/edit-slider.png)

    在表单中，**价格**字段显示**滑块**而不是控制**文本输入**控件。

1. （可选）请遵循相同的过程，若要更改的控件**概述**字段**编辑多行文本**控件。

## <a name="edit-form-only-save-changes"></a>（仅限编辑窗体）保存更改

1. 重命名窗体**EditForm**。

1. 添加“**[按钮](controls/control-button.md)**”控件，并将其 **[OnSelect](controls/properties-core.md)** 属性设置为以下公式：

   `SubmitForm(EditForm)`

1. 按 F5 打开预览，更改产品的名称，然后选择创建按钮。

    **[SubmitForm](functions/function-form.md)** 函数将所做的更改保存到数据源。

1. （可选）通过按 esc 键 （或通过选择右上角的关闭图标） 关闭预览。

## <a name="next-steps"></a>后续步骤
详细了解如何使用[窗体](working-with-forms.md)和[公式](working-with-formulas.md)。
