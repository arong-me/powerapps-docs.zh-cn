---
title: 查看并将其存储在 Azure Blob 存储中的门户错误日志 |MicrosoftDocs
description: 了解如何查看门户错误日志，并将其存储在 Azure Blob 存储帐户中。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7989c15b0c5c4cf50d4b55f518244758afc067e1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542929"
---
# <a name="view-portal-error-logs"></a>查看门户错误信息日志

作为门户管理员或开发人员，你可以使用 PowerApps 门户为你的客户创建一个网站。 开发人员的一项常见任务是在开发门户时调试问题。 若要帮助进行调试，可以在门户中访问详细的错误日志，以解决任何问题。 可以通过多种方式获取门户的错误日志。

## <a name="custom-error"></a>自定义错误

如果门户中发生任何服务器端异常，则默认情况下会显示具有用户友好错误消息的自定义错误页。 若要配置错误消息，请参阅[显示自定义错误消息](#display-a-custom-error-message)。

但出于调试目的，更好的做法是查看 ASP.NET 详细的错误页，也称为黄色的死亡（YSOD）屏幕。 详细的错误页可帮助你获取服务器错误的完整堆栈。

> [!div class=mx-imgBorder]
> ![死亡的黄色屏幕](../media/ysod.png "死亡的黄色屏幕")

若要启用 YSOD，需要在门户上[禁用自定义错误](#disable-custom-error)。

> [!NOTE]
> 建议仅在你处于开发阶段时禁用自定义错误，并在你上线后启用自定义错误。

有关自定义错误的详细信息：[显示自定义错误页](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>禁用自定义错误

可以禁用门户上的自定义错误，以便在门户中发生任何服务器端异常时显示详细的异常消息。

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2. 中转到**门户操作** > **禁用自定义错误**。

   > [!div class=mx-imgBorder]
   > ![禁用自定义错误](../media/disable-custom-errors.png "禁用自定义错误")

3. 在确认消息中选择 "**禁用**"。 禁用自定义错误时，门户将重新启动并不可用。 禁用自定义错误时，将显示一条消息。

### <a name="enable-custom-error"></a>启用自定义错误

你可以在门户上启用自定义错误，以显示专业外观的页面，而不是 YSOD。 此页提供有意义的信息，如果应用程序中发生任何异常。

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2. 中转到**门户操作** > **启用自定义错误**。

   > [!div class=mx-imgBorder]
   > ![启用自定义错误](../media/enable-custom-errors.png "启用自定义错误")

3. 在确认消息中选择 "**启用**"。 当启用自定义错误时，门户将重新启动并不可用。 启用自定义错误时，将显示一条消息。

> [!NOTE]
> - 如果更改门户连接到的实例，则 "自定义错误" 设置会设置为 "已启用"。 如果需要，您必须再次禁用自定义错误。
> - 如果正在更改门户连接到的实例，则不能启用或禁用自定义错误;否则，会显示一条错误消息。

### <a name="display-a-custom-error-message"></a>显示自定义错误消息

你可以配置门户以显示专业外观的自定义错误，而不是一般错误。

若要定义自定义错误，请使用内容片段 `Portal Generic Error`。 在此代码段中定义的内容将显示在错误页中。 此内容片段不是现成可用的，你必须创建它。 内容段**类型**可以是**文本**或**HTML**。 若要创建或编辑内容段，请参阅[使用内容片段自定义内容](../configure/customize-content-snippets.md)。

> [!NOTE]
> 如果在内容代码段中写入液体代码，则将跳过此内容并不呈现。

启用自定义错误时，消息将显示在错误页上的以下结构中：

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

下面是使用 HTML 类型的内容代码段的自定义错误消息示例：

这是一个自定义错误，请通过单击此处提交支持票证并显示错误屏幕截图

> [!div class=mx-imgBorder]
> ![自定义错误消息](../media/custom-error-message.png "自定义错误消息")

> [!NOTE]
> 如果门户无法检索内容片段，因为它无法连接到 Common Data Service 或者如果代码片段在 Common Data Service 中不可用，则会出现一条错误消息。

## <a name="access-portal-error-logs"></a>访问门户错误日志

开发和发布门户之后，仍需要能够访问门户日志来调试客户报告的问题。 若要访问日志，可以配置门户将所有应用程序错误发送到你拥有的 Azure Blob 存储帐户。 通过访问门户错误日志，您可以有效地响应客户查询，因为您有问题的详细信息。 若要将门户错误日志导入到 Azure Blob 存储，必须从 PowerApps 门户管理中心启用诊断日志记录。

> [!NOTE]
> 如果更改门户连接到的 Common Data Service 实例，则将禁用诊断日志记录。 必须再次启用诊断日志记录。

### <a name="enable-diagnostic-logging"></a>启用诊断日志记录

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2.  > **启用诊断日志记录**，请参阅**门户操作**。

   > [!div class=mx-imgBorder]
   > ![启用诊断日志记录](../media/enable-diagnostic-logging.png "启用诊断日志记录")

3. 在 "**启用诊断日志记录**" 窗口中，输入以下值：

   - **Azure Blob 存储服务的连接字符串**：用于存储门户错误日志的 Azure blob 存储服务的 URL。 URL 的最大长度为2048个字符。 如果 URL 的长度超过2048个字符，则会出现一条错误消息。 有关连接字符串的详细信息：[配置 Azure 存储连接字符串](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **选择 "保持期**：持续时间"，以在 blob 存储中保留门户错误日志。 错误日志将在所选持续时间后删除。 您可以选择下列值之一：
     - 1天
     - 7天
     - 30天
     - 60天
     - 90天
     - 180天
     - 始终

   默认情况下，保持期为30天。
  
   > [!div class=mx-imgBorder]
   > ![启用诊断日志记录窗口](../media/enable-diagnostic-logging-window.png "启用诊断日志记录窗口")

4. 单击 "**配置**"。

配置诊断日志记录后，将在 Azure 存储帐户中创建新的**遥测日志**blob 容器，并将日志写入存储在容器中的 blob 文件。 以下屏幕截图显示了 Azure 存储资源管理器中的**遥测日志**blob 容器：

> [!div class=mx-imgBorder]
> ![Azure 博客存储帐户](../media/azure-blob-storage.png "Azure 博客存储帐户")

成功启用诊断日志记录后，可以使用以下操作：
- **更新诊断日志记录配置**：允许你更新或删除门户的诊断日志记录配置。
- **禁用诊断日志记录**：允许你为门户禁用诊断日志记录配置。
 
### <a name="update-diagnostic-logging"></a>更新诊断日志记录

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2. 请参阅**门户操作** > **更新诊断日志记录配置**。

   > [!div class=mx-imgBorder]
   > ![更新诊断日志记录配置](../media/update-diagnostic-logging.png "更新诊断日志记录配置")

3. 在 "更新诊断日志记录配置" 窗口中，输入以下值：
   - **是否要更新 Azure Blob 存储服务的连接字符串？** ：允许指定是否更新 Azure blob 存储服务的连接字符串。 默认情况下，此选项处于选中状态。
   - **Azure Blob 存储服务的连接字符串**：用于存储门户错误日志的 Azure blob 存储服务的 URL。 URL 的最大长度为2048个字符。 如果 URL 的长度超过2048个字符，则会出现一条错误消息。 仅当选择了 "**是否要更新 Azure Blob 存储服务的连接字符串？** " 复选框时，才会显示此字段。 有关连接字符串的详细信息：[配置 Azure 存储连接字符串](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **选择 "保持期**：持续时间"，以在 blob 存储中保留门户错误日志。 错误日志将在所选持续时间后删除。 您可以选择下列值之一：
     - 1天
     - 7天
     - 30天
     - 60天
     - 90天
     - 180天
     - 始终

   默认情况下，保持期为30天。

   > [!div class=mx-imgBorder]
   > ![更新诊断日志记录配置窗口](../media/update-diagnostic-logging-window.png "更新诊断日志记录配置窗口")

4. 单击 "**更新**"。

### <a name="disable-diagnostic-logging"></a>禁用诊断日志记录

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2. 请参阅**门户操作** > **禁用诊断日志记录**。

   > [!div class=mx-imgBorder]
   > ![禁用诊断日志记录](../media/disable-diagnostic-logging.png "禁用诊断日志记录")

3. 在确认消息中单击 "**禁用**"。

## <a name="display-plugin-error"></a>显示插件错误

开发门户时经常发生的另一种情况是在 Common Data Service 环境中编写的自定义插件和业务逻辑产生的错误。 通常可以通过[禁用自定义错误](#disable-custom-error)或[启用诊断日志记录](#enable-diagnostic-logging)来访问这些错误。 但是，在某些情况下，在门户中直接显示这些错误可以更快地诊断问题。 为此，可以配置门户，以便在门户屏幕上显示 Common Data Service 中的自定义插件错误。

若要显示自定义插件错误，请 `Site/EnableCustomPluginError` 创建站点设置，并将其值设置为 True。 自定义插件错误将显示在屏幕上，而不是一般错误。 该错误将仅显示插件错误的消息部分，而不显示完整的堆栈跟踪。

下面是将出现自定义插件错误的屏幕： 
- 实体列表 
    - 检索记录 
- 实体窗体 
    - 恢复 
    - 创建/更新等 
- Web 窗体 
    - 恢复 
    - 创建/更新等

如果站点设置不存在，则默认情况下会将其视为 false，且不会呈现插件错误。
