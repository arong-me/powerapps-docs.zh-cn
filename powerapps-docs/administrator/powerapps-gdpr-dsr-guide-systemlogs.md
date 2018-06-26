---
title: 响应针对 PowerApps、Microsoft Flow 和 Common Data Service (CDS) for Apps 中系统生成的日志的 DSR 请求 | Microsoft Docs
description: 演练如何响应针对 PowerApps、Microsoft Flow 和 Common Data Service (CDS) for Apps 中系统生成的日志的 DSR 请求
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 2c06be34d46688e3a25ce531d0e791dc0b1aca62
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "34553004"
---
# <a name="responding-to-dsr-requests-for-system-generated-logs-in-powerapps-microsoft-flow-and-common-data-service-for-apps"></a>响应 PowerApps、Microsoft Flow 和 Common Data Service for Apps 中系统生成的日志的 DSR 请求
Microsoft 允许你访问、导出和删除系统生成的日志，根据欧盟 (EU) 个人数据的一般数据保护条例 (GDPR) 的广泛定义，这些日志可能被视为个人数据。 在 GDPR 下，可能被视为个人数据的系统生成日志的示例包括：
* 产品和服务使用情况数据，例如用户活动日志
* 用户搜索请求和查询数据
* 由产品和服务生成的数据作为系统功能和用户或其他系统交互的产物

请注意，不支持在系统生成的日志中限制或纠正数据。 系统生成日志中的数据构成了在 Microsoft 云内部进行的实际操作，而诊断数据&mdash;包括对此类数据的修改&mdash;将会影响操作的历史记录，并增加欺诈和安全风险。

## <a name="prerequisites"></a>先决条件
本文重点介绍在托管和非托管租户中响应系统生成日志的 DSR 请求。 若要确定你是属于托管还是非托管租户，请参阅以下“确定租户类型”部分。

## <a name="accessing-and-exporting-system-generated-logs-for-managed-tenants"></a>访问和导出托管租户的系统生成日志
管理员可以访问与用户使用 PowerApps、Microsoft Flow 和 Common Data Service (CDS) for Apps 服务及应用程序关联的系统生成的日志。

要访问和导出系统生成的日志，请执行以下操作：

1. 转到 [Microsoft 服务信任门户](https://servicetrust.microsoft.com/)，并使用 Office 365 全局管理员凭据登录。

2. 从页面顶部的“隐私”下拉列表中，选择“数据主体请求”。

3. 在“数据主体请求”页的“系统生成的日志”下，选择“数据日志导出”。 随即出现“数据日志导出”，并显示组织提交的导出数据请求列表。

4. 若要创建新的用户请求，请单击“创建导出数据请求”。

    创建新请求后，“数据日志导出”页将列出请求，可以在其中跟踪其状态。 请求完成后，可以单击链接来访问系统生成的日志，这些日志将在创建请求的 30 天内导出到组织的 Azure 存储位置。 数据将以常见的计算机可读文件格式保存，如 XML、CSV 或 JSON。 如果没有 Azure 帐户和 Azure 存储位置，则需要为组织创建 Azure 帐户和/或 Azure 存储位置，以便数据日志导出工具可以导出系统生成的日志。 有关详细信息，请参阅 [Azure 存储简介](https://docs.microsoft.com/azure/storage/common/storage-introduction)。

下表总结了有关访问和导出托管租户的系统生成日志的信息：

| 问题 | 答案 |
| --- | --- |
| Microsoft 数据日志导出工具需要多长时间完成请求？ |    这取决于几个因素。 在大多数情况下，这应在一两天内完成，但最长可能需要 30 天。
| 输出将采用何种格式？ | 输出将采用结构化的计算机可读文件格式，如 XML、CSV 或 JSON。
| 谁有权访问数据日志导出工具以提交对系统生成日志的访问请求？ | Office 365 全局管理员将具有访问 GDPR 日志管理器工具的权限。
| 数据日志导出工具会返回哪些数据？ | 数据日志导出工具会返回 Microsoft 存储的系统生成日志。 导出的数据跨越各种 Microsoft 服务，包括 Office 365、Azure、Dynamics、PowerApps、Microsoft Flow 和 CDS for Apps。
| 数据将如何返回给用户？ |   数据将导出到组织的 Azure 存储位置；它将由组织管理员决定如何向用户显示/返回这些数据。
| 系统生成日志中的数据是什么样的？ |  采用 JSON 格式的系统生成日志记录示例： <br> [{ <br>"DateTime": "2017-04- 28T12:09:29-07:00",  <br> "AppName": "SharePoint", <br> "Action": "OpenFile", "IP": "154.192.13.131", <br> "DevicePlatform": "Windows 1.0.1607" <br>}]

> [!NOTE]
>  出于安全和审核目的，某些功能不允许导出或删除系统生成的日志，以便维护个人信息的完整性。
>
>

## <a name="deleting-system-generated-logs-for-managed-tenants"></a>删除托管租户的系统生成日志
若要删除通过访问请求检索到的系统生成日志，必须从服务中移除用户，并永久删除其 Azure Active Directory 帐户。 有关如何永久删除用户的说明，请参阅 [Office 365 服务信任门户](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)中 Azure 数据主体请求 GDPR 文档的“删除用户”部分。 请务必注意，永久删除用户帐户一经实施不可撤销。

永久删除用户帐户将在 30 天内从 PowerApps、Microsoft Flow 和 CDS for Apps 服务的系统生成日志中移除用户数据。


## <a name="accessing-and-exporting-system-generated-logs-for-unmanaged-tenants"></a>访问和导出非托管租户的系统生成日志

用户可以访问与其使用 PowerApps、Microsoft Flow 和 Common Data Service (CDS) for Apps 服务及应用程序关联的系统生成日志。

要访问和导出系统生成的日志，请执行以下操作：
1. 转到[工作和学校隐私门户](https://go.microsoft.com/fwlink/?linkid=873123)。
1. 在“我的数据请求”页上，用户可以通过单击“新导出请求”按钮请求数据输出。
1. 单击此按钮后，将要求确认请求。 单击“是”继续操作。
1. 新的导出请求可能需要长达 1 个月才能完成。 在此期间，将显示状态“正在运行”。
1. 完成后，将填充“完成日期”列，并提供指向“系统生成日志”的链接。
1. 单击此链接下载数据。 可使用文本编辑器查看此数据。
1. 另请注意，将在“到期日期”列中填充此内容的“到期日期”。 在此之前，必须检索系统生成日志。

下表总结了有关访问和导出非托管租户的系统生成日志的信息：

| 问题 | 答案 |
| --- | --- |
| Microsoft 数据日志导出工具需要多长时间完成请求？ |    这取决于几个因素。 在大多数情况下，这应在一两天内完成，但最长可能需要 30 天。
| 输出将采用何种格式？ | 输出将采用结构化的计算机可读文件格式，如 XML、CSV 或 JSON。
| 谁有权访问数据日志导出工具以提交对系统生成日志的访问请求？ | 非托管租户成员用户可访问提交请求。
| 数据导出工具会返回哪些数据？ | 数据导出工具会返回 Microsoft 存储的系统生成日志。 导出的数据跨越各种 Microsoft 服务，包括 Office 365、Azure、Dynamics、PowerApps、Microsoft Flow 和 CDS for Apps。
| 数据将如何返回给用户？ |   数据将被导出到 Microsoft 网站，并且会向提出 DSR 请求的用户安全提供此网站的链接。
| 系统生成日志中的数据是什么样的？ |  采用 JSON 格式的系统生成日志记录示例： <br> [{ <br>"DateTime": "2017-04- 28T12:09:29-07:00",  <br> "AppName": "SharePoint", <br> "Action": "OpenFile", "IP": "154.192.13.131", <br> "DevicePlatform": "Windows 1.0.1607" <br>}]

> [!NOTE]
>  出于安全和审核目的，某些功能不允许导出或删除系统生成的日志，以便维护个人信息的完整性。
>
>

## <a name="deleting-system-generated-logs-for-unmanaged-tenants"></a>删除非托管租户的系统生成日志
若要删除通过访问请求检索到的系统生成日志，必须关闭帐户，这将在 30 天内删除系统生成日志并删除 PowerApps、Microsoft Flow 和 CDS for Apps 服务中的数据。

若要删除系统生成日志，请执行以下操作：
1. 转到[工作和学校隐私门户](https://go.microsoft.com/fwlink/?linkid=873123)。
1. 在“我的数据请求”页上，用户可以通过单击“关闭帐户”按钮请求删除其数据。
1. 单击此按钮后，将要求确认请求。 单击“是”继续操作。
1. 关闭帐户后，将无法访问 PowerApps、Microsoft Flow 和 CDS。

## <a name="determining-tenant-type"></a>确定租户类型
若要确定你是托管还是非托管租户的用户，请执行以下操作：
1. 在浏览器中打开以下 URL，确保在 URL 中替换电子邮件地址：[https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1](https://login.windows.net/common/userrealm/foobar@contoso.com?api-version=2.1)。

2. 如果你是“非托管租户”的成员，则将会在响应中看到 `"IsViral": true`。
  ```
      {
      ...
      "Login": "foobar@unmanagedcontoso.com",
      "DomainName": "unmanagedcontoso.com",
      "IsViral": **true**,
      ...
      }
  ```

3. 否则，你就属于托管租户。
