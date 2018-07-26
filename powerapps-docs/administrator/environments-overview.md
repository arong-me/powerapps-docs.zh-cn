---
title: 环境概述 | Microsoft Docs
description: 了解 PowerApps 中的环境及其用法
author: manasmams
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: b38f0d1b029708e8130363d54ccc1354084b0ae4
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218156"
---
# <a name="environments-overview"></a>环境概述
环境是用来存储、管理和共享组织的业务数据、应用和流的空间。 还可以将环境用作分隔具有不同角色、安全要求或目标受众的应用的容器。 环境的使用方式视组织和要生成的应用而定。 例如：

* 可以选择仅在一个环境中生成应用。
* 可以创建不同的环境，对测试版和生产版应用进行分组。
* 可以创建不同的环境，对应于公司中的特定团队或部门，每个环境包含各个受众的相关数据和应用。
* 还可以创建不同的环境，对应于公司的其他全球分支机构。  

## <a name="environment-scope"></a>环境范围
每个环境都是在 Azure AD 租户下创建的，只有相应租户中的用户才能访问环境中的资源。 环境还会与地理位置（如美国）绑定。 在环境中创建应用后，此应用只会路由到位于该地理位置的数据中心。 在此环境中创建的所有项（包括连接、网关、使用 Microsoft Flow 的流等）也会与此环境的地理位置绑定。

每个环境可以有 0 或 1 个 Common Data Service 数据库，从而为应用提供存储空间。 能否为环境创建数据库取决于你购买的 PowerApps 许可证以及你在相应环境内拥有的权限。 有关详细信息，请参阅[定价信息](pricing-billing-skus.md)。

在环境中创建应用后，此应用只能连接也在同一环境中部署的数据源，包括连接、网关、流和 Common Data Service 数据库。  例如，假设在一个应用场景中，你创建了两个名为“Test”和“Dev”的环境，并在每个环境中创建了 Common Data Service 数据库。 如果你在“Test”环境中创建应用，那么此应用只能连接“Test”数据库，无法连接“Dev”数据库。

此外，还可以在两个环境之间移动资源。 有关详细信息，请参阅[迁移资源](environment-and-tenant-migration.md)。

![](./media/environments-overview/Environments.png)

## <a name="environment-permissions"></a>环境权限
环境中内置两个角色，在环境中拥有相应的权限：

* 环境管理员角色可以执行所有环境管理操作，包括以下操作：

  * 授予或撤销用户或组的“环境管理员”或“环境创建者”角色

  * 为环境预配 Common Data Service 数据库

  * 查看和管理在环境中创建的所有资源

  * 设置数据丢失防护策略。 有关详细信息，请参阅[数据丢失防护策略](prevent-data-loss.md)。

    在环境中创建数据库后，可以使用系统管理员角色，而不是环境管理员角色。

* 环境创建者角色角色可以在环境中创建资源，包括应用、连接、自定义连接器、网关和 Microsoft Flow 流。

环境创建者还可以与个人用户共享自己在环境中生成的应用，从而向组织中的其他用户分发此应用，或向安全组或组织中的所有用户分发此应用。 有关详细信息，请参阅[在 PowerApps 中共享应用](../maker/canvas-apps/share-app.md)。

分配到这些环境角色的用户或组并不会自动获得对环境内数据库（若有）的访问权限，必须由数据库所有者单独授予。 有关详细信息，请参阅[配置数据库安全性](database-security.md)。

环境管理员可以在 [PowerApps 管理中心][1]向用户或安全组分配这两个角色中的任意一个。 有关详细信息，请参阅[管理 PowerApps 中的环境](environments-administration.md)。

![](./media/environments-overview/EnvironmentRoles.png)

## <a name="the-default-environment"></a>默认环境
PowerApps 自动为每个租户创建一个默认环境，并由相应租户中的所有用户共享。 只要新用户注册 PowerApps，就会自动获得默认环境的创建者角色。 默认环境在离 AAD 租户的默认区域最近的区域创建。

> [!NOTE]
> 任何用户都不会自动获得默认环境的环境管理员角色。 有关详细信息，请参阅[管理 PowerApps 中的环境](environments-administration.md)。
>
>

默认环境的命名方式如下：“{Azure AD 租户名称} (默认)”

![](./media/environments-overview/DefaultEnvironment.png)

## <a name="production-and-trial-environments"></a>生产和试用环境
你可以创建不同的环境用于不同的用途。 试用环境用于借助 Common Data Service 体验尝试环境和数据库。 它将在某个时间段后过期。 有关详细信息，请参阅[管理 PowerApps 中的环境](environments-administration.md)。

## <a name="choosing-an-environment"></a>选择环境
随着环境的引入，访问 [https://web.powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 时现在将获得全新的体验。  站点中可见的应用、连接和其他项现在会根据当前选定的环境进行筛选。  当前环境在标头右侧边缘附近的环境选取器中指定。 若要选择其他环境，请单击或点击选取器，查看可用环境列表。 单击或点击要进入的环境。

当你满足下列条件之一时，选取器中会显示环境：

* 你是相应环境的环境管理员角色的成员。
* 你是相应环境的环境创建者角色的成员。
* 你不是相应环境的环境管理员或环境创建者，但你拥有对相应环境中至少一个应用的“参与者”访问权限。 有关详细信息，请参阅[共享应用](../maker/canvas-apps/share-app.md)。 在这种情况下，将无法在此环境中创建应用。 只能修改已与你共享的现有应用。

![](./media/environments-overview/EnvironmentPicker.png)

## <a name="creating-an-environment"></a>创建环境
### <a name="who-can-create-environments"></a>谁能创建环境？
你的许可证决定了你能否创建环境。

| 许可证 | 允许创建环境 |
| --- | --- |
| PowerApps P2 |√（两个生产环境和两个试用环境）|
| PowerApps P2 试用版 |√（两个试用环境）|
| PowerApps P1 |x |
| PowerApps P1 试用版 |x |
| Dynamics 365 计划 |x |
| Office 365 计划 |x |
| Dynamics 365 应用和团队计划 |x |


### <a name="where-can-environments-be-created"></a>在哪里可以创建环境？
可以通过 [PowerApps.com][2] 和 [PowerApps 管理中心][1]新建环境。 创建环境后，你会自动获得该环境的环境管理员角色。 作为环境管理员或环境创建者角色成员可以加入无限多个环境。 有关环境的详细信息，请参阅[管理 PowerApps 中的环境](environments-administration.md)。 有关如何创建环境的说明，请参阅[创建环境](create-environment.md)。

![](./media/environments-overview/CreateEnvironmentDialog-New.png)


## <a name="managing-environments-for-your-organization"></a>为组织管理环境
在 PowerApps 管理中心，可以管理所有已创建或已添加环境管理员角色的环境。 在管理中心内，可以执行所有环境管理操作，包括以下操作：

* 授予或撤销用户或组的环境管理员或环境创建者角色。  有关详细信息，请参阅[管理 PowerApps 中的环境](environments-administration.md)。
* 为环境预配 Common Data Service 数据库。 有关详细信息，请参阅[创建 Common Data Service 数据库](create-database.md)。
* 设置数据丢失防护策略。 有关详细信息，请参阅[数据丢失防护策略](prevent-data-loss.md)。
* 设置数据库安全策略（由数据库角色设置为开放或受限）。 有关详细信息，请参阅[配置数据库安全性](database-security.md)。
* Azure AD 租户全局管理员角色（包括 Office 365 全局管理员）的成员也可以在 PowerApps 管理中心内管理自己已在租户中创建的所有环境，并在整个租户范围内设置策略。

<!--Reference links in article-->
[1]: https://admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://aka.ms/cdspreviewtoga
