---
title: 向窗体中添加 azure 存储空间 web 资源 |MicrosoftDocs
description: 向窗体中添加 azure 存储空间 web 资源的步骤，用于将附件上传到 Azure 存储。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ed1053c758f97234ad94a09832683ff00ef17744
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977556"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>将 Azure 存储 Web 资源添加到表单

已上传到 Azure 存储，而不是直接上传到 Common Data Service 可以通过使用 Common Data Service 中的说明来管理。

若要使来自特定表单的附件能够上传到 Azure 存储，必须将 web 资源添加到该表单，并且必须[为组织配置 Azure 存储](enable-azure-storage.md)。

> [!Note]
> 在此示例中，窗体将添加到潜在顾客实体的潜在顾客窗体中。 建议在编辑现有窗体时小心。

使用门户将一个文件（例如，附件 .zip）上传到 Azure 存储时，该文件由实体上的注释和附件的占位符表示。

窗体上附件的![窗体](media/notes-attachment-lead-form.png "占位符")上的附件

请注意，附件文件现在命名为 "附件"。 默认情况下，Common Data Service 没有 Azure 文件的概念，因此此占位符 .txt 文件存储在 Common Data Service 中。 占位符文件的 Azure 存储上下文显示有关该文件的详细信息。
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

若要查看 Azure 中存储的文件并与其进行交互，必须将 web 资源 adx 添加到窗体中。 作为必备组件，请确保用户对 adx_setting 具有读取访问权限。 否则，web 资源将不会正确呈现。

1. 在相关窗体的窗体编辑器中，选择 "**插入**" 选项卡上的 " **Web 资源**"。

2. 在 " **Web 资源**" 框中，选择 " **adx_annotations/adx**"。

3. 输入资源的 "名称" 和 "标签"。

4. 在 "**自定义参数（数据）** " 框中，输入**azureEnabled = true**。 <br>你还可以使用 web 资源，而无需以这种方式启用 Azure 支持，在这种情况下，它的作用与默认控件几乎完全相同。</br>

5. 在 "**格式**" 选项卡上，选择你喜欢的任何格式规则。 建议清除 "**显示边框**" 复选框。

6. 选择 **"确定"** 保存资源。

7. 您也可以选择删除现有备注控件，或将其移动到标记为在默认情况下不可见的选项卡或部分。

8. 保存窗体，然后发布所做的更改。

   ![添加 web 资源](media/add-web-resource.png "添加 web 资源")

新控件现在将呈现在页面上，使你能够在 Azure 存储中管理附件。

(media/azure-file-attachment-lead-form.png "表单上")![的 azure 文件附件]

已将纸张剪辑图标替换为云图标，表示此文件存储在 Azure 存储中。 你可以继续在 Common Data Service 中存储附件;这些文件将用回形针图标表示。

> [!Note]
> 你必须按如下所示在你的 Azure 存储帐户上添加跨域资源共享（CORS）规则，否则你将看到常规附件图标而不是云图标。
> - **允许的来源**：指定你的域。 例如，contoso.crm.dynamics.com。
> - **允许的谓词**： GET、PUT、DELETE、HEAD、POST
> - **允许的标头**：指定源域可以在 CORS 请求上指定的请求标头。 例如，x-ms-元数据\*，x-ms 元目标\*。 对于这种情况，必须指定 *，否则 web 资源将不会正确呈现。
> - **公开标头**：指定可在 CORS 请求响应中发送并由浏览器向请求颁发者公开的响应标头。 例如，x-ms\*。
> - **最长持续时间（秒）** ：指定浏览器应缓存预检 OPTIONS 请求的最长时间。 例如，200。
> 
> [!include[More information](../../includes/proc-more-information.md)][对 Azure 存储服务的 CORS 支持](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)。

如果附加文件是一个图像，则无论该图像存储在 Common Data Service 还是 Azure 存储中，它都将以缩略图的形式显示图像。

> [!Note]
> 缩略图功能限制为大小低于 1 MB 的图像。

![备注缩略]图(media/notes-thumbnail.png "备注缩略图")

## <a name="cors-protocol-support"></a>CORS 协议支持

[跨域资源共享（CORS）](http://www.w3.org/TR/cors/)协议由一组标头组成，这些标头指示是否可与其他域共享响应。
以下站点设置用于配置 CORS：

|                 名称                  |                                                                            描述                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HTTP/访问控制-允许-凭据 | 此标头的唯一有效值为 true （区分大小写）。 如果不需要凭据，请完全省略此标头（而不是将其值设置为 false）。 |
|   HTTP/访问控制-允许-标头   |                                                   受支持的 HTTP 请求标头的逗号分隔列表。                                                   |
|   HTTP/访问控制-允许-方法   |                                      允许的 HTTP 请求方法（如 GET、POST、OPTIONS）的逗号分隔列表。                                       |
|   HTTP/访问控制-允许-源    |                   若要允许任何资源访问资源，可以指定 \*。 否则，请指定可以访问资源的 URI。                   |
|  HTTP/访问控制-公开标头   |                以逗号分隔的 HTTP 标头名称的列表，该列表不是资源可能使用并可公开的简单响应标头。                 |
|      HTTP/访问控制-最大期限      |                                                       可缓存结果的最大秒数。                                                        |
|                                       |                                                                                                                                                                   |

