---
title: "管理环境 | Microsoft 文档"
description: "管理 PowerApps 中的环境，包括创建、重命名、删除和安全性"
services: 
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/11/2017
ms.author: jamesol
ms.openlocfilehash: 1eeb79d0c109181ae75b86a78cecdb4babe058ab
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="environments-administration-in-powerapps"></a>PowerApps 中的环境管理
在 [PowerApps 管理中心][1]内，管理已创建的环境及已将已添加到其环境管理员角色的环境。 从管理中心可执行以下管理操作：

* 创建环境。
* 重命名环境。
* 授予或撤销用户或组的环境管理员或环境创建者角色。
* 为环境预配 Common Data Service 数据库。
* 设置数据丢失防护策略。
* 设置数据库安全策略（由数据库角色设置为开放或受限）。
* Azure AD 租户全局管理员角色（包括 Office 365 全局管理员）的成员也可以管理自己已在租户中创建的所有环境，并在整个租户范围内设置策略。

## <a name="access-the-powerapps-admin-center"></a>访问 PowerApps 管理中心
若要访问 PowerApps 管理中心，请执行以下操作：

* 直接转到 [admin.powerapps.com][1]，或
* 转到 [powerapps.com][2]，然后在导航标题中选择齿轮图标。
  
    ![](./media/environment-admin/powerapps-gear-dropdown.png)

若要在 PowerApps 管理中心管理某个环境，必须拥有以下角色之一：

* 该环境的“环境管理员”角色，或
* Azure AD 或 Office 365 租户的“全局管理员”角色。

此外，还需要 PowerApps 计划 2 或 Flow 计划 2 才能访问管理中心。 有关详细信息，请参阅 [PowerApps 定价页][3]。

**重要说明**：在 PowerApps 管理中心所做的任何更改将影响 [Flow 管理中心][4]，反之亦然。

## <a name="create-an-environment"></a>创建环境
首先，单击“+ 新建环境”打开一个对话框并创建环境。

![](./media/environment-admin/new-environment-button.png)

然后输入以下信息：

| 属性 | 说明 |
| --- | --- |
| 环境名称 |输入环境的名称。 |
| 区域 |选择用于托管环境的位置。 建议使用最靠近用户的位置。 例如，如果应用用户位于伦敦，请选择“欧洲”作为位置。 如果应用用户位于纽约，请选择“美国”。有关支持的环境区域列表，请参阅[支持的区域](regions-overview.md)。 |
| 为此环境创建数据库 |选择此复选框为此环境创建 Common Data Service 数据库。 可将数据库配置为向环境中的所有用户开放，或者仅限向数据库角色开放。 有关详细信息，请参阅[配置数据库安全性](database-security.md)。 |

![](./media/environment-admin/new-environment-updated.png)

最后，选择“创建环境”。

新环境随即出现在环境表中。

> [!NOTE]
> 当你创建环境时，系统会自动将你添加到该环境的“环境管理员”角色。
> 
> 

## <a name="view-your-environments"></a>查看环境
打开管理中心时，默认会显示“环境”选项卡，其中列出了你是其环境管理员的所有环境（如下所示）：

![](./media/environment-admin/environment-list-updated.png)

如果你是 Azure AD 或 Office 365 租户的“全局管理员”角色的成员，将显示租户中用户创建的所有环境，因为你已自动成为所有这些环境的环境管理员。

## <a name="rename-your-environment"></a>重命名环境
1. 打开 [PowerApps 管理中心][1]，在列表中找到要重命名的环境，然后单击或点击它。
   
    ![](./media/environment-admin/environment-list-updated3.png)
2. 单击或点击“详细信息”。
   
    ![](./media/environment-admin/environment-rename-details-2.png)
3. 在“名称”文本框中输入新名称，然后单击“保存”。
   
    ![](./media/environment-admin/environment-rename-2.png)

## <a name="delete-your-environment"></a>删除环境
1. 在 [PowerApps 管理中心][1]单击或点击要删除的环境。
   
    ![](./media/environment-admin/environment-list-updated3.png)
2. 单击或点击“详细信息”。
   
    ![](./media/environment-admin/environment-rename-details-2.png)
3. 单击或点击“删除环境”以删除该环境。
   
    ![](./media/environment-admin/delete-environment-2.png)

## <a name="create-a-common-data-service-database-for-an-environment"></a>为环境创建 Common Data Service 数据库
如果某个环境没有数据库，环境管理员可在 [PowerApps 管理中心][1]执行以下步骤创建一个数据库。 只有拥有 PowerApps 计划 2 许可证的用户才能创建 Common Data Service 数据库。

1. 在环境表中选择一个环境。
   
    ![](./media/environment-admin/choose-environment-updated.png)
2. 选择“数据库”选项卡。
3. 选择“创建数据库”。
   
    ![](./media/environment-admin/database-tab.png)
   
    预配该数据库后，将显示以下确认消息：
   
    ![](./media/environment-admin/database-tab-success.png)

创建数据库后，请选择安全模型。 有关详细信息，请参阅[配置数据库安全性](database-security.md)。

## <a name="manage-security-for-your-environments"></a>管理环境的安全性
### <a name="environment-permissions"></a>环境权限
在环境中，Azure AD 租户中的所有用户都是该环境的用户。 但是，若要让这些用户扮演更高特权的角色，需要将他们添加到特定的环境角色。 环境中内置两个角色，在环境中拥有相应的权限：

* “环境管理员”角色可以执行所有环境管理操作，包括：
  
  o    授予或撤销用户或组的“环境管理员”或“环境创建者”角色。
  
  o    为环境预配 Common Data Service 数据库。
  
  o    查看和管理环境中的所有资源。
  
  o    设置数据丢失防护策略。 有关详细信息，请参阅[数据丢失防护策略](prevent-data-loss.md)。
* **环境创建者**角色可以在环境中创建资源，包括应用、连接、自定义连接器、网关和 Microsoft Flow 流。 环境创建者还可将他们在环境中构建的应用分发到组织中的其他用户。 他们可与组织中的单个用户、安全组或所有用户共享应用。 有关详细信息，请参阅[在 PowerApps 中共享应用](share-app.md)。

若要将用户或安全组分配到某个环境角色，环境管理员可在 [PowerApps 管理中心][1]执行以下步骤：

1. 在环境表中选择该环境。
   
    ![](./media/environment-admin/choose-environment-updated.png)
2. 在“安全”选项卡中选择“环境角色”。
3. 选择“环境管理员”或“环境创建者”角色。
   
    ![](./media/environment-admin/choose-environment-role.png)
4. 指定 Azure Active Directory 中一个或多个用户或安全组的名称，或指定要添加整个组织。
   
    ![](./media/environment-admin/enter-name.png)
5. 选择“保存”更新环境角色分配。

若要删除某个用户或组的所有权限，请单击或点击该用户或组对应的“x”图标。

> [!NOTE]
> 分配到这些环境角色的用户或组并不会自动获得对环境内数据库（若有）的访问权限，必须由数据库所有者单独授予。 有关详细信息，请参阅[配置数据库安全性](database-security.md)。  
> 
> 

### <a name="database-security"></a>数据库安全性
创建和修改数据库架构以及连接到在环境中预配的某个数据库内存储的数据的能力，由该数据库的用户角色和权限集控制。 可通过“安全”选项卡的“用户角色”和“权限集”部分管理环境数据库的用户角色和权限集。有关详细信息，请参阅[配置数据库安全性](database-security.md)。

![](./media/environment-admin/database-security.png)

> [!NOTE]
> 环境管理员无权创建和管理环境数据库的用户角色和权限集。 这种超级权限仅限于“数据库所有者”用户角色的成员。  
> 
> 

## <a name="data-policies"></a>数据策略
组织的数据必须受到保护，防止与不应有权访问这些数据的受众共享。 若要保护这些数据，可以创建并实施策略来定义可共享的特定于使用者服务和连接器的业务数据。 用于定义如何共享数据的策略称为数据丢失防护 (DLP) 策略。 可以通过 [PowerApps 管理中心][1]的“数据策略”部分管理环境的 DLP 策略。  有关详细信息，请参阅[数据丢失防护策略](prevent-data-loss.md)。

![](./media/environment-admin/data-policies.png)

## <a name="frequently-asked-questions"></a>常见问题
### <a name="how-many-environments-can-i-create"></a>可以创建多少个环境？
每个用户最多可以创建两个环境。

### <a name="how-many-databases-can-i-provision"></a>可以预配多少个数据库？
每个用户最多可以预配两个数据库。

### <a name="can-i-rename-an-environment"></a>是否可以重命名环境？
可以，可在 PowerApps 管理中心找到此功能。 有关详细信息，请参阅[环境管理](environments-administration.md#rename-your-environment)。

### <a name="can-i-delete-an-environment"></a>是否可以删除环境？
可以，可在 PowerApps 管理中心找到此功能。 有关详细信息，请参阅[环境管理](environments-administration.md#delete-your-environment)。

### <a name="as-an-environment-admin-can-i-view-and-manage-all-resources-apps-flows-apis-etc-for-an-environment"></a>环境管理员是否可以查看和管理环境的所有资源（应用、流、API 等等）？
可以，可在 PowerApps 管理中心找到查看环境的应用和流的功能。 有关详细信息，请参阅[查看应用](admin-view-apps.md)。

### <a name="which-license-includes-common-data-service"></a>哪个许可证包含 Common Data Service？
PowerApps 计划 2。  有关包含此许可证的所有计划的详细信息，请参阅 [PowerApps 定价页][3]。

### <a name="can-the-common-data-service-be-used-outside-of-an-environment"></a>是否可以在环境外部使用 Common Data Service？
不。 Common Data Service 需要一个环境。

<!--Reference links in article-->
[1]: https://admin.powerapps.com
[2]: https://web.powerapps.com
[3]: https://powerapps.microsoft.com/pricing/
[4]: https://admin.flow.microsoft.com
