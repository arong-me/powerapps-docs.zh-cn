---
title: 在门户中管理 SharePoint 文档 |MicrosoftDocs
description: 门户上的管理 SharePoint 文档的说明。
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543330"
---
# <a name="manage-sharepoint-documents"></a>管理 SharePoint 文档

Common Data Service 支持与 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] 的集成，使你能够使用 Common Data Service 中 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 的文档管理功能。 PowerApps 门户现在支持通过门户中的实体窗体或 web 窗体上的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 直接上传和显示文档。 这样，门户用户便可以在门户中查看、下载、添加和删除文档。 门户用户还可以创建子文件夹来组织其文档。

> [!NOTE]
> - 文档管理仅适用于 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)]。
> - 基于服务器的集成支持文档管理。

若要在 Common Data Service 中使用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 的文档管理功能，必须执行以下操作：

1.  [在 Dynamics 365 的模型驱动应用中启用文档管理功能](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [从 PowerApps 门户管理中心设置 SharePoint 集成](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)

3.  [为实体启用文档管理](#step-3-enable-document-management-for-entities)

4.  [在 PowerApps 文档中配置适当的窗体](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [创建相应的实体权限，并将其分配给相应的 web 角色](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>步骤1：在 Dynamics 365 中启用模型驱动应用中的文档管理功能

你必须通过使用基于服务器的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成在 Dynamics 365 中的模型驱动应用中启用文档管理功能。 基于服务器的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成允许 Dynamics 365 和 [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] 中的模型驱动应用执行服务器到服务器连接。 门户将使用默认 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 站点记录。 有关如何在 Dynamics 365 的模型驱动应用中启用文档管理功能的信息，请参阅[在 dynamics 365 中设置模型驱动的应用，以使用 SharePoint Online](https://docs.microsoft.com/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online)。

## <a name="step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center"></a>步骤2：设置 SharePoint 与 PowerApps 门户管理中心的集成

若要使用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]的文档管理功能，必须从 PowerApps 门户管理中心启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成。

> [!NOTE]
> 只有全局管理员才能执行此操作。

1. 打开[PowerApps 门户管理中心](admin/admin-overview.md)。

2.  请参阅**设置 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成** > **启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成**。

    > [!div class=mx-imgBorder]
    > ![启用 SharePoint 集成](media/enable-sharepoint-integration.png "启用 SharePoint 集成")

3.  在确认窗口中选择 "**启用**"。 这会使门户能够与 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]通信。 虽然正在启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成，但门户在几分钟内就会重新启动并不可用。 启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成后，将显示一条消息。

启用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成后，可以使用以下操作：

- **禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成**：允许你禁用与门户的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成。 虽然正在禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成，但门户在几分钟内就会重新启动并不可用。 禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成时，会出现一条消息。

    > [!div class=mx-imgBorder]
    > ![禁用 SharePoint 集成](media/disable-sharepoint-integration.png "禁用 SharePoint 集成")

启用或禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成将更新门户的 [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] （[!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD）应用程序，并分别添加或删除所需的 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 权限。 你还将被重定向以向你授予在 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 应用程序中进行更改的许可。 

> [!div class=mx-imgBorder]
> ![禁用 SharePoint 集成](media/sharepoint-integration-consent.png "禁用 SharePoint 集成")

如果未提供许可：

- 启用或禁用 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成将不会完成，并将显示一条错误消息。

- 门户中的现成 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 登录将不起作用。 


## <a name="step-3-enable-document-management-for-entities"></a>步骤3：为实体启用文档管理
您必须对实体启用文档管理，以存储与 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]中的实体记录相关的文档。 有关如何为实体启用文档管理的信息，请参阅为[特定实体启用 SharePoint 文档管理](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities)。

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>步骤4：配置适当的窗体以显示文档

### <a name="powerapps-customization"></a>PowerApps 自定义

确定要使用文档管理功能的窗体。 必须通过使用模型驱动应用窗体编辑器来编辑窗体，并向其添加子网格。 子网格将向窗体添加一个节，这允许您在门户中处理文档。 若要使此功能正常工作，必须在子网格中设置以下属性：

- 在 "**数据源**" 下，选择 "**实体**" 列表中的**文档位置**。

- 在 "**数据源**" 下，从**默认视图**列表中选择 "**活动文档位置**"。

你可以根据需要指定名称和标签。 添加并配置子网格后，保存并发布该窗体。

> [!NOTE]
> 对于您编辑窗体的实体，必须启用文档管理。 详细信息：[为实体启用文档管理](#step-3-enable-document-management-for-entities)

### <a name="powerapps-portals-configuration"></a>PowerApps 门户配置

除了实体窗体或 web 窗体所需的标准配置之外，您还必须设置以下属性以启用文档管理：

- **实体名称**和**窗体名称**：分别输入在上一步中自定义的实体和窗体名称。

- 选中窗体上的 "**启用实体权限**" 复选框，以允许用户读取文档。

- 将**模式**设置为 "**编辑**" 以允许文档上传。

> [!NOTE]
> 文档上传要求存在父实体记录。 如果将模式设置为 "插入"，文档上传将不起作用，因为在提交窗体之前不会创建父实体记录。

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>步骤5：创建适当的实体权限，并将其分配给相应的 web 角色

需要两个实体权限记录来建立查看和上载文档所必需的访问权限。

- 实体或 web 窗体实体的权限： 
    - 创建**实体权限**记录，将**实体名称**指定为以前配置的实体窗体或 web 窗体的实体。 
    - 选择适合于窗体所需行为的**作用域**和作用域关系。 
    - 启用 "**读取**" 和 "**追加到**" 权限以允许对文档进行读访问，还可以选择启用 "**写入**" 权限以允许文档上传。 现在忽略**子实体权限**部分，因为它将在下一步中进行填充。
- 具有引用以前的权限记录的**父作用域**的**文档位置**权限： 
    - 创建**实体权限**记录，将**实体名称**指定为 "**文档位置**" 实体，并将 "**范围**" 设置为 "**父级**"。 
    - 为在上一步中创建的实体权限记录选择父实体权限。 
    - 特权 
        - 允许读取、**创建**和**追加** **文档的最**小特权。 
        - 包含文档上传访问权限的**写入**权限。 
        - 包含**删除**以允许删除文档。

> [!NOTE]
> 对于在需要显示文档的实体或 web 窗体实体上存在的每个父实体权限记录实例，需要为该实体的每个实例创建**相应的子**实体权限。

## <a name="configure-file-upload-size"></a>配置文件上传大小

默认情况下，文件大小设置为 10 MB。 但是，可以使用站点设置 `SharePoint/MaxUploadSize`将文件大小配置为最大为 50 MB。

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>在案例实体窗体上启用文档管理的示例配置

下面的示例演示如何使用事例实体进行配置，该实体需要 Dynamics 365 客户服务应用程序作为必备组件。 虽然此示例使用的是 Case 实体，但它只是上述步骤的图示，可以跟任何其他自定义实体或支持在 SharePoint 中管理文档的任何 Common Data Service 实体。 

1.  按照[步骤 1](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)中的说明，确保基于服务器的配置对于 Dynamics 365 中的模型驱动应用和 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 集成都是完整的。

2.  按照[步骤 2](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)中的说明进行操作，以确保门户有权与 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]集成。 

3.  按照[步骤 3](#step-3-enable-document-management-for-entities)中的说明进行操作，以确保为案例实体启用文档管理。

4.  按照[步骤 4](#step-4-configure-the-appropriate-form-to-display-documents)中的说明进行操作，并进行以下配置：

    - Dynamics 365 中模型驱动的应用自定义

        a. 请参阅 "**设置**" > **自**定义 > **自定义系统**。 

        b. 在**默认解决方案**中，请参阅**Case**实体 >**窗体**。 
    
        c. 在窗体编辑器中打开**Web 编辑事例**。

         > [!div class=mx-imgBorder]
         > ![Web 编辑 Case 窗体](media/web-edit-case-form.png "Web 编辑 Case 窗体")
    
        d. 选择窗体上的 "**创建于**" 字段，然后在 "**插入**" 选项卡上选择 "**子网格**"。

         > [!div class=mx-imgBorder]
         > ![向 Web 编辑用例窗体添加子网格](media/add-sub-grid.png "向 Web 编辑用例窗体添加子网格")
    
        e. 在 "**设置属性**" 对话框中，设置以下属性，然后选择 **"确定"** ：

         - **名称**（可以是任何名称）： CaseDocuments 
    
         - **标签**（可以是任何标签名称）：案例文档 
      
         - **实体**：文档位置 
    
         - **默认视图**：活动文档位置

         > [!div class=mx-imgBorder]
         > ![子网格属性](media/sub-grid-properties.png "子网格属性")

        果. 在窗体编辑器中，选择 "**保存**"，然后选择 "**发布**"。

    - PowerApps 门户配置

        a.  > **实体窗体**中转到**门户**。
    
        b. 查找并打开**客户服务-编辑案例**实体窗体。
    
        c. 查看并确保已设置以下属性：
    
         - **实体名称**：事例（事件）
    
         - **表单名称**： Web –编辑事例
    
         - **模式**：编辑
    
         - **实体权限**：已启用
    
         > [!div class=mx-imgBorder]
         > ![客户服务-编辑案例窗体](media/customer-service-edit-case-form.png "客户服务-编辑案例窗体")
    
        d. 如果对窗体进行了任何更改，请选择 "**保存**"。

5. 按照[步骤 5](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
)确保向用户授予实体权限。

   1. 中转到与用户关联的**Web 角色**记录。 对于此示例，我们假定用户具有管理员 web 角色。

   2. 确保实体权限记录位于**contact 为 customer 的客户服务事例**的名称中。 

      > [!NOTE]
      > 确保你的 web 角色已添加此实体权限。 如果用户已是管理员，则不需要显式分配上述 entity 权限。

   3. 创建新的实体权限，输入以下详细信息，然后选择 "**保存**"：

    - **名称**（可以是任何名称）：与客户服务相关的文档

    - **实体名称**：文档位置
        
    - **作用域**：父项
        
    - **父实体权限**：客户服务-联系人为 Customer 的案例
        
    - **父关系**： incident_SharePointDocumentLocations
        
    - **权限**：读取、创建、追加、写入、删除

      > [!div class=mx-imgBorder]
      > ![Customer Service 实体权限](media/customer-service-entity-permission.png "Customer Service 实体权限")
  
   4. 登录到门户，确保为 "案例" 实体启用文档管理。

      a. 请参阅**支持**页。

      > [!div class=mx-imgBorder]
      > ![门户支持页](media/portal-support-page.png "门户支持页")

      b. 单击列表中的现有事例记录。 中转到页面上的 "**案例文档**" 部分，并查看添加的文档列表。

      > [!div class=mx-imgBorder]
      > ![案例文档](media/case-document.png "案例文档")

