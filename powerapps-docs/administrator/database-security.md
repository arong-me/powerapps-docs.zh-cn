---
title: 配置环境安全设置 | Microsoft Docs
description: 本主题介绍如何配置环境安全设置。
author: manasmams
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: 620152a684e5bf0399bd938172f328892b137325
ms.sourcegitcommit: 44ecb3ace4c865bc592dfb7f0b5fffa289d3b035
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2018
ms.locfileid: "36306111"
---
# <a name="configure-environment-security"></a>配置环境安全设置
Common Data Service (CDS) for Apps 使用基于角色的安全模型来帮助保护对数据库的访问。 本主题介绍了如何创建保护应用所必需的安全项目。 用户角色可控制对数据的运行时访问，不同于管理环境管理员和环境创建者的环境角色。 有关环境的概述，请参阅[环境概述](environments-overview.md)。

## <a name="assign-security-roles-to-users"></a>为用户分配安全角色
安全角色通过一组访问级别和权限控制用户对数据的访问。 特定的安全角色包括访问级别和权限的组合，这种组合限制了用户对数据的查看以及与数据的交互操作。

若要将用户或安全组分配到某个环境角色，环境管理员可在 [PowerApps 管理中心][1]执行以下步骤：

1. 在环境表中选择该环境。

    ![](./media/environment-admin/environment-list-new.png)

2. 选择“安全性”选项卡。

3. 通过选择“查看环境中的用户列表”，查看环境中是否已存在用户。
    
    ![](./media/database-security/security-viewuser.png)

4. 如果没有用户，可从 PowerApps 管理中心进行添加。添加方式是在组织中添加用户的电子邮件地址，然后选择“添加用户”。

    ![](./media/database-security/security-adduser.png)

    请稍等几分钟，然后检查该用户是否在环境内的用户列表中可用。
  
5. 从环境的用户列表中选择用户。

    ![](./media/environment-admin/D365-Select-User.png)

6. 向用户分配角色。

    ![](./media/environment-admin/D365-Assign-Role.png)

    > [!NOTE]
    > 目前，只能向用户分配角色。 向安全组分配角色是我们积压的工作。

7. 选择“确定”更新环境角色分配。

## <a name="predefined-security-roles"></a>预定义的安全角色
PowerApps 环境包括预定义的安全角色，它反映访问级别定义为匹配安全最佳做法目标的常见用户任务，该目标为提供对使用应用所需最小业务数据量的访问。

|安全角色  |*数据库权限  |描述 |
|---------|---------|---------|
|系统管理员     |  创建、读取、写入、删除、自定义、安全角色       | 具有自定义或管理环境的完整权限，包括创建、修改和分配安全角色。 可以查看环境中的所有数据。 有关详细信息，请参阅：[自定义所需的特权](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|系统定制员     | 创建（自我）、读取（自我）、写入（自我）、删除（自我）、自定义         | 具有自定义环境的完整权限。 但是，仅可以查看他们创建的环境实体的记录。 详细信息：[自定义项所需权限](https://docs.microsoft.com/dynamics365/customer-engagement/customize/privileges-required-customization)        |
|环境创建者     |  无       | 可以创建与环境相关联的新资源，包括应用、连接、自定义 API、网关和使用 Microsoft Flow 的流。 但是，没有在环境中访问数据的任何特权。 有关详细信息：[环境概述](https://powerapps.microsoft.com/blog/powerapps-environments/)        |
|Common Data Service 用户     |  读取、创建（自我）、写入（自我）、删除（自我）       | 可在环境内运行应用并执行常规任务（例如，读取所有[应用程序和 Crm 常用实体](https://github.com/Microsoft/CDM/tree/master/schemaDocuments#click-this-image-to-explore-the-cdm-entities-using-the-entity-navigator)），但会从这些实体中创建、写入和删除自拥有的记录（帐户、联系人和连接除外，在这些项中，无论所有者是谁，它都可以写入到所有记录）。          |
|代理人     | 代表其他用户执行操作        | 允许以其他用户身份或模拟身份运行代码。  通常配合另一个安全角色使用以允许访问记录。 有关详细信息，请参阅：[模拟其他用户](https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/impersonate-another-user)        |

*除非另有指定，否则特权是全局范围。

- 环境创建者角色不仅可以在环境中创建资源，还可以将环境中生成的应用分配给组织中的其他用户。 可以与个人用户共享应用。 有关详细信息，请参阅[在 PowerApps 中共享应用](../maker/canvas-apps/share-app.md)。

- 应该向制作连接到数据库和需要创建或更新实体和安全角色的用户和环境创建者分配系统自定义角色，因为环境创建者角色没有数据库特权。

## <a name="create-or-configure-a-custom-security-role"></a>创建或配置自定义安全角色
如果你的应用基于自定义实体，那么必须在用户开始工作前显式指定特权。 若要执行此操作，可以选择执行下列操作之一。
- 展开现有预定义安全角色，确保其包括对基于自定义实体的记录的特权。
- 创建自定义安全角色，以便管理应用用户的特权。

环境可能维护由多个应用使用的记录，你可能需要多个安全角色访问具有不同特权的数据。 例如
- 某些用户（类型 A）可能仅需要读取、更新和附加其他记录，因此它们的安全角色会有读取、编写和附加特权。
- 其他用户可能需要类型 A 用户的所有权限，再加上创建、追加到、删除和共享特权，因此它们的安全角色会有创建、读取、编写、追加、删除、分配、追加到和共享特权。

有关访问和作用域特权的详细信息，请参阅[安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges#security-roles)。

1. 在 [PowerApps 管理中心][1]中，选择想要更新安全角色的环境。

    ![](./media/environment-admin/choose-environment-updated.png)

2. 单击“详细信息”选项卡中的链接管理 Dynamics 365 管理中心的环境。

3. 选择实例（环境同名），然后单击“打开”

    ![](./media/database-security/glados-instance-list.png)

4. 在标题中，单击“设置”并选择“安全”

    ![](./media/database-security/dyn365-settings-security.png)

5. 选择“安全角色”

    ![](./media/database-security/dyn365-securityroles.png)

6. 单击“新建”

7. 从安全角色设计器选择操作（例如读取、编写或删除）和执行该操作的作用域。

8. 选择选项卡并搜索实体（例如“自定义视图”选项卡）以便在自定义实体上设置特权。

9. 选择“读取、编写、追加”特权

10. 选择“保存并关闭”。


<!--Reference links in article-->
[1]: https://admin.powerapps.com
