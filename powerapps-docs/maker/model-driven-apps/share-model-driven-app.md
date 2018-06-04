---
title: 借助 PowerApps 共享模型驱动应用的教程 | Microsoft Docs
description: 本教程介绍如何共享模型驱动应用
documentationcenter: ''
author: Mattp123
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: 4068bbc4e67adee344544c0ba69895244d3dab83
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "32330367"
---
# <a name="tutorial-share-a-model-driven-app-with-powerapps"></a>教程：借助 PowerApps 共享模型驱动应用

[!INCLUDE [powerapps](../../includes/powerapps.md)] 应用采用基于角色的安全性策略进行共享。 基于角色的安全性中的基本概念是包含特权的安全角色，这些特权定义了一套在应用中可以执行的操作。 必须向应用的所有用户分配一种或多种预定义角色或自定义角色。 或者，也可以向团队分配角色。 当用户或团队分配到其中一种角色时，该个人或团队成员就获得了与该角色关联的一组特权。 

在本教程中，你将执行共享模型驱动应用的任务，让其他人可以使用应用。 你将了解如何：
- 创建自定义安全角色
- 向用户分配自定义安全角色
- 向应用分配安全角色

## <a name="prerequisites"></a>先决条件
要共享应用，必须具备 [!INCLUDE [powerapps](../../includes/powerapps.md)] 环境管理员角色或系统管理员角色。 

## <a name="sign-in-to-powerapps"></a>登录到 PowerApps
登录 [PowerApps](https://powerapps.microsoft.com/)。 如果还没有 [!INCLUDE [powerapps](../../includes/powerapps.md)] 帐户，请选择“开始免费使用”链接。

## <a name="share-an-app"></a>共享应用 
本教程将以 Contoso 公司为例，该公司的主营业务是针对狗和猫的宠物美容。 已创建并发布包含跟踪宠物美容业务的自定义实体的应用。 现在必须共享该应用，让负责宠物美容的工作人员可以使用它。 要共享该应用，管理员或应用创建者需要将一种或多种安全角色分配给用户和应用。 

## <a name="create-or-configure-a-security-role"></a>创建或配置安全角色
[!INCLUDE [powerapps](../../includes/powerapps.md)] 环境包括[预定义的安全角色](#about-predefined-security-roles)，这些角色反映定义了访问级别以满足安全最佳做法目标（即在保证应用正常使用的基础上最大限度地控制用户对业务数据的访问）的常见用户任务。 请记住，Contoso 宠物美容应用是基于自定义实体的。 由于实体是自定义的，必须在用户开始使用前明确指定特权。 若要完成这项操作，可以选择执行下列操作之一。
- 展开现有预定义安全角色，确保其包括对基于自定义实体的记录的特权。 
- 创建自定义安全角色，以便管理应用用户的特权。 

因为该环境会维护对 Contoso 公司运行的其他应用也有用的宠物美容记录，所以会创建宠物美容应用的专用自定义安全角色。 此外，需要两组不同的访问特权。
- 宠物美容技术员可能仅需读取、更新和附加其他记录，因此他们的安全角色会有读取、写入和追加特权。 
- 宠物美容计划员可能需要宠物美容技术员的所有特权，再加上创建、追加到、删除和共享特权，因此它们的安全角色会有创建、读取、写入、追加、删除、分配、追加到和共享特权。

有关访问和范围特权的详细信息，请参阅[安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles)。

## <a name="create-a-custom-security-role"></a>创建自定义安全角色
1. 在 [!INCLUDE [powerapps](../../includes/powerapps.md)] 站点上选择“模型驱动” > “应用” > “...”> “共享链接”。
2. 在“共享此应用”对话框中，选择“创建安全角色”下的“安全设置”。
3. 在“设置”页上选择“新建”。  

4. 从安全角色设计器中选择操作（例如读取、写入或删除）和操作对应的执行范围。 执行范围决定了用户在环境层次结构中执行特定操作的深度或高度。 在“角色名称”框中，输入“宠物美容技术员”。
5. 选择“自定义实体”选项卡，然后找到需要的自定义实体。 本例使用名为“宠物”的自定义实体。 
6. 在“宠物”行中，选择下列每个特权四次，直到将其对应的组织范围选为![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)为止：读取、写入、追加
![新建安全角色](media/share-model-driven-app/custom-security-role.png)
7. 由于宠物美容应用还与帐户实体相关，请选择“核心记录”选项卡，然后在“帐户”行中选择“读取”四次，直到将组织范围选为![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)为止。 
8. 选择“保存并关闭”。 
9. 在安全角色设计器上的“角色名称”框中，输入“宠物美容计划员”。 
10. 选择“自定义实体”选项卡，然后找到“宠物”实体。 
11. 在“宠物”行中，选择下列每个特权四次，直到将其对应的组织范围选为![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)为止：创建、读取、写入、删除、追加、追加到、分配和共享
12. 由于宠物美容应用还与帐户实体相关，并且计划员需要创建并修改帐户记录，请选择“核心记录”选项卡，然后在“帐户”行选择下列每个特权四次，直到将组织范围选为![组织全局范围](media/share-model-driven-app/organizational-scope-privilege.png)为止。 
    创建、读取、写入、删除、追加、追加到、分配和共享
13. 选择“保存并关闭”。

## <a name="assign-security-roles-to-users"></a>为用户分配安全角色
安全角色通过一组访问级别和权限控制用户对数据的访问。 特定的安全角色包括访问级别和权限的组合，这种组合限制了用户对数据的查看以及与数据的交互操作。

### <a name="assign-a-security-role-to-pet-grooming-technicians"></a>为“宠物美容技术员”分配安全角色
1. 在“共享此应用”对话框中，选择“向用户分配安全角色”下的“安全用户”。
2. 在显示的列表中，选择宠物美容师。
3. 选择“管理角色”。

    ![管理角色](media/share-model-driven-app/select-users-for-security-roles.png)

4. 在“管理用户角色”对话框中选择之前创建的“宠物美容技术员”安全角色，然后选择“确定”。

### <a name="assign-a-security-role-to-pet-grooming-schedulers"></a>为“宠物美容计划员”分配安全角色
1. 在“共享此应用”对话框中，选择“向用户分配安全角色”下的“安全用户”。
2. 在显示的列表中，选择宠物美容计划员。
3. 选择“管理角色”。
4. 在“管理用户角色”对话框中选择之前创建的“宠物美容计划员”安全角色，然后选择“确定”。


## <a name="add-security-roles-to-the-app"></a>将安全角色添加到应用
下一步，需要将一个或多个安全角色分配到应用。 用户将基于分配到的安全角色对应用进行访问。
1. 在“共享此应用”对话框中，选择“将安全角色添加到应用”下的“我的应用”。
2. 在 Contoso 宠物美容应用的应用磁贴右下角选择“更多选项 (...)”，然后选择“管理角色”。

    ![管理应用角色](media/share-model-driven-app/manage-roles.png)

4. 在“角色”部分，可以选择向所有安全角色或选定角色授予应用访问权限。 选择之前创建的“宠物美容计划员”角色和“宠物美容技术员”角色。

    ![选择应用的安全角色](media/share-model-driven-app/app-security-roles.png)

5. 选择“保存”。
 
## <a name="share-the-link-to-your-app"></a>共享应用链接
1. 在“共享此应用”对话框中，复制显示在“直接与用户共享应用链接”下的 URL。
 
2. 选择“关闭”。
3. 将应用的 URL 粘贴在便于用户访问的地方，例如将 URL 发布在 SharePoint 站点上，或者通过电子邮件发送 URL。

![共享链接](media/share-model-driven-app/share-model-driven-URL.PNG)

还可以在应用设计器中的“属性”选项卡上找到应用 URL。 
    
![复制应用 URL](media/share-model-driven-app/app-designer-copy-web-url.png)

## <a name="about-predefined-security-roles"></a>关于预定义的安全角色
这些预定义的安全角色可用于 [!INCLUDE [powerapps](../../includes/powerapps.md)] 环境。


|安全角色  |*特权  |描述 |
|---------|---------|---------|
|环境创建者     |  无       | 可以创建与环境相关联的新资源，包括应用、连接、自定义 API、网关和使用 Microsoft Flow 的流。 但是，没有在环境中访问数据的任何特权。 有关详细信息，请参阅：[环境概述](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|系统管理员     |  创建、读取、写入、删除、自定义、安全角色       | 具有自定义或管理环境的完整权限，包括创建、修改和分配安全角色。 可以查看环境中的所有数据。 有关详细信息，请参阅：[自定义所需的特权](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|系统定制员     | 创建（自我）、读取（自我）、写入（自我）、删除（自我）、自定义         | 具有自定义环境的完整权限。 但是，仅可以查看他们创建的环境实体的记录。 有关详细信息，请参阅：[自定义所需的特权](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|Common Data Service 用户     |  读取、创建（自我）、写入（自我）、删除（自我）       | 可以在环境中运行应用，并对他们所拥有的记录执行常见任务。        |
|代理人     | 代表其他用户执行操作        | 允许以其他用户身份或模拟身份运行代码。  通常配合另一个安全角色使用以允许访问记录。 有关详细信息，请参阅：[模拟其他用户](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*除非另有指定，否则特权的范围为全局。

## <a name="next-steps"></a>后续步骤
[快速入门：在移动设备上运行模型驱动应用](../../user/run-app-client-model-driven.md)



