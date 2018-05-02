---
title: 在应用中添加数据连接 | Microsoft 文档
description: 在现有应用或空白应用中添加数据连接
documentationcenter: na
author: lancedMicrosoft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 04/06/2018
ms.author: lanced
ms.openlocfilehash: 44ee7b992f5817a5d6b8d791b05e1db671d3e6ba
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="add-a-data-connection-in-powerapps"></a>在 PowerApps 中添加数据连接
在 PowerApps 中，向现有应用或从头开始生成的应用添加数据连接。 应用可以连接到 SharePoint、Salesforce、OneDrive 或[许多其他数据源](connections-list.md)。

阅读完本文的[后续步骤](#next-steps)是，在应用中显示和管理相应数据源中的数据，如下面这些示例所述：

* 连接到 OneDrive，并在应用中管理 Excel 工作簿中的数据。
* 连接到 Twilio，并从应用发送短信。
* 连接 SQL Server，然后通过应用更新表。

## <a name="prerequisites"></a>先决条件
[注册](../signup-for-powerapps.md) PowerApps，然后使用注册所用的同一凭据[登录](http://web.powerapps.com)。

## <a name="add-a-data-source"></a>添加数据源
1. 在“主页”选项卡上，将鼠标悬停在“从空白开始”磁贴上方，然后选择“生成此应用”。

    ![从头开始创建应用](./media/add-data-connection/blank-app-tile.png)

1. 如果出现“欢迎使用 PowerApps Studio”对话框，则单击“跳过”。

3. 在中心窗格中，单击或点击“连接到数据”。

4. 如果“数据”窗格中的连接列表包含要使用的连接，请选择相应连接，将其添加到应用中。 否则，请跳到下一步。

    ![添加数据源](./media/add-data-connection/choose-existing-connections.png)

5. 选择“新建连接”，查看连接器列表。

    ![添加连接](./media/add-data-connection/new-connection.png)

6. 滚动浏览连接器列表，直到发现要创建的连接类型（例如，Office 365 Outlook），然后选择此类型。

    ![选择连接](./media/add-data-connection/choose-connection.png)

7. 选择“创建”，创建连接并将其添加到应用中。

    某些连接器（如 Office 365 Outlook）不需要执行额外步骤即可立即从中显示数据。 其他连接器将提示你提供凭据，指定一组特定的数据或执行其他步骤。 例如，[SharePoint](connections/connection-sharepoint-online.md) 和 [SQL Server](connections/connection-azure-sqldatabase.md) 需要在使用之前提供其他信息。

## <a name="add-another-data-source"></a>添加其他数据源
1. 添加你想要添加数据源的控件。

    控件必须具有“Items”属性，就像库和列表框那样，或者像窗体一样具有“Item”属性。

1. 在“数据”窗格（可自动打开）中，打开“数据源”下的列表，然后选择“添加数据源”。

1. 按照前面的过程，从步骤 4 开始。

## <a name="identify-or-change-a-data-source"></a>标识或更改数据源
如果正在更新应用，则可能需要确定或更改库、窗体或其他控件中显示的数据源。 例如，可能需要在更新应用时确定他人创建的或你在很久以前创建的数据源。

1. 选择想要为其标识或更改数据源的控件。

    例如，通过在左边缘附近的屏幕和控件的层次结构列表中单击或点击一个库（而非库中的控件）来选择此库。

    数据源的名称在右侧窗格的“属性”选项卡上显示。

2. 选择数据源以对其进行更改，或显示相关详细信息。

    ![“数据”窗格](./media/add-data-connection/data-pane.png)

3. 若要更改数据源，打开列表中的数据源，然后选择或创建另一个源。

     ![“数据”窗格](./media/add-data-connection/datasource-list.png)

## <a name="next-steps"></a>后续步骤
* 若要显示和更新数据源（如 Excel、SharePoint Online 或 SQL Server）中的数据，请先[添加库](add-gallery.md)，然后[添加窗体](add-form.md)。
* 对于其他源中的数据，请使用连接器特定的函数，例如，适用于 [Office 365 Outlook](connections/connection-office365-outlook.md)、[Twitter](connections/connection-twitter.md) 和 [Microsoft Translator](connections/connection-microsoft-translator.md) 的函数。
