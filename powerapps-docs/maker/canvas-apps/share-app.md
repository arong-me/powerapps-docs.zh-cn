---
title: 共享应用 | Microsoft 文档
description: 通过授予其他用户运行或修改应用的权限来共享应用
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 07/11/2018
ms.author: anneta
ms.openlocfilehash: 9c4bdc6e56f84b6724fcbe44cfe1f3e4c065edb3
ms.sourcegitcommit: 0e9af8cace2bdc04750f4c5a70a3c4af8e3d2292
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2018
ms.locfileid: "39195303"
---
# <a name="share-an-app-in-powerapps"></a>在 PowerApps 中共享应用

生成满足业务需求的应用后，指定组织中哪些用户可以运行应用，哪些用户可以修改并重新共享应用。 按姓名指定每个用户或在 Azure Active Directory 中指定安全组。 如果每个人都可利用你的应用，则指定整个组织可以运行应用。

> [!IMPORTANT]
> 若要使共享应用按预期方式运行，还必须管理应用所基于的数据源或源的权限，例如 [Common Data Service for Apps](#common-data-service-for-apps) 或 [Excel](share-app-data.md)。 可能还需要共享应用依赖的[其他资源](share-app-resources.md)，例如流、网关或连接。

## <a name="prerequisites"></a>先决条件

共享应用前，必须将其保存至云（而非本地），然后发布应用。

- 为应用提供有意义的名称和明确说明，以便人们了解应用的功能并且可在列表中轻松找到该应用。 在 PowerApps Studio 中的“文件”菜单上，选择“应用设置”，指定名称，然后键入或粘贴说明。

- 无论何时进行更改，如果想要其他人看到这些更改，必须保存并重新发布应用。

## <a name="share-an-app"></a>共享应用

1. [登录](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) PowerApps，然后选择左边缘附近的“应用”。

    ![显示应用列表](./media/share-app/file-apps.png)

1. 选择要共享应用的省略号 (...)，再选择“共享”。

    ![打开共享屏幕](./media/share-app/ellipsis-share.png)

1. 指定要与 Azure Active Directory 中的哪些用户或安全组共享应用。

    > [!NOTE]
    > 无法与组织中的通讯组或组织外的任何用户或组共享应用。

    ![指定用户](./media/share-app/share-list.png)

    你也可以与整个组织共享应用，这样他们就可以运行此应用，但是不能修改或共享应用。

1. （可选）若要帮助用户查找应用，选择向其发送电子邮件邀请的复选框。

    邀请中包含一个链接，用户选择此链接可运行应用。

    - 如果用户在台式计算机上选择该链接，应用将在 [Dynamics 365](http://home.dynamics.com) 中打开。
    - 如果用户在移动设备上选择该链接，应用将在 PowerApps Mobile 中打开。

    如果授予用户修改应用的权限，该邮件还包含一个单独的链接，通过该链接可在 PowerApps Studio 中打开应用进行编辑。

    无论你是否发送邀请，用户均可以从 [Dynamics 365](http://home.dynamics.com) 上的 AppSource 中运行应用。 具有“可以编辑”权限的用户也可以在 [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 中编辑应用。

1. 指定每个用户或安全组的权限，然后选择“保存”。

    - 可以使用：用户可以运行应用，但无法共享应用。
    - 可以编辑：用户可以运行、修改应用，并可与其他用户共享自定义版本。

        ![指定权限](./media/share-app/edit-use.png)

    若要更改用户或安全组的权限，请选择用户或组已有权限旁边的向下箭头，然后指定其他权限。

    若要删除某个用户或组的所有权限，请选择该用户或组对应的“x”图标。

## <a name="security-group-considerations"></a>安全组注意事项

- 如果与某个安全组共享应用，则该组的现有成员和加入该组的任何人都将具有你为该组所指定的权限。 退出该组的任何人将失去该权限，除非他们属于有访问权限的其他组或你为他们提供个人身份的权限。
- 每个安全组成员都具有与整个组相同的应用权限。 但是，可以为该组的一个或多个成员指定更高的权限，以允许他们具有更高的访问级别。 例如，你可以给安全组 A“可以使用”的权限，但是同时可以给该组中的用户 B“可以编辑”的权限。 安全组中的每个成员都可以运行该应用，但是只有用户 B 可以编辑它。 如果你给安全组 A“可以编辑”权限并给用户 B“可以使用”权限，则该用户依然能编辑此应用。

## <a name="manage-entity-permissions"></a>管理实体权限

### <a name="common-data-service-for-apps"></a>Common Data Service for Apps

如果创建基于 Common Data Service for Apps 的应用，还必须确保运行应用的用户具有应用所依赖实体的相应权限。 具体而言，这些用户必须属于可执行任务（如创建、读取、写入和/或删除相关记录）的安全角色。 如果你具有此环境中数据库的系统管理员或系统定制员权限，可创建自定义角色，然后向其添加用户。

#### <a name="create-a-security-role"></a>创建安全角色

1. [登录 PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，并确保你与想要共享的应用位于相同环境中。

1. 选择右上角的齿轮图标，然后选择“高级自定义”。

    ![打开“高级自定义”窗格](media/share-app/advanced-customizations.png)

1. 选择“安全角色”链接。

    ![打开安全角色](media/share-app/security-roles.png)

1. 在“全部角色”下，选择“新建”，然后为要创建的角色键入或粘贴名称。

    ![创建安全角色](media/share-app/new-role.png)

1. 选择一个或多个选项卡，查找应用使用的实体，并选择想要授予安全角色的权限。

    例如，此图显示“帐户”实体中可创建、读取、写入和删除记录的安全角色，该角色在“核心记录”选项卡上显示。

    ![指定权限](media/share-app/grant-access.png)

1. 选择“保存并关闭”。

#### <a name="assign-a-user-to-a-role"></a>将用户分配给角色

1. 如上一过程所述，打开“高级自定义”窗格，然后选择“用户”链接。

    ![用户链接](media/share-app/open-users.png)

1. 在右上角中键入或粘贴想要分配给角色的用户的姓名，然后选择搜索图标。

    ![搜索用户](media/share-app/search-users.png)

1. 在搜索结果中，指向所需的结果，然后选择显示的复选框。

1. 在顶部横幅中，选择“管理角色”。

1. 在出现的对话框中，选择“Common Data Service 用户”对应的复选框和用户所需的应用角色，然后选择“确定”。

    ![将用户分配给角色](media/share-app/assign-users.png)

### <a name="common-data-service-previous-version"></a>Common Data Service（上一版本）

在共享基于较旧版本的 Common Data Service 的应用时，必须单独对该服务共享运行时权限。 如果缺少执行此操作的权限，请查看环境管理。