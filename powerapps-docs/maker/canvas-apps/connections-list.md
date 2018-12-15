---
title: 用于画布应用的连接器概述 | Microsoft Docs
description: 可用于构建画布应用的所有可用连接概述
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/28/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f7a053aff947ffd543381956cf725a7e656d8a65
ms.sourcegitcommit: ebe0a9c41b693a2134e9198ffc7e7a8eabee4330
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "51276363"
---
# <a name="overview-of-canvas-app-connectors-for-powerapps"></a>PowerApps 画布应用连接器概述
数据是大多数应用（包括在 PowerApps 中生成的应用）的关键所在。 数据存储在数据源中，应用是通过创建的连接来连接数据。 连接使用特定的连接器与数据源进行通信。 PowerApps 提供连接器，适用于许多常用服务和本地数据源，包括 SharePoint、SQL Server、Office 365、Salesforce 和 Twitter。 若要开始向画布应用添加数据，请参阅[在 PowerApps 中添加数据连接](add-data-connection.md)。

连接器可能会提供数据或操作的表。 某些连接器仅提供表，某些连接器仅提供操作，而某些连接器会提供两者。 此外，你的连接器可能是标准连接器或自定义连接器。

## <a name="tables"></a>表

如果你的连接器提供表，则添加数据源，然后选择要管理的数据源中的表。 PowerApps 会将表数据检索到应用中并为你更新数据源中的数据。 例如，可以添加一个包含名为 Lessons 的表的数据源，然后在编辑栏中将控件的 Items 属性（如库或表单）设置为以下值：

 ![纯数据源 Items 属性](./media/connections-list/ItemPropertyPlain.png)

通过自定义用于显示数据的控件的 Items 属性，你可以指定应用检索的数据。 继续前面的示例，通过将该名称用作 Search 和 SortByColumn 函数的参数，你可以对 Lessons 表中的数据进行排序或筛选。 在此图中，Items 属性所设置的公式指定基于 **TextSearchBox1** 中的文本对数据进行排序和筛选。 

 ![扩展数据源 Items 属性](./media/connections-list/ItemPropertyExpanded.png)

有关如何使用表自定义公式的详细信息，请参阅以下主题：

  [了解 PowerApps 中的数据源](working-with-data-sources.md)<br> 
  [通过 Excel 数据生成应用](get-started-create-from-data.md)<br> 
  [从头开始创建应用](get-started-create-from-blank.md)<br>
  [了解 PowerApp 中的表格和记录](working-with-tables.md)

  > [!NOTE]
  > 若要连接到 Excel 工作簿数据，工作簿必须托管在 OneDrive 等云存储服务中。 有关详细信息，请参阅[从 PowerApps 连接到云存储](connections/cloud-storage-blob-connections.md)。

## <a name="actions"></a>操作

如果你的连接器提供操作，则必须与前面一样仍选择数据源。 而不是选择表作为下一步，但是，通过编辑将显示数据的控件的 Items 属性，可以手动将控件连接到操作。 Items 属性所设置的公式指定用于检索数据的操作。 例如，如果连接到 Yammer，然后将 Items 属性设置为数据源的名称，则应用不会检索任何数据。 若要用数据填充控件，请指定 **GetMessagesInGroup(5033622).messages** 等操作。

![操作数据源 Items 属性](./media/connections-list/ItemPropertyAction.png)

如果需要处理操作连接器的自定义数据更新，请生成包含 Patch 函数的公式。 在公式中，标识操作以及将绑定到操作的字段。  

有关如何为自定义更新自定义公式的详细信息，请参阅以下主题：

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

## <a name="popular-connectors"></a>常用连接器

单击下表中列出的链接，可详细了解最常用的连接器。 若要获取连接器的完整列表，请参阅[所有的连接器](#all-standard-connectors)。

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive for Business](./media/connections-list/onedrive.png) |[**OneDrive for Business**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Office 365 用户](./media/connections-list/office365.png) |[**Office 365 用户**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="standard-and-custom-connectors"></a>标准和自定义连接器
PowerApps 为多个常用数据源（如上面列出的数据源）提供标准连接器。 如果 PowerApps 的标准连接器适用于要使用的数据源的类型，则应使用该连接器。 如果要连接到其他类型的数据源（如已构建的服务），请参阅[注册和使用自定义连接器](../canvas-apps/register-custom-api.md)。

## <a name="all-standard-connectors"></a>所有标准连接器
请参阅 [Microsoft 连接器参考](https://docs.microsoft.com/connectors/)，查看所有标准连接器的列表。 高级连接器需要具备 PowerApps 计划 1 或计划 2。 有关详细信息，请参阅 [PowerApps 计划](https://powerapps.microsoft.com/pricing/)。

你可以在 [PowerApps 论坛](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)中提出有关具体连接器的问题，也可以建议添加连接器或在 [PowerApps 建议](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas)中做出其他改进。
