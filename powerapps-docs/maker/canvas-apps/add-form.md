---
title: 在画布应用中显示、编辑或添加记录 |Microsoft Docs
description: 使用画布应用窗体显示、编辑或添加数据源中的表记录。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/06/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed7493dcc9c2ef5f0b84052a11dbadb0947af38e
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994194"
---
# <a name="show-edit-or-add-a-record-in-a-canvas-app"></a>在画布应用中显示、编辑或添加记录

在画布应用中，添加和配置 " **[显示](controls/control-form-detail.md)** 窗体" 控件以显示记录中的所有字段，还可以添加和配置 " **[编辑](controls/control-form-detail.md)** 窗体" 控件以编辑记录中的任何字段、添加记录，并将更改保存回数据源。

## <a name="prerequisites"></a>先决条件

- 了解如何在 PowerApps 中[添加和配置控件](add-configure-controls.md)。
- 下载[此 Excel 文件](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)，其中包含本教程的示例数据。
- 将 Excel 文件上传到[云存储帐户](connections/cloud-storage-blob-connections.md)（如 OneDrive for Business）中。
- 为手机创建或打开应用，[将连接添加](add-data-connection.md)到 Excel 文件中的**FlooringEstimates**表。

    可以将窗体添加到平板电脑应用程序，但它不会匹配此主题，因为默认情况下窗体将有三列。

- 如果打开现有应用，请向其[添加一个屏幕](add-screen-context-variables.md)。

## <a name="add-a-form-and-show-data"></a>添加窗体并显示数据
1. 在空白屏幕上，添加 **[下拉](controls/control-drop-down.md)** 控件，并将其命名为**ChooseProduct**。

    > [!NOTE]
   > 如果不确定如何添加控件、重命名控件或设置属性，请参阅[添加和配置控件](add-configure-controls.md)。

1. 在右侧窗格的 "**属性**" 选项卡上，将 "**项**" 设置为 `FlooringEstimates`，将**值**设置为 `Name`。

    ![设置窗体的 Items 属性](./media/add-form/items-property.png)

    此列表显示数据源中地面材料产品的名称。

1. 添加 "**编辑**窗体" 控件，将其移到 " **ChooseProduct**" 下，然后调整窗体的大小以覆盖大部分屏幕。

    ![添加表单](./media/add-form/add-a-form.png)

    > [!NOTE]
   > 本主题介绍 "**编辑**窗体" 控件，但类似的原则适用于 "**显示**窗体" 控件。

1. 将窗体的 **[DataSource](controls/control-form-detail.md)** 属性设置为**FlooringEstimates** ，并将其 **[Item](controls/control-form-detail.md)** 属性设置为以下公式：

    `First(Filter(FlooringEstimates, Name=ChooseProduct.Selected.Value))`

   此公式指定，在配置完窗体后，显示用户在“ChooseProduct”中选择的记录。

1. 在右侧窗格的 "**属性**" 选项卡上，选择 "**编辑字段**"。

    ![编辑字段](./media/add-form/edit-fields.png)

1. 在“字段”窗格中，选择“添加字段”，选中每个字段的复选框，然后选择“添加”。

    ![添加字段](./media/add-form/add-fields.png)

1. 选择 "**添加字段**" 旁边的省略号（...），选择 "**全部折叠**"，然后将 "**名称**" 拖到列表顶部。

    ![移动字段](./media/add-form/move-field.png)

    **编辑**窗体控件反映了您的更改。

    ![显示窗体](./media/add-form/show-form1.png)

## <a name="set-the-card-type-for-a-field"></a>设置字段的卡类型
1. 在 "**字段**" 窗格中，通过选择 "**价格**" 字段，展开其向下箭头。

1. 打开 "**控件类型**" 列表，然后选择 "**编辑滑块**"。

    ![编辑滑块](./media/add-form/edit-slider.png)

    在窗体中，"**价格**" 字段显示**滑块**控件而不是**文本输入**控件。

1. 可有可无按照相同的过程将 "**概述**" 字段的控件更改为 "**编辑多行文本**" 控件。

## <a name="edit-form-only-save-changes"></a>（仅限编辑窗体）保存更改

1. 重命名窗体**EditForm**。

1. 添加“ **[按钮](controls/control-button.md)** ”控件，并将其 **[OnSelect](controls/properties-core.md)** 属性设置为以下公式：

   `SubmitForm(EditForm)`

1. 按 F5 打开预览，更改产品的名称，然后选择所创建的按钮。

    **[SubmitForm](functions/function-form.md)** 函数将更改保存到数据源。

1. 可有可无按 Esc （或选择右上角的关闭图标）关闭预览。

## <a name="next-steps"></a>后续步骤
详细了解如何使用[窗体](working-with-forms.md)和[公式](working-with-formulas.md)。
