---
title: 查看门户错误日志并将其存储到 Azure Blob 存储中 | MicrosoftDocs
description: 了解如何查看门户错误日志并将其存储到 Azure Blob 存储帐户中。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4b7fe184dce7475bf2b7fc373fc98d875fffb515
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979853"
---
# <a name="view-portal-error-logs"></a>查看门户错误日志

门户管理员或开发者可以使用 Power Apps 门户为客户创建网站。 开发人员的一项常见任务是调试门户开发问题。 若要帮助调试，您可以访问详细的错误日志以了解门户的任何问题。 可通过多种方式获取门户的错误日志。

## <a name="custom-error"></a>自定义错误

如果门户中发生任何服务器端异常，默认将显示定制的错误页面和用户友好的错误消息。 若要配置，请参阅[显示自定义错误消息](#display-a-custom-error-message)。

但是，如果出于调试目的，最好查看详细的 ASP.NET 错误页面，也称为“死亡黄屏 (YSOD)”。 详细的错误页面有助于获取服务器错误全栈。

> [!div class=mx-imgBorder]
> ![死亡黄屏](../media/ysod.png "死亡黄屏")

若要启用 YSOD，需要在门户上[禁用自定义错误](#disable-custom-error)。

> [!NOTE]
> 建议仅在开发阶段禁用自定义错误，一旦投入使用则启用自定义错误。

有关自定义错误的详细信息：[显示自定义错误页面](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>禁用自定义错误

可在门户中禁用自定义错误，以便门户中发生任何服务器端异常时显示详细的异常消息。

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 转到**门户操作** > **禁用自定义错误**。

   > [!div class=mx-imgBorder]
   > ![禁用自定义错误](../media/disable-custom-errors.png "禁用自定义错误")

3. 在确认消息中选择**禁用**。 禁用自定义错误时，门户将自动启动，并且变为不可用。 禁用自定义错误时，将显示一条消息。

### <a name="enable-custom-error"></a>启用自定义错误

可在门户中启用自定义错误，以便显示外观专业的页面，而不是 YSOD。 如果应用程序中发生任何异常，此页面都将提供有意义的信息。

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 转到**门户操作** > **启用自定义错误**。

   > [!div class=mx-imgBorder]
   > ![启用自定义错误](../media/enable-custom-errors.png "启用自定义错误")

3. 在确认消息中选择**启用**。 启用自定义错误时，门户将自动启动，并且变为不可用。 启用自定义错误时，将显示一条消息。

> [!NOTE]
> - 如果更改门户相连的实例，将把自定义错误设置设为启用。 如果需要，必须禁用自定义错误。
> - 正在更改门户相连的实例时，不得启用或禁用自定义错误，否则将显示错误消息。

### <a name="display-a-custom-error-message"></a>显示自定义错误消息

可将门户配置为显示外观专业的自定义错误，而不是一般错误。

若要定义自定义错误，请使用内容片段 `Portal Generic Error`。 此片段中定义的内容在错误页面中显示。 此内容片段并非现成可用，必须经过创建。 内容片段的**类型**可以是**文本**或 **HTML**。 若要创建或编辑内容片段，请参阅[使用内容片段自定义内容](../configure/customize-content-snippets.md)。

> [!NOTE]
> 如果内容片段是使用 liquid 代码编写的，将跳过，不予显示。

启用自定义错误时，错误页面将显示以下结构的消息：

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

下面是使用类型为 HTML 的内容片段的自定义错误消息示例：

这是自定义错误，请单击此处使用错误屏幕截图开一个支持票证

> [!div class=mx-imgBorder]
> ![自定义错误消息](../media/custom-error-message.png "自定义错误消息")

> [!NOTE]
> 如果因为门户无法连接到 Common Data Service 或内容片段在 Common Data Service 中不可用而导致门户无法检索片段，将显示错误消息。

## <a name="access-portal-error-logs"></a>访问门户错误日志

开发和发布门户后，仍然需要可以访问门户日志，以便调试客户报告的调试问题。 若要访问日志，可以配置门户以将任何应用程序错误发送到您负责的 Azure Blob 存储帐户中。 通过访问门户错误日志，可高效响应客户查询，因为您了解问题的详细信息。 若要将门户日志存储到 Azure Blob 存储中，必须从 Power Apps 门户管理中心启用诊断日志记录。

> [!NOTE]
> 如果更改门户相连的 Common Data Service 实例，将禁用诊断日志记录。 必须再次启用诊断日志记录。

### <a name="enable-diagnostic-logging"></a>启用诊断日志记录

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 转到**门户操作** > **启用诊断日志记录**。

   > [!div class=mx-imgBorder]
   > ![启用诊断日志记录](../media/enable-diagnostic-logging.png "启用诊断日志记录")

3. 在**启用诊断日志记录**窗口中，输入下列值：

   - **Azure Blob 存储服务的连接字符串**：用于存储门户错误日志的 Azure Blob 存储服务的 URL。 该 URL 的最大长度为 2048 个字符。 如果该 URL 的长度超过 2048 个字符，将显示错误消息。 有关连接字符串的详细信息：[配置 Azure 存储连接字符串](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **选择保留时间段**：将门户错误日志保存在 blob 存储中的持续时间。 所选持续时间之后，将删除错误日志。 可以选择下列值之一：
     - 1 天
     - 7 天
     - 30 天
     - 60 天
     - 90 天
     - 180 天
     - 始终

   默认情况下，保留期为 30 天。
  
   > [!div class=mx-imgBorder]
   > ![启用诊断日志记录窗口](../media/enable-diagnostic-logging-window.png "启用诊断日志记录窗口")

4. 单击**配置**。

配置诊断日志记录之后，将在 Azure 存储帐户中创建一个新的 **telemetry-logs** blob 容器，并将日志写入该容器中存储的 blob 文件内。 以下屏幕截图在 Azure 资源管理器中显示 **telemetry-logs** blob 容器：

> [!div class=mx-imgBorder]
> ![Azure 日志存储帐户](../media/azure-blob-storage.png "Azure 日志存储帐户")

成功启用诊断日志记录之后，以下操作将变为可用：
- **更新诊断日志记录配置**：允许您更新或移除门户的诊断日志记录配置。
- **禁用诊断日志记录**：允许您禁用门户的诊断日志记录配置。
 
### <a name="update-diagnostic-logging"></a>更新诊断日志记录

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 转到**门户操作** > **更新诊断日志记录配置**。

   > [!div class=mx-imgBorder]
   > ![更新诊断日志记录配置](../media/update-diagnostic-logging.png "更新诊断日志记录配置")

3. 在“更新诊断日志记录配置”窗口中，输入下列值：
   - **是否要更新 Azure Blob 存储服务的连接字符串?**：允许您指定是否更新 Azure Blob 存储服务的连接字符串。 默认情况下已选中。
   - **Azure Blob 存储服务的连接字符串**：用于存储门户错误日志的 Azure Blob 存储服务的 URL。 该 URL 的最大长度可以为 2048 个字符。 如果该 URL 的长度超过 2048 个字符，将显示错误消息。 仅当选中了**是否要更新 Azure Blob 存储服务的连接字符串?** 复选框，才会显示此字段。 有关连接字符串的详细信息：[配置 Azure 存储连接字符串](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **选择保留时间段**：将门户错误日志保存在 blob 存储中的持续时间。 所选持续时间之后，将删除错误日志。 可以选择下列值之一：
     - 1 天
     - 7 天
     - 30 天
     - 60 天
     - 90 天
     - 180 天
     - 始终

   默认情况下，保留期为 30 天。

   > [!div class=mx-imgBorder]
   > ![更新诊断日志记录配置窗口](../media/update-diagnostic-logging-window.png "更新诊断日志记录配置窗口")

4. 单击**更新**。

### <a name="disable-diagnostic-logging"></a>禁用诊断日志记录

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 转到**门户操作** > **禁用诊断日志记录**。

   > [!div class=mx-imgBorder]
   > ![禁用诊断日志记录](../media/disable-diagnostic-logging.png "禁用诊断日志记录")

3. 在确认消息中，单击**禁用**。

## <a name="display-plugin-error"></a>显示插件错误

开发门户时还经常发生下面的情况：Common Data Service 环境中编写的自定义插件和业务逻辑生成错误。 这些错误通常可以通过[禁用自定义错误](#disable-custom-error)或[启用诊断日志记录](#enable-diagnostic-logging)访问。 但是在某些情况下，直接在门户中显示这些错误的速度更快，从而可以更快地诊断问题。 这样就可以将门户配置为在门户屏幕中显示 Common Data Service 产生的自定义插件错误。

若要显示自定义插件错误，请创建站点设置 `Site/EnableCustomPluginError`，并将其值设置为 True。 将在屏幕上显示自定义插件错误，而不是普通错误。 错误将仅显示插件错误的消息部分，而不是显示整个堆栈跟踪。

下面是显示自定义插件错误的屏幕： 
- 实体列表 
    - 检索记录 
- 实体窗体 
    - 检索 
    - 创建/更新等 
- Web 窗体 
    - 检索 
    - 创建/更新等

如果不存在此站点设置，默认将把它视为 false，并且不显示插件错误。
