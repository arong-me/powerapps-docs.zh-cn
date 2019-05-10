---
title: 画布应用中创建响应式布局 |Microsoft Docs
description: 有关配置上的画布应用中的控件的高度、 宽度、 X 和 Y 属性的参考信息
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: af07bcb7b343a14f6342c53ed2e083e214a12368
ms.sourcegitcommit: b27a5206f8c7b4b4c1bcca814a1f7c32724c1fcf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65206384"
---
# <a name="create-responsive-layouts-in-canvas-apps"></a>画布应用中创建响应式布局

生成画布应用在 PowerApps 中的之前，指定是否定制为手机或平板电脑应用。 选择此选项确定大小和形状的画布将在其构建您的应用程序。

做出此决定后，你可以进行少量的更多选择，如果选择**文件** > **应用设置** > **屏幕大小和方向**。 可以选择纵向或横向方向和屏幕的大小 （仅适用于平板电脑）。 此外可以锁定或解锁纵横比和 （或不） 支持设备旋转。

这些选择基础作为设计屏幕布局所做的每种其他选择。 如果您的应用程序运行在不同大小的设备上或在 web 上找到，整个布局可以进行扩展以适合运行该应用屏幕的大小。 如果在一个大型的浏览器窗口中运行专为手机设计的应用，例如，应用可进行缩放以补偿，并查找其空间过大。 应用程序不能通过显示更多控件或更多的内容来充分利用其他像素。

如果您创建响应式布局，控件可以响应不同的设备或窗口大小，使各种体验感觉更自然。 若要实现响应式布局，调整一些设置，并在整个应用中编写表达式。 

## <a name="disable-scale-to-fit"></a>禁用缩放以适合

你可以配置每个屏幕，以便其布局可适应应用程序正在其中运行的实际空间。

通过关闭应用程序的激活响应能力**缩放以适合**设置，默认情况下。 当你关闭此设置时，您还将关闭**锁定纵横比**因为您不再对特定屏幕形状设计。 （您仍可以指定您的应用程序是否支持设备旋转。）

![禁用缩放以适应的设置](media/create-responsive-layout/scale-to-fit-off.png)

若要使应用能够响应，必须执行其他步骤，但此更改使响应能力可能的第一步。

## <a name="understand-app-and-screen-dimensions"></a>了解应用程序和屏幕尺寸

若要使应用程序的布局响应中的屏幕尺寸的更改，你将编写使用的公式**宽度**并**高度**屏蔽的属性。 若要显示这些属性，在 PowerApps Studio 中打开应用，然后选择屏幕。 在显示这些属性的默认公式**高级**的右侧窗格的选项卡。

**Width** = `Max(App.Width, App.DesignWidth)`

**Height** = `Max(App.Height, App.DesignHeight)`

这些公式中引用**宽度**，**高度**， **DesignWidth**，以及**DesignHeight**应用属性。 应用程序的**宽度**并**高度**属性对应于在其中运行您的应用程序的设备或浏览器窗口的尺寸。 如果在用户调整浏览器窗口 (或旋转设备，如果已关闭**锁定方向**)，这些属性的值动态更改。 在屏幕中的公式**宽度**并**高度**重新评估属性，这些值更改时。

**DesignWidth**并**DesignHeight**属性来自于你在中指定的尺寸**屏幕大小和方向**窗格**应用设置**. 例如，如果选择手机布局纵向**DesignWidth** 640 个，并**DesignHeight**是 1136年。

因为它们在屏幕的公式中使用**宽度**并**高度**属性，您可以看作**DesignWidth**并**DesignHeight**作为将为其设计应用的最小尺寸。 如果提供给您的应用程序的实际区域甚至比这些最小小的维度，在屏幕的公式**宽度**并**高度**属性确保它们的值不会变得不小于最小值。 在这种情况下，用户必须滚动以查看所有屏幕的内容。

建立应用的后**DesignWidth**并**DesignHeight**，不会 （在大多数情况下） 需要更改每个屏幕的默认公式**宽度**和**高度**属性。 更高版本，本主题讨论在其中你可能想要自定义这些公式的情况。

## <a name="use-formulas-for-dynamic-layout"></a>使用公式进行动态布局

若要创建响应式设计，找到并调整每个控件的大小而不是绝对的 （固定） 坐标值中使用公式。 这些公式 express 每个控件的位置和大小方面的总体屏幕大小或相对于其他控件在屏幕上。

> [!IMPORTANT]
> 您编写的公式后**X**， **Y**，**宽度**并**高度**控件的属性，你的公式将被覆盖如果你随后将该控件在画布编辑器中的常量值。 当你开始使用公式来实现动态布局时，应避免拖动控件。

在简单的情况下，一个控件将填充整个屏幕。 若要创建这种效果，请对这些值设置控件的属性：

| 属性      | Value            |
|--------|---------------|
| **X**      | `0`             |
| **Y**      | `0`             |
| **Width**  | `Parent.Width`  |
| **Height** | `Parent.Height` |

这些公式使用**父**运算符。 直接在屏幕上放置的控件**父**指的是屏幕。 这些属性值，该控件显示在屏幕 （0，0） 的左上角与具有相同**宽度**并**高度**作为屏幕。

稍后在本主题中，您将应用这些原则 (和**父**运算符) 若要如库放置在其他容器内的控件，组控件和组件。

作为替代方法，该控件可以填充仅在屏幕的上半。 若要创建这种效果，请设置**高度**属性设置为**Parent.Height** / 2，并将保持不变的其他公式。

如果你想要在同一个屏幕的下半部分填充底部的第二个控件，您可能需要至少两种其他方法构造其公式。 为简单起见，可以采用此方法：

| 控件 | 属性 | 公式           |
|-|----------|-------------------|
| **Upper** | **X**        | `0`                 |
| **Upper** | **Y**        | `0`                 |
| **Upper** | **Width**    | `Parent.Width`      |
| **Upper** | **Height**   | `Parent.Height / 2` |
| **较低** | **X**        | `0`                 |
| **较低** | **Y**        | `Parent.Height / 2` |
| **较低** | **Width**    | `Parent.Width`      |
| **较低** | **Height**   | `Parent.Height / 2` |

![上限，并降低控件](media/create-responsive-layout/dynamic-layout.png)

此配置会达到所需的效果，但您需要编辑每个公式，如果您改变了主意有关控件的相对大小。 例如，可能会决定顶部的控件应使用底部控件填充较低的三分之二占用仅顶部有三分之一的屏幕。 

若要创建该效果，您需要更新**高度**的属性**上部**控件和**Y**并**高度**的属性**较低**控件。 相反，应考虑编写的公式**较低**的控制**上部**控件 （和本身），如本例所示：


| 控件 | 属性 | 公式           |
|-|----------|-------------------|
| **Upper** | **X**        | `0`                 |
| **Upper** | **Y**        | `0`                 |
| **Upper** | **Width**    | `Parent.Width`      |
| **Upper** | **Height**   | `Parent.Height / 2` |
| **较低** | **X**        | `0`                       |
| **较低** | **Y**        | `Upper.Y + Upper.Height`  |
| **较低** | **Width**    | `Parent.Width`            |
| **较低** | **Height**   | `Parent.Height - Lower.Y` |

![上部和较低的控件相对大小调整](media/create-responsive-layout/dynamic-layout2.png)

使用这些位置中的公式，您需要仅更改**高度**的属性**上部**控件来表达的屏幕的高度不同部分。 **较低**控制自动移动和调整大小以考虑了更改。

您可以使用这些公式模式用于表示名为的控件之间的常见布局关系**C**，和其父级或同级控件，名为**D**。

| C 及其父级之间的关系 | 属性 | 公式 | 图 |
|--|--|--|--|
| **C**填充的边距宽度的父代、 *N* | **X**| `N` | ![C 的父级的填充宽度的示例](media/create-responsive-layout/c1.png) |
|  | **Width** | `Parent.Width - (N * 2)` |  |
| **C**边距为填充的父代、 高度*N* | **Y** | `N` | ![C 的父填充高度的示例](media/create-responsive-layout/c2.png) |
|  | **Height** | `Parent.Height - (N * 2)` |  |
| **C**与父代、 右边缘与距对齐*N* | **X** | `Parent.Width - (C.Width + N)` | ![C 与父项的边缘对齐的示例](media/create-responsive-layout/c3.png) |
| **C**与父代、 下边缘与距对齐*N* | **Y** | `Parent.Height - (C.Height + N)` | ![C 与父项的边缘对齐的示例](media/create-responsive-layout/c4.png) |
| **C**父水平居中 | **X** | `(Parent.Width - C.Width) / 2` | ![父级上水平居中的 C 示例](media/create-responsive-layout/c5.png) |
| **C**父垂直居中 | **Y** | `(Parent.Height - C.Height) / 2` | ![在父垂直居中位置 C 的示例](media/create-responsive-layout/c6.png) |

| C 和 D 之间的关系 | 属性 | 公式 | 图 |
|--|--|--|--|
| **C**与水平对齐**D**和宽度相同**D** | **X** | `D.X` | ![模式的示例](media/create-responsive-layout/d1.png) |
|  | **Width**    | `D.Width` |  |
| **C**与垂直对齐**D**和相同的高度**D**  | **Y** | `D.Y` | ![模式的示例](media/create-responsive-layout/d2.png) |
|  | **Height** | `D.Height` |  |
| 边缘**C**的右边缘对齐**D** | **X** | `D.X + D.Width - C.Width` | ![模式的示例](media/create-responsive-layout/d3.png) |
| 底端对齐边缘**C**的下边缘对齐**D** | **Y** | `D.Y + D.Height - C.Height` | ![模式的示例](media/create-responsive-layout/d4.png) |
| **C**相对于水平居中**D** | **X** | `D.X + (D.Width - C.Width) / 2`  | ![模式的示例](media/create-responsive-layout/d5.png) |
| **C**相对于垂直居中**D** | **Y** | `D.Y + (D.Height - C.Height) /2` | ![模式的示例](media/create-responsive-layout/d6.png) |
| **C**定位到右侧**D**与 N 的间隔 | **X** | `D.X + D.Width + N` | ![模式的示例](media/create-responsive-layout/d7.png) |
| **C**之下**D**的间隙较*N*             | **Y** | `D.Y + D.Height + N` | ![模式的示例](media/create-responsive-layout/d8.png) |
| **C**填充之间的空间**D**和右边缘的父级 | **X** | `D.X + D.Width` | ![模式的示例](media/create-responsive-layout/d9.png) |
|  | **Width** | `Parent.Width - C.X` |  |
| **C**填充之间的空间**D**边距和下边缘的父级 | Y | `D.Y + D.Height` | ![模式的示例](media/create-responsive-layout/d10.png) |

## <a name="hierarchical-layout"></a>层次结构布局

在构造屏幕，其中包含更多控件，它将成为更方便 （或甚至有必要） 来定位控件相对于父控件，而不是相对于屏幕或同级控件。 通过将您的控件组织成层次结构，可以使易于编写和维护你的公式。

### <a name="galleries"></a>库

如果应用程序中使用库，你将需要库的模板中的控件进行布局。 您可以使用的编写公式来定位这些控件**父**运算符，将引用的库模板。 在库模板中的控件上的公式，使用**Parent.TemplateHeight**并**Parent.TemplateWidth**属性，不使用**Parent.Width**和**Parent.Height**，表示库的总体大小。

![显示模板宽度和高度的垂直库](media/create-responsive-layout/gallery-vertical.png)

### <a name="enhanced-group-control"></a>增强组控件

可以使用试验性功能，增强**组**控件，作为父控件。 若要启用此功能，请选择**文件** > **应用设置** > **高级设置**。

请考虑在屏幕顶部的标头的示例。 它是常见的具有标题和你的用户可与之交互的几个图标的标头。 您可以构造使用增强的此类标头**组**控件，其中包含**标签**控件和两个**图标**控件：

![使用组的标头示例](media/create-responsive-layout/header-group.png)

这些控件的属性设置为这些值：

| 属性 | 标题 | 菜单 | 关闭 | 标题 |
|--|--|--|--|--|
| **X** | `0`  | `0` | `Parent.Width - Close.Width` | `Menu.X + Menu.Width` |
| **Y** | `0` | `0` | `0` | `0` |
| **Width**  | `Parent.Width` | `Parent.Height` | `Parent.Height` | `Close.X - Title.X` |
| **Height** | `64` | `Parent.Height` | `Parent.Height` | `Parent.Height` |

有关**标头**控件，`Parent`指的是屏幕。 对于其他操作系统，`Parent`是指**标头**控件。

编写这些公式后，可以调整大小或位置**标头**控件通过更改其属性的公式。 相应地将自动调整大小和位置的子控件。

### <a name="components"></a>组件

如果使用另一个实验性功能，名为组件，可以构造构建基块，并重复使用它们在整个应用。 如同**组**控件，组件内放置的控件应使其位置和大小的公式，基于`Parent.Width`和`Parent.Height`，表示组件的大小。 详细信息：[创建组件](create-component.md)。

## <a name="adapting-layout-for-device-size-and-orientation"></a>调整设备的大小和方向的布局

到目前为止，您已经学习了如何使用公式来更改每个控件的大小，以响应的可用空间，同时保持控件相对于彼此对齐。 但是，您可能希望或需要响应不同设备的大小和方向进行布局的重大更改。 当设备从纵向向横向方向旋转时，例如，你可能想要从垂直布局，切换到水平。 在更大的设备，可以提供更多的内容或重新排列以提供更大的吸引力的布局。 在较小设备上，可能需要多个屏幕之间进行拆分的内容。

### <a name="device-orientation"></a>设备方向

屏幕的默认公式**宽度**并**高度**属性，为本主题之前所述，将不一定提供良好的体验如果用户旋转设备。 例如，适用于纵向 phone 设计的应用具有**DesignWidth** 640 的和一个**DesignHeight** 1136年。 上一部手机横向方向的相同应用程序将具有以下属性值：

- 在屏幕**宽度**属性设置为`Max(App.Width, App.DesignWidth)`。 应用程序的**宽度**(1136) 大于其**DesignWidth** (640)，因此该公式计算结果为 1136年。
- 在屏幕**高度**属性设置为`Max(App.Height, App.DesignHeight)`。 应用程序的**高度**(640) 小于其**DesignHeight** (1136)，因此该公式计算结果为 1136年。

一个屏幕**高度**的 1136年 640 设备高度 （以此方向），用户必须向下滚动屏幕垂直显示其所有的内容，这可能不是所需的体验。

以适应屏幕**宽度**并**高度**属性设备方向，您可以使用以下公式：

**Width** = `Max(App.Width, If(App.Width < App.Height, App.DesignWidth, App.DesignHeight))`

**Height** = `Max(App.Height, If(App.Width < App.Height, App.DesignHeight, App.DesignWidth))`

这些公式交换应用的**DesignWidth**并**DesignHeight**基于设备的宽度是否小于它的高度 （纵向） 或多个窗体的高度 （横向） 的值.

调整屏幕的后**宽度**并**高度**公式，您可能还想要重新排列屏幕以更好地利用可用空间中的控件。 例如，如果两个控件都只占据屏幕的一半，可能纵向中垂直堆叠，但在布局中并排排列。

您可以使用屏幕**方向**属性来确定在屏幕的方向是垂直还是水平。

> [!NOTE]
> 在横向方向**上部**并**较低**控件显示为左侧和右侧的控件。

| 控件 | 属性 | 公式 |
|--|----------|---|
| **Upper** | **X** | `0` |
| **Upper** | **Y** | `0` |
| **Upper** | **Width** | `If(Parent.Orientation = Layout.Vertical, Parent.Width, Parent.Width / 2)` |
| **Upper** | **Height**   | `If(Parent.Orientation = Layout.Vertical, Parent.Height / 2, Parent.Height)` |
| **较低** | X | `If(Parent.Orientation = Layout.Vertical, 0, Upper.X + Upper.Width)`  |
| **较低** | Y | `If(Parent.Orientation = Layout.Vertical, Upper.Y + Upper.Height, 0)` |
| **较低** | **Width** | `Parent.Width - Lower.X` |
| **较低** | **Height** | `Parent.Height - Lower.Y` |

![若要调整方向为纵向的表达式](media/create-responsive-layout/portrait.png)

![若要调整横向方向的表达式](media/create-responsive-layout/landscape.png)

### <a name="screen-sizes-and-breakpoints"></a>屏幕大小和断点

您可以调整您的布局基于设备的大小。 在屏幕**大小**属性将分为两类的当前设备大小。 大小是一个正整数;屏幕大小类型提供了有助于提高可读性的已命名的常数。 此表列出的常量：

| 常量              | Value | 典型的设备类型 （使用默认应用设置） |
|-----------------------|-------|--------------------------------------------------|
| ScreenSize.Small      | 1     | 电话                                            |
| ScreenSize.Medium     | 2     | 垂直持有的平板电脑                          |
| ScreenSize.Large      | 3     | 水平持有的平板电脑                        |
| ScreenSize.ExtraLarge | 4     | 台式计算机                                 |

使用这些大小决定应用的布局。 例如，如果你想控制大小电话的设备上可见但否则为隐藏，您可以设置控件的**Visible**属性设为此公式：

`Parent.Size >= ScreenSize.Medium`

此公式的计算结果为 **，则返回 true**大小为中等或较大时， **false**否则为。

如果你想控制以占据屏幕宽度基于屏幕大小的不同部分，设置控件的**宽度**属性设为此公式：

```powerapps-dot
Parent.Width *  
    Switch(Parent.Size,  
        ScreenSize.Small, 0.5,  
        ScreenSize.Medium, 0.3,  
        0.25)
```
此公式在小屏幕上，在中等屏幕上的屏幕宽度的三个的十分之几和每个季度的所有其他屏幕上的屏幕宽度上将控件的宽度设置为屏幕宽度的一半。

## <a name="custom-breakpoints"></a>自定义断点

在屏幕**大小**属性通过比较屏幕的计算**宽度**属性设置为应用程序的中值**SizeBreakpoints**属性。 此属性是数值，表明分隔命名的屏幕大小的宽度断点的单列的表：

在创建平板电脑或 web 应用中的默认值在应用中**SizeBreakpoints**属性是 **[600、 900，1200年]**。 在创建手机应用中，当值 **[1200年、 1800年、 2400年]**。 （针对手机应用程序的值将增加一倍因为此类应用程序使用双有效地在其他应用中使用的坐标的坐标。）

![App.SizeBreakpoints 属性的默认值](media/create-responsive-layout/default-breakpoints.png)

可以通过更改应用程序的中值来自定义应用程序的断点**SizeBreakpoints**属性。 选择**应用程序**在树视图中，选择**SizeBreakpoints**属性中列出，然后单击编辑栏中的值。 您可以创建很多断点如你的应用需求，但仅大小的 1 到 4 对应于已命名的屏幕大小。 可以在公式中，指 ExtraLarge 超出由其数字值的大小 （5、 6 和等）。

此外可以指定更少的断点。 例如，您的应用程序可能需要仅三个大小 （两个断点），因此可能的屏幕大小是小型、 中型和大型。

## <a name="known-limitations"></a>已知的限制

创作画布不响应的大小调整公式创建。 若要测试响应行为，保存并发布你的应用，然后在设备上或在各种大小和方向的浏览器窗口中打开它。

如果您编写表达式或中的公式**X**， **Y**，**宽度**，以及**高度**属性的一个控件，将会覆盖这些表达式或公式，如果你稍后将控件拖动到另一个位置或调整控件通过拖动其边框的大小。
