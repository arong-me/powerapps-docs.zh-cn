---
title: 添加和配置画布应用控件 | Microsoft Docs
description: 有关直接在“属性”选项卡的工具栏或编辑栏中添加和配置画布应用控件的分步说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b2a2aa1baf93008fa908ca3f73aebfde64c9b239
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680043"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>在 PowerApps 中添加和配置画布应用控件

将各种 UI 元素添加到画布应用中，然后直接在“属性”选项卡的工具栏或编辑栏中配置其各方面外观和行为。 这些 UI 元素称为“控件”，配置的各方面外观和行为称为“属性”。

## <a name="prerequisites"></a>必备组件

1. 如果还没有 Power Apps 许可证，请[注册](../signup-for-powerapps.md)，然后[登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
1. 在 "**制作自己的应用**" 下，将鼠标悬停在**画布应用上，从空白开始**，然后选择 "**生成此应用**"。
1. 如果系统提示你执行简介教程，请选择 "**下一步**" 以熟悉电源应用界面的关键区域（或选择 "**跳过**"）。

    稍后，你可以通过选择屏幕右上角附近的问号图标，然后选择 **"拍摄简介教程**"，来随时学习教程。

## <a name="add-and-select-a-control"></a>添加并选择控件

在 "**插入**" 选项卡上，执行以下步骤之一：

- 选择 "**标签**" 或 "**按钮**" 添加这些类型的控件之一。
- 选择控件的类别，然后选择要添加的控件的类型。

例如，选择 "**新屏幕**"，然后选择 "**空白**"，将空白屏幕添加到应用。 （屏幕是一种可以包含其他类型的控件的控件。）

![添加屏幕](./media/add-configure-controls/add-screen.png)

新屏幕名为 " **Screen2** " 并显示在左侧导航窗格中。 此窗格显示应用程序中控件的层次列表，以便您可以轻松地查找和选择每个控件。

![列表中的 Screen2](./media/add-configure-controls/list-screen2.png)

若要演示此列表的工作方式，请在 "**插入**" 选项卡上选择 "**标签**"。新控件将出现在层次结构列表中的 " **Screen2** " 下。

![列表中的 Screen2](./media/add-configure-controls/add-label.png)

在屏幕中，默认情况下，带有六个图柄的框会环绕标签。 这种类型的 box 环绕选定的任何控件。 如果通过单击或点击（但在标签外）来选择屏幕，则该框将从标签中消失。 若要再次选择该标签，可以单击或点击该标签，也可以在控件的层次结构列表中单击或点击其名称。

> [!IMPORTANT]
> 必须始终选择控件，然后才能对其进行配置。

## <a name="rename-a-control"></a>重命名控件

在控件的层次结构列表中，将鼠标悬停在要重命名的控件上，选择显示的省略号按钮，然后选择 "**重命名**"。 然后，可以键入一个独特的、便于记忆的名称，使应用程序更易于构建。

![重命名控件](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>删除控件

在控件的层次结构列表中，将鼠标悬停在要删除的控件上方，选择显示的省略号按钮，然后选择 "**删除**"。 若要删除不是屏幕的控件，还可以在画布上选择控件，然后按 Delete 键。

![删除控件](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>重新排序屏幕

在控件的层次结构列表中，将鼠标悬停在要上移或下移的屏幕上，选择显示的省略号按钮，然后选择 "**上移**"**或 "下移"** 。

![重新排序屏幕](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> 打开应用后，控件分层列表顶部的屏幕通常会首先出现。 但可以通过将 **[OnStart](controls/control-screen.md)** 属性设置为包含 **[导航](functions/function-navigate.md)** 函数的公式来指定其他屏幕。

## <a name="move-and-resize-a-control"></a>移动控件并调整其大小

若要移动控件，请选择该控件，将鼠标悬停在其中心，以便显示四向箭头，然后将该控件拖动到另一个位置。

![移动控件](./media/add-configure-controls/move-control.png)

若要调整控件大小，请选择该控件，将鼠标悬停在选择框中的任何控点上，使双向箭头显示，然后拖动控点。

![移动控件](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> 如本主题后面所述，还可以通过修改公式栏中的 " **[X](controls/properties-size-location.md)** "、" **[Y](controls/properties-size-location.md)** "、" **[高度](controls/properties-size-location.md)** " 和 " **[宽度](controls/properties-size-location.md)** " 属性的任意组合来移动控件并调整其大小。

## <a name="change-the-text-of-a-label-or-a-button"></a>更改标签或按钮的文本

选择标签或按钮，双击控件中显示的文本，然后键入所需的文本。

![更改文本](./media/add-configure-controls/change-text.png)

> [!NOTE]
> 如本主题后面所述，还可以通过修改公式栏中的 **[文本](controls/properties-core.md)** 属性来更改此文本。

## <a name="configure-a-control-from-the-toolbar"></a>在工具栏中配置控件

与直接配置控件相比，在工具栏中配置控件可以指定更多不同类型的选项。

例如，您可以选择标签，选择 "**主页**" 选项卡，然后更改标签中文本的字体。

![更改字体](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>在“属性”选项卡中配置控件

通过使用 "**属性**" 选项卡，您可以通过从工具栏配置控件来指定范围更多的选项。

例如，您可以选择一个控件，然后通过更改其**Visible**属性来显示或隐藏该控件。

![设置可见性](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>在编辑栏中配置控件

您可以通过在 "属性" 列表中选择一个属性，然后在编辑栏中指定一个值，来配置控件，而不是直接在工具栏或 "**属性**" 选项卡中配置控件。 使用这种方法，可以按字母顺序搜索属性，并能指定更多类型的值。

例如，你可以选择一个标签，然后通过以下方式对其进行配置：

- 通过选择 "属性" 列表中的 " **X** " 或 " **Y** "，然后在编辑栏中指定其他数字来移动它。

    ![设置 X 属性](./media/add-configure-controls/x-property.png)

- 通过选择 "属性" 列表中的 "**高度**" 或 "**宽度**"，然后在编辑栏中指定其他数字来调整其大小。

    ![设置高度属性](./media/add-configure-controls/height-property.png)

- 通过选择 "属性" 列表中的 "**文本**"，然后在编辑栏中指定文本字符串、表达式或公式的任意组合来更改其文本。

    - 文本字符串用引号括起来，并在您键入时完全显示。 **"Hello，world"** 是文本字符串。

        ![将 Text 属性设置为文本字符串](./media/add-configure-controls/literal-string.png)

    - 表达式不包含函数，并且通常基于另一个控件的属性。 **Screen1**是显示**Screen1**高度的表达式。

        ![将 Text 属性设置为表达式](./media/add-configure-controls/expression.png)

    - 公式包括一个或多个函数。 **Now**函数返回本地时区的当前日期和时间，而**Text**函数对日期、时间和货币等值进行格式设置。

        ![将 Text 属性设置为公式](./media/add-configure-controls/formula.png)

        公式通常比此示例复杂得多，因此，它们可以更新数据、对数据进行排序、筛选和执行其他操作。 有关详细信息，请参阅[公式参考](formula-reference.md)。

## <a name="next-steps"></a>后续步骤

- 查找配置常见控件（如[屏幕](add-screen-context-variables.md)、[列表](add-list-box-drop-down-list-radio-button.md)、[库](add-gallery.md)、[窗体](add-form.md)和[图表](use-line-pie-bar-chart.md)）的分步过程。
- 查找有关[控件引用](reference-properties.md)中每种类型的控件的引用信息。
