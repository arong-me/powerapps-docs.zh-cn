---
title: 了解 SharePoint 窗体集成 | Microsoft 文档
description: 了解如何自定义适用于 SharePoint 的窗体
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9befcf4cb0e7267820c62ab78a14ee28ba985490
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732383"
---
# <a name="understand-sharepoint-forms-integration"></a>了解 SharePoint 窗体集成
你现在可以在 Power Apps 中轻松[自定义任何 SharePoint 列表窗体](customize-list-form.md)。 在本文中，我们将详细演示这些窗体的工作原理，以及如何对其作进一步的自定义。

如果你已自定义 SharePoint 列表窗体，则可能已经注意到默认生成的窗体适用于所有操作，如创建、显示或编辑项。 此操作是借助生成的公式和 SharePointIntegration 控件来实现的。

## <a name="understand-the-default-generated-form"></a>了解默认生成的窗体

默认生成的窗体包含以下控件及其相应默认值：

* FormScreen1 - 这是包含窗体的[屏幕](controls/control-screen.md)。

* **SharePointForm1** - 这是用于创建、显示或编辑列表项的[表单](working-with-forms.md)。

    * Data Source - 已为其自定义窗体的列表。

    * Item - 从列表中选定的项。 此项设置为列表中的第一项（），方便你在 Power Apps Studio 中工作时使用。

        **If(IsBlank(SharePointIntegration.Selected) || IsEmpty(SharePointIntegration.Selected),First('*YourListName*'),SharePointIntegration.Selected)**

    * OnSuccess - 一旦成功创建或保存项，则将重置窗体并且 SharePoint 会隐藏窗体。

        ResetForm(SharePointForm1); RequestHide()

* **SharePointIntegration** -负责在 SharePoint 和 Power Apps 之间传达用户操作的控件。

    * Data Source - 已为其自定义窗体的列表。

        **'*YourListName*'**

    * **OnNew** - 将“SharePointForm1”设置为新建模式。

        NewForm(SharePointForm1)

    * **OnView** - 将“SharePointForm1”设置为视图模式。

        ViewForm(SharePointForm1)

    * **OnEdit** - 将“SharePointForm1”设置为编辑模式。

        EditForm(SharePointForm1)

    * **OnSave** - 提交对“SharePointForm1”所做的更改。 成功提交表单时，将执行 SharePointForm1.OnSuccess 公式。

        SubmitForm(SharePointForm1)

    * OnCancel - 重置对 SharePointForm1 的更改。 如果用户在 SharePoint 中单击或点击“取消”，SharePoint 始终都会隐藏表单。

        **ResetForm(SharePointForm1)**

这些默认值确保窗体在 SharePoint 中运行时工作，在用户与 SharePoint 中的用户交互时，它们会更改 Power Apps 窗体模式，并确保将更改提交到 SharePoint。

## <a name="understand-the-sharepointintegration-control"></a>了解 SharePointIntegration 控件
**SharePointIntegration**控件在 SharePoint 和 Power Apps 之间传达用户操作。

![](./media/sharepoint-form-integration/sharepointintegration-object.png)

>[!NOTE]
>仅当窗体在 SharePoint 中运行时，才可以访问**SharePointIntegration**控件的属性，而不能在 Power Apps Studio 中自定义窗体。 这些属性可能无法在 OnStart 或 OnVisible 中使用。 

SharePointIntegration 控件具有以下属性：

Selected - SharePoint 列表中的选定项。

OnNew - 当用户单击或点击 SharePoint 中的“新建”按钮或打开“创建项”窗体时，应用的响应方式。

OnView - 当用户单击或点击 SharePoint 中的“项”或打开“项详细信息”窗体时，应用的响应方式。

OnEdit - 当用户单击或点击 SharePoint 中的“编辑全部”按钮或打开“编辑项”窗体时，应用的响应方式。

**OnSave** - 应用如何响应在 SharePoint 中单击或点击“保存”按钮的用户。

**OnCancel** - 应用如何响应在 SharePoint 中单击或点击“取消”按钮的用户。

SelectedListItemID - SharePoint 列表中选定项的项 ID。

Data Source – 包含窗体将显示、编辑或创建的记录的列表。 请注意，如果更改此属性，则 Selected 和 SelectedItemID 属性可能会停止工作。

## <a name="customize-the-default-form"></a>自定义默认窗体
至此，已更深入了解默认生成的表单和 SharePointIntegration 控件，现在可以更改公式来进一步自定义表单。 下面是自定义窗体时需要注意一些事项：

* 若要针对创建、显示或编辑项创建单独的自定义体验，请设置 SharePointIntegration 控件的 OnNew、OnView，或 OnEdit 公式，以设置变量或导航到不同屏幕。

* 使用 SharePointIntegration 控件的 OnSave 公式，可自定义如何响应在 SharePoint 中单击或点击“保存”的用户。 如果有多个窗体，请确保只提交当前正在使用的窗体的更改。

  > [!TIP]
  >    为 OnNew、OnView 和 OnEdit 公式中的变量设置不同的值。 你可以在 OnSave 公式中使用此变量，以确定正在使用的窗体。

* 请务必在所有表单的 OnSuccess 公式中添加 RequestHide()。 如果忘记了此操作，SharePoint 将不知道何时隐藏窗体。

* 当用户单击或点击 SharePoint 中的“取消”，你将无法控制窗体的隐藏，因此，请确保在 SharePointIntegration 控件的 OnCancel 公式中重置窗体。

* SharePointIntegration 控件的属性可能无法在 OnStart 或 OnVisible 中使用，并且这些事件在加载列表后只执行一次。 可使用 OnNew、OnView 或 OnEdit 公式，在每次向用户显示窗体之前运行逻辑。 
