---
title: 应用程序对象 |Microsoft Docs
description: 参考信息，包括语法和示例，在 PowerApps 中的应用程序对象
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 232accd1050fb84816e86ea95069b8c8778f6586
ms.sourcegitcommit: 562c7ed5fbb116be1cbb0f45e3f6e75e3e4cf011
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451601"
---
# <a name="app-object-in-powerapps"></a>在 PowerApps 中的应用程序对象

提供有关当前正在运行的应用程序和好地控制应用的行为的信息。

## <a name="description"></a>描述

与控件相似**应用**对象提供的属性，用于标识显示的屏幕并提示用户以保存更改，以便它们不丢失。 每个应用程序具有**应用**对象。

您可以编写的某些属性的公式**应用**对象。 在顶部**树视图**窗格中，选择**应用**对象作为您将任何其他控件或屏幕上。 查看和编辑通过公式栏的左侧的下拉列表中选择一个对象的属性。

> [!div class="mx-imgBorder"]
> ![树视图窗格中的应用程序对象](media/object-app/appobject.png)

## <a name="activescreen-property"></a>ActiveScreen 属性

**ActiveScreen**属性标识显示的屏幕。

此属性返回一个屏幕对象，可用于引用屏幕属性或比较到另一个屏幕来确定显示哪个屏幕。 此外可以使用表达式**App.ActiveScreen.Name**检索显示在屏幕的名称。

使用 **[回](function-navigate.md)** 或 **[Navigate](function-navigate.md)** 函数来更改显示的屏幕。

## <a name="onstart-property"></a>OnStart 属性

**OnStart**用户启动应用时运行的属性。 应用创建者通常使用此属性来执行这些任务：

- 检索并缓存到集合的数据，通过使用 **[收集](function-clear-collect-clearcollect.md)** 函数。
- 使用设置全局变量 **[设置](function-set.md)** 函数。
- 导航到使用的初始屏幕 **[Navigate](function-navigate.md)** 函数。

第一屏出现之前，会计算此公式。 加载没有屏幕，因此不能设置与上下文变量 **[UpdateContext](function-updatecontext.md)** 函数。 但是，可以传递与上下文变量**Navigate**函数。

更改后**OnStart**属性，对其进行测试悬停**应用**对象中**树视图**窗格中，选择显示的省略号 （...），然后选中**运行 OnStart**。 当首次加载应用，与现有集合和变量已设置。 开始使用空集合，请使用 **[ClearCollect](function-clear-collect-clearcollect.md)** 函数而不是**收集**函数。

> [!div class="mx-imgBorder"]
> ![运行 OnStart 应用项快捷菜单](media/object-app/appobject-runonstart.png)

## <a name="confirmexit-properties"></a>ConfirmExit 属性

没有人会愿意放弃未保存的更改。 使用**ConfirmExit**并**ConfirmExitMessage**来警告用户他们关闭应用之前的属性。

> [!NOTE]
> **ConfirmExit**不起作用的应用中的嵌入在中，例如，Power BI 和 SharePoint。

> [!NOTE]
> 目前，这些属性可以引用仅在第一个屏幕上的控件如果**延迟加载**预览功能启用 （这是默认情况下，为新应用程序）。 如果进行了引用，PowerApps Studio 不会显示一个错误，但生成的已发布的应用不会在 PowerApps Mobile 或浏览器中打开。 我们正在努力取消此限制。 在此期间，你可以关闭**延迟负载**中**文件** > **应用程序设置** > **高级设置**(下**预览功能**)。

### <a name="confirmexit"></a>ConfirmExit

**ConfirmExit**是一个布尔值属性的当*true*，打开一个确认对话框之前在关闭应用程序。 默认情况下，此属性是*false*，并且会显示任何对话框。

使用此属性以显示确认对话框中，是否用户已进行了更改，但不是会保存它们。 使用公式，可以检查变量并控制属性 (例如， **Unsaved**的属性[**编辑窗体**](../controls/control-form-detail.md)控件)。

确认对话框中将出现在任何情况下，数据可能丢失，如以下示例所示：

- 运行[**退出**](function-exit.md)函数。
- 如果在浏览器中运行应用：
  - 关闭浏览器或在其中运行应用的浏览器选项卡。
  - 选择浏览器的后退按钮。
- 如果在 PowerApps Mobile （iOS 或 Android） 中运行应用：
  - 运行[**启动**](function-param.md)函数。<br>**启动**函数不会触发在浏览器对话框中，因为另一个选项卡将打开，以便数据不会丢失。
  - 轻扫以切换到在 PowerApps Mobile 中不同的应用。
  - 选择 Android 设备上的后退按钮。

确认对话框中的确切外观可能不同跨设备和版本的 PowerApps。

确认对话框中没有出现在 PowerApps Studio。

### <a name="confirmexitmessage"></a>ConfirmExitMessage

默认情况下，确认对话框中显示一条常规消息，如 **"您可能有未保存的更改。"** 在用户的语言。

使用**ConfirmExitMessage**可提供在确认对话框中的自定义信息。 如果此属性为*空白*，则使用默认值。 根据需要使其容纳在确认对话框，因此，请将消息到几行最多情况下，自定义消息将被截断。

在浏览器中，确认对话框中可能从浏览器显示使用一条常规消息。

### <a name="example"></a>示例

1. 创建的应用程序包含两个窗体控件**AccountForm**并**ContactForm**。

1. 设置**应用程序**对象的**ConfirmExit**属性设置为此表达式：

    ```powerapps-dot
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    如果用户更改任一格式的数据，然后尝试关闭应用程序而不保存这些更改，将出现此对话框。

    > [!div class="mx-imgBorder"]
    > ![泛型的确认对话框](media/object-app/confirm-native.png)

1. 设置**应用程序**对象的**ConfirmExitMessage**属性设为此公式：

    ```powerapps-dot
    If( AccountsForm.Unsaved,
        "Accounts form has unsaved changes.",
        "Contacts form has unsaved changes."
    )
    ```

    如果用户更改帐户窗体中的数据，然后尝试关闭应用程序而不保存这些更改，将出现此对话框。

    > [!div class="mx-imgBorder"]
    > ![特定于窗体的确认对话框](media/object-app/confirm-native-custom.png)
