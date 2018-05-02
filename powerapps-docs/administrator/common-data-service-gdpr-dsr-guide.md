---
title: 客户编写数据的 DSR 指南 | Microsoft Docs
description: 客户编写数据的 PowerApps DSR 指南
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/17/2018
ms.author: paulliew
ms.openlocfilehash: cff822e24f1384833caa0baa945a7d3d07a8ee9b
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-customer-data-in-common-data-service-for-apps"></a>响应数据主体权限 (DSR) 对 Common Data Service for Apps 中客户数据的请求

## <a name="introduction-to-dsr-requests"></a>DSR 请求简介
在履行一般数据保护条例 (GDPR) 过程中，作为与你合作的承诺的一部分，我们创建了此文档来帮助你做好准备。 本文档不仅介绍要为 GDPR 进行的准备工作，还分享了一些可以立即采取的步骤示例，在使用 PowerApps、Microsoft Flow 和 Common Data Service (CDS) for Apps 时，Microsoft 将提供对 GDPR 合规性的支持。

GDPR 为用户（在条例中称为“数据主体”）提供权限来管理由雇主或其他类型机构或组织收集的个人数据（称为“数据控制者”或简称为“控制者”）。 在 GDPR 下，个人数据被定义为与一个确定或可识别的自然人相关的任何数据。 GDPR 向数据主体授予其个人数据的特定权限；这些权限包括获取个人数据副本、请求更正数据、限制数据处理、删除数据，或以电子格式接收数据，以此数据可以转移给另一个控制者。 数据主体向控制者发出的在其个人数据上执行操作的正式请求称为“数据主体权限 (DSR) 请求”。

本指南讨论了如何使用 Microsoft 的产品、服务和管理工具，以帮助我们的控制者客户发现并处理个人数据，从而响应 DSR 请求。 具体而言，这包括如何查找、访问和处理驻留在 Microsoft 云中的个人数据。 以下是本指南中所述过程的快速概览：

1. 发现 — 使用搜索和发现工具轻松找到可能是 DSR 请求主体的客户数据。 一旦收集了潜在的响应性文档，就可以执行以下步骤中描述的一个或多个 DSR 操作来响应请求。 或者，可以确定请求不符合组织用于响应 DSR 请求的指导原则。

2. 访问 — 检索驻留在 Microsoft 云中的个人数据，如果收到请求，则复制一份副本以供数据主体使用。

3. 纠正 — 在适用情况下，对个人数据进行更改或执行其他请求的操作。

4. 限制 — 限制对个人数据的处理，可以通过取消各种在线服务的许可证，或者在可能的情况下关闭所需的服务。 此外还可以从 Microsoft 云中删除数据，并将其保留在本地或另一个位置。

5. 删除 — 永久删除驻留在 Microsoft 云中的个人数据。

6. 导出 — 向数据主体提供个人数据的电子副本（采用计算机可读格式）。

本指南中的每一节都概述了数据控制者组织可以采取的技术步骤，以响应 DSR 对 Microsoft 云中个人数据的请求。

## <a name="common-data-service-customer-data"></a>Common Data Service 客户数据

> [!IMPORTANT]
> 适用于 Common Data Service for Apps 和 Common Data Service（先前版本）

有两种类型的 Common Data Service (CDS) - CDS for Apps 和先前版本的 CDS，每一种类型都有不同的进程来处理个人数据。

通过以下这些来自 [PowerApps 网站](https://web.powerapps.com)的步骤，可以确定你所拥有的 CDS 环境类型：

1.  从“环境”下拉列表中选择“环境”。
2.  导航到“数据” > “实体”。

    如果这些实体显示以下内容，则你的环境为 CDS for Apps：

    ![PowerApps 实体列表](./media/common-data-service-gdpr-dsr-guide/powerapps-entities-list.png)

    如果这些实体显示以下内容，则你的环境为先前版本的 CDS：

    ![PowerApps 旧实体列表](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-list.png)

在确定你所拥有的 CDS 环境类型之后，可以按照本文档中的相应部分来识别个人数据。

> [!NOTE]
> 你可能在 CDS for Apps 和 CDS（先前版本）中都有一些环境，因此需要重复下面列出的针对组织各环境的过程。

## <a name="user-personal-data-in-common-data-service-for-apps"></a>Common Data Service for Apps 中的用户个人数据

### <a name="prerequisites"></a>先决条件
用户必须在 Office 365 管理中心创建，并向其分配适当的 Common Data Service 用户许可证来访问 CDS。  在用户开始使用 Common Data Service 之前，还需要一个安全角色。

用户个人数据保存在 Office 365 管理中心和 CDS 系统用户实体中。  在 Office 365 管理中心，保存和维护了一组标准的用户个人数据（例如用户名、用户 ID、电话、电子邮件和地址）。 这组用户个人数据被同步到所有环境中的 CDS 系统用户实体。  系统管理员只能在 Office 365 管理中心更新这组个人数据，然后这些属性会自动同步到 CDS for Apps。 系统管理员还可以创建自定义属性，以便在 CDS 系统用户实体中获取其他用户个人数据。  这些自定义属性由系统管理员在 CDS 中手动维护和管理。

从 Office 365 管理中心删除用户时，用户记录不会自动从 CDS 系统用户实体中删除，以避免可能对组织运作至关重要的业务应用程序的中断。  CDS 系统管理员需采取措施，以便从使用该应用程序的 CDS 中查找和删除用户个人数据。

只有拥有 Office 365 全局管理员角色和 CDS 系统管理员安全角色的用户才能执行下面列出的发现、纠正、导出和删除操作。

### <a name="discover"></a>发现

系统管理员可以创建多个 CDS 实例。  这些实例可用于试验、开发或生产目的。   每一个实例都具有系统用户实体副本，其中包含系统管理员可能已添加的任何自定义属性，以及自 Office 365 管理中心同步的用户个人数据。

系统管理员可以通过从 PowerApps 管理中心导航到 Dynamics 365 管理中心，找到所有 CDS 实例列表。

从 [PowerApps 管理中心](https://admin.powerapps.com/)：

1.  导航到“环境”选项卡。
2.  从“环境”列表中选择一个环境。
3.  单击“Dynamics 365 管理中心”链接。

    ![PowerApps 环境详细信息](./media/common-data-service-gdpr-dsr-guide/powerapps-environment-details.png)

    将显示所有实例列表。

    ![PowerApps 实例选取器](./media/common-data-service-gdpr-dsr-guide/powerapps-instance-picker.png)

可以在下面找到来自 CDS 用户的个人数据：

|包含个人数据的资源 | 用途 | 网站访问 | 编程访问
| --- | --- | --- | ---
| 实体记录 | 系统用户实体 | [PowerApps 管理中心](https://admin.powerapps.com) | [通过 Web API](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)
| 审核历史记录 | 若要允许客户表示用户在实体级别创建、访问、更改或删除的资源。 | [PowerApps 管理中心](https://admin.powerapps.com) | [通过 Web API](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)

#### <a name="user"></a>用户
在 Office 365 管理中心维护和管理的用户个人数据存储在 Azure Active Directory 中。  这些个人数据是在 Office 365 管理中心进行管理的，并自动同步到所有 CDS 环境中。  系统管理员不能在用户处于活动状态时直接在 CDS 中更新这些个人数据，它必须在 Office 365 管理中心内直接更新。  其他个人数据（例如自定义属性）可以直接添加到 CDS 中，并且需要由系统管理员手动维护和管理。

CDS 系统管理员可以通过以下步骤找到用户并找到与给定用户相关联的个人数据：

从 [PowerApps 管理中心](https://admin.powerapps.com/)：

1.  导航到“环境”选项卡。
2.  从“环境”列表选择一个环境。
3.  单击“Dynamics 365 管理中心”链接。
4.  单击环境的名称。
5.  单击“打开”按钮。
6.  导航到“设置” > “安全”。
7.  单击“用户”。
8.  在“搜索”输入框中输入用户。
9.  单击“搜索”按钮。
10. 双击用户。

    ![PowerApps 用户表单](./media/common-data-service-gdpr-dsr-guide/powerapps-user-form.png)

#### <a name="audit-history"></a>审核历史记录
当在 Common Data Service 中为实体[启用审核跟踪](https://docs.microsoft.com/dynamics365/customer-engagement/admin/audit-data-user-activity)时，用户个人数据将与用户执行的事件一同记录到审核历史记录中。

### <a name="rectify"></a>纠正

如果数据主体要求纠正驻留在组织数据中的个人数据，你和你的组织需要确定是否可以接受此请求。  纠正数据可能包括采取诸如编辑、编校或从文档或其他类型或项目中删除个人数据等操作。

可以使用 Azure Active Directory 来管理 Common Data Service for Apps 中的终端用户身份（个人数据）。 企业客户可以管理 DSR 纠正请求，包括根据给定的 Microsoft 服务的性质进行有限的编辑功能。  作为数据处理方，Microsoft 不提供纠正系统生成的日志的功能，因为它们反映真实性活动，并构成 Microsoft 服务内部事件的历史记录。 有关详细信息，请参阅 [GDPR：数据主体请求 (DSR)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)。

一旦用户记录从 Azure Active Directory 中删除，系统管理员就可以从所有实例中删除用户的任何剩余个人数据（比如他们可能添加的自定义属性）。  

### <a name="export"></a>导出

#### <a name="system-user"></a>系统用户
存储在系统用户实体中的用户个人数据可以从门户的用户列表中导出到 Excel。

从 [PowerApps 管理中心](https://admin.powerapps.com/)：

1.  导航到“环境”选项卡。
2.  从“环境”列表选择一个环境。
3.  单击“Dynamics 365 管理中心”链接。
4.  单击环境的名称。
5.  单击“打开”按钮。导航到“设置”>“安全”。
6.  选择“已启用的用户”视图。
7.  单击“导出到 Excel”按钮。

#### <a name="audit-history"></a>审核历史记录
可以通过下面所述的步骤从应用程序捕获和复制审核历史记录的屏幕截图。
从 [PowerApps 管理中心](https://admin.powerapps.com/)，
1.  导航到“环境”选项卡。
2.  从“环境”列表选择一个环境。
3.  单击“Dynamics 365 管理中心”链接。
4.  单击环境的名称。
5.  单击“打开”按钮。
6.  导航到“设置“>“审核”。

    ![PowerApps 审核历史记录菜单](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-menu.png)

7.  单击“审核摘要”视图。
8.  找到用户审核记录。

    ![PowerApps 审核历史记录详细信息](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-details.png)

9.  按 Alt-PrtScn 捕获屏幕截图。
10. 将屏幕截图保存到文件中。
11. 然后可以将文件发送给 DSR 请求者。

### <a name="delete"></a>删除

#### <a name="user"></a>用户
从 Office 365 管理中心删除用户时，用户状态将在 CDS 中设置为“已禁用”；然而，用户个人数据不会自动删除，以避免可能对组织运作至关重要的业务应用程序的中断。
若要从 CDS 删除用户个人数据，系统管理员需手动删除禁用用户的个人数据。

#### <a name="remove-user-personal-data-via-user-form"></a>通过用户表单删除用户个人数据
当用户记录从 Azure Active Directory 中删除时，将在用户表单上显示以下消息。
此用户信息不再由 Office 365 管理。 可以通过删除或替换与该用户相关联的所有个人数据来更新此记录以响应 DSR 请求。

从 [PowerApps 管理中心](https://admin.powerapps.com/)，
1.  导航到“环境”选项卡。
2.  从“环境”列表选择一个环境。
3.  单击“Dynamics 365 管理中心”链接。
4.  单击环境的名称。
5.  单击“打开”按钮。
6.  单击“设置” > “安全” > “用户”。
7.  选择“已禁用的用户”视图。
8.  在“搜索记录”中输入用户名称，并单击“搜索”按钮。
9.  双击搜索结果中的用户名。
10. 删除所有个人数据，然后单击“保存”。

#### <a name="remove-user-personal-data-via-excel-importexport"></a>通过 Excel 导入/导出删除用户个人数据
1.  单击“设置” > “安全” > “用户”。
2.  选择“已禁用的用户”视图。
3.  创建 Excel 模板，其中包含想要更新的所有用户个人数据列。
4.  单击“下载文件”
5.  打开下载的 Excel 文件进行更新，然后保存该文件。
6.  返回“已禁用的用户”视图窗口，然后单击“导入数据”。
7.  在“上传数据文件”对话框中选择更新的 Excel。
8.  请在“映射字段”窗口上执行所有必要的更改。
9.  单击“下一步”并提交。

有关使用 Excel 模板的信息，请参阅[其他 Excel 信息](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/analyze-your-data-with-excel-templates)。


#### <a name="remove-audit-history-via-the-audit-summary-view-form"></a>通过“审核摘要”视图窗体删除审核历史记录

从 [PowerApps 管理中心](https://admin.powerapps.com/)，
1.  导航到“环境”选项卡。
2.  从“环境”列表选择一个环境。
3.  单击“Dynamics 365 管理中心”链接。
4.  单击环境的名称。
5.  单击“打开”按钮。
6.  单击“设置”>“审核”。
7.  选择“审核摘要”视图。
8.  找到用户执行的更改历史记录
9.  单击相关行中的复选框。
10. 单击“删除更改历史记录”图标。

## <a name="personal-data-stored-in-common-data-service-for-apps-databases"></a>存储在 Common Data Service for Apps 数据库中的个人数据

### <a name="prerequisites"></a>先决条件
可以将个人（如你自己的客户）的个人数据存储在 CDS 实体内容中。  

当某个人向组织提交 DSR 请求时，CDS 系统管理员将需要查找应用程序中个人可能引用的所有实体。  CDS 管理员负责维护你正在使用的各个实体内在其中存储个人数据的清单，以便你能够响应来自个人的 DSR 请求。

然后，内容中的个人数据可以在一个实体中使用产品功能导出、纠正或删除。  

### <a name="discover"></a>发现
当 CDS 管理员收到来自某个人的 DSR 请求时，管理员需要确定哪些环境/CDS 实例包含此人的个人数据。  应制定策略和过程来维护已决定在其中存储来自个人的个人数据的环境、实例和实体清单，以帮助识别存储在内容中的个人数据。

使用在其中存储个人数据的环境、实例、实体和字段清单，可以配置 CDS 搜索引擎来发现个人数据。  CDS 管理员可以配置搜索实体和字段 — 请参阅[配置相关性搜索](https://go.microsoft.com/fwlink/?linkid=872506)获取详细信息。
然后，CDS 管理员可以访问 CDS 环境并执行搜索。

1.  单击“搜索”图标。
2.  选择“相关性搜索”

    ![PowerApps 相关性搜索菜单](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3.  在“搜索”框中输入个人的个人数据。
4.  单击“搜索”按钮。

    ![PowerApps 相关性搜索结果](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

内容中的个人数据通常存储在关键实体中，例如帐户、联系人、潜在客户、机会等等，但你有责任维护存储个人的个人数据的清单。

### <a name="rectify"></a>纠正
CDS 系统管理员可以通过使用“相关性搜索”的结果列表来更新个人的个人数据。  但是，你也可能已经将此人的个人数据存储在其他自定义实体中。  CDS 系统管理员负责维护这些其他自定义实体清单，并对个人的个人数据进行适当的更新。

从相关性搜索结果中：

1.  单击已找到个人的个人数据的项。
2.  在适当情况下更新个人的个人数据。
3.  单击“保存”

    ![PowerApps 帐户详细信息](./media/common-data-service-gdpr-dsr-guide/powerapps-account-details.png)

### <a name="export"></a>导出
可以通过下面列出的步骤，捕获数据的屏幕截图并与 DSR 请求者共享。

从 [PowerApps 管理中心](https://admin.powerapps.com/)，
1.  导航到“环境”选项卡。
2.  从“环境”列表选择一个环境。
3.  单击“Dynamics 365 管理中心”链接。
4.  单击环境的名称。
5.  单击“搜索”图标。
6.  选择“相关性搜索”。
7.  在“搜索”框中输入个人的个人数据。
8.  单击“搜索”按钮。
9.  找到项并双击。
10. 按 <alt> <PrtScn> 捕获屏幕截图。
11. 将屏幕截图保存到文件中。
12. 然后可以将文件发送给 DSR 请求者。

### <a name="delete"></a>删除

CDS 管理员可以从存储该数据的记录中删除个人的个人数据。  CDS 管理员可以选择 (1) 删除存储个人数据的记录，或 (2) 从记录中删除个人数据的内容。  

> [!NOTE]
> CDS 管理员可以自定义环境，以防止记录从实体中删除。 如果以这种方式进行配置，将需要从记录中删除个人数据的内容，而不是删除记录本身。

从相关性搜索结果中，
1.  单击已找到个人的个人数据的项。
2.  单击功能区上的“删除”图标（注意：如果不能删除记录，将禁用此图标）。

    ![PowerApps 帐户删除](./media/common-data-service-gdpr-dsr-guide/powerapps-account-delete.png)

## <a name="personal-data-stored-in-common-data-service-previous-version-databases"></a>存储在 Common Data Service（先前版本）数据库中的个人数据

### <a name="prerequisites"></a>先决条件

可以将个人（如你自己的客户或用户）的个人数据存储在 CDS 实体内容中。  

当某个人向组织提交 DSR 请求时，CDS 系统管理员将需要查找应用程序中个人可能引用的所有实体。  CDS 管理员负责维护你正在使用的各个实体内在其中存储个人数据的清单，以便你能够响应来自个人的 DSR 请求。

然后，内容中的个人数据可以在一个实体中使用产品功能导出、纠正或删除。  

### <a name="discover"></a>发现
当 CDS 管理员收到来自某个人的 DSR 请求时，管理员需要确定哪些环境/CDS 实例包含此人的个人数据。  应制定策略和过程来维护已决定在其中存储来自个人的个人数据的环境、实例和实体清单，以帮助识别存储在内容中的个人数据。

可以在下面找到来自个人的个人数据：

|包含个人数据的资源 | 用途 | 网站访问 |    编程访问
| --- | --- | --- | ---
|实体记录 | 若要在各自的业务实体中捕获业务事务。 | PowerApps Maker 门户 |    否

#### <a name="entity-records"></a>实体记录
个人的个人数据可以存储在任何业务实体中。
此版本 Common Data Service 包含它自己的数据库架构和基础结构。  它有自己的实体，并且这些实体的管理是通过 [PowerApps 网站](http://web.powerapps.com/)进行管理。

若要查看你的实体列表：

1.  选择环境

    ![PowerApps 旧实体](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2.  导航到“数据” > “实体”选项卡。
3.  选择实体，例如“帐户”实体。

    ![PowerApps 旧实体详细信息列表](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

4.  单击实体。
5.  单击“数据”选项卡。将显示实体的记录列表。

    ![PowerApps 旧帐户数据](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

6.  单击“导出数据”图标。
7.  导出完成后，请打开 Excel 工作表。
8.  单击“启用编辑”框。
9.  单击“查找”和“搜索”图标。
10. 输入要搜索的个人信息。
内容中的个人数据通常存储在关键实体中，例如帐户、联系人、潜在客户、机会、工作人员等等，但你有责任维护存储个人的个人数据的清单。
11. 使用存储个人数据的实体的库存列表，**重复上述步骤，以便每个业务实体发现个人的个人数据**。

### <a name="rectify"></a>纠正
如果数据主体要求纠正驻留在组织数据中的个人数据，你和你的组织需要确定是否可以接受此请求。  纠正数据可能包括采取诸如编辑、编校或从文档或其他类型或项目中删除个人数据等操作。

可以使用 Azure Active Directory 来管理 Common Data Service for Apps 中的终端用户身份（个人数据）。 企业客户可以管理 DSR 纠正请求，包括根据给定的 Microsoft 服务的性质进行有限的编辑功能。  作为数据处理方，Microsoft 不提供纠正系统生成的日志的功能，因为它反映真实性活动，并构成 Microsoft 服务内部事件的历史记录。  

有关详细信息，请参阅 [GDPR：数据主体请求 (DSR)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)。

若要纠正驻留在 CDS 环境中的个人数据，可以将实体数据导出到 Excel 工作表，更新它，然后将更新导入回数据库。
CDS 管理员负责标识在其中存储个人的个人数据的所有实体，并为每个实体重复以下步骤。

从 [PowerApps 网站](http://web.powerapps.com/)：

1.  单击“数据” > “实体”。
2.  单击实体，例如 “帐户”。
3.  单击“数据”选项。
4.  单击“导出数据”图标。
5.  单击“在 Excel 中打开”图标（完成导出操作后）。
6.  在 Excel 工作表上启用编辑，并更新个人数据。
7.  保存更新的工作表（执行“另存为”操作，以便知晓文件所在位置）。

    ![PowerApps 旧帐户数据](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

8.  进行必要的个人数据更新
9.  保存更新
10. 在“数据”>“实体”>“帐户”窗体上，单击“导入数据”图标。
11. 单击“搜索”框。
12. 选择包含更新的文件。
13. 单击“打开”框。
14. 单击“导入”按钮。

### <a name="export"></a>导出

可以查看每个实体中的个人数据并将其导出到 Excel 工作表中。

从 [PowerApps 网站](http://web.powerapps.com/)：

1.  导航到“数据” > “实体”。
2.  选择要查看的实体并导出数据。
3.  单击“数据”选项。
4.  单击“导出数据”图标。 此导出操作在后台运行，完成后将收到通知。
5. 若要查看导出的数据，请单击“在 Excel 中打开”图标。

### <a name="delete"></a>删除
可以通过使用“导出/导入数据”功能，删除存储在实体中的个人数据。

CDS 管理员负责标识包含个人的个人数据的所有实体，并为每个实体重复以下步骤。

从 [PowerApps 网站](http://web.powerapps.com/)：

1.  单击“数据” > “实体”。
2.  向下滚动“实体”列表并找到想要删除个人数据的实体。
3.  单击实体。
4.  单击“数据”选项。
5.  单击“导出数据”图标。
6.  单击“在 Excel 中打开”图标（完成导出操作后）。
7.  Excel 工作表上启用编辑。
8.  保存更新的工作表（执行“另存为”操作，以便知晓文件所在位置）。
9.  删除想要删除的个人数据记录的行。
10. 保存更新
11. 在“实体”窗体上，单击“导入数据”图标。
12. 单击“搜索”框。
13. 选择包含更新的文件。
14. 单击“打开”框。
15. 单击“导入”按钮。
