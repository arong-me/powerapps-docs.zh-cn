---
title: 在门户中管理 SharePoint 文档 | MicrosoftDocs
description: 在门户中管理 SharePoint 文档的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f94dee983d5d2d9cedf417f2843a2c10c46b82c1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756970"
---
# <a name="manage-sharepoint-documents"></a>管理 SharePoint 文档

Common Data Service 支持与 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] 集成，您可以使用来自 Common Data Service 内的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 的文档管理功能。 PowerApps 门户现在支持直接在门户中的实体窗体和 Web 窗体上从 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 或向其中上载和显示文档。 这使门户用户可以从门户查看、下载、添加和删除文档。 门户用户还可以创建子文件夹来管理文档。

> [!NOTE]
> - 文档管理只能通过 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] 使用。
> - 文档管理通过基于服务器的集成来支持。

若要从 Common Data Service 内使用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 的文档管理功能，您必须：

1.  [在 Dynamics 365 中的模型驱动应用中启用文档管理功能](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [从 PowerApps 门户管理中心设置 SharePoint 集成](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)

3.  [对实体启用文档管理](#step-3-enable-document-management-for-entities)

4.  [在 PowerApps 文档中配置适当的窗体](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [创建相应的实体权限并将其分派给相应的 Web 角色](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>步骤 1：在 Dynamics 365 中的模型驱动应用中启用文档管理功能

您必须使用基于服务器的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成来在 Dynamics 365 中的模型驱动应用中启用文档管理功能 。 基于服务器的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成允许 Dynamics 365 和 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] 中的模型驱动应用执行服务器到服务器的连接。 默认的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 网站记录供门户使用。 有关如何在 Dynamics 365 中的模型驱动应用中启用文档管理功能的信息，请参阅[在 Dynamics 365 中设置模型驱动应用以使用 SharePoint Online](https://docs.microsoft.com/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online)。

## <a name="step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center"></a>步骤 2：从 PowerApps 门户管理中心设置 SharePoint 集成

若要使用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 的文档管理功能，您必须从 PowerApps 门户管理中心启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成。

> [!NOTE]
> 您必须是全局管理员才可以执行此操作。

1. 打开 [PowerApps 门户管理中心](admin/admin-overview.md)。

2.  转到**设置 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成** > **启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成**。

    > [!div class=mx-imgBorder]
    > ![启用 SharePoint 集成](media/enable-sharepoint-integration.png "启用 SharePoint 集成")

3.  在确认窗口中选择**启用**。 这使门户可以与 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 通信。 在 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成启用后，门户将重启，并且会在几分钟内不可用。 在启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成后将显示一条消息。

启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成后，以下操作将变为可用：

- **禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成**：让您可以禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 与您的门户的集成。 在 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成禁用后，门户将重启，并且会在几分钟内不可用。 在禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成后将显示一条消息。

    > [!div class=mx-imgBorder]
    > ![禁用 SharePoint 集成](media/disable-sharepoint-integration.png "禁用 SharePoint 集成")

启用或禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成将更新门户的 [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD) 应用程序，并分别添加或移除所需的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 权限。 您还将被重定向以为您提供对 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 应用程序所做更改的同意表示。 

> [!div class=mx-imgBorder]
> ![禁用 SharePoint 集成](media/sharepoint-integration-consent.png "禁用 SharePoint 集成")

如果您不提供同意表示：

- 启用或禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成将不会完成，并将显示错误消息。

- 您在门户上的现成可用的 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] 登录将不工作。 


## <a name="step-3-enable-document-management-for-entities"></a>步骤 3：为实体启用文档管理
您必须为实体启用文档管理以在 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 中存储与实体记录相关的文档。 有关如何为实体启用文档管理的信息，请参阅[为特定实体启用 SharePoint 文档管理](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities)。

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>步骤 4：配置用于显示文档的合适窗体

### <a name="powerapps-customization"></a>PowerApps 自定义

确定您要使用文档管理功能的窗体。 您必须使用模型驱动应用窗体编辑器编辑窗体，并向其添加子网格。 子网格向窗体添加分区，这允许您从门户内处理文档。 您必须在子网格中设置下列属性才可以使用此功能：

- 在**数据源**下，从**实体**列表中选择**文档位置**。

- 在**数据源**下，从**默认视图**列表中选择**可用文档位置**。

您可以按照您的要求指定名称和标签。 在添加和配置子网格后保存并发布窗体。

> [!NOTE]
> 必须为您要编辑窗体的实体启用文档管理。 更多信息：[对实体启用文档管理](#step-3-enable-document-management-for-entities)

### <a name="powerapps-portals-configuration"></a>PowerApps 门户配置

除了实体窗体或 Web 窗体所需的标准配置外，您还必须设置以下属性以启用文档管理：

- **实体名称**和**窗体名称**：分别输入在先前步骤中自定义的实体和窗体名称。

- 在窗体上选择**启用实体权限**复选框以允许用户阅读文档。

- 设置**编辑**的**模式**以允许文档上载。

> [!NOTE]
> 需要父实体记录才能上传文档。 如果将“模式”设置为“插入”，将无法上传文档，因为提交窗体之前不会创建父实体记录。

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>步骤 5：创建相应的实体权限并将其分派给相应的 Web 角色

建立查看和上载文档的必要访问权限需要两个实体权限记录。

- 实体或 Web 窗体的实体的权限： 
    - 创建将**实体名称**指定为以前配置的实体窗体或 Web 窗体的实体的**实体权限**记录。 
    - 选择适合所需的窗体行为的**范围**和范围关系。 
    - 启用**读取**和**追加到**权限以允许读取访问文档，并有选择地启用**写入**权限以允许文档上载。 请暂时忽略**子实体权限**部分，下一步会加以说明。
- 具有引用以前权限记录的**父范围**的**文档位置**中的权限： 
    - 创建指定**实体名称**为**文档位置**实体（**范围**设置为**父**）的**实体权限**记录。 
    - 选择在上一步中创建的实体权限记录的父实体权限。 
    - 权限 
        - 允许读取访问文档的最低权限为**读取**、**创建**和**追加**。 
        - 包括**写入**权限以允许文档上载访问。 
        - 包括**删除**以允许删除文档。

> [!NOTE]
> **文档位置**实体中对应的子实体权限需要为存在于实体窗体或 Web 窗体（文档需要在其中显示）的实体的父实体权限记录的每个实例创建。

## <a name="configure-file-upload-size"></a>配置文件上载大小

默认情况下，文件大小设置为 10 MB。 不过，您可以使用站点设置 `SharePoint/MaxUploadSize` 将文件大小配置为最大 50 MB。

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>在案例实体窗体上启用文档管理的示例配置

下面的示例演示了使用案例实体进行的配置，其必须要有 Dynamics 365 Customer Service 使用程序。 虽然此示例使用案例实体，但是它只是上述步骤的说明，可以与支持在 SharePoint 中管理文档的任何其他自定义实体或任何 Common Data Service 实体结合使用。 

1.  按照[步骤 1](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365) 中的说明操作，以确保基于服务器的配置对于 Dynamics 365 中的模型驱动应用和 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成是完整的。

2.  按照[步骤 2](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center) 中的说明操作，以确保门户有权与 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成。 

3.  按照[步骤 3](#step-3-enable-document-management-for-entities) 中的说明操作，以确保为案例实体启用了文档管理。

4.  按照[步骤 4](#step-4-configure-the-appropriate-form-to-display-documents) 中的说明进行以下配置：

    - Dynamics 365 自定义中的模型驱动应用

        a. 转到**设置** > **自定义** > **自定义系统**。 

        b. 在**默认解决方案**中，转到**案例**实体 > **窗体**。 
    
        c. 在窗体编辑器中打开 **Web – 编辑案例**。

         > [!div class=mx-imgBorder]
         > ![Web - 编辑案例窗体](media/web-edit-case-form.png "Web - 编辑案例窗体")
    
        d. 在窗体中选择**创建日期**字段，在**插入**选项卡中，选择**子网格**。

         > [!div class=mx-imgBorder]
         > ![向 Web - 编辑案例窗体添加子网格](media/add-sub-grid.png "向 Web - 编辑案例窗体添加子网格")
    
        e. 在**设置属性**对话框中，设置以下属性，然后选择**确定**：

         - **名称**（可以是任何名称）：CaseDocuments 
    
         - **标签**（可以是任何标签名称）：案例文档 
      
         - **实体**：文档位置 
    
         - **默认视图**：可用文档位置

         > [!div class=mx-imgBorder]
         > ![子网格属性](media/sub-grid-properties.png "子网格属性")

        f. 在窗体编辑器中，选择**保存**，然后选择**发布**。

    - PowerApps 门户配置

        a. 转到**门户** > **实体窗体**。
    
        b. 找到并打开**客户服务 - 编辑案例**实体窗体。
    
        c. 检查并确保设置了以下属性：
    
         - **实体名称**：案例（事件）
    
         - **窗体名称**：Web – 编辑案例
    
         - **模式**：退出
    
         - **实体权限**：已启用
    
         > [!div class=mx-imgBorder]
         > ![客户服务 - 编辑案例窗体](media/customer-service-edit-case-form.png "客户服务 - 编辑案例窗体")
    
        d. 如果您对窗体进行了任何更改，请选择**保存**。

5. 按照[步骤 5](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
) 操作以确保向用户授予了实体权限。

   1. 转到与用户关联的 **Web 角色**记录。 对于此示例，我们假定用户具有管理员 Web 角色。

   2. 通过名称**客户服务 - 案例(联系人为客户时)** 确保实体权限记录存在。 

      > [!NOTE]
      > 确保您的 Web 角色已添加了此实体权限。 如果您的用户已经是管理员，则不需要明确分派上面的实体权限。

   3. 创建新实体特权，输入以下详细信息，然后选择**保存**：

    - **名称**（可以是任何名称）：客户服务 - 相关文档

    - **实体名称**：文档位置
        
    - **范围**：父
        
    - **父实体权限**：客户服务 - 案例(联系人为客户时)
        
    - **父关系**：incident_SharePointDocumentLocations
        
    - **权限**：读取、创建、追加、写入、删除

      > [!div class=mx-imgBorder]
      > ![客户服务实体权限](media/customer-service-entity-permission.png "客户服务实体权限")
  
   4. 登录到门户以确保为案例实体启用了文档管理。

      a. 转到**支持**页。

      > [!div class=mx-imgBorder]
      > ![门户支持页面](media/portal-support-page.png "门户支持页面")

      b. 从列表单击现有的案例记录。 转到页面上的**案例文档**部分并查看添加的文档列表。

      > [!div class=mx-imgBorder]
      > ![案例文档](media/case-document.png "案例文档")

