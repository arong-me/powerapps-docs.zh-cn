---
title: 将 Azure 存储 Web 资源添加到窗体 | MicrosoftDocs
description: 将 Azure 存储 Web 资源添加到窗体以启用将附件上载到 Azure 存储的步骤。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 02/11/2020
ms.author: tapanm
ms.reviewer: tapanm
ms.openlocfilehash: 0c011c61c2084662d1e759d7226140dcf3ddfad6
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "3126177"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>将 Azure 存储 Web 资源添加到窗体

上载到 Azure 存储而不是直接上载到 Common Data Service 的附件可以使用 Common Data Service 中的注释进行管理。

若要启用将来自特定窗体的附件上载到 Azure 存储，则必须将 Web 资源添加到该窗体，且必须[为您的组织配置 Azure 存储](enable-azure-storage.md)。

> [!NOTE]
在此示例中，窗体将添加到潜在顾客实体的潜在顾客窗体。 我们建议在编辑现有窗体时要注意。

当使用门户将文件（例如，attachments.zip）上载到 Azure 存储时，它由对实体的注释和附件的占位符代表。

![窗体中的附件](media/notes-attachment-lead-form.png "窗体上附件的占位符")

请注意，附件文件现在命名为 attachment.zip.txt。 默认情况下，Common Data Service 没有 Azure 文件的概念，因此该占位符 .txt 文件而是存储在 Common Data Service 中。 占位符文件的 Azure 存储上下文显示文件的详细信息。
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

若要查看存储在 Azure 中的文件并与其交互，则必须将 Web 资源 adx.annotations.html 添加到窗体。 必备条件要求您确保用户具有 adx_setting 的读取访问权限。 否则无法正确呈现此 Web 资源。

1. 在相关窗体的表单编辑器中，选择**插入**选项卡上的 **Web 资源**。

2. 在 **Web 资源**框，请选择 **adx_annotations/adx.annotations.html**。

3. 为资源输入名称和标签。

4. 在**自定义参数（数据）** 框中，输入 **azureEnabled=true**。 <br>不按照此方式启用 Azure 支持也可以使用 Web 资源，在这种情况下，它的功能几乎与默认控件完全相同。</br>

5. 在**格式化**选项卡上，选择您喜爱的任何格式化规则。 建议您清除**显示边框**复选框。

6. 选择**确定**以保存资源。

7. 有时，您可能希望取消现有注释控件或将它移动到标记默认不显示的选项卡或节。

8. 保存窗体，然后发布更改。

   ![添加 Web 资源](media/add-web-resource.png "添加 Web 资源")

新的控件现在将呈现在页面上，使您能够管理 Azure 存储中的附件。

![窗体上的 Azure 文件附件](media/azure-file-attachment-lead-form.png "窗体上的 Azure 文件附件")

回形针图标已更换为云图标以表示此文件存储在 Azure 存储中。 您可以继续将附件存储在 Common Data Service 中；这些文件将使用回形针图标表示。

> [!Note]
> 您还必须按照下面的说明在您的 Azure 存储帐户上添加跨源资源共享 (CORS) 规则，否则您将看到常规的附件图标，而不是云图标。
> - **允许的源**：指定您的域。 例如，`https://contoso.crm.dynamics.com`。
> - **允许的动词**：GET、PUT、DELETE、HEAD、POST
> - **允许的标头**：指定原始域可能对 CORS 请求指定的请求标头。 例如，x-ms-meta-data\*、x-ms-meta-target\*。 对于此场景，必须指定 *，否则无法正确呈现此 Web 资源。
> - **显示的标头**：指定可能在响应 CORS 请求时发送并由浏览器向请求颁发者显示的响应标头。 例如，x-ms-meta-\*。
> - **最长存在时间（秒）**：指定浏览器缓存预检 OPTIONS 请求的最大时间量。 例如，200。
> 
> [!include[More information](../../includes/proc-more-information.md)] [Azure 存储服务的 CORS 支持](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)。

如果附加的文件是图像，则控件将显示图像的缩略图，无论它是存储在 Common Data Service 中还是 Azure 存储中。

> [!Note]
> 缩略图功能仅限于大小为 1 MB 以下的图像。

![注释缩略图](media/notes-thumbnail.png "注释缩略图")

## <a name="cors-protocol-support"></a>CORS 协议支持

[跨源资源共享 (CORS)](https://www.w3.org/TR/cors/)协议包含一组指示是否与其他源共享响应的标题。
以下站点设置用于配置 CORS：

| 站点设置 | 请求头 | 说明 |
|-|-|-|
| HTTP/Access-Control-Allow-Credentials | Access-Control-Allow-Credentials | 该标题的唯一有效值是 true（区分大小写）。 如果您不需要凭据，请完全忽略此标题（不将其值设置为 false）。 
| HTTP/Access-Control-Allow-Headers | Access-Control-Allow-Headers | 用逗号分隔的受支持的 HTTP 请求标题的列表。
| HTTP/Access-Control-Allow-Methods | Access-Control-Allow-Methods | 用逗号分隔的允许的 HTTP 请求方法（如 GET、POST、OPTIONS）的列表。
| HTTP/Access-Control-Allow-Origin | Access-Control-Allow-Origin | 若要允许任何资源访问您的资源，则可以指定 \*。 否则，请指定可以访问资源的 URI。                   |
|  HTTP/Access-Control-Expose-Headers | Access-Control-Expose-Headers | 用逗号分隔的除资源可以使用且可以公开的简单响应标题以外的 HTTP 标题名称的列表。
| HTTP/Access-Control-Max-Age | Access-Control-Max-Age |  结果进行缓存的最大秒数。
| HTTP/Content-Security-Policy | Content-Security-Policy | 控制允许用户代理为给定页面加载的资源。
| HTTP/Content-Security-Policy-Report-Only | Content-Security-Policy-Report-Only | 允许 Web 开发人员通过监视（而不是强制）其效果来试验策略。 这些冲突报告包含通过 HTTP POST 请求发送到指定 URI 的 JSON 文档。
| HTTP/X-Frame-Options | X-Frame-Options | 指示是否应该允许浏览器在 *\<frame\>*、*\<iframe\>*、*\<embed\>* 或 *\<object\>* 中呈现页面。
| HTTP/X-Content-Type-Options | X-Content-Type-Options | 禁用 MIME 探查并强制浏览器使用*内容类型*中给出的类型。
