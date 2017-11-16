---
title: "了解 SharePoint 窗体集成 | Microsoft 文档"
description: "了解如何自定义适用于 SharePoint 的窗体"
services: 
suite: powerapps
documentationcenter: na
author: sarafankit
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/11/2017
ms.author: ankitsar
ms.openlocfilehash: 2bb6aae9ab460e4fc03f6c7e3243f47da0ffe455
ms.sourcegitcommit: ce66ba8eadc41d5f260217d164f8317b90ae1504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2017
---
# <a name="understand-sharepoint-forms-integration"></a>了解 SharePoint 窗体集成
现在可以在 PowerApps 中轻松[自定义任何 SharePoint 列表窗体](customize-list-form.md)。 在本文中，我们将详细演示这些窗体的工作原理，以及如何对其作进一步的自定义。

如果你已自定义 SharePoint 列表窗体，则可能已经注意到默认生成的窗体适用于所有操作，如创建、显示或编辑项。 此操作是借助生成的公式和 SharePointIntegration 控件来实现的。

## <a name="understand-the-default-generated-form"></a>了解默认生成的窗体

默认生成的窗体包含以下控件及其相应默认值：

* FormScreen1 - 这是包含窗体的[屏幕](./controls/control-screen.md)。

* SharePointForm1 - 这是用于创建、显示，或编辑列表项的[窗体](working-with-forms.md)。

    * Data Source - 已为其自定义窗体的列表。

    * Item - 从列表中选定的项。 在 PowerApps Studio 中工作时，为方便起见，这在列表中将设置为 First() 项。

        **If(IsBlank(SharePointIntegration.Selected) || IsEmpty(SharePointIntegration.Selected),First('YourListName**'),SharePointIntegration.Selected)**

    * OnSuccess - 一旦成功创建或保存项，则将重置窗体并且 SharePoint 会隐藏窗体。

        ResetForm(SharePointForm1); RequestHide()

* SharePointIntegration - 负责在 SharePoint 和 PowerApps 之间沟通用户操作的控件。

    * Data Source - 已为其自定义窗体的列表。

        **'YourListName**'**

    * OnNew - 在新模式中设置“SharePointForm1”。

        NewForm(SharePointForm1)

    * OnView - 在视图模式中设置“SharePointForm1”。

        ViewForm(SharePointForm1)

    * OnEdit - 在编辑模式中设置“SharePointForm1”。

        EditForm(SharePointForm1)

    * OnSave - 提交对 SharePointForm1 的更改。 成功提交窗体时，将执行 SharePointForm1.OnSuccess 公式。

        SubmitForm(SharePointForm1)

    * OnCancel - 重置对 SharePointForm1 的更改。 当用户在 SharePoint 中单击或点击“取消”时，SharePoint 将始终隐藏窗体。

        SubmitForm(SharePointForm1)

这些默认设置将确保窗体在 SharePoint 中运行时正常工作。 当用户在 SharePoint 中与之交互时，它们会更改 PowerApps 的窗体模式，并确保这些更改会被提交到 SharePoint。

## <a name="understand-the-sharepointintegration-control"></a>了解 SharePointIntegration 控件
SharePointIntegration 控件在 SharePoint 和 PowerApps 之间沟通用户操作。

![](./media/sharepoint-form-integration/sharepointintegration-object.png)

>[!NOTE]
>SharePointIntegration 控件的属性仅当窗体在 SharePoint 中运行时才可用，并且在 PowerApps studio 中自定义窗体时无法访问这些属性。

SharePointIntegration 控件具有以下属性：

Selected - SharePoint 列表中的选定项。

OnNew - 当用户单击或点击 SharePoint 中的“新建”按钮或打开“创建项”窗体时，应用的响应方式。

OnView - 当用户单击或点击 SharePoint 中的“项”或打开“项详细信息”窗体时，应用的响应方式。

OnEdit - 当用户单击或点击 SharePoint 中的“编辑全部”按钮或打开“编辑项”窗体时，应用的响应方式。

OnSave - 当用户单击或点击 SharePoint 中的“保存”按钮时，应用的响应方式。

OnCancel - 当用户单击或点击 SharePoint 中的“取消”按钮时，应用的响应方式。

SelectedListItemID - SharePoint 列表中选定项的项 ID。

Data Source – 包含窗体将显示、编辑或创建的记录的列表。 请注意，如果更改此属性，则 Selected 和 SelectedItemID 属性可能会停止工作。

## <a name="customize-the-default-form"></a>自定义默认窗体

至此，你对默认生成的窗体和 SharePointIntegration 控件已经有了很好的了解，接下来请继续学习如何更改公式以进一步自定义窗体。 下面是自定义窗体时需要注意一些事项：

* 若要针对创建、显示或编辑项创建单独的自定义体验，请设置 SharePointIntegration 控件的 OnNew、OnView，或 OnEdit 公式，以设置变量或导航到不同屏幕。

* 使用 SharePointIntegration 控件的 OnSave 公式，可自定义当用户单击或点击 SharePoint 中的“保存”时会发生的情况。 如果有多个窗体，请确保只提交当前正在使用的窗体的更改。

    >[!TIP]
     为 OnNew、OnView 和 OnEdit 公式中的变量设置不同的值。 你可以在 OnSave 公式中使用此变量，以确定正在使用的窗体。

* 请确保在所有窗体的 OnSuccess 中包含 RequestHide()。 如果忘记了此操作，SharePoint 将不知道何时隐藏窗体。

* 当用户单击或点击 SharePoint 中的“取消”，你将无法控制窗体的隐藏，因此，请确保在 SharePointIntegration 控件的 OnCancel 公式中重置窗体。
