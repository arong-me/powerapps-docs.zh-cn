---
title: 管理 PowerApps 中的现有门户 |Microsoft Docs
description: 在 PowerApps 中管理门户的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f21671368bfdaf9623a294c86b113b6b62f028e7
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976429"
---
# <a name="manage-existing-portals-in-powerapps"></a>管理 PowerApps 中的现有门户

创建门户后，它将显示在 PowerApps 主页的 "**最近使用的应用**" 部分下。

> [!div class=mx-imgBorder]
> ![最近](media/recent-apps.png "")使用的应用应用  

若要管理应用，请为门户选择 "**更多命令**（ **...** ）"，然后从上下文菜单中选择 "操作"。

> [!div class=mx-imgBorder]
> ![门户应用选项](media/portal-app-options.png "门户应用选项")  

## <a name="edit"></a>编辑

打开[PowerApps 门户 Studio](portal-designer-anatomy.md)以编辑门户的内容和组件。  

> [!div class=mx-imgBorder]
> ![门户 maker](media/portal-maker.png "门户 maker")  

## <a name="browse"></a>浏览

打开门户以浏览网站。 这可以帮助你查看门户，因为它会对客户显示。

> [!div class=mx-imgBorder]
> ![门户网站](media/portal-website.png "门户网站")  

或者，还可以通过选择[PowerApps Portal Studio](portal-designer-anatomy.md)中的 "浏览"**网站**来浏览网站，以便查看对网站所做的更改。 网站将在新选项卡中打开，其中包含网站的 URL。

## <a name="share"></a>共享

与内部或外部用户共享你的门户。 按照**共享此门户**窗格中所述的步骤操作。

> [!div class=mx-imgBorder]
> ![共享门户](media/share-portal.png "共享门户")  

### <a name="share-with-internal-users"></a>与内部用户共享

要与内部用户共享门户，必须首先创建安全角色，然后将用户分配到安全角色，以便他们能够使用门户。

> [!NOTE]
> 作为 Common Data Service 中的用户，如果你没有门户实体的适当权限，你可能会看到一些错误，如 "你没有权限查看此环境中的解决方案。" 或 "你没有访问权限在此环境中查看网站"。 建议你处于相应 Common Data Service 数据库中的系统管理员安全角色。

#### <a name="step-1-create-a-security-role"></a>步骤1：创建安全角色

1.  在 "**共享此门户**" 窗格的 "**创建安全角色**" 下，选择 "**安全角色**"。 将显示所有已配置安全角色的列表。

2.  在操作工具栏上，选择 "**新建**"。

3.  在 "**新建安全角色**" 窗口中，输入角色名称。

4.  设置门户中使用的所有实体的权限。

5.  完成配置安全角色后，请在工具栏上选择 "**保存并关闭**"。

有关安全角色和权限的信息，请参阅[安全角色和特权](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges)。  

#### <a name="step-2-assign-users-to-the-security-role"></a>步骤2：将用户分配到安全角色

1.  在 "**共享此门户**" 窗格的 "**将用户分配到安全角色**" 下，选择 "**用户**"。 将显示所有用户的列表。

2.  选择要为其分配安全角色的用户。

3.  选择“管理角色”。

    > [!NOTE]
    > 如果在命令栏上看不到 "**管理角色**" 按钮，则必须通过在 URL 中将 forceUCI 设置为0来更改客户端。 例如， https://&lt;org\_url&gt;/main.aspx？ pagetype = entitylist & etn = systemuser & forceUCI = 0

4.  在 "**管理用户角色**" 对话框中，选择之前创建的安全角色，然后选择 **"确定"** 。

### <a name="share-with-external-users"></a>与外部用户共享

门户应以匿名方式工作，并且可供外部用户访问。 如果你想要尝试高级功能来管理外部用户的角色和权限，请参阅[配置用于门户的联系人](https://docs.microsoft.com/dynamics365/customer-engagement/portals/configure-contacts)、[邀请联系人到](https://docs.microsoft.com/dynamics365/customer-engagement/portals/invite-contacts)门户、[创建门户 web 角色](https://docs.microsoft.com/dynamics365/customer-engagement/portals/create-web-roles)、[分配实体权限](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions).  

## <a name="settings"></a>设置

显示门户设置，并允许您更改门户的名称。 你还可以执行高级操作，例如通过 PowerApps 门户管理中心和使用站点设置来管理门户。 设置提供指向 PowerApps 门户管理中心和站点设置的链接。 详细信息：[高级门户管理](admin/admin-overview.md)和[配置站点设置](configure/configure-site-settings.md)。  

> [!div class=mx-imgBorder]
> ![门户网站设置](media/portal-settings.png "门户设置")  

## <a name="delete"></a>Delete

删除门户和托管资源。 删除门户时，其 URL 变为不可访问。 删除门户不会影响环境中存在的任何门户配置或解决方案，它们将保持原样。
必须手动删除门户配置才能从环境中完全删除门户配置。 为此，请使用门户管理应用，并为门户删除相应的网站记录。

> [!NOTE]
> 如果没有足够的权限删除门户，则会显示错误。 您必须具有 "系统管理员" 角色才能删除门户。 此外，你必须是 Azure Active Directory 中的门户应用程序的所有者。 默认情况下，创建门户的用户是所有者，可以删除门户。 有关将自己添加为所有者的信息，请参阅[将自己添加为 Azure AD 应用程序的所有者](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal#to-add-yourself-as-an-owner-of-the-azure-ad-application)。

## <a name="details"></a>详细信息

显示详细信息，如门户所有者、创建和上次修改的日期和时间，以及门户的 URL。

> [!div class=mx-imgBorder]
> ![门户详细信息](media/portal-details.png "门户详细信息")  

