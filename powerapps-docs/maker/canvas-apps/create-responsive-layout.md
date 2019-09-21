---
title: 在画布应用中创建响应式布局 |Microsoft Docs
description: 有关配置画布应用中控件的高度、宽度、X 和 Y 属性的参考信息
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm-msft
ms.date: 9/20/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: eee82691b288f21749fe58adbf02ab5ffc3bd8b4
ms.sourcegitcommit: 7016ff837eff2cb0985fc71edab95cbf99335677
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "71159860"
---
# <a name="create-responsive-layouts-in-canvas-apps"></a>在画布应用中创建响应式布局

在 PowerApps 中生成画布应用之前，请指定是否为手机或平板电脑定制应用。 此选择确定要在其上生成应用的画布的大小和形状。

做出此选择后，如果选择 "**文件** > " "**应用设置** > " "**屏幕大小**" 和 "方向"，则可以进行更多的选择。 可以选择 "纵向" 或 "横向" 或 "屏幕大小" （仅限平板电脑）。 还可以锁定或解锁纵横比，并支持设备旋转（或不支持设备旋转）。

当您设计屏幕布局时，这些选择将以您的所有其他选择为基础。 如果你的应用程序在不同大小的设备上运行，或者在 web 上运行，则整个布局会缩放以适应应用运行的屏幕。 例如，如果为手机设计的应用在大浏览器窗口中运行，则该应用会进行伸缩，使其空间看起来过大。 应用程序无法通过显示更多控件或更多内容来利用其他像素。

如果创建响应式布局，控件可以响应不同的设备或窗口大小，使得各种体验感觉更自然。 若要实现响应式布局，请调整某些设置并在应用程序中编写表达式。 

## <a name="disable-scale-to-fit"></a>禁用缩放以适合

可以配置每个屏幕，使其布局适应应用运行时的实际空间。

通过关闭应用的 "**缩放到合适大小**" 设置来激活响应能力，默认情况下启用该设置。 关闭此设置后，还会关闭**锁定纵横比**，因为你不再设计特定屏幕形状。 （你仍可以指定你的应用程序是否支持设备旋转。）

![禁用缩放以适合设置](media/create-responsive-layout/scale-to-fit-off.png)

若要使应用程序保持响应状态，必须执行额外的步骤，但这种更改是实现响应能力的第一步。

## <a name="understand-app-and-screen-dimensions"></a>了解应用和屏幕尺寸

若要使应用的布局响应屏幕尺寸的变化，需编写使用屏幕的 "**宽度**" 和 "**高度**" 属性的公式。 若要显示这些属性，请在 PowerApps Studio 中打开应用程序，然后选择屏幕。 这些属性的默认公式显示在右侧窗格的 "**高级**" 选项卡上。

**Width** = `Max(App.Width, App.DesignWidth)`

**高** = `Max(App.Height, App.DesignHeight)`

这些公式引用应用的**Width**、 **Height**、 **DesignWidth**和**DesignHeight**属性。 应用的**宽度**和**高度**属性对应于运行应用的设备或浏览器窗口的尺寸。 如果用户调整浏览器窗口的大小（或在关闭**锁定方向**时旋转设备），则这些属性的值将动态更改。 当这些值改变时，屏幕的**宽度**和**高度**属性中的公式会重新计算。

**DesignWidth**和**DesignHeight**属性来自于你在 "**应用设置**" 的 "**屏幕大小**" 和 "方向" 窗格中指定的维度。 例如，如果选择纵向的手机布局，则**DesignWidth**为640， **DesignHeight**为1136。

在屏幕的**宽度**和**高度**属性的公式中使用时，可以将**DesignWidth**和**DesignHeight**视为要为其设计应用的最小尺寸。 如果你的应用程序可用的实际区域甚至小于这些最小维度，则屏幕的 "**宽度**" 和 "**高度**" 属性的公式将确保它们的值不会成为最小值。 在这种情况下，用户必须滚动以查看屏幕的所有内容。

建立应用的**DesignWidth**和**DesignHeight**后，你将不会（在大多数情况下）需要更改每个屏幕的**宽度**和**高度**属性的默认公式。 稍后，本主题将讨论可能需要自定义这些公式的情况。

## <a name="use-formulas-for-dynamic-layout"></a>将公式用于动态布局

若要创建响应式设计，可使用公式而不是绝对（恒定）坐标值来查找和调整每个控件的大小。 这些公式表示每个控件的位置和大小，并以整体屏幕大小或相对于屏幕上其他控件的方式表示。

> [!IMPORTANT]
> 为控件的**X**、 **Y**、**宽度**和**高度**属性编写公式后，如果随后在画布编辑器中拖动该控件，则将使用常量值覆盖公式。 当你开始使用公式来实现动态布局时，应避免拖动控件。

在最简单的情况下，一个控件会填充整个屏幕。 若要创建此效果，请将控件的属性设置为以下值：

| 属性      | Value            |
|--------|---------------|
| **X-BLADE**      | `0`             |
| **误差**      | `0`             |
| **宽度**  | `Parent.Width`  |
| **高** | `Parent.Height` |

这些公式使用**父**运算符。 对于直接放置在屏幕上的控件，**父级**指的是屏幕。 对于这些属性值，控件显示在屏幕的左上角（0，0），并且具有与屏幕相同的**宽度**和**高度**。

稍后在本主题中，你将应用这些原则（和**父**运算符），将控件放置在其他容器（如库、组控件和组件）中。

作为替代方法，控件只能填写屏幕的上半部分。 若要创建此效果，请将**height**属性设置为**Parent** /2，并使其他公式保持不变。

如果您想要使用另一个控件来填充同一屏幕的下半部分，则可以至少使用两种方法来构造其公式。 为简单起见，可以采用以下方法：

| 控件 | 属性 | 公式           |
|-|----------|-------------------|
| **左上** | **X-BLADE**        | `0`                 |
| **左上** | **误差**        | `0`                 |
| **左上** | **宽度**    | `Parent.Width`      |
| **左上** | **高**   | `Parent.Height / 2` |
| **下移** | **X-BLADE**        | `0`                 |
| **下移** | **误差**        | `Parent.Height / 2` |
| **下移** | **宽度**    | `Parent.Width`      |
| **下移** | **高**   | `Parent.Height / 2` |

![上部和下部控件](media/create-responsive-layout/dynamic-layout.png)

此配置将实现所需的效果，但如果您对控件的相对大小改变主意，则需要编辑每个公式。 例如，你可能会决定顶部控件应仅占用屏幕的顶部-第三个，而底部控件填充了下三分之二。 

若要创建该效果，您需要更新**上部**控件**的 Height**属性和**下限**的**Y**和**Height**属性。 相反，请考虑在**上部**控件（和其自身）的情况下编写**低**控件的公式，如以下示例中所示：


| 控件 | 属性 | 公式           |
|-|----------|-------------------|
| **左上** | **X-BLADE**        | `0`                 |
| **左上** | **误差**        | `0`                 |
| **左上** | **宽度**    | `Parent.Width`      |
| **左上** | **高**   | `Parent.Height / 2` |
| **下移** | **X-BLADE**        | `0`                       |
| **下移** | **误差**        | `Upper.Y + Upper.Height`  |
| **下移** | **宽度**    | `Parent.Width`            |
| **下移** | **高**   | `Parent.Height - Lower.Y` |

![上限和下限控件相对大小](media/create-responsive-layout/dynamic-layout2.png)

准备好这些公式后，只需更改**上部**控件的**height**属性即可表示屏幕高度的不同部分。 **下半**部分控件会自动移动，并调整大小以进行更改。

您可以使用这些公式模式来表示名为**C**的控件及其父控件或同级控件（名为**D**）之间的公共布局关系。

| C 及其父项之间的关系 | 属性 | 公式 | 图 |
|--|--|--|--|
| **C**填充父级的宽度，边距为*N* | **X-BLADE**| `N` | ![父项的 C 填充宽度的示例](media/create-responsive-layout/c1.png) |
|  | **宽度** | `Parent.Width - (N * 2)` |  |
| **C**填充父级的高度，边距为*N* | **误差** | `N` | ![父项的 C 填充高度示例](media/create-responsive-layout/c2.png) |
|  | **高** | `Parent.Height - (N * 2)` |  |
| **C**与父级的右边缘对齐，边距为*N* | **X-BLADE** | `Parent.Width - (C.Width + N)` | ![C 的示例与父级的边缘对齐](media/create-responsive-layout/c3.png) |
| 与父级的下边缘对齐的**C** ，边距为*N* | **误差** | `Parent.Height - (C.Height + N)` | ![C 的示例与父级的边缘对齐](media/create-responsive-layout/c4.png) |
| **C**水平居中在父级上 | **X-BLADE** | `(Parent.Width - C.Width) / 2` | ![父项上水平居中的 C 示例](media/create-responsive-layout/c5.png) |
| **C**垂直居中于父项 | **误差** | `(Parent.Height - C.Height) / 2` | ![在父级上垂直居中的 C 示例](media/create-responsive-layout/c6.png) |

| C 和 D 之间的关系 | 属性 | 公式 | 图 |
|--|--|--|--|
| **C**与 d 水平对齐 **，与** **d**的宽度相同 | **X-BLADE** | `D.X` | ![模式示例](media/create-responsive-layout/d1.png) |
|  | **宽度**    | `D.Width` |  |
| **C** **与 d 垂直**对齐，与**d**具有相同高度  | **误差** | `D.Y` | ![模式示例](media/create-responsive-layout/d2.png) |
|  | **高** | `D.Height` |  |
| **C**右边缘与**D**的右边缘对齐 | **X-BLADE** | `D.X + D.Width - C.Width` | ![模式示例](media/create-responsive-layout/d3.png) |
| **C**的下边缘与**D**的下边缘对齐 | **误差** | `D.Y + D.Height - C.Height` | ![模式示例](media/create-responsive-layout/d4.png) |
| **C**相对于**D**水平居中居中 | **X-BLADE** | `D.X + (D.Width - C.Width) / 2`  | ![模式示例](media/create-responsive-layout/d5.png) |
| 垂直**居中相对**于**D** | **误差** | `D.Y + (D.Height - C.Height) /2` | ![模式示例](media/create-responsive-layout/d6.png) |
| **C**位于**2**的右侧，间隙为 N | **X-BLADE** | `D.X + D.Width + N` | ![模式示例](media/create-responsive-layout/d7.png) |
| **C**位于**D**下，间隙为*N*             | **误差** | `D.Y + D.Height + N` | ![模式示例](media/create-responsive-layout/d8.png) |
| **C**填充父对象的**D**和右边缘之间的空间 | **X-BLADE** | `D.X + D.Width` | ![模式示例](media/create-responsive-layout/d9.png) |
|  | **宽度** | `Parent.Width - C.X` |  |
| **C**填充父级的**D**和下边缘之间的空间 | Y | `D.Y + D.Height` | ![模式示例](media/create-responsive-layout/d10.png) |

## <a name="hierarchical-layout"></a>分层布局

在构造包含更多控件的屏幕时，相对于父控件（而不是相对于屏幕或同级控件）定位控件更方便（甚至需要这样做）。 通过将控件组织到层次结构中，可以使公式更易于编写和维护。

### <a name="galleries"></a>协调性

如果在应用中使用库，则需要在库的模板中布局控件。 您可以通过编写使用**父**运算符（将引用库模板）的公式来定位这些控件。 在库模板中的控件的公式中，使用**TemplateHeight**和**TemplateWidth**属性;不要使用**父. width**和**parent**，这是指库的总体大小。

![显示模板宽度和高度的垂直库](media/create-responsive-layout/gallery-vertical.png)

### <a name="container-control"></a>容器控件

可以将实验性功能（**容器**控件）用作父控件。 若要启用此功能，请选择 "**文件** > " "**应用设置** > " "**高级设置**"。

请考虑屏幕顶部标题的示例。 有一个标题，其中包含一个标题和多个图标，用户可以通过它们进行交互。 可以使用**容器**控件构造此类标头，其中包含一个 "**标签**" 控件和两个**图标**控件：

![使用组的标头示例](media/create-responsive-layout/header-group.png)

将这些控件的属性设置为以下值：

| 属性 | 标题 | 下拉菜单 | 封闭 | 标题 |
|--|--|--|--|--|
| **X-BLADE** | `0`  | `0` | `Parent.Width - Close.Width` | `Menu.X + Menu.Width` |
| **误差** | `0` | `0` | `0` | `0` |
| **宽度**  | `Parent.Width` | `Parent.Height` | `Parent.Height` | `Close.X - Title.X` |
| **高** | `64` | `Parent.Height` | `Parent.Height` | `Parent.Height` |

对于**标头**控件， `Parent`指的是屏幕。 对于其他，请`Parent`参考**标头**控件。

编写这些公式后，您可以通过更改**标题**控件的属性的公式来调整其大小或位置。 子控件的大小和位置将自动进行相应调整。

### <a name="components"></a>组分

如果使用名为 "组件" 的另一个实验功能，则可以构造构建基块并在应用程序中重复使用它们。 与**容器**控件一样，在组件中放置的控件应基于`Parent.Width`和`Parent.Height`中的位置和大小公式，这是指组件的大小。 详细信息：[创建组件](create-component.md)。

## <a name="adapting-layout-for-device-size-and-orientation"></a>调整设备大小和方向布局

到目前为止，您已经学习了如何使用公式来更改每个控件的大小以响应可用空间，同时使控件彼此保持一致。 但你可能希望或需要进行更多的布局更改，以响应不同的设备大小和方向。 例如，当设备从纵向旋转到横向方向时，可能需要从垂直布局切换到水平布局。 在较大的设备上，可以提供更多内容或对其进行重新排列，以提供更具吸引力的布局。 在较小的设备上，可能需要跨多个屏幕拆分内容。

### <a name="device-orientation"></a>设备方向

如前面所述，屏幕的 "**宽度**" 和 "**高度**" 属性的默认公式，如果用户要旋转设备，则不一定能提供良好的体验。 例如，为纵向电话设计的应用程序的**DesignWidth**为640， **DesignHeight**为1136。 在同一手机上，同一应用的横向方向将具有以下属性值：

- 屏幕的**Width**属性设置为`Max(App.Width, App.DesignWidth)`。 应用的**宽度**（1136）大于其**DesignWidth** （640），因此公式的计算结果为1136。
- 屏幕的 "**高度**" 属性设置为`Max(App.Height, App.DesignHeight)`。 应用的**高度**（640）小于其**DesignHeight** （1136），因此公式的计算结果为1136。

如果屏幕**高度**为1136，并且设备高度（方向）为640，则用户必须垂直滚动屏幕以显示其所有内容，这可能不是你所需的体验。

若要将屏幕的**宽度**和**高度**属性调整到设备方向，可以使用以下公式：

**Width** = `Max(App.Width, If(App.Width < App.Height, App.DesignWidth, App.DesignHeight))`

**高** = `Max(App.Height, If(App.Width < App.Height, App.DesignHeight, App.DesignWidth))`

这些公式根据设备的宽度是否小于其高度（纵向）或超出其高度（横向）来交换应用的**DesignWidth**和**DesignHeight**值。

调整屏幕的**宽度**和**高度**公式后，你可能还需要重新排列屏幕中的控件以更好地使用可用空间。 例如，如果两个控件中的每个控件都占据了一半的屏幕，则可以纵向堆叠它们，但将它们并排排列。

您可以使用屏幕的 "**方向**" 属性来确定屏幕的方向是垂直还是水平。

> [!NOTE]
> 在横向方向上，**上下**控件**显示为左右控件。**

| 控件 | 属性 | 公式 |
|--|----------|---|
| **左上** | **X-BLADE** | `0` |
| **左上** | **误差** | `0` |
| **左上** | **宽度** | `If(Parent.Orientation = Layout.Vertical, Parent.Width, Parent.Width / 2)` |
| **左上** | **高**   | `If(Parent.Orientation = Layout.Vertical, Parent.Height / 2, Parent.Height)` |
| **下移** | X | `If(Parent.Orientation = Layout.Vertical, 0, Upper.X + Upper.Width)`  |
| **下移** | Y | `If(Parent.Orientation = Layout.Vertical, Upper.Y + Upper.Height, 0)` |
| **下移** | **宽度** | `Parent.Width - Lower.X` |
| **下移** | **高** | `Parent.Height - Lower.Y` |

![用于调整纵向方向的表达式](media/create-responsive-layout/portrait.png)

![用于调整横向方向的表达式](media/create-responsive-layout/landscape.png)

### <a name="screen-sizes-and-breakpoints"></a>屏幕大小和断点

你可以根据设备大小调整布局。 屏幕的 " **Size** " 属性将当前设备大小分类。 大小为正整数;ScreenSize 类型提供了可帮助提高可读性的命名常量。 下表列出了常量：

| 常量              | Value | 典型设备类型（使用默认应用设置） |
|-----------------------|-------|--------------------------------------------------|
| ScreenSize      | 1     | 移动                                            |
| ScreenSize     | 2     | Tablet，垂直保留                          |
| ScreenSize      | 3     | Tablet，水平按住                        |
| ScreenSize. 超大型 | 4     | 台式计算机                                 |

使用这些大小来确定应用程序的布局。 例如，如果希望控件在手机大小的设备上隐藏，但却可见，则可以将控件的**visible**属性设置为以下公式：

`Parent.Size >= ScreenSize.Medium`

当大小为 "中" 或 "大" 时，此公式的计算结果为**true** ; 否则为**false** 。

如果希望控件根据屏幕大小占用不同的屏幕宽度比例，请将控件的**width**属性设置为以下公式：

```powerapps-dot
Parent.Width *  
    Switch(Parent.Size,  
        ScreenSize.Small, 0.5,  
        ScreenSize.Medium, 0.3,  
        0.25)
```
此公式将控件的宽度设置为屏幕宽度的一半（在屏幕上显示为屏幕宽度的一半），将屏幕宽度设置为在所有其他屏幕上以屏幕宽度的四分之一。

## <a name="custom-breakpoints"></a>自定义断点

屏幕的**大小**属性是通过将屏幕的**Width**属性与应用的**SizeBreakpoints**属性中的值进行比较来计算的。 此属性是一个单列表数字表，用于指示分隔命名屏幕大小的宽度断点：

在为平板电脑或 web 创建的应用中，应用的**SizeBreakpoints**属性中的默认值为 **[600，900，1200]** 。 在为手机创建的应用中，该值为 **[1200，1800，2400]** 。 （由于此类应用使用的坐标有效地翻倍了其他应用中使用的坐标，因此电话应用程序的值会加倍。）

![SizeBreakpoints 属性的默认值](media/create-responsive-layout/default-breakpoints.png)

可以通过更改应用的**SizeBreakpoints**属性中的值来自定义应用的断点。 在树视图中选择 "**应用**"，在属性列表中选择 " **SizeBreakpoints** "，然后在编辑栏中编辑这些值。 您可以根据应用程序的需要创建任意数量的断点，但仅大小为1到4的相对于命名屏幕大小。 在公式中，可以按超大型的数值（5、6等）来引用大小。

还可以指定较少的断点。 例如，你的应用程序可能只需要三个大小（两个断点），因此可能的屏幕大小为小、中和大。

## <a name="known-limitations"></a>已知的限制

创作画布不响应创建的大小调整公式。 若要测试响应行为，请保存并发布你的应用，然后在设备上或在不同大小和方向的浏览器窗口中打开它。

如果在控件的**X**、 **Y**、**宽度**和**高度**属性中编写表达式或公式，以后将控件拖到其他位置或通过拖动调整控件大小，则会覆盖这些表达式或公式边框。
