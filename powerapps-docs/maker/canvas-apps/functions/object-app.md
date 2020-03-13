---
title: 应用对象 |Microsoft Docs
description: Power Apps 中的应用对象的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f5f09bab44f3f229b47d9a801703b3aa10cba06d
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212161"
---
# <a name="app-object-in-power-apps"></a>Power Apps 中的应用对象

提供有关当前正在运行的应用程序的信息，并控制应用程序的行为。

## <a name="description"></a>说明

与控件一样，**应用程序**对象提供的属性用于标识显示的屏幕，并提示用户保存更改，使其不会丢失。 每个应用程序都有一个**应用程序**对象。

您可以为**应用**对象的某些属性编写公式。 在 "**树视图**" 窗格的顶部，选择 "**应用**" 对象，就像选择任何其他控件或屏幕一样。 通过在编辑栏左侧的下拉列表中选择某个对象的属性来查看和编辑该对象的属性。

> [!div class="mx-imgBorder"]
> ![树视图窗格中的应用对象](media/object-app/appobject.png)

## <a name="activescreen-property"></a>App.activescreen 属性

**App.activescreen**属性标识所显示的屏幕。

此属性返回一个屏幕对象，您可以使用该屏幕对象引用屏幕的属性，或与另一个屏幕进行比较以确定显示的屏幕。 还可以使用表达式**App.ActiveScreen.Name**来检索显示的屏幕的名称。

使用 "**[后退](function-navigate.md)**" 或 "**[导航](function-navigate.md)**" 功能可更改显示的屏幕。

## <a name="onstart-property"></a>OnStart 属性

当用户启动应用程序时，将运行**OnStart**属性。 应用程序制造商通常使用此属性来执行以下任务：

- 使用**[Collect](function-clear-collect-clearcollect.md)** 函数检索数据并将其缓存到集合中。
- 使用**[set](function-set.md)** 函数设置全局变量。
- 使用**[导航](function-navigate.md)** 函数导航到初始屏幕。

在第一个屏幕出现之前计算此公式。 未加载屏幕，因此无法通过**[UpdateContext](function-updatecontext.md)** 函数设置上下文变量。 但是，可以通过**导航**函数传递上下文变量。

更改**OnStart**属性后，通过将鼠标指针悬停在 "**树视图**" 窗格中的**应用**对象上进行测试，选择显示的省略号（...），然后选择 "**运行 OnStart**"。 与第一次加载应用时不同，现有集合和变量将被设置。 若要从空集合开始，请使用**[ClearCollect](function-clear-collect-clearcollect.md)** 函数而不是**Collect**函数。

> [!div class="mx-imgBorder"]
> 用于运行 OnStart](media/object-app/appobject-runonstart.png) 的 ![应用项快捷菜单

## <a name="confirmexit-properties"></a>ConfirmExit 属性

无人想要丢失未保存的更改。 使用**ConfirmExit**和**ConfirmExitMessage**属性在用户关闭应用之前向用户发出警告。

> [!NOTE]
> **ConfirmExit**不适用于嵌入的应用，例如 Power BI 和 SharePoint。

> [!NOTE]
> 目前，如果启用**延迟加载**预览功能（对于新应用，默认情况下），则这些属性只能引用第一个屏幕上的控件。 如果进行了引用，Power Apps Studio 不会显示错误，但生成的已发布应用不会在 Power Apps Mobile 或浏览器中打开。 我们正在积极努力提升此限制。 同时，可以在 "高级设置" > "**高级设置** **" 下，** 关闭 "**文件** > **应用设置**" 中的**延迟加载**。

### <a name="confirmexit"></a>ConfirmExit

**ConfirmExit**是一个布尔值属性，当*设置为 true*时，在应用程序关闭之前将打开一个确认对话框。 默认情况下，此属性为*false*，并且不显示任何对话框。

如果用户已进行了更改但未保存，则使用此属性显示确认对话框。 使用可检查变量和控件属性（例如，[**编辑窗体**](../controls/control-form-detail.md)控件的**未保存**属性）的公式。

在任何可能丢失数据的情况下，都会出现确认对话框，如以下示例中所示：

- 运行[**Exit**](function-exit.md)函数。
- 如果应用在浏览器中运行：
  - 关闭浏览器或运行应用程序的浏览器选项卡。
  - 选择浏览器的 "后退" 按钮。
- 如果应用在 Power Apps Mobile （iOS 或 Android）中运行：
  - 运行[**启动**](function-param.md)函数。<br>**启动**函数不会在浏览器中触发对话框，因为其他选项卡会打开，使数据不会丢失。
  - 轻扫，切换到 Power Apps Mobile 中的其他应用。
  - 选择 Android 设备上的 "后退" 按钮。

确认对话框的确切外观可能因电源应用的不同设备和版本而异。

"确认" 对话框不会出现在 Power Apps Studio 中。

### <a name="confirmexitmessage"></a>ConfirmExitMessage

默认情况下，确认对话框会显示一般消息，如 **"您可能有未保存的更改。"** 以用户的语言。

使用**ConfirmExitMessage**可在确认对话框中提供自定义消息。 如果此属性为*空白*，则使用默认值。 自定义消息根据需要在确认对话框内被截断，因此，最多可将消息保存到几行。

在浏览器中，"确认" 对话框可能会显示来自浏览器的一般消息。

### <a name="example"></a>示例

1. 创建包含两个窗体控件**AccountForm**和**ContactForm**的应用。

1. 将**App**对象的**ConfirmExit**属性设置为以下表达式：

    ```powerapps-dot
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    如果用户更改任一格式的数据，然后尝试关闭应用而不保存这些更改，则会显示此对话框。

    > [!div class="mx-imgBorder"]
    > ![一般确认对话框](media/object-app/confirm-native.png)

1. 将**App**对象的**ConfirmExitMessage**属性设置为以下公式：

    ```powerapps-dot
    If( AccountsForm.Unsaved,
        "Accounts form has unsaved changes.",
        "Contacts form has unsaved changes."
    )
    ```

    如果用户在帐户窗体中更改了数据，然后尝试关闭应用而不保存这些更改，则会显示此对话框。

    > [!div class="mx-imgBorder"]
    > ![窗体特定的确认对话框](media/object-app/confirm-native-custom.png)
