---
title: 用于画布应用的连接器概述 | Microsoft Docs
description: 可用于构建画布应用的所有可用连接概述
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/19/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c0710f36b5c49037d5104ab1085d1c990290b967
ms.sourcegitcommit: 1b29cd1fa1492037ef04188dd857a911edeb4985
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80122887"
---
# <a name="overview-of-canvas-app-connectors-for-power-apps"></a>画布概述-适用于电源应用的应用连接器
数据是大多数应用程序（包括在 Power Apps 中构建的应用程序）的核心。 数据存储在数据源中，应用是通过创建的连接来连接数据。 连接使用特定的连接器与数据源进行通信。 Power Apps 为许多常用的服务和本地数据源（包括 SharePoint、SQL Server、Office 365、Salesforce 和 Twitter）提供了连接器。 若要开始将数据添加到画布应用，请参阅[在 Power Apps 中添加数据连接](add-data-connection.md)。

连接器可能会提供数据或操作的表。 某些连接器仅提供表，某些连接器仅提供操作，而某些连接器会提供两者。 此外，你的连接器可能是标准连接器或自定义连接器。

## <a name="tables"></a>表

如果你的连接器提供表，则添加数据源，然后选择要管理的数据源中的表。 Power Apps 会将表数据检索到应用程序中，并为您更新数据源中的数据。 例如，可以添加一个包含名为 Lessons 的表的数据源，然后在编辑栏中将控件的 Items 属性（如库或表单）设置为以下值：

 ![纯数据源 Items 属性](./media/connections-list/ItemPropertyPlain.png)

你可以通过自定义显示数据的控件的**Items**属性来指定你的应用程序检索的数据。 继续前面的示例，通过将该名称用作 Search 和 SortByColumn 函数的参数，你可以对 Lessons 表中的数据进行排序或筛选。 在此图中，Items 属性所设置的公式指定基于 **TextSearchBox1** 中的文本对数据进行排序和筛选。 

 ![扩展数据源 Items 属性](./media/connections-list/ItemPropertyExpanded.png)

有关如何用表自定义公式的详细信息，请参阅以下主题：

  [了解 Power Apps 中的数据源](working-with-data-sources.md)<br> 
  [通过 Excel 数据生成应用](get-started-create-from-data.md)<br> 
  [从头开始创建应用](get-started-create-from-blank.md)<br>
  [了解 Power Apps 中的表和记录](working-with-tables.md)

  > [!NOTE]
  > 若要连接到 Excel 工作簿数据，工作簿必须托管在 OneDrive 等云存储服务中。 有关详细信息，请参阅[从 Power Apps 连接到云存储](connections/cloud-storage-blob-connections.md)。

## <a name="actions"></a>Actions

如果你的连接器提供操作，则必须与前面一样仍选择数据源。 而不是选择表作为下一步，但是，通过编辑将显示数据的控件的Items 属性，可以手动将控件连接到操作。 Items 属性所设置的公式指定用于检索数据的操作。 例如，如果连接到 Yammer，然后将 Items 属性设置为数据源的名称，则应用不会检索任何数据。 若要用数据填充控件，请指定 **GetMessagesInGroup(5033622).messages** 等操作。

![操作数据源 Items 属性](./media/connections-list/ItemPropertyAction.png)

如果需要处理操作连接器的自定义数据更新，请生成包含 Patch 函数的公式。 在公式中，标识操作以及将绑定到操作的字段。  

有关如何为自定义更新自定义公式的详细信息，请参阅以下主题：

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

> [!NOTE]
>  **Power Apps 不适用于动态架构**。 短语动态架构指的是相同操作可能返回具有不同列的其他表。 可能导致表中的列不同的情况包括操作输入参数、执行该操作的用户或角色、用户在其中工作的组以及其他人。 例如，如果以不同的输入运行，SQL Server 存储过程可能会返回不同的列。 对于动态架构的操作，连接器文档显示**此操作的输出是动态的。** 作为返回值。 与此相反，Power 自动功能适用于动态架构，并可能为你的方案提供了解决方法。

## <a name="popular-connectors"></a>常用连接器

单击下表中列出的链接，可详细了解最常用的连接器。 若要获取连接器的完整列表，请参阅[所有的连接器](https://docs.microsoft.com/connectors/)。

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](connections/connection-common-data-service.md) |&nbsp; |![云存储](./media/connections-list/onedrive.png) |[**云存储**](connections/cloud-storage-blob-connections.md) ** |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; | ![Dynamics AX](./media/connections-list/dynamics-ax.png) |[**Dynamics AX**](connections/connection-dynamicsax.md) |
|![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |&nbsp; |![Microsoft Translator](./media/connections-list/microsoft-translator.png) |[**Microsoft Translator**](connections/connection-microsoft-translator.md) |
|![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |&nbsp; | ![Office 365 用户](./media/connections-list/office365.png) |[**Office 365 用户**](connections/connection-office365-users.md) |
| ![Oracle](./media/connections-list/oracle-icon.png) |[**联手**](connections/connection-oracledb.md) |&nbsp; | ![Power BI](./media/connections-list/powerbi.png) |[**Power BI**](connections/connection-powerbi.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; | ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) 
|![Twitter](./media/connections-list/twitter.png) |[**Twitter**](connections/connection-twitter.md)

\* * 适用于 Azure Blob、Box、Dropbox、Google Drive、OneDrive 和 OneDrive for business

## <a name="standard-and-custom-connectors"></a>标准和自定义连接器
Power Apps 为许多常用数据源提供*标准*连接器。 如果 Power Apps 为要使用的数据源类型提供了标准连接器，则应使用该连接器。 如果要连接到其他类型的数据源（如已构建的服务），请参阅[注册和使用自定义连接器](../canvas-apps/register-custom-api.md)。

## <a name="all-standard-connectors"></a>所有标准连接器
标准连接器不需要特殊许可。 有关详细信息，请参阅[电源应用计划](https://powerapps.microsoft.com/pricing/)。

可以在[Power apps 论坛](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)中提问有关特定连接器的问题，还可以建议连接器添加或其他改进功能以在[电源应用程序](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas)中进行学习。

## <a name="security-and-types-of-authentication"></a>身份验证的安全性和类型

创作应用并创建到数据源的连接时，你可能会看到你选择的连接器允许你使用不同的身份验证方式。 例如，SQL Server 连接器允许使用 Azure AD 集成、SQL Server 身份验证和 Windows 身份验证。 每种类型的身份验证都具有与之关联的不同安全级别。  务必要了解与使用应用程序的用户共享的信息和权限。 本文中的主要示例是 SQL Server 的，但原则适用于所有类型的连接。

### <a name="azure-ad-integrated"></a>Azure AD 集成

这是一种安全的连接类型。  例如，SharePoint 使用这种类型的身份验证。  SQL Server 还允许这种类型的身份验证。  在您连接时，Azure AD 服务代表您单独标识您的 SharePoint。  不需要提供用户名或密码。  作为作者，你可以使用凭据创建和使用数据源。  当你发布应用程序时，应用程序用户登录时，它们会以其凭据执行此操作。 如果在后端上对数据进行了适当的保护，则用户只能根据其凭据查看他们有权查看的内容。   这种类型的安全性使你可以在发布应用程序后，更改后端数据源上的特定应用程序用户的权限。  例如，你可以授予访问权限、拒绝访问权限，或优化用户或用户组可以在后端数据源上看到的所有内容。

### <a name="open-standard-authorization-oauth"></a>开放标准授权（OAuth）

这种类型的连接也是安全的。  例如，Twitter 使用这种类型的身份验证。  当你连接时，必须提供你的用户名和密码。  作为作者，你可以使用凭据创建和使用数据源。  当你发布应用程序时，应用程序用户登录时，还必须提供其凭据。  因此，这种类型的连接是安全的，因为用户必须使用自己的凭据来访问数据源服务。 

### <a name="sql-user-name-and-password-authentication"></a>SQL 用户名和密码身份验证

这种类型的连接不太安全，因为它不依赖于最终用户身份验证。  SQL Server 还允许这种类型的身份验证。  在 SQL Server 此类身份验证称为**SQL Server 身份验证**。  许多其他数据库数据源提供了类似的功能。  发布应用程序时，用户不需要提供唯一的用户名和密码。  他们使用创作应用程序时提供的用户名和密码。  对数据源的连接身份验证与用户**隐式共享**。  发布应用程序后，该连接也将发布并可供用户使用。  最终用户还可以使用与之共享 SQL Server 身份验证的任何连接来创建应用程序。  你的用户看不到密码的用户名，但该连接将可供他们使用。  对于这种类型的连接，有一个有效方案。  例如，如果您拥有可供公司中所有人使用的只读数据库，则此类型的连接可能有效。 

### <a name="windows-authentication"></a>Windows 身份验证

这种类型的连接不太安全，因为它不依赖于最终用户身份验证。 需要连接到**本地**数据源时，请使用 Windows 身份验证。 此类连接的一个示例是指具有 SQL Server 的本地服务器。 连接必须通过网关。 由于它通过网关，连接器可以访问该数据源中的所有数据。 因此，可使用提供的 Windows 凭据访问的任何信息都可用于连接器。 发布应用程序后，该连接也将发布并可供用户使用。  这意味着，最终用户还可以使用此相同的连接创建应用程序，并访问该计算机上的数据。 与该应用共享的用户也会**隐式共享**与数据源的连接。 当数据源仅位于本地服务器上并且该源上的数据可自由共享时，此类型的连接可能有效。
