---
title: 共享画布应用 | Microsoft Docs
description: 通过授予其他用户运行或修改应用的权限来共享画布应用
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 11/28/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 34cf740bb029440480618a180ac45bc094c061d5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61539814"
---
# <a name="share-a-canvas-app-in-powerapps"></a>在 PowerApps 中共享画布应用

生成满足业务需求的画布应用后，指定组织中哪些用户可以运行应用，哪些用户可以修改并重新共享应用。 按姓名指定每个用户或在 Azure Active Directory 中指定安全组。 如果每个人都可利用你的应用，则指定整个组织可以运行应用。

> [!IMPORTANT]
> 若要正常使用共享应用，还必须管理权限的数据源或源应用程序所基于的如[Common Data Service](#common-data-service)或[Excel](share-app-data.md)。 可能还需要共享应用依赖的[其他资源](share-app-resources.md)，例如流、网关或连接。

## <a name="prerequisites"></a>先决条件

共享应用前，必须将其保存至云（而非本地），然后发布应用。

- 为应用提供有意义的名称和明确说明，以便人们了解应用的功能并且可在列表中轻松找到该应用。 在 PowerApps Studio 中的“文件”菜单上，选择“应用设置”，指定名称，然后键入或粘贴说明。

- 无论何时进行更改，如果想要其他人看到这些更改，必须保存并重新发布应用。

## <a name="share-an-app"></a>共享应用

1. [登录](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) PowerApps，然后选择左边缘附近的“应用”。

    ![显示应用列表](./media/share-app/file-apps.png)

1. 选择你想要通过选择其图标共享的应用。

    ![选择一个应用](./media/share-app/select-app.png)

1. 在横幅中，选择**共享**。

    ![打开共享屏幕](./media/share-app/banner-share.png)

1. 按名称或别名的用户或安全组中指定你希望与其共享应用的 Azure Active Directory。

    - 若要允许您运行该应用程序 （但不是修改或共享） 的整个组织中，键入**每个人都**共享面板中。
    - 可以使用的别名、 友好名称或这些组合列表共享应用 (例如， **Jane Doe &lt; jane.doe@contoso.com>**) 如果项由分号分隔。 如果有多个一个人拥有相同名称但不同的别名，找到的第一个人就会添加到列表。 如果名称或别名已具有的权限或无法解析，将出现一个工具提示。 
    
    ![指定用户和共同所有者](./media/share-app/share-everyone.png)

    > [!NOTE]
    > 不能共享应用与组织中分发组或与用户或组不属于组织。

1. 如果你想要允许那些要与之共享应用程序以编辑和共享 （除了运行它），选择**共同所有者**复选框。

    不能授予**共有者**权限到安全组，如果您[创建的解决方案中使用此应用](add-app-solution.md)。
    
    > [!NOTE]
    > 无论何种权限，没有两名人员可以在同一时间编辑应用。 如果一个人打开应用进行编辑，其他人可以运行它，但无法编辑它。

1. 如果您的应用程序连接到为其用户需要访问权限的数据时，指定它们。

    例如，您的应用程序可能会连接到 Common Data Service 数据库中的实体。 当您共享此类应用时，共享面板会提示您管理的该实体的安全。

    ![设置权限](./media/share-app/set-permissions.png)

    有关管理安全性的实体的详细信息，请参阅[管理实体权限](share-app.md#manage-entity-permissions)本主题中更高版本。

1. 如果你想要帮助用户查找您的应用程序，选择**发送给新用户的电子邮件邀请**复选框。

1. 在共享面板的底部，选择**共享**。

    与之共享应用程序的每个人都可以在运行该在 PowerApps Mobile 中移动设备上或在 AppSource [Dynamics 365](https://home.dynamics.com)在浏览器中。 共同所有者可以编辑和共享中的应用程序[PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    如果发送的电子邮件邀请，与之共享应用程序的每个人都可以选择的链接，邀请中运行。

    - 如果用户选择在移动设备上的链接，在 PowerApps Mobile 中打开应用。
    - 如果用户选择的桌面计算机上的链接，在浏览器中打开应用。

    接收邀请发件人的共同所有者获取另一个在 PowerApps Studio 中打开用于编辑应用的链接。

可以通过选择其姓名，然后执行下列步骤之一来更改用户或安全组的权限：

- 若要允许运行应用，但不是能再编辑或共享它的共同所有者，请清除**共同所有者**复选框。
- 若要停止与该用户或组共享应用程序，请选择删除 (x) 图标。

## <a name="security-group-considerations"></a>安全组注意事项

- 如果与某个安全组共享应用，则该组的现有成员和加入该组的任何人都将具有你为该组所指定的权限。 退出该组的任何人将失去该权限，除非他们属于有访问权限的其他组或你为他们提供个人身份的权限。
- 每个安全组成员都具有与整个组相同的应用权限。 但是，可以为该组的一个或多个成员指定更高的权限，以允许他们具有更高的访问级别。 例如，可授予安全组的权限，才能运行应用，但你还可以允许用户 B，而属于该组，后者**共同所有者**权限。 安全组中的每个成员都可以运行该应用，但是只有用户 B 可以编辑它。 如果给安全组 A**共同所有者**权限和用户 B 的权限来运行应用程序中，该用户仍可以编辑此应用。

## <a name="manage-entity-permissions"></a>管理实体权限

### <a name="common-data-service"></a>Common Data Service

如果创建基于 Common Data Service 的应用，还必须确保与你共享应用程序的用户具有适当的权限或多个应用程序所依赖的实体。 具体而言，这些用户必须属于可执行任务，例如创建、 读取、 写入和删除相关记录的安全角色。 在许多情况下，你将想要使用的用户运行应用所需的确切权限创建一个或多个自定义安全角色。 然后可以根据每个用户分配角色。

> [!NOTE]
> 在撰写本文时，可以将安全角色分配给单个用户而非安全组中。

#### <a name="prerequisite"></a>先决条件

若要执行以下两个过程，必须拥有**系统管理员**Common Data Service 数据库的权限。

#### <a name="create-a-security-role"></a>创建安全角色

1. 在共享的面板中，选择**设置权限**下**数据权限**，然后选择**安全角色**链接。

    ![打开安全角色](media/share-app/security-roles.png)

1. 在“全部角色”下，选择“新建”，然后为要创建的角色键入或粘贴名称。

    ![创建安全角色](media/share-app/new-role.png)

1. 选择一个或多个选项卡，查找应用使用的实体，并选择想要授予安全角色的权限。

    例如，此图显示了该**核心记录**选项卡包含**帐户**实体，并向其分配此安全角色的用户可以创建、 读取、 写入和删除该实体中的记录.

    ![指定权限](media/share-app/grant-access.png)

1. 选择“保存并关闭”。

#### <a name="assign-a-user-to-a-role"></a>将用户分配给角色

1. 在共享的面板中，选择**设置权限**下**数据权限**，然后选择**用户**链接。

    ![用户链接](media/share-app/open-users.png)

1. 在右上角中键入或粘贴想要分配给角色的用户的姓名，然后选择搜索图标。

    ![搜索用户](media/share-app/search-users.png)

1. 在搜索结果中，指向所需的结果，然后选择显示的复选框。

1. 在顶部横幅中，选择“管理角色”。

1. 在出现的对话框中，选择对应的复选框**Common Data Service 用户**和角色，而且用户必须为你的应用，然后选择**确定。**

    ![将用户分配给角色](media/share-app/assign-users.png)

### <a name="common-data-service-previous-version"></a>Common Data Service（上一版本）

共享的应用程序基于 Common Data Service 的较旧版本时，必须单独共享对该服务的运行时权限。 如果你没有权限来执行此操作，请参阅您的环境的管理员联系。
