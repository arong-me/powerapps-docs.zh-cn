---
title: 添加和配置画布应用控件 | Microsoft Docs
description: 有关直接在“属性”选项卡的工具栏或编辑栏中添加和配置画布应用控件的分步说明。
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 798a355e1c8728b41f3e92f183d4a4e2831b7cc2
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61530247"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>在 PowerApps 中添加和配置画布应用控件

将各种 UI 元素添加到画布应用中，然后直接在“属性”选项卡的工具栏或编辑栏中配置其各方面外观和行为。 这些 UI 元素称为“控件”，配置的各方面外观和行为称为“属性”。

## <a name="prerequisites"></a>先决条件

1. 如果你没有 PowerApps 许可证[注册](../signup-for-powerapps.md)，然后[登录](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
1. 下**使您自己的应用程序**，将鼠标悬停**从空白画布应用**，然后选择**使此应用**。
1. 如果系统提示获取简介教程，请选择**下一步**来熟悉 PowerApps 界面的主要区域 (或选择**跳过**)。

    你可以随时获取教程更高版本通过选择屏幕的右上角附近的问号图标，然后选择**获取简介教程**。

## <a name="add-and-select-a-control"></a>添加并选择一个控件

上**插入**选项卡上，执行以下步骤之一：

- 选择**标签**或**按钮**添加一个这些类型的控件。
- 选择控件、 一个类别，然后选择你想要添加的控件的类型。

例如，选择**新屏幕**，然后选择**空白**将空白屏幕添加到您的应用程序。 （屏幕是控件的一种可以包含其他类型的控件。）

![添加屏幕](./media/add-configure-controls/add-screen.png)

名为新屏幕**Screen2**出现在左侧的导航窗格中。 以便可以轻松地查找和选择的每个控件，此窗格显示应用程序中的控件的层次列表。

![在列表中的屏幕 2](./media/add-configure-controls/list-screen2.png)

若要演示此列表的工作原理，请选择**标签**上**插入**选项卡。新控件将显示下**Screen2**中的层次结构列表。

![在列表中的屏幕 2](./media/add-configure-controls/add-label.png)

在屏幕中，具有六个句柄的框默认情况下会环绕标签。 该类型的框会环绕任何控件处于选中状态。 如果单击或点击它 （以外中标签） 来选择屏幕，框将从标签消失。 若要选择的标签同样，可以单击或点击它，或单击或点击**Label2**中控件的层次结构列表。

> [!IMPORTANT]
> 始终必须选择一个控件，然后才能配置它。

## <a name="rename-a-control"></a>重命名控件

在控件，悬停在想要重命名，该控件的层次结构列表中选择省略号按钮，将出现，然后选择**重命名**。 然后可以键入一个唯一且易记的名称，使构建您的应用程序更容易。

![重命名控件](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>删除控件

在控件，悬停在想要删除，该控件的层次结构列表中选择省略号按钮，将出现，然后选择**删除**。 若要删除的控件不屏幕，你还可以选择在画布上的控件，然后按 Delete 键。

![删除控件](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>重新排列屏幕

在控件的分层列表中，悬停在想要上移或向下，选择省略号按钮显示的屏幕，然后选择**上移**或**向下移动**。

![重新排列屏幕](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> 打开应用时，屏幕顶部的控件的层次结构列表通常会显示第一个。 但您可以通过设置指定不同的屏幕 **[OnStart](controls/control-screen.md)** 属性设置为公式，其中包括 **[Navigate](functions/function-navigate.md)** 函数。

## <a name="move-and-resize-a-control"></a>移动并调整控件的大小

若要将一个控件移动，以便显示四向箭头，选择它，悬停在其中心，然后将控件拖到另一个位置。

![移动控件](./media/add-configure-controls/move-control.png)

调整控件的大小，以便显示双向箭头时，选择它，悬停在任一句柄选择框中，并将句柄。

![移动控件](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> 如本主题稍后所述，还可以移动并调整控件的大小由修改的任意组合其 **[X](controls/properties-size-location.md)**，  **[Y](controls/properties-size-location.md)**， **[高度](controls/properties-size-location.md)**，并 **[宽度](controls/properties-size-location.md)** 在编辑栏中的属性。

## <a name="change-the-text-of-a-label-or-a-button"></a>更改标签或按钮的文本

选择标签或按钮，双击在控件中，显示的文本，然后键入所需的文本。

![更改文本](./media/add-configure-controls/change-text.png)

> [!NOTE]
> 如本主题稍后所述，还可以通过修改来更改此文本及其 **[文本](controls/properties-core.md)** 在编辑栏中的属性。

## <a name="configure-a-control-from-the-toolbar"></a>在工具栏中配置控件

与直接配置控件相比，在工具栏中配置控件可以指定更多不同类型的选项。

例如，你可以选择一个标签，请选择**主页**选项卡，然后将更改该标签中的文本的字体。

![更改字体](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>在“属性”选项卡中配置控件

通过使用**属性**选项卡上，可以指定更广的各种选项不是您可以通过在工具栏中配置控件。

例如，可以选择一个控件，然后显示或隐藏它通过更改其**Visible**属性。

![设置可见性](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>在编辑栏中配置控件

而不是直接、 从工具栏中，或在配置控件**属性**选项卡上，您可以通过在属性列表中选择一个属性，然后在编辑栏中指定一个值配置一个控件。 使用这种方法，可以按字母顺序搜索属性，并能指定更多类型的值。

例如，可以选择一个标签，然后将其配置中通过以下方式：

- 通过选择移动**X**或**Y**在属性列表中，然后在编辑栏中指定一个不同的数字。

    ![设置 X 属性](./media/add-configure-controls/x-property.png)

- 重设其大小通过选择**高度**或**宽度**在属性列表中，然后在编辑栏中指定一个不同的数字。

    ![设置高度属性](./media/add-configure-controls/height-property.png)

- 通过选择更改其文本**文本**在属性列表中，然后在编辑栏中指定的文本字符串、 一个表达式或公式的任意组合。

    - 文字字符串括在引号内，并显示完全按照输入它。 **"Hello，world"** 是文字字符串。

        ![将文本属性设置为文本字符串](./media/add-configure-controls/literal-string.png)

    - 表达式不包括函数和通常基于另一个控件的属性。 **Screen1.Height**是一个表达式，显示的高度**Screen1**。

        ![将文本属性设置为表达式](./media/add-configure-controls/expression.png)

    - 公式包含一个或多个函数。 **现在**函数在您的本地时区，将返回当前日期和时间以及**文本**函数设置值，例如日期、 时间和货币的格式。

        ![将文本属性设置为一个公式](./media/add-configure-controls/formula.png)

        公式是通常比此示例复杂得多，以便它们可以更新数据、 对其进行排序、 筛选它，并执行其他操作。 有关详细信息，请参阅[公式参考](formula-reference.md)。

## <a name="next-steps"></a>后续步骤

- 查找分步操作过程，如配置公共控件[屏幕](add-screen-context-variables.md)，[列出](add-list-box-drop-down-list-radio-button.md)，[库](add-gallery.md)，[窗体](add-form.md)，和[图表](use-line-pie-bar-chart.md)。
- 查找有关每种类型的控件中的参考信息[控制引用](reference-properties.md)。
