---
title: 为门户启用 Azure 存储 | MicrosoftDocs
description: 有关如何为门户启用 Azure 存储以利用更大的 Azure 文件存储容量。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3da40cfdcb88726384218c4b1df370c301f8ac16
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759896"
---
# <a name="enable-azure-storage"></a>启用 Azure 存储

Azure 存储门户集成在默认文件附件方面使用相同界面和提供相同的用户体验，使用户可以利用 Azure 的更大的文件存储功能。 此功能支持 Web 文件、实体窗体和 Web 窗体。

您必须使用**资源管理器**作为部署模型创建存储帐户。 [!include[More information](../../includes/proc-more-information.md)] [创建 Azure 存储帐户](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account)。

运行存储帐户后，门户需要特定的全局设置以告知应用程序如何查找您的存储帐户。 在门户管理应用中，转至**设置** > **新建**，然后添加名为 **FileStorage/CloudStorageAccount** 的新设置。

> [!NOTE]
> 上传文件大小的上限为 125 MB。

若要查找 FileStorage/CloudStorageAccount 的值，则必须从您的 [!include[Azure portal](../../includes/pn-azure-portal.md)] 获得连接字符串。

1. 登录到你的 [!include[Azure portal](../../includes/pn-azure-portal.md)]。

2. 导航到您的存储帐户。

3. 选择**访问键**。

    ![从您的 Azure 门户找到连接字符串的值](media/key-azure-storage.png "从您的 Azure 门户找到连接字符串的值")

4. 在生成的面板中，找到标记为**连接字符串**的字段。 选择需要复制值的字段旁边的**复制**图标，然后将该值粘贴到新设置中：

    ![主要连接字符串值](media/primary-connection-string-azure-storage.png "主要连接字符串值")

    ![门户云存储帐户设置](media/portal-site-setting-cloud-storage-account.png "门户云存储帐户设置")

## <a name="specify-the-storage-container"></a>指定存储容器

如果在您的存储帐户中还没有 Azure Blob 容器，您必须使用 [!include[Azure portal](../../includes/pn-azure-portal.md)] 添加一个。

在[门户管理应用](configure/configure-portal.md)中，转至**设置** > **新建**，并添加名为 **FileStorage/CloudStorageContainerName** 的新字符串，使用您的容器名称作为值。

![门户云存储容器设置](media/portal-site-setting-cloud-storage-container.png "门户云存储容器设置")

## <a name="add-cors-rule"></a>添加 CORS 规则

您还必须按照下面的说明在您的 Azure 存储帐户上添加跨源资源共享 (CORS) 规则，否则您将看到常规的附件图标，而不是云图标：

- **允许的源**：指定您的域。 例如，contoso.crm.dynamics.com。
- **允许的动词**：GET、PUT、DELETE、HEAD、POST
- **允许的标头**：指定原始域可能对 CORS 请求指定的请求标头。 例如，x-ms-meta-data\*、x-ms-meta-target\*。 
- **显示的标头**：指定可能在响应 CORS 请求时发送并由浏览器向请求颁发者显示的响应标头。 例如，x-ms-meta-\*。
- **最长存在时间（秒）**：指定浏览器缓存预检 OPTIONS 请求的最大时间量。 例如，200。
 
[!include[More information:](../../includes/proc-more-information.md)] [Azure 存储服务的 CORS 支持](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)

## <a name="add-site-settings"></a>添加站点设置

从**门户** > **站点设置**添加以下站点设置。 [!include[More information:](../../includes/proc-more-information.md)] [管理门户站点设置](configure/configure-site-settings.md#manage-portal-site-settings)。

|姓名|值|
|-----|-----|
|WebFiles/CloudStorageAccount|提供与为 FileStorage/CloudStorageAccount 设置提供的相同的连接字符串。|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

您现在可以在门户中创建子文件，并在 Azure Blob 地址 URL 中提及完全限定的名称（及容器）。 进行这些设置后，您的门户已准备好开始从 Azure 存储上载和下载文件。 但是，在您[添加 Web 资源以启用将附件上载到 Azure 存储](add-web-resource.md) 并配置[实体窗体](configure-notes.md#notes-configuration-for-entity-forms) 或 [Web 窗体](configure-notes.md#notes-configuration-for-web-forms) 以使用它以前，您无法完全使用该功能。

### <a name="see-also"></a>另请参阅

[添加 Web 资源](add-web-resource.md)

[配置注释](configure-notes.md)
