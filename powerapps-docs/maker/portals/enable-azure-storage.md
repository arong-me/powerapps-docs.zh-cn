---
title: 为门户启用 Azure 存储 |MicrosoftDocs
description: 有关为门户启用 Azure 存储以利用 Azure 的更大文件存储功能的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c9201f02074920b65fdf904c5dbe81826114f4c6
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975463"
---
# <a name="enable-azure-storage"></a>启用 Azure 存储

使用 azure 的 azure 存储集成，你可以利用 Azure 的更大文件存储功能，使用相同的接口，并提供与默认文件附件相同的用户体验。 Web 文件、实体窗体和 web 窗体支持此功能。

必须使用**Resource manager**作为部署模型来创建存储帐户。 [!include[More information](../../includes/proc-more-information.md)][创建 Azure 存储帐户](https://docs.microsoft.com/en-us/azure/storage/storage-create-storage-account#create-a-storage-account)。

存储帐户运行后，门户需要某些全局设置，告诉应用程序如何查找存储帐户。 在门户管理应用程序中， > "**新建**" 中转到 "**设置**"，然后添加名为 " **FileStorage/CloudStorageAccount**" 的新设置。

> [!NOTE]
> 最大文件上传大小为 125 MB。

若要查找 FileStorage/CloudStorageAccount 的值，必须从 [!include[Azure portal](../../includes/pn-azure-portal.md)]获取连接字符串。

1. 登录到 [!include[Azure portal](../../includes/pn-azure-portal.md)]。

2. 导航到你的存储帐户。

3. 选择 "**访问密钥**"。

    ![从 Azure 门户中找到连接字符串的值]从(media/key-azure-storage.png "Azure 门户中找到连接字符串的值")

4. 在生成的面板中，找到标记为 "**连接字符串**" 的字段。 选择需要为其复制值的字段旁边的**复制**图标，然后将该值粘贴到新设置中：

    ![主连接字符串值](media/primary-connection-string-azure-storage.png "主连接字符串值")

    云存储帐户的![门户设置]云(media/portal-site-setting-cloud-storage-account.png "存储帐户的设置")

## <a name="specify-the-storage-container"></a>指定存储容器

如果你的存储帐户中还没有 Azure Blob 容器，则必须使用你的 [!include[Azure portal](../../includes/pn-azure-portal.md)]添加一个。

在[门户管理应用程序](configure/configure-portal.md)中， > "**新建**" 中转到 "**设置**"，然后添加名为 " **FileStorage/CloudStorageContainerName**" 的新设置，并使用容器名称作为值。

云存储容器的![门户设置容器](media/portal-site-setting-cloud-storage-container.png "门户设置")

## <a name="add-cors-rule"></a>添加 CORS 规则

你必须按如下所示在你的 Azure 存储帐户上添加跨域资源共享（CORS）规则，否则你将看到常规附件图标而不是云图标：

- **允许的来源**：指定你的域。 例如，contoso.crm.dynamics.com。
- **允许的谓词**： GET、PUT、DELETE、HEAD、POST
- **允许的标头**：指定源域可以在 CORS 请求上指定的请求标头。 例如，x-ms-元数据\*，x-ms 元目标\*。 
- **公开标头**：指定可在 CORS 请求响应中发送并由浏览器向请求颁发者公开的响应标头。 例如，x-ms\*。
- **最长持续时间（秒）** ：指定浏览器应缓存预检 OPTIONS 请求的最长时间。 例如，200。
 
[!include[More information:](../../includes/proc-more-information.md)][对 Azure 存储服务的 CORS 支持](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)

## <a name="add-site-settings"></a>添加站点设置

从**门户** > **站点设置**添加以下站点设置。 [!include[More information:](../../includes/proc-more-information.md)][管理门户网站设置](configure/configure-site-settings.md#manage-portal-site-settings)。

|名称|Value|
|-----|-----|
|WebFiles/CloudStorageAccount|提供与为 FileStorage/CloudStorageAccount 设置提供的相同的连接字符串。|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

你现在可以在门户中创建一个子文件，并在 Azure Blob 地址 URL 中提及完全限定的名称（连同容器）。 利用这些设置，你的门户可以开始上传和下载 Azure 存储的文件。 但是，你不能充分利用此功能，除非你[添加了一个 web 资源来支持将附件上传到 Azure 存储](add-web-resource.md)，并配置[实体窗体](configure-notes.md#notes-configuration-for-entity-forms)或[web 窗体](configure-notes.md#notes-configuration-for-web-forms)以便使用该存储。

### <a name="see-also"></a>另请参阅

[添加 web 资源](add-web-resource.md)

[配置说明](configure-notes.md)
