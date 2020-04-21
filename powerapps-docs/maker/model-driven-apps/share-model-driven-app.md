---
title: 使用 Power Apps 共享模型驱动应用 | Microsoft Docs
description: 了解如何共享模型驱动应用程序
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/04/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e1187757c90af2ec245ace51031f5e0345c92bd2
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "3238446"
---
# <a name="share-a-model-driven-app-with-power-apps"></a>使用 Power Apps 共享模型驱动应用

[!INCLUDE [powerapps](../../includes/powerapps.md)] 应用程序使用基于角色的安全性进行共享。 基于角色的安全性的基本概念是，权限角色包含定义了可以在应用程序内执行的操作集权限。 必须为所有应用程序用户分派一个或多个预定义角色或自定义角色。 或者，角色还可以分派给团队。 将用户或团队分派给这些角色之一时，会为该用户或团队成员授予与该角色相关联的权限集。 

## <a name="prerequisites"></a>先决条件
确保您具有一个[安全角色](https://docs.microsoft.com/power-platform/admin/security-roles-privileges)，其权限等于或大于您分配给应用用户和其他用户的角色。 

## <a name="create-a-security-role-for-your-app"></a>为您的应用创建安全角色
模型驱动应用通常包含自定义实体和其他自定义配置。 首先[创建安全角色](#create-a-security-role-for-your-app)并具有您应用中使用的所有组件的权限，这一点很重要。  
> [!NOTE]
> 如果现有角色授予应用中的数据的访问权限，则可以跳过此步骤。 

## <a name="preview-share-a-model-driven-app"></a>预览：共享模型驱动应用 
共享模型驱动应用涉及两个主要步骤。 首先，将一个或多个安全角色与应用关联，然后将安全角色分配给用户。 
1. 访问 https://make.powerapps.com
2. 选择一个模型驱动应用并单击**共享**。
3. 选择该应用，然后从列表中选择安全角色。
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/share-app.png "Assign a role to the app")
4. 搜索用户
5. 选择用户，然后从列表中选择一个角色。
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/share-user.png "Assign a role to the user")
6. 单击**共享**。

### <a name="share-the-link-to-your-app"></a>共享应用程序的链接
与共享画布应用不同，共享模型驱动应用当前不会发送包含应用链接的电子邮件。

要获取指向应用的直接链接：
1. 编辑应用并单击**属性**选项卡
2. 复制**统一接口 URL**。
3. 在一个位置粘贴应用 URL 以便用户能够访问，如将它发布到 SharePoint 站点或通过电子邮件发送。


## <a name="create-or-configure-a-security-role"></a>创建或配置安全角色
[!INCLUDE [powerapps](../../includes/powerapps.md)] 环境包含[预定义的安全角色](#about-predefined-security-roles)，这些角色反映了常见用户任务，并且定义了访问级别以匹配安全性最佳实践目标：提供对使用应用程序所需的最少量的业务数据的访问。 例如，如果您的应用基于自定义实体，则必须明确指定实体特权，然后用户才可以使用它。 为此，您可以选择执行以下操作之一。
- 扩展现有的预定义的安全角色，以便它在基于自定义实体的记录中包括权限。 
- 为管理应用程序用户的权限创建自定义安全角色。 

有关访问和范围权限的详细信息，请参阅[安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles)。

### <a name="create-a-custom-security-role"></a>创建自定义安全角色
1. 在 [!INCLUDE [powerapps](../../includes/powerapps.md)] 站点中，选择**应用**，选择要共享的应用旁边的 **…**，然后选择**共享**。

2. 选择该应用，然后展开安全角色列表。

3. 在**所有角色**页上，选择**新建**。  

4. 从安全角色设计器，选择操作，如用于执行该操作的阅读、编写、删除和范围。 范围确定用户在环境层次结构中可以执行某项操作的深度或高度。 在**角色名称**框中输入*宠物美容技术人员*。

5. 选择**自定义实体**选项卡，然后找到所需的自定义实体。 对于此示例，使用名为**宠物**的自定义实体。 

6. 在**宠物**行，选择下列权限中每个权限四次，直到组织范围的全局![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)已选择：**阅读、编写、附加**

   > [!div class="mx-imgBorder"] 
   > ![新安全角色](media/share-model-driven-app/custom-security-role.png)

7. 由于宠物美容应用程序还与客户实体之间存在关系，选择**核心记录**选项卡，在**客户**行选择**阅读**四次直到组织范围的全局![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)已选择。 

8. 选择**自定义**选项卡，然后在权限列表中，选择**模型驱动应用程序**旁边的**读取**权限，以便选择组织范围 ![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)。

    > [!div class="mx-imgBorder"] 
    > ![选择应用程序的安全角色](media/app-access-specific-use.png)

9. 选择**保存并关闭**。 

10. 在安全角色设计器上，在**角色名称**框中输入*宠物美容计划人员*。 

11. 选择**自定义实体**选项卡，然后找到**宠物**实体。 

12. 在**宠物**行，选择下列权限中每个权限四次，直到组织范围的全局![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)已选择：**创建、阅读、编写、删除、附加、附加到、分派、共享**

13. 由于宠物美容应用程序还与客户实体之间存在关系，计划人员必须能够创建和修改客户记录，选择**核心记录**选项卡，在**客户**行选择下列权限中每个权限四次，直到组织范围的全局![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)已选择。 
    **创建、读取、写入、删除、追加、追加到、分派、共享**

14. 选择**保存并关闭**。

### <a name="assign-security-roles-to-users"></a>将安全角色分派给用户
安全角色通过一组访问级别和权限来控制用户对数据的访问。 包括在特定安全角色中的访问级别和权限的组合对用户查看数据以及与该数据交互设置了限制。

#### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>向宠物美容技术人员分派安全角色
1. 在**共享此应用程序**对话框中，在**向安全角色分派用户**下选择**安全用户**。
2. 在显示的列表中，选择宠物美容人员用户，然后在命令栏上选择**管理角色**。

3. 单击**管理安全角色**。
    > [!div class="mx-imgBorder"] 
    > ![](media/share-model-driven-app/manage-roles.png "Manage roles")

4. 在**所有角色**页面上，选择 **Common Data Service 用户**，然后依次单击**操作**、**复制角色**。 

> [!TIP]
> 您还可以创建新的空角色，而不是复制现有角色。 

6. 在**角色名称**框中，提供描述性的角色名称，例如*我的自定义应用访问*。  单击**确定**。

7. 从安全角色设计器，选择操作（如阅读、编写、删除）和[访问级别](https://docs.microsoft.com/power-platform/admin/security-roles-privileges#security-roles)。 访问级别确定用户在环境层次结构中可以执行某项操作的深度或高度。 

8. 选择**自定义实体**选项卡，然后找到您的应用使用的自定义实体。 

9.  在自定义实体所在的行中，设置每个权限的访问级别。  

10. 对应用中使用的其他实体重复上述操作。 

11. 选择**自定义**选项卡，确保为**模型驱动应用**设置了**读取**权限，以便选择组织访问级别 ![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)。

    > [!IMPORTANT]
    > 授予**模型驱动应用**权限**读取**、**创建**和**写入**的用户有权访问环境中的所有应用，即使他们不属于有权访问应用的任何角色。
    > ![模型驱动应用的创建和写入权限](media/app-access-cds.png)

12. 选择**保存并关闭**。 


## <a name="about-predefined-security-roles"></a>关于预定义的安全角色
这些预定义角色随 [!INCLUDE [powerapps](../../includes/powerapps.md)] 环境提供。


|安全角色  |*权限  |说明 |
|---------|---------|---------|
|环境制造者     |  无       | 可以使用 Power Automate 创建与环境关联的新资源，包括应用、连接、自定义 API、网关和流。 但是，不具有访问环境中的数据的任何权限。 更多信息：[环境概述](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|系统管理员     |  创建、阅读、编写、删除、自定义、安全角色       | 具有自定义或管理环境的完全权限，包括创建、修改和分派安全角色。 可以查看环境中的所有数据。 详细信息：[自定义所需的权限](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|系统定制员     | 创建（自助）、阅读（自助）、编写（自助）、删除（自助）、自定义         | 拥有自定义环境的所有权限 但是，只能查看其创建的环境实体的记录。 详细信息：[自定义所需的权限](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Common Data Service 用户     |  阅读、创建（自助）、编写（自助）、删除（自助）       | 可在环境中运行应用程序并对其所有的记录执行常规任务。        |
|代理     | 代表其他用户执行操作        | 允许代码作为另一个用户运行或模拟运行。  通常用于另一个安全角色以允许访问记录。 详细信息：[模拟其他用户](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*除非另外指定，否则权限是全局范围。

## <a name="use-azure-active-directory-groups-to-manage-access"></a>使用 Azure Active Directory 组管理访问权限
管理员可以使用其组织的 Azure Active Directory (Azure AD) 组管理已获得许可的 Common Data Service 用户的访问权限。 两种 Azure AD 组（“办公室”和“安全”）均可用用于保护用户的应用访问权限。 详细信息：[关于组团队](/power-platform/admin/manage-teams#about-group-teams) 


### <a name="see-also"></a>另请参阅
[在移动设备上运行模型驱动应用程序](../../user/run-app-client-model-driven.md)

[创建用户和分配安全角色](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)


