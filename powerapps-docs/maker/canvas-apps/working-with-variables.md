---
title: 了解画布应用中的变量 | Microsoft Docs
description: 有关在画布应用中使用状态、上下文变量和集合的参考信息
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6f46dcdf300c91be9fbc2f39e6b2a5418a4b82de
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61558700"
---
# <a name="understand-canvas-app-variables-in-powerapps"></a>了解 PowerApps 中的画布应用变量

如果你使用另一种编程工具，如 Visual Basic 或 JavaScript 中，您可能会问：**变量在哪里？** PowerApps 稍有不同，需要不同的方法。 而不是去获取变量时生成画布应用，问问自己：**在 Excel 中，我将做什么？**

在其他工具中，你可能会显式执行某个计算，然后将结果存储在变量中。 但是，PowerApps 和 Excel 都会在输入数据更改时自动重新计算公式，因此你通常不需要创建和更新变量。 尽可能使用这种方法，你就可以更轻松地创建、了解和维护应用。

某些情况下，需要在 PowerApps 中使用变量，通过添加[行为公式](working-with-formulas-in-depth.md)扩展 Excel 的模型。 这些公式在特定情况下（例如，用户选择某个按钮）运行。 在行为公式中，设置一个可在其他公式中使用的变量通常很有用。

一般情况下，应避免使用变量。 但有时候，只有使用变量才能获得所需的体验。 隐式创建变量和类型化它们出现在函数中设置其值。 

## <a name="translate-excel-into-powerapps"></a>将 Excel 转换成 PowerApps

### <a name="excel"></a>Excel

让我们回顾一下 Excel 的工作原理。 单元格可以包含值（例如数字或字符串），也可以包含公式（基于其他单元格的值）。 用户向单元格输入其他值以后，Excel 会自动根据新的值重新计算任何公式。 不需编程即可启用此行为。

在以下示例中，单元格**A3**设置为公式**A1 + A2**。 如果**A1**或**A2**更改**A3**自动重新计算以反映更改。 此行为无需编码之外的公式本身。

![重新计算在 Excel 中的两个数字之和的动画](media/working-with-variables/excel-recalc.gif)

Excel 没有变量。 包含公式的单元格的值随输入而更改，但无法记住公式的结果，也无法将结果存储在单元格或任何其他地方。 如果更改某个单元格的值，则整个电子表格都会更改，以前计算出来的值就会丢失。 Excel 用户可以复制和粘贴单元格，但那是在用户的手动控制之下完成的，不可能通过公式来完成。

### <a name="powerapps"></a>PowerApp

在 PowerApps 中创建的应用的行为与 Excel 很类似。 可以将控件添加到屏幕的任意位置，并根据其在公式中的用途为其命名，不需更新单元格。

例如，可以通过添加复制的应用程序中的 Excel 行为 **[标签](controls/control-text-box.md)** 控件，名为**Label1**，并将两个 **[文本输入](controls/control-text-input.md)** 控件，分别命名为**TextInput1**并**TextInput2**。 如果你随后将设置 **[文本](controls/properties-core.md)** 属性**Label1**到**TextInput1 + TextInput2**，它将始终显示中的任何数字的总和**TextInput1**并**TextInput2**自动。

![计算在 PowerApps 中的两个数字的总和](media/working-with-variables/recalc1.png)

请注意， **Label1**选择控件后，显示其**[文本](controls/properties-core.md)** 公式在屏幕顶部的公式栏中。 在这里，我们可以找到公式 **TextInput1 + TextInput2**。 该公式在这些控件之间创建了一个依赖关系，就像在 Excel 工作簿中的单元格之间创建依赖关系一样。  让我们更改的值**TextInput1**:

![计算在 PowerApps 中的两个数字之和的动画](media/working-with-variables/recalc2.gif)

有关公式**Label1**已自动重新计算，显示新值。

在 PowerApps 中，使用公式不仅可以确定控件的主值，还可以确定属性（例如格式设置）。 在下一示例中，标签的“[Color](controls/properties-color-border.md)”属性的公式会自动将负值显示为红色。 **[If](functions/function-if.md)** 函数看起来应该与 Excel 中的很相似：

`If( Value(Label1.Text) < 0, Red, Black )`

![条件格式设置的动画](media/working-with-variables/recalc-color.gif)

很多情况下都可以使用公式：

* 启用设备的 GPS 后，地图控件就可以使用公式通过 **Location.Latitude** 和 **Location.Longitude** 来显示当前位置。  移动时，地图会自动跟踪你的位置。
* 其他用户可能会更新[数据源](working-with-data-sources.md)。  例如，团队中的其他人可能会更新 SharePoint 列表中的项。  刷新数据源时，相关公式会根据更新的数据自动重新计算。 就此示例来说，你可以进一步将库的 **[Items](controls/properties-core.md)** 属性设置为公式 **Filter( SharePointList )** ，以便自动显示新筛选的[记录](working-with-tables.md#records)集。

### <a name="benefits"></a>权益

使用公式生成应用具有很多优点：

* 如果你知道 Excel，你就知道 PowerApps。 二者的模型和公式语言是相同的。
* 如果你使用过其他编程工具，可以试想一下，完成这些示例需要多少代码。  在 Visual Basic 中，需要为每个文本输入控件上发生的更改事件编写事件处理程序。  在每个这样的处理程序中，用于执行计算的代码很冗长，并且可能会出现不同步的情况，或者需要你编写通用子例程。  而在 PowerApps 中，这一切只需一个单行公式即可完成。
* 若要了解在何处**Label1**的文本来自，您就知道从中查找： 中的公式 **[文本](controls/properties-core.md)** 属性。  其他方式不会影响该控件的文本。  在传统编程工具中，可以从程序的任何位置通过任何事件处理程序或子例程更改该标签的值。  这就难以跟踪变量的更改时间和位置。
* 如果用户更改了滑块控件，然后又改变了主意，则可将滑块改回其原始值。  这样一来，就好像没有做过任何更改一样：应用所显示的控件值与以前显示的一样。  不需进行分支试验并询问假设性的问题，就像在 Excel 中一样。  

如果可以使用公式达到某种效果，则通常会选择使用公式。 让 PowerApps 中的公式引擎为你服务。  

## <a name="know-when-to-use-variables"></a>了解何时使用变量

让我们将简单的加法器更改一下，使之操作起来就像一台老式的带汇总功能的加法机。 如果选择“加”按钮，则会将一个数字加到汇总中。 如果选择“清除”按钮，则会将汇总重置为零。

| 显示 | 描述 |
|----|----|
| <style> i m g {最大宽度： none} </style> ![应用的文本输入控件、 标签和两个按钮](media/working-with-variables/button-changes-state-1.png) | 当应用启动时的正在运行的总为 0。<br><br>红点表示在文本输入框中，用户在此处输入的用户的手指**77**。 |
| ![文本输入的控件包含 77，并按下添加按钮](media/working-with-variables/button-changes-state-2.png) | 用户选择**添加**按钮。 |
| ![总为 77，和另一个 77 添加到它](media/working-with-variables/button-changes-state-3.png) | 77 添加到正在运行的总数。<br><br>用户选择**添加**按钮再次。 |
| ![总和为 154 之前清除它。](media/working-with-variables/button-changes-state-4.png) | 77 再次添加到正在运行的总数，从而导致 154。<br><br>用户选择**清除**按钮。 |
| ![总被清除。](media/working-with-variables/button-changes-state-5.png) | 汇总重置为 0。 |

我们的加法机使用了某个 Excel 中不存在的东西：按钮。 在该应用中，不能仅使用公式来计算汇总，因为其值取决于用户采取的一系列操作。 必须手动记录和更新汇总。 大多数编程工具将该信息存储在“变量”中。

有时候，需要使用变量才能让应用的表现符合预期。  但该方法需注意以下事项：

* 必须手动更新汇总。 自动重新计算在此方面不会为你代劳。
* 不能再根据其他控件的值计算汇总。 汇总结果取决于用户选择“加”按钮的次数，以及每次操作时文本输入控件中的具体值。 在执行加法计算时，到底是用户输入了 77 并选择“加”两次，还是用户指定了 24 和 130？ 你只知道总和为 154，但无法分辨上述两种过程。
* 可以通过不同的方式来改变总和。 在此示例中，“加”按钮和“清除”按钮都可以更新总和。 如果应用表现异常，则到底是哪个按钮引发的问题？

## <a name="use-a-global-variable"></a>使用全局变量

创建加法机需要一个变量来存储汇总。 可用于 PowerApps 的最简单变量是全局变量。  

全局变量的工作方式：

* 使用 [Set](functions/function-set.md) 函数设置全局变量的值。  Set( MyVar, 1 ) 可将全局变量 MyVar 的值设置为 1。
* 可以通过引用 Set 函数使用的名称来使用全局变量。  在这种情况下， MyVar 将返回 1。
* 全局变量可以存储包括字符串、数字、记录和[表](working-with-tables.md)在内的任何值。

让我们使用全局变量重新生成加法机：

1. 添加一个文本输入控件，将其命名为 **TextInput1**，同时添加两个按钮，分别命名为 **Button1** 和 **Button2**。

2. 将 **Button1** 的 **[Text](controls/properties-core.md)** 属性设置为“加”，将 **Button2** 的“Text”属性设置为“清除”。

3. 若要在用户选择“加”按钮时更新汇总，请将 **[OnSelect](controls/properties-core.md)** 属性设置为以下公式：

    **Set( RunningTotal, RunningTotal + TextInput1 )**

    此公式只存在建立**RunningTotal**与全局变量包含许多由于 **+** 运算符。 可以引用**RunningTotal**应用中的任意位置。 用户打开此应用程序，每当**RunningTotal**初始值*空白*。

    用户选择的第一次**外**按钮并 **[设置](functions/function-set.md)** 运行时， **RunningTotal**设置为值**RunningTotal + TextInput1**。

    ![添加按钮的 OnSelect 属性设置为设置函数](media/working-with-variables/global-variable-1.png)

4. 若要在用户选择“清除”按钮时将汇总设置为 **0**，请将 **[OnSelect](controls/properties-core.md)** 属性设置为以下公式：

    Set( RunningTotal, 0 )

    ![清除按钮的 OnSelect 属性设置为设置函数](media/working-with-variables/global-variable-2.png)

5. 添加一个“[标签](controls/control-text-box.md)”控件，然后将“[Text](controls/properties-core.md)”属性设置为“RunningTotal”。

    此公式将自动重新计算，为用户显示的 **RunningTotal** 值随用户选择的按钮而变化。

    ![标签的 text 属性设置为变量的名称](media/working-with-variables/global-variable-3.png)

6. 预览该应用，我们创建的加法机完全符合上述说明。 在文本框中输入数字，然后按几次“添加”按钮。 准备就绪时，使用 Esc 键返回到创作体验。

    ![文本输入控件包含一个值和标签包含正在运行总计](media/working-with-variables/global-variable-4.png)

7. 若要显示全局变量的值，请选择**文件**菜单，然后选择**变量**的左窗格中。

    ![在文件菜单中的变量选项](media/working-with-variables/global-variable-file-1.png)

8. 若要显示在其中定义和使用该变量的所有位置，请选择它。

    ![使用变量的位置的列表](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>变量类型

PowerApps 提供三种类型的变量：

| 变量类型 | 范围 | 描述 | 建立函数 |
| --- | --- | --- | --- |
| 全局变量 |App |用法最为简单。 包含可从应用程序的任何位置进行引用的数字、文本字符串、布尔值、记录、表等。 |[Set](functions/function-set.md) |
| 上下文变量 |屏幕 |非常适合将值传递到屏幕，与其他语言中的过程的参数非常类似。 只有一个屏幕中，可以引用。 |[UpdateContext](functions/function-updatecontext.md)<br>[Navigate](functions/function-navigate.md) |
| 集合 |App |包含可以引用从任意位置的应用中的表。 允许修改表的内容，而不是作为一个整体进行设置。 可以保存到本地设备，以供将来使用。 |[Collect](functions/function-clear-collect-clearcollect.md)<br>[ClearCollect](functions/function-clear-collect-clearcollect.md) |

## <a name="create-and-remove-variables"></a>创建和删除变量

中出现时，将隐式创建的所有变量**设置**， **UpdateContext**， **Navigate**，**收集**，或**ClearCollect**函数。 若要声明一个变量，其类型，您只需包含它在任何这些函数中任意位置应用程序中。 这些函数均不创建变量;它们仅使用值填充变量。 您永远不会声明变量显式可能在另一种编程工具中以及所有键入是隐式从使用情况。

例如，你可能具有的按钮控件**OnSelect**公式等于**集 (X，1)** 。 此公式建立**X**为具有数字的类型的变量。 可以使用**X** as 编号和该变量的公式中的值为*空白*打开应用之后，但之前选择的按钮。 时选择的按钮，需授予**X**的值**1**。

如果你添加另一个按钮，然后设置其**OnSelect**属性设置为**集 (X，"Hello")** ，将发生错误，因为类型 （文本字符串） 的类型不匹配在以前**设置**（数字）。 所有隐式定义的变量必须达成类型。 同样，所有发生此情况由于你提到**X**在公式中，不是因为有实际运行任何这些公式。

通过删除所有删除变量**设置**， **UpdateContext**， **Navigate**，**收集**，或**ClearCollect**隐式建立该变量的函数。 而无需这些函数，该变量不存在。 此外必须删除对该变量的任何引用，因为它们会导致错误。

## <a name="variable-lifetime-and-initial-value"></a>变量的生存期和初始值

当应用程序在运行时，所有变量都保存在内存中。 在应用关闭后，变量持有的值会丢失。

可以通过使用数据源中存储变量的内容**修补程序**或**收集**函数。 您也可以将值通过使用存储在本地设备上的集合中[ **SaveData** ](functions/function-savedata-loaddata.md)函数。

当用户打开应用时，所有变量都具有初始值*空白*。

## <a name="reading-variables"></a>读取变量

使用变量的名称来读取其值。 例如，可以定义具有此公式的变量：

`Set( Radius, 12 )`

然后您可以直接使用**Radius**任意位置，可以使用一个数字，并且它将替换**12**:

`Pi() * Power( Radius, 2 )`

如果提供的上下文变量的全局变量或集合的名称相同，上下文变量优先。 但是，可以仍引用全局变量或集合如果您使用[消除歧义运算符](functions/operators.md#disambiguation-operator) **@[Radius]** 。

## <a name="use-a-context-variable"></a>使用上下文变量

我们来看看如何使用上下文变量而不是全局变量创建加法机。

上下文变量的工作原理：

* 隐式地建立并通过设置上下文变量 **[UpdateContext](functions/function-updatecontext.md)** 或 **[Navigate](functions/function-navigate.md)** 函数。 应用程序启动时，是所有上下文变量的初始值*空白*。
* 使用记录更新上下文变量。 在其他编程工具中，通常使用“=”来赋值，例如“x = 1”。 对于上下文变量，请使用 **{x:1}** 相反。 当使用上下文变量时，使用记录语法不直接其名称。
* 当你使用时，还可以设置上下文变量 **[Navigate](functions/function-navigate.md)** 函数来显示的屏幕。 如果您将屏幕视为一种类型的过程或子例程，此方法类似于其他编程工具中的参数传递。
* 上下文变量的作用范围仅限于单个屏幕的上下文（**[Navigate](functions/function-navigate.md)** 除外），这也是其得名的原因。 不能超出相应的上下文使用或设置上下文变量。
* 上下文变量可以存储包括字符串、数字、记录和[表](working-with-tables.md)在内的任何值。

让我们使用一个上下文变量重新生成加法机：

1. 添加一个文本输入控件，将其命名为 **TextInput1**，同时添加两个按钮，分别命名为 **Button1** 和 **Button2**。

2. 将 **Button1** 的 **[Text](controls/properties-core.md)** 属性设置为“加”，将 **Button2** 的“Text”属性设置为“清除”。

3. 若要在用户选择“加”按钮时更新汇总，请将 **[OnSelect](controls/properties-core.md)** 属性设置为以下公式：

    **UpdateContext( { RunningTotal:RunningTotal + TextInput1 } )**

    此公式只存在建立**RunningTotal**作为包含许多由于一个上下文变量 **+** 运算符。 可以引用**RunningTotal**此屏幕中的任意位置。 用户打开此应用程序，每当**RunningTotal**初始值*空白*。

    用户选择的第一次**外**按钮并 **[UpdateContext](functions/function-updatecontext.md)** 运行时， **RunningTotal**设置为值**RunningTotal + TextInput1**。

    ![添加按钮的 OnSelect 属性](media/working-with-variables/context-variable-1.png)

4. 若要在用户选择“清除”按钮时将汇总设置为 **0**，请将 **[OnSelect](controls/properties-core.md)** 属性设置为以下公式：

    **UpdateContext( { RunningTotal:0 } )**

    同样， **[UpdateContext](functions/function-updatecontext.md)** 与公式一起使用**UpdateContext ({RunningTotal:0 } )** .

    ![清除按钮的 OnSelect 属性](media/working-with-variables/context-variable-2.png)

5. 添加一个“[标签](controls/control-text-box.md)”控件，然后将“[Text](controls/properties-core.md)”属性设置为“RunningTotal”。

    此公式将自动重新计算，为用户显示的 **RunningTotal** 值随用户选择的按钮而变化。

    ![标签的 text 属性](media/working-with-variables/context-variable-3.png)

6. 预览该应用，我们创建的加法机完全符合上述说明。 在文本框中输入数字，然后按几次“添加”按钮。 准备就绪时，使用 Esc 键返回到创作体验。

    ![文本输入控件将显示一个值，并标签显示运行总数](media/working-with-variables/context-variable-4.png)

7. 导航到屏幕时，可以设置上下文变量的值。 这对于将“上下文”或“参数”从一个屏幕传递到另一个屏幕很有用。 若要演示此技术，插入一个屏幕、 插入按钮，并设置其**OnSelect**属性设为此公式：

    Navigate( Screen1, None, { RunningTotal: -1000 } )

    ![按钮的 OnSelect 属性](media/working-with-variables/context-variable-5.png)

    按住 Alt 键，同时选择这两个显示此按钮**Screen1**并设置上下文变量**RunningTotal**为-1000年。

    ![Screen1 处于打开状态](media/working-with-variables/context-variable-6.png)

8. 若要显示的上下文变量的值，请选择**文件**菜单，并选择**变量**的左窗格中。

    ![在文件菜单上的变量选项](media/working-with-variables/context-variable-file-1.png)

9. 若要显示在其中定义和使用上下文变量，请选择它。

    ![使用一个变量的列表](media/working-with-variables/context-variable-file-2.png)

## <a name="use-a-collection"></a>使用集合

最后，我们来看一下如何使用集合创建加法机。  由于集合包含一个易于修改的表，我们将使此加法机保留每个值输入时的“纸带”。

集合工作原理：

* 通过 **[ClearCollect](functions/function-clear-collect-clearcollect.md)** 函数创建和设置集合。  可以改用 **[Collect](functions/function-clear-collect-clearcollect.md)** 函数，但该函数实际上需要另一个变量，而不能替换旧的变量。  
* 集合是一种类型的数据源，因此也是表。 若要访问集合中的单个值，请使用 **[First](functions/function-first-last.md)** 函数，并从生成的记录中提取一个字段。 如果使用了单个值和 **[ClearCollect](functions/function-clear-collect-clearcollect.md)**，则该字段为“Value”字段，如以下示例所示：<br>
**First(** *VariableName* **).Value**

让我们使用集合重新创建加法机：

1. 添加一个 **[文本输入](controls/control-text-input.md)** 控件，将其命名为 **TextInput1**，同时添加两个按钮，分别命名为 **Button1** 和 **Button2**。

2. 将 **Button1** 的 **[Text](controls/properties-core.md)** 属性设置为“加”，将 **Button2** 的“Text”属性设置为“清除”。

3. 若要在用户选择“加”按钮时更新汇总，请将 **[OnSelect](controls/properties-core.md)** 属性设置为以下公式：

    Collect( PaperTape, TextInput1.Text )

    此公式只存在建立**PaperTape**作为包含文本字符串的单列的表的集合。 可以引用**PaperTape**此应用中的任意位置。 每当用户打开此应用，请**PaperTape**是一个空表。

    此公式在运行时，它将新值添加到集合的末尾。 我们添加了一个值，因为**收集**会自动将其放在单列的表中，并且列的名称为**值**，你将使用更高版本。

    ![添加按钮的 OnSelect 属性](media/working-with-variables/papertape-1.png)

4. 若要在用户选择时清除纸带**清除**按钮，设置其 **[OnSelect](controls/properties-core.md)** 属性设为此公式：

    Clear( PaperTape )

    ![清除按钮的 OnSelect 属性](media/working-with-variables/papertape-2.png)

5. 若要显示汇总，请添加一个标签，然后将“[Text](controls/properties-core.md)”属性设置为以下公式：

    Sum( PaperTape, Value )

    ![标签的 text 属性](media/working-with-variables/papertape-3.png)

6. 若要运行加法机，请按 F5 打开“预览”，在文本输入控件中输入数字，然后选择相应的按钮。

    ![文本输入的控件显示值和标签显示正在运行总计](media/working-with-variables/papertape-run-1.png)

7. 若要返回到默认工作区，请按 Esc 键。

8. 要显示纸带，请插入“数据表”控件，并将其 [Items](controls/properties-core.md) 属性设置为此公式：

    PaperTape

    在右侧窗格中，选择**值**列以显示它。

    ![显示了添加到集合的值的数据表](media/working-with-variables/papertape-4.png)

9. 若要查看集合中的值，请在“文件”菜单上选择“集合”。

    ![PaperTape 集合的预览](media/working-with-variables/papertape-file.png)

10. 要存储和检索您的集合，添加两个附加按钮控件，并将其**文本**属性设置为**负载**并**保存**。 设置**OnSelect**的属性**负载**按钮为以下公式：

     Clear( PaperTape ); LoadData( PaperTape, "StoredPaperTape", true )

     您需要先清除集合，因为**LoadData**会将存储的值追加到集合的末尾。

     ![加载按钮的 OnSelect 属性](media/working-with-variables/papertape-5.png)

11. 设置**OnSelect**的属性**保存**按钮为以下公式：

     SaveData( PaperTape, "StoredPaperTape" )

     ![保存按钮的 OnSelect * 属性](media/working-with-variables/papertape-6.png)

12. 按 F5 键再次预览，在文本输入控件中输入数字，然后选择按钮。 选择“保存”按钮。 关闭并重新加载应用程序中，并选择**负载**按钮以重新加载集合。

> [!NOTE]
> **SaveData**并**LoadData** PowerApps Mobile，但不是 PowerApps Studio 或 powerapps web player 中的函数。