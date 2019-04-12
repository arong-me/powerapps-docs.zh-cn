---
title: 使用 PowerApps 共享模型驱动应用程序 | Microsoft Docs
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
ms.date: 03/19/2019
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="share-a-model-driven-app-with-powerapps"></a>使用 PowerApps 共享模型驱动应用程序

[!INCLUDE [powerapps](../../includes/powerapps.md)] 应用程序使用基于角色的安全性进行共享。 基于角色的安全性的基本概念是，权限角色包含定义了可以在应用程序内执行的操作集权限。 必须为所有应用程序用户分派一个或多个预定义角色或自定义角色。 或者，角色还可以分派给团队。 将用户或团队分派给这些角色之一时，会为该用户或团队成员授予与该角色相关联的权限集。 

在本主题中，您执行共享模型驱动应用程序的任务，以便其他人可以使用它。 您了解如何：
- 创建自定义安全角色
- 将用户分派给自定义安全角色
- 为应用程序分派安全角色

## <a name="prerequisites"></a>必备条件 
若要共享应用程序，您必须具有 [!INCLUDE [powerapps](../../includes/powerapps.md)] 环境管理员或系统管理员角色。 

## <a name="sign-in-to-powerapps"></a>登录到 PowerApps
登录到 [PowerApps](https://powerapps.microsoft.com/)。 如果还没有 [!INCLUDE [powerapps](../../includes/powerapps.md)] 帐户，请选择**免费开始**链接。

## <a name="share-an-app"></a>共享应用程序 
本主题将以公司 Contoso 为例，其经营为狗和猫服务的宠物美容业务。 包含跟踪宠物美容业务的自定义实体的应用程序已经创建并发布。 现在必须共享该应用程序，以便宠物美容人员可以使用它。 若要共享应用程序，管理员或应用程序制造者向用户和应用程序分派一个或多个安全角色。 

## <a name="create-or-configure-a-security-role"></a>创建或配置安全角色
[!INCLUDE [powerapps](../../includes/powerapps.md)] 环境包含[预定义的安全角色](#about-predefined-security-roles)，这些角色反映了常见用户任务，并且定义了访问级别以匹配安全性最佳实践目标：提供对使用应用程序所需的最少量的业务数据的访问。 请记住，Contoso 宠物美容应用程序基于自定义实体。 由于实体是自定义的，必须明确指定权限，然后用户才可以使用它。 为此，您可以选择执行以下操作之一。
- 扩展现有的预定义的安全角色，以便它在基于自定义实体的记录中包括权限。 
- 为管理应用程序用户的权限创建自定义安全角色。 

由于维护宠物美容记录的环境还用于 Contoso 业务运行的其他应用程序，因此将创建特定于宠物美容应用程序的自定义安全角色。 此外，还需要两组不同的访问权限。
- 宠物美容技术人员只需阅读、更新和附加其他记录，以便其安全角色具有阅读、编写和附加权限。 
- 宠物美容计划人员需要宠物美容技术人员所具有的所有权限，以及创建、附加、删除和共享功能，以便其安全角色具有创建、阅读、编写、附加、删除、分派、附加到和共享权限。

有关访问和范围权限的详细信息，请参阅[安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles)。

## <a name="create-a-custom-security-role"></a>创建自定义安全角色
1. 在 [!INCLUDE [powerapps](../../includes/powerapps.md)] 站点，选择**应用** > **…**> **共享链接**。

2. 在**共享此应用程序**对话框中，在**创建安全角色**下选择**安全设置**。

3. 在**设置**页上，选择**新建**。  

4. 从安全角色设计器，选择操作，如用于执行该操作的阅读、编写、删除和范围。 范围确定用户在环境层次结构中可以执行某项操作的深度或高度。 在**角色名称**框中输入*宠物美容技术人员*。

5. 选择**自定义实体**选项卡，然后找到所需的自定义实体。 对于此示例，使用名为**宠物**的自定义实体。 

6. 在**宠物**行，选择下列权限中每个权限四次，直到组织范围的全局![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)已选择：**阅读、编写、附加**

   > [!div class="mx-imgBorder"] 
   > ![新安全角色](media/share-model-driven-app/custom-security-role.png)

7. 由于宠物美容应用程序还与客户实体之间存在关系，选择**核心记录**选项卡，在**客户**行选择**阅读**四次直到组织范围的全局![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)已选择。 

8. 选择**自定义**选项卡，然后在权限列表中，选择**模型驱动应用程序**旁边的**读取**权限，以便选择组织范围 ![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)。

9. 选择**保存并关闭**。 

10. 在安全角色设计器上，在**角色名称**框中输入*宠物美容计划人员*。 

11. 选择**自定义实体**选项卡，然后找到**宠物**实体。 

12. 在**宠物**行，选择下列权限中每个权限四次，直到组织范围的全局![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)已选择：**创建、阅读、编写、删除、附加、附加到、分派、共享**

13. 由于宠物美容应用程序还与客户实体之间存在关系，计划人员必须能够创建和修改客户记录，选择**核心记录**选项卡，在**客户**行选择下列权限中每个权限四次，直到组织范围的全局![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)已选择。 
    **创建、读取、写入、删除、追加、追加到、分派、共享**

14. 选择**保存并关闭**。

## <a name="assign-security-roles-to-users"></a>将安全角色分派给用户
安全角色通过一组访问级别和权限来控制用户对数据的访问。 包括在特定安全角色中的访问级别和权限的组合对用户查看数据以及与该数据交互设置了限制。

### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>向宠物美容技术人员分派安全角色
1. 在**共享此应用程序**对话框中，在**向安全角色分派用户**下选择**安全用户**。
2. 在显示的列表中，选择宠物美容人员。
3. 选择**管理角色**。

    > [!div class="mx-imgBorder"] 
    > ![管理角色](media/share-model-driven-app/select-users-for-security-roles.png)

4. 在**管理用户角色**对话框中，选择您之前创建的**宠物美容技术人员**安全角色，然后选择**确定**。

### <a name="assign-a-security-role-to-pet-grooming-schedulers"></a>向宠物美容计划人员分派安全角色
1. 在**共享此应用程序**对话框中，在**向安全角色分派用户**下选择**安全用户**。
2. 在显示的列表中，选择宠物美容计划人员。
3. 选择**管理角色**。
4. 在**管理用户角色**对话框中，选择您之前创建的**宠物美容计划人员**安全角色，然后选择**确定**。


## <a name="add-security-roles-to-the-app"></a>向应用程序添加安全角色
接下来，需要将一个或多个安全角色分派到应用程序。 用户基于被分配的安全角色拥有访问应用程序的权限。
1. 在**共享此应用程序**对话框中，在**向应用程序添加安全角色**下选择**我的应用程序**。
2. 在 Contoso 宠物美容应用程序的应用程序磁贴的右下角，选择**更多选项 (...)**，然后选择**管理角色**。

    ![管理应用程序的角色](media/share-model-driven-app/manage-roles.png)

4. 在**角色**分区，您可以选择是否授予应用程序访问所有安全角色或选择角色的权限。 选择您之前创建的**宠物美容计划人员**和**宠物美容技术人员**角色。

    > [!div class="mx-imgBorder"] 
    > ![选择应用程序的安全角色](media/share-model-driven-app/app-security-roles.png)

5. 选择**保存**。
 
## <a name="share-the-link-to-your-app"></a>共享应用程序的链接
1. 从**共享此应用程序**对话框，在**直接与用户共享您的应用程序的链接**下复制显示的 URL。
 
2. 选择**关闭**。
3. 在一个位置粘贴应用程序 URL 以便用户能够访问，如将它发布到 SharePoint 站点或通过电子邮件发送。

> [!div class="mx-imgBorder"] 
> ![共享链接](media/share-model-driven-app/share-model-driven-URL.PNG)

您还可以在应用程序设计器中的**属性**选项卡上找到应用程序 URL。 

> [!div class="mx-imgBorder"] 
> ![复制应用程序 URL](media/share-model-driven-app/app-designer-copy-web-url.png)

## <a name="about-predefined-security-roles"></a>关于预定义的安全角色
这些预定义角色随 [!INCLUDE [powerapps](../../includes/powerapps.md)] 环境提供。


|安全角色  |*权限  |说明 |
|---------|---------|---------|
|环境制造者     |  无       | 可以使用 Microsoft Flow 创建与环境关联的新资源，包括应用程序、连接、自定义 API、网关和流。 但是，不具有访问环境中的数据的任何权限。 更多信息：[环境概述](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|系统管理员     |  创建、阅读、编写、删除、自定义、安全角色       | 具有自定义或管理环境的完全权限，包括创建、修改和分派安全角色。 可以查看环境中的所有数据。 详细信息：[自定义所需的权限](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|系统定制员     | 创建（自助）、阅读（自助）、编写（自助）、删除（自助）、自定义         | 拥有自定义环境的所有权限 但是，只能查看其创建的环境实体的记录。 详细信息：[自定义所需的权限](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Common Data Service 用户     |  阅读、创建（自助）、编写（自助）、删除（自助）       | 可在环境中运行应用程序并对其所有的记录执行常规任务。        |
|代理     | 代表其他用户执行操作        | 允许代码作为另一个用户运行或模拟运行。  通常用于另一个安全角色以允许访问记录。 详细信息：[模拟其他用户](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*除非另外指定，否则权限是全局范围。

## <a name="next-steps"></a>后续步骤
[在移动设备上运行模型驱动应用程序](../../user/run-app-client-model-driven.md)



