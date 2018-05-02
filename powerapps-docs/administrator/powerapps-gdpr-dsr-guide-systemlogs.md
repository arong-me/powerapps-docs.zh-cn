---
title: 响应 PowerApps、Microsoft Flow 和 Common Data Service 中系统生成的日志的 DSR | Microsoft 文档
description: 响应 PowerApps、Microsoft Flow 和 Common Data Service 中系统生成的日志的 DSR
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms-topic: article
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/18/2018
ms.author: jamesol
ms.openlocfilehash: 1b85ac81969407fe4e84c41fd93debeccddb0f05
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-dsr-requests-for-system-generated-logs-in-powerapps-microsoft-flow-and-common-data-service-for-apps"></a>响应 PowerApps、Microsoft Flow 和 Common Data Service for Apps 中系统生成的日志的 DSR 请求
Microsoft 允许你访问、导出和删除系统生成的日志，根据个人数据的一般数据保护条例 (GDPR) 的广泛定义，这些日志可能被视为个人数据。 在 GDPR 下，可能被视为个人数据的系统生成日志的示例包括：
* 产品和服务使用情况数据，例如用户活动日志
* 用户搜索请求和查询数据
* 由产品和服务生成的数据作为系统功能和用户或其他系统交互的产物

请注意，不支持在系统生成的日志中限制或纠正数据。 系统生成日志中的数据构成了在 Microsoft 云内部进行的实际操作，而诊断数据&mdash;包括对此类数据的修改&mdash;将会影响操作的历史记录，并增加欺诈和安全风险。

## <a name="accessing-and-exporting-system-generated-logs"></a>访问和导出系统生成的日志
管理员可以访问与用户使用 PowerApps、Microsoft Flow 和 CDS for Apps 服务及应用程序相关联的系统生成的日志。 若要访问和导出系统生成的日志：

1. 转到 [Microsoft 服务信任门户](https://servicetrust.microsoft.com/)并使用 Office 365 全局管理员凭据登录。

2. 从页面顶部的“隐私”下拉列表中，选择“数据主体请求”。

3. 在“数据主体请求”页的“系统生成的日志”下，选择“数据日志导出”。 随即出现“数据日志导出”，并显示组织提交的导出数据请求列表。

4. 若要创建新的用户请求，请单击“创建导出数据请求”。

    创建新请求后，“数据日志导出”页将列出请求，可以在其中跟踪其状态。 请求完成后，可以单击链接来访问系统生成的日志，这些日志将在创建请求的 30 天内导出到组织的 Azure 存储位置。 数据将以常见的计算机可读文件格式保存，如 XML、CSV 或 JSON。 如果没有 Azure 帐户和 Azure 存储位置，则需要为组织创建 Azure 帐户和/或 Azure 存储位置，以便数据日志导出工具可以导出系统生成的日志。 有关详细信息，请参阅 [Azure 存储简介](https://docs.microsoft.com/azure/storage/common/storage-introduction)。

下表总结了有关访问和导出系统生成日志的信息：

| 问题 | 答案 |
| --- | --- |
| Microsoft 数据日志导出工具需要多长时间完成请求？ |    这取决于几个因素。 在大多数情况下，这应在一两天内完成，但最长可能需要 30 天。
| 输出将采用何种格式？ | 输出将采用结构化的计算机可读文件格式，如 XML、CSV 或 JSON。
| 谁有权访问数据日志导出工具以提交对系统生成日志的访问请求？ | Office 365 全局管理员将具有访问 GDPR 日志管理器工具的权限。
| 数据日志导出工具会返回哪些数据？ | 数据日志导出工具会返回 Microsoft 存储的系统生成日志。 导出的数据跨越各种 Microsoft 服务，包括 Office 365、Azure、Dynamics、PowerApps、Microsoft Flow 和 CDS for Apps。
| 数据将如何返回给用户？ |   数据将导出到组织的 Azure 存储位置；它将由组织管理员决定如何向用户显示/返回这些数据。
| 系统生成日志中的数据是什么样的？ |  采用 JSON 格式的系统生成日志记录示例： <br> [{ <br>"DateTime": "2017-04- 28T12:09:29-07:00",  <br> "AppName": "SharePoint", <br> "Action": "OpenFile", "IP": "154.192.13.131", <br> "DevicePlatform": "Windows 1.0.1607" <br>}]

> [!NOTE]
>  某些功能不允许导出或删除包含个人信息的系统生成日志，以便出于安全和审核原因维护此类信息的完整性。
>
>

## <a name="deleting-system-generated-logs"></a>删除系统生成的日志
若要删除通过访问请求检索到的系统生成日志，必须从服务中移除用户，并永久删除其 Azure Active Directory 帐户。 有关如何永久删除用户的说明，请参阅 [Office 365 服务信任门户](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)中 Azure 数据主体请求 GDPR 文档的“删除用户”部分。 请务必注意，永久删除用户帐户一经实施不可撤销。

永久删除用户帐户将在 30 天内从 PowerApps、Microsoft Flow 和 CDS for Apps 服务的系统生成日志中移除用户数据。
