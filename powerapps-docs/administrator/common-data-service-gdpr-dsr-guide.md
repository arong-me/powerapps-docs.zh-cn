---
title: 响应针对 Common Data Service (CDS) for Apps 客户数据的 DSR 请求 | Microsoft Docs
description: 演练如何响应针对 Common Data Service (CDS) for Apps 客户数据的 DSR 请求
author: jamesol-msft
ms.reviewer: paulliew
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: b550d5fe7e36c36177fff017adcf9d9034c93dd4
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218041"
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-common-data-service-for-apps-customer-data"></a>响应针对 Common Data Service for Apps 客户数据的数据主体权限 (DSR) 请求

## <a name="introduction-to-dsr-requests"></a>DSR 请求简介
欧盟 (EU) 一般数据保护条例 (GDPR) 为用户（在条例中称为“数据主体”）提供了多种权限，使其有权管理由雇主或其他类型的机构或组织（称为“数据控制者”或简称为“控制者”）收集的个人数据。 在 GDPR 下，个人数据被广泛定义为与确定的或可识别的自然人相关的任何数据。 GDPR 为数据主体提供针对其个人数据的以下权限：

* 获取副本
* 请求更正
* 限制处理
* 删除个人数据
* 接收电子格式的个人数据，以便将其发送给另一个控制者

数据主体权限 (DSR) 请求是数据主体向控制者发出的正式请求，请求对其个人数据执行操作。

本文介绍 Microsoft 如何针对 GDPR 进行准备工作，还提供了一些可以采取的步骤示例，在使用 PowerApps、Microsoft Flow 和 Common Data Service (CDS) for Apps 时，提供对 GDPR 符合性的支持。 你可了解如何使用 Microsoft 产品、服务和管理工具，帮助控制者客户发现、访问并处理 Microsoft 云中的个人数据，以响应 DSR 请求。

本文介绍了以下操作：

* 发现 — 使用搜索和发现工具轻松找到可能是 DSR 请求主体的客户数据。 收集了潜在的响应性文档后，就可以执行以下一个或多个 DSR 操作，以响应请求。 或者，可以确定请求不符合组织用于响应 DSR 请求的指导原则。

* 访问 - 检索驻留在 Microsoft 云中的个人数据，如果收到请求，则复制一份可供数据主体使用的数据副本。

* 纠正 — 在适用情况下，对个人数据进行更改或执行其他请求的操作。

* 限制 — 通过移除各种在线服务的许可证，或者在可能的情况下关闭所需的服务，限制对个人数据的处理。 此外还可以从 Microsoft 云中移除数据，并将其保留在本地或另一个位置。

* 删除 - 永久删除驻留在 Microsoft 云中的个人数据。

* 导出 — 向数据主体提供个人数据的电子副本（采用计算机可读格式）。

## <a name="cds-for-apps-customer-data"></a>CDS for Apps 客户数据

> [!IMPORTANT]
> 适用于 CDS for Apps 和 Common Data Service 早期版本

CDS for Apps 和 Common Data Service (CDS) 早期版本具有与个人数据交互的单独过程。

要确定所拥有 CDS 环境的类型，可登录到 [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，并执行以下步骤：

1. 在“环境”下拉列表中，选择你的环境。
2. 在导航窗格中，单击或点击“数据”，然后单击或点击“实体”。

    如果看到以下实体列表，则环境为 CDS for Apps：

    ![PowerApps 实体列表](./media/common-data-service-gdpr-dsr-guide/powerapps-entities-list.png)

    如果看到以下实体列表，则环境为 CDS 早期版本：

    ![PowerApps 旧实体列表](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-list.png)

确定所拥有 CDS 环境的类型之后，可通过执行以下各节中的步骤来确定个人数据。

> [!NOTE]
> 你的环境可能部分属于 CDS for Apps，部分属于 CDS 早期版本，因此需要针对组织中每个环境重复下列过程。

## <a name="user-personal-data-in-cds-for-apps"></a>CDS for Apps 中的用户个人数据

### <a name="prerequisites"></a>先决条件
必须在 Office 365 管理中心创建用户，并为其分配相应的用户许可证和安全角色，以便他们能够访问和使用 CDS for Apps。

标准用户个人数据（例如用户名、用户 ID、电话、电子邮件和地址）保存在 Office 365 管理中心，并在其中得到维护。 系统管理员只能在 Office 365 管理中心更新此个人数据，然后此数据会自动同步到所有环境中的 CDS for Apps 系统用户实体。 系统管理员还可以创建自定义属性，以便在 CDS for Apps 系统用户实体中获取其他用户个人数据，然后手动维护和管理这些属性。

为避免可能对组织运作至关重要的业务应用程序出现中断，从 Office 365 管理中心删除用户时，用户记录不会自动从 CDS for Apps 系统用户实体中删除。 用户的状态在 CDS for Apps 中设置为禁用，但 CDS for Apps 系统管理员必须在应用程序中找到并删除 CDS for Apps 用户个人数据。

只有 Office 365 全局管理员和 CDS 系统管理员才能执行下面列出的发现、纠正、导出和删除操作。

### <a name="discover"></a>发现
系统管理员可以创建多个 CDS for Apps 实例。 这些实例可用于试验、开发或生产目的。 每一个实例都具有系统用户实体副本，其中包含系统管理员可能已添加的任何自定义属性，以及从 Office 365 管理中心同步的用户个人数据。

系统管理员可以通过从 PowerApps 管理中心导航到 Dynamics 365 管理中心，找到包含所有 CDS for Apps 实例的列表。

从 [PowerApps 管理中心](https://admin.powerapps.com/)执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

3.  单击或点击“Dynamics 365 管理中心”。

    ![PowerApps 环境详细信息](./media/common-data-service-gdpr-dsr-guide/powerapps-environment-details.png)

    随即显示包含所有实例的列表。

    ![PowerApps 实例选取器](./media/common-data-service-gdpr-dsr-guide/powerapps-instance-picker.png)

可以在以下资源中找到 CDS for Apps 用户的个人数据：

|资源 | 用途 | 网站访问 | 编程访问
| --- | --- | --- | ---
| 实体记录 | 称为系统用户实体，用于存储用户的个人数据。 | [PowerApps 管理中心](https://admin.powerapps.com) | 通过 [Web API](https://docs.microsoft.com/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)
| 审核历史记录 | 允许客户标识用户在实体级别创建、访问、更改或删除的资源。 | [PowerApps 管理中心](https://admin.powerapps.com) | 通过 [Web API](https://docs.microsoft.com/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)

#### <a name="user"></a>用户
用户个人数据存储在 Azure Active Directory 中，并自动同步到所有 CDS for Apps 环境。 系统管理员无法在用户处于活动状态时直接在 CDS for Apps 中更新这些个人数据 &mdash; 必须在 Office 365 管理中心进行更新。 系统管理员可以直接将个人数据（例如，自定义属性）添加到 CDS for Apps，但必须手动管理此数据。

要查找某个用户及其个人数据，请转到 [PowerApps 管理中心](https://admin.powerapps.com/)，并执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

2. 单击或点击“Dynamics 365 管理中心”，从列表中选择一个环境，然后单击或点击“打开”。

3. 转到“设置” > “安全” > “用户”。

4. 在“搜索”框中输入用户的名字，然后单击或点击“搜索”。

5. 要查看用户的个人数据，请双击用户的名字。

    ![PowerApps 用户表单](./media/common-data-service-gdpr-dsr-guide/powerapps-user-form.png)

#### <a name="audit-history"></a>审核历史记录
如果在 CDS for Apps 中为实体启用了[审核跟踪](https://docs.microsoft.com/dynamics365/customer-engagement/admin/audit-data-user-activity)，则用户个人数据随用户执行的操作一同记录在审核历史记录中。

### <a name="rectify"></a>纠正
如果数据主体要求纠正驻留在组织数据中的个人数据，你和你的组织需要确定是否可以接受此请求。 纠正数据包括编辑、编校或从文档或其他类型的项目中删除个人数据。

可以使用 Azure Active Directory 来管理 CDS for Apps 中的用户身份（个人数据）。 企业客户可以在给定的 Microsoft 服务内使用有限的编辑功能来管理 DSR 纠正请求。 作为数据处理方，Microsoft 不提供纠正系统生成的日志的功能，因为它们反映真实性活动，并构成 Microsoft 服务内部事件的历史记录。 有关详细信息，请参阅 [GDPR：数据主体请求 (DSR)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)。

从 Azure Active Directory 中删除用户记录后，系统管理员即可从所有实例中删除与该用户相关的任何剩余个人数据（例如，自定义属性）。  

### <a name="export"></a>导出

#### <a name="system-user"></a>系统用户
可以将存储在系统用户实体中的用户个人数据从管理中心的用户列表导出到 Excel。

从 [PowerApps 管理中心](https://admin.powerapps.com/)执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

2. 单击或点击“Dynamics 365 管理中心”，从列表中选择一个环境，然后单击或点击“打开”。

3. 转到“设置” > “安全”，然后选择“启用用户视图”。

4. 单击“导出到 Excel”。

#### <a name="audit-history"></a>审核历史记录
可在管理中心内对审核历史记录进行屏幕截图。

从 [PowerApps 管理中心](https://admin.powerapps.com/)执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

2. 单击或点击“Dynamics 365 管理中心”，从列表中选择一个环境，然后单击或点击“打开”。

3. 转到“设置” > “审核”，然后选择“审核摘要视图”。

    ![PowerApps 审核历史记录菜单](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-menu.png)

4. 找到用户审核记录，然后按 Alt+PrtScn 进行屏幕截图。

    ![PowerApps 审核历史记录详细信息](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-details.png)

5. 将屏幕截图保存到文件，之后可将其发送给 DSR 请求者。

### <a name="delete"></a>删除

#### <a name="user"></a>用户
为避免可能对组织运作至关重要的业务应用程序出现中断，从 Office 365 管理中心删除用户时，用户记录不会自动从 CDS for Apps 系统用户实体中删除。 用户的状态在 CDS for Apps 中设置为禁用，但 CDS for Apps 系统管理员必须在应用程序中找到并删除 CDS for Apps 用户个人数据。

#### <a name="remove-a-users-personal-data-from-the-users-summary-page"></a>从用户的摘要页面删除用户的个人数据
从 Azure Active Directory 中删除用户记录时，用户的摘要页面上会显示以下消息：

此用户信息不再由 Office 365 管理。可以通过删除或替换与此用户关联的所有个人数据来更新此记录以响应 DSR 请求。

从 [PowerApps 管理中心](https://admin.powerapps.com/)执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

2. 单击或点击“Dynamics 365 管理中心”，从列表中选择一个环境，然后单击或点击“打开”。

3. 转到“设置” > “安全” > “用户”，然后选择“禁用用户视图”。

4. 在“搜索”框中输入用户的名字，然后单击或点击“搜索”。

9. 双击搜索结果列表中的用户名字。

10. 在用户的摘要页面上，删除所有个人数据，然后单击或点击“保存”。

#### <a name="remove-a-users-personal-data-by-using-excel"></a>使用 Excel 删除用户的个人数据
从 [PowerApps 管理中心](https://admin.powerapps.com/)执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

2. 单击或点击“Dynamics 365 管理中心”，从列表中选择一个环境，然后单击或点击“打开”。

3. 转到“设置” > “安全” > “用户”，然后选择“禁用用户视图”。

4. 基于用户的个人数据创建 Excel 模板文件，并下载该文件。 有关分步说明，请参阅[创建新 Excel 模板](https://docs.microsoft.com/dynamics365/customer-engagement/admin/analyze-your-data-with-excel-templates#create-a-new-excel-template)。

8. 打开下载的 Excel 模板文件，删除用户的个人数据，然后保存该文件。

9. 返回“已禁用的用户视图”页面，然后单击或点击“导入数据”。

10. 在“上传数据文件”对话框中选择 Excel 模板文件，并在“映射字段”窗口中执行所有必要更改。

12. 单击或点击“下一步”，然后单击或点击“提交”。

#### <a name="remove-audit-history-from-the-audit-summary-view-page"></a>从“审核摘要视图”页面删除审核历史记录
从 [PowerApps 管理中心](https://admin.powerapps.com/)执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

2. 单击或点击“Dynamics 365 管理中心”，从列表中选择一个环境，然后单击或点击“打开”。

3. 转到“设置” > “审核”，然后选择“审核摘要视图”。

4. 找到用户的更改历史记录，单击或点击行旁边的复选框，然后单击或点击“删除更改历史记录”。

## <a name="personal-data-stored-in-databases-of-cds-for-apps"></a>个人数据存储在 CDS for Apps 的数据库中

### <a name="prerequisites"></a>先决条件
可以将个人（如你自己的客户）的个人数据存储在 CDS for Apps 实体中。  

CDS 系统管理员负责维护不同实体中存储的每个人的个人数据的清单，以便这些人可以找到该数据，响应任何 DSR 请求。  

然后，可以使用产品内功能在实体中导出、纠正或删除个人数据。  

### <a name="discover"></a>发现
在收到来自某个人的 DSR 请求时，CDS 系统管理员必须确定哪些环境/CDS 实例包含该个人的个人数据。 个人数据通常存储在密钥实体（例如，帐户、联系人、潜在客户和机会等）中，但你有责任制定策略和步骤，维护存储每个人的个人数据的清单，做好响应 DSR 请求的准备。

CDS 系统管理员可使用清单来配置搜索实体和字段，然后访问 CDS for Apps 环境以发现个人数据。 有关详细信息，请参阅[配置相关性搜索](https://go.microsoft.com/fwlink/?linkid=872506)。

从 [PowerApps 管理中心](https://admin.powerapps.com/)执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

2. 单击或点击“Dynamics 365 管理中心”，从列表中选择一个环境，单击或点击搜索按钮，然后单击或点击“相关性搜索”。

    ![PowerApps 相关性搜索菜单](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3. 在搜索框中输入个人的个人数据，然后单击或点击“搜索”。

    ![PowerApps 相关性搜索结果](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

### <a name="rectify"></a>纠正
CDS 系统管理员可以通过“相关性搜索”的结果列表来更新个人的个人数据。 但是，个人的个人数据也可能存储在其他自定义实体中。 CDS 系统管理员负责维护这些其他自定义实体清单，并对个人的个人数据进行相应更新。

从相关性搜索结果中，执行以下操作：

1. 单击或点击包含个人的个人数据的项。

2. 在适当情况下更新个人的个人数据，然后单击或点击“保存”。

    ![PowerApps 帐户详细信息](./media/common-data-service-gdpr-dsr-guide/powerapps-account-details.png)

### <a name="export"></a>导出
可对数据进行屏幕截图，然后与 DSR 请求者共享。

从 [PowerApps 管理中心](https://admin.powerapps.com/)执行以下操作：

1. 在导航窗格中，单击或点击“环境”，然后从列表中选择一个环境。

2. 单击或点击“Dynamics 365 管理中心”，从列表中选择一个环境，单击或点击搜索按钮，然后单击或点击“相关性搜索”。

    ![PowerApps 相关性搜索菜单](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3. 在搜索框中输入个人的个人数据，然后单击或点击“搜索”。

    ![PowerApps 相关性搜索结果](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

4. 双击搜索结果列表中的项。

5. 按 Alt+PrtScn 进行屏幕截图。

6. 将屏幕截图保存到文件，之后可将其发送给 DSR 请求者。

### <a name="delete"></a>删除
CDS 系统管理员可以从存储个人数据的记录中删除个人的个人数据。  CDS 系统管理员可以选择删除存储个人数据的记录，或从记录中删除个人数据的内容。  

> [!NOTE]
> CDS 管理员可以自定义环境，以防止记录从实体中删除。 如果以这种方式进行配置，需要从记录中删除个人数据的内容，而不是删除记录本身。

从相关性搜索结果中，执行以下操作：

1. 单击或点击包含个人的个人数据的项。

2. 在功能区中，单击或点击“删除”。 （请注意，如果无法删除记录，则将禁用“删除”）。

    ![PowerApps 帐户删除](./media/common-data-service-gdpr-dsr-guide/powerapps-account-delete.png)

## <a name="personal-data-stored-in-databases-of-the-previous-version-of-cds"></a>存储在 CDS 早期版本数据库中的个人数据

### <a name="prerequisites"></a>先决条件
可以将个人（如你自己的客户）的个人数据存储在 CDS 实体中。  

CDS 系统管理员负责维护不同实体中存储的每个人的个人数据的清单，以便这些人可以找到该数据，响应任何 DSR 请求。  

然后，可以使用产品内功能在实体中导出、纠正或删除个人数据。  

### <a name="discover"></a>发现
在收到来自某个人的 DSR 请求时，CDS 系统管理员必须确定哪些环境/CDS 实例包含该个人的个人数据。 个人数据通常存储在密钥实体（例如，帐户、联系人、潜在客户和机会等）中，但你有责任制定策略和步骤，维护存储每个人的个人数据的清单，做好响应 DSR 请求的准备。

可以在以下资源中找到 CDS 早期版本用户的个人数据：

|资源 | 用途 | 网站访问 |  编程访问
| --- | --- | --- | ---
|实体记录 | 在各自的业务实体中捕获业务事务。 | [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) |    否

#### <a name="entity-records"></a>实体记录
个人的个人数据可以存储在任何业务实体中。

此版本 CDS 包含它自己的数据库架构和基础结构。 它具有自己的实体，而你可在 [PowerApps](http://web.powerapps.com/) 中管理这些实体。

要查看实体列表，请执行以下操作：

1. 在“环境”下拉列表中，选择你的环境。

2. 在导航窗格中，单击或点击“数据”，然后单击或点击“实体”。

    ![PowerApps 旧实体](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

3. 从实体列表中，单击或点击一个实体（例如，帐户实体），如下所示。

    ![PowerApps 旧实体详细信息列表](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

4. 单击或点击“数据”选项卡。随即显示实体的记录列表。

    ![PowerApps 旧帐户数据](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

5. 单击或点击“导出数据”。

6. 完成导出时，单击或点击“在 Excel 中打开”，然后单击或点击“启用编辑”。

7. 单击或点击搜索按钮，在搜索框中输入个人的个人数据，然后单击或点击“搜索”。

8. 使用清单列表，针对每个业务实体重复上述步骤，发现所有个人的个人数据。

### <a name="rectify"></a>纠正
如果数据主体要求纠正驻留在组织数据中的个人数据，你和你的组织需要确定是否可以接受此请求。 纠正数据包括编辑、编校或从文档或其他类型的项目中删除个人数据。

可以使用 Azure Active Directory 来管理 CDS 早期版本中的用户身份（个人数据）。 企业客户可以在给定的 Microsoft 服务内使用有限的编辑功能来管理 DSR 纠正请求。 作为数据处理方，Microsoft 不提供纠正系统生成的日志的功能，因为它们反映真实性活动，并构成 Microsoft 服务内部事件的历史记录。 有关详细信息，请参阅 [GDPR：数据主体请求 (DSR)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)。

要纠正驻留在 CDS 环境中的个人数据，可以将实体数据导出到 Excel 电子表格，更新它，然后将更新导入回数据库。

CDS 系统管理员负责标识包含个人的个人数据的所有实体，并针对每个实体重复以下步骤。

从 [PowerApps](http://web.powerapps.com/) 中执行以下操作：

1. 在导航窗格中，单击或点击“数据”，然后单击或点击“实体”。

    ![PowerApps 旧实体](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. 从实体列表中，单击或点击一个实体（例如，帐户实体），如下所示。

    ![PowerApps 旧实体详细信息列表](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. 单击或点击“数据”选项卡。随即显示实体的记录列表。

    ![PowerApps 旧帐户数据](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. 单击或点击“导出数据”。

5. 完成导出时，单击或点击“在 Excel 中打开”，然后单击或点击“启用编辑”。

6. 在菜单栏，单击或点击“文件”，单击或点击“另存为”，然后选择保存文件的位置。

7. 进行必要的个人数据更新并保存电子表格。

10. 在 PowerApps 中，返回到实体的“数据”选项卡，然后单击或点击“导入数据”。

11. 单击“搜索”，然后选择并打开刚刚更新的 Excel 电子表格。

12. 单击“**导入**”。

### <a name="export"></a>导出
可以将每个实体中的个人数据导出到 Excel 电子表格并进行查看。

从 [PowerApps](http://web.powerapps.com/) 中执行以下操作：

1. 在导航窗格中，单击或点击“数据”，然后单击或点击“实体”。

    ![PowerApps 旧实体](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. 从实体列表中，单击或点击想要导出并查看的实体（例如，帐户实体），如下所示。

    ![PowerApps 旧实体详细信息列表](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. 单击或点击“数据”选项卡。随即显示实体的记录列表。

    ![PowerApps 旧帐户数据](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. 单击或点击“导出数据”。

    导出操作在后台运行，你可在该操作完成后收到通知。

5. 要查看导出的数据，请单击或点击“在 Excel 中打开”。

### <a name="delete"></a>删除
可以通过使用“导出/导入数据”功能，删除存储在实体中的个人数据。

CDS 系统管理员负责标识包含个人的个人数据的所有实体，并针对每个实体重复以下步骤。

从 [PowerApps](http://web.powerapps.com/) 中执行以下操作：

1. 在导航窗格中，单击或点击“数据”，然后单击或点击“实体”。

    ![PowerApps 旧实体](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. 从实体列表中，单击或点击想要删除个人数据的实体（例如，帐户实体），如下所示。

    ![PowerApps 旧实体详细信息列表](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. 单击或点击“数据”选项卡。随即显示实体的记录列表。

    ![PowerApps 旧帐户数据](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. 单击或点击“导出数据”。

5. 完成导出时，单击或点击“在 Excel 中打开”，然后单击或点击“启用编辑”。

6. 在菜单栏，单击或点击“文件”，单击或点击“另存为”，然后选择保存文件的位置。

7. 删除包含要从实体中删除的个人数据的行，然后保存电子表格。

10. 在 PowerApps 中，返回到实体的“数据”选项卡，然后单击或点击“导入数据”。

11. 单击“搜索”，然后选择并打开刚刚更新的 Excel 电子表格。

12. 单击“**导入**”。