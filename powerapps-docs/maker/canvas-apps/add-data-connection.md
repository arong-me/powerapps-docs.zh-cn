---
title: 在画布应用中添加数据连接 | Microsoft Docs
description: 在现有画布应用或空白应用中添加数据连接
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/06/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d1397f9fd2859611a3cd54023210a27cd5977834
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212276"
---
# <a name="add-a-data-connection-to-a-canvas-app-in-power-apps"></a>在 Power Apps 中向画布应用添加数据连接

在 Power Apps 中，将数据连接添加到现有画布应用或从头开始生成的应用。 您的应用程序可以连接到 SharePoint、Common Data Service、Salesforce、OneDrive 或[许多其他数据源](connections-list.md)。

阅读完本文的[后续步骤](#next-steps)是，在应用中显示和管理相应数据源中的数据，如下面这些示例所述：

* 连接到 OneDrive，并在应用中管理 Excel 工作簿中的数据。
* 连接到 Twilio，并从应用发送短信。
* 连接到 Common Data Service，并更新应用程序中的实体。
* 连接到 SQL Server，并从应用更新表。

## <a name="prerequisites"></a>先决条件

[注册](../signup-for-powerapps.md)Power Apps，并[提供注册所](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)用的相同凭据。

## <a name="open-a-blank-app"></a>打开一个空白应用

1. 在 "**主**文件夹" 选项卡上，**从空白选择画布应用**。

1. 指定应用的名称，然后选择 "**创建**"。

1. 如果出现 "**欢迎使用 Power Apps Studio** " 对话框，请选择 "**跳过**"。

## <a name="add-data-source"></a>添加数据源

1. 在中心窗格中，选择 "**连接到数据**" 以打开 "**数据**" 窗格。

    如果这是现有应用，并且该屏幕已包含控件，请选择 "**查看** > **数据源**" 以打开相同窗格。

1. 选择 "**添加数据源**"。

1. 如果连接列表包含所需的连接列表，请选择它以将其添加到应用中。 否则，请跳到下一步。

    ![选择现有连接](./media/add-data-connection/choose-existing-connection.png)

1. 选择 "**新建连接**" 以显示连接列表。

    ![添加连接](./media/add-data-connection/add-connection.png)

1. 在搜索栏中，键入或粘贴所需的连接的前几个字母，然后在出现连接时选择连接。

    ![搜索连接](./media/add-data-connection/search-connections.png)

1. 选择“创建”，创建连接并将其添加到应用中。

    某些连接器（如 Office 365 Outlook）不需要执行额外步骤即可立即从中显示数据。 其他连接器将提示你提供凭据，指定一组特定的数据或执行其他步骤。 例如，[SharePoint](connections/connection-sharepoint-online.md) 和 [SQL Server](connections/connection-azure-sqldatabase.md) 需要在使用之前提供其他信息。 使用[Common Data Service](connections/connection-common-data-service.md)，可以在选择实体之前更改环境。

## <a name="identify-or-change-a-data-source"></a>标识或更改数据源
如果正在更新应用，则可能需要确定或更改库、窗体或其他控件中显示的数据源。 例如，你可能需要在更新其他人创建的应用或在以前创建的应用时标识数据源。

1. 选择要为其标识或更改数据源的控件，如库。

    数据源的名称在右侧窗格的“属性”选项卡上显示。

    ![标识连接](./media/add-data-connection/identify-connection.png)

1. 若要显示有关数据源或更改数据源的详细信息，请选择其名称旁边的向下箭头。

    此时会显示有关当前数据源的详细信息，您可以选择或创建另一个源。

    ![更改连接](./media/add-data-connection/change-connection.png)

## <a name="next-steps"></a>后续步骤

* 若要显示和更新源（如 Excel、SharePoint、Common Data Service 或 SQL Server）中的数据，请[添加一个库](add-gallery.md)并[添加一个窗体](add-form.md)。
* 对于其他源中的数据，请使用连接器特定的函数，例如，适用于 [Office 365 Outlook](connections/connection-office365-outlook.md)、[Twitter](connections/connection-twitter.md) 和 [Microsoft Translator](connections/connection-microsoft-translator.md) 的函数。
