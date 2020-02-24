---
title: 在 Power Apps 中管理现有门户 | Microsoft Docs
description: 有关在 Power Apps 中管理门户的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3eea977cf59629c7f2b758affa145f520838b39f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978841"
---
# <a name="manage-existing-portals-in-power-apps"></a>在 Power Apps 中管理现有门户

创建门户后，将立即在 Power Apps 主页的**最近应用程序**下显示该门户。

> [!div class=mx-imgBorder]
> ![最近应用](media/recent-apps.png "最近应用")  

若要管理应用程序，请选择门户的**更多命令** (**…**)，然后从上下文菜单选择操作。

> [!div class=mx-imgBorder]
> ![门户应用选项](media/portal-app-options.png "门户应用选项")  

## <a name="edit"></a>编辑

打开 [Power Apps 门户 Studio](portal-designer-anatomy.md) 以编辑门户的内容和组件。  

> [!div class=mx-imgBorder]
> ![门户开发者](media/portal-maker.png "门户开发者")  

## <a name="browse"></a>浏览

打开门户以浏览网站。 这将帮助您按照门户对客户的显示查看门户。

> [!div class=mx-imgBorder]
> ![门户网站](media/portal-website.png "门户网站")  

此外，也可以通过在 [Power Apps 门户 Studio](portal-designer-anatomy.md) 中选择**浏览网站**打开门户浏览网站，以便查看已对网站进行的更改。 将使用该网站的 URL 在新标签页中打开该网站。

## <a name="share"></a>共享

将门户与内部或外部用户共享。 执行**共享此门户**窗格中介绍的步骤。

> [!div class=mx-imgBorder]
> ![共享门户](media/share-portal.png "共享门户")  

### <a name="share-with-internal-users"></a>与内部用户共享

若要与内部用户共享门户，首先必须创建安全角色，然后为用户分配该安全角色，使其可使用此门户。

> [!NOTE]
> 作为 Common Data Service 用户，如果您没有门户实体的相应权限，可能会看到“您无权查看此环境中的解决方案”。 或“您无权查看此环境中的网站”之类错误。 建议您在相应的 Common Data Service 数据库中担任系统管理员安全角色。

#### <a name="step-1-create-a-security-role"></a>步骤 1：创建安全角色

1.  在**共享此门户**窗格中**创建安全角色**下选择**安全角色**。 将显示配置的所有安全角色的列表。

2.  在“操作”工具栏上，选择**新建**。

3.  在**新安全角色**窗口中，输入角色名称。

4.  为门户中使用的所有实体设置权限。

5.  完成安全角色配置时，在工具栏上选择**保存并关闭**。

有关安全角色和特权的信息，请参阅[安全角色和特权](https://docs.microsoft.com/power-platform/admin/security-roles-privileges)。

#### <a name="step-2-assign-users-to-the-security-role"></a>步骤 2：将用户分派给安全角色

1.  在**共享此门户**窗格中，在**向安全角色分派用户**下选择**用户**。 将显示所有用户的列表。

2.  选择要为其分派安全角色的用户。

3.  选择**管理角色**。

    > [!NOTE]
    > 如果在命令栏上无法看到**管理角色**按钮，必须通过将 URL 中的 forceUCI 设置为 0 来更改客户端。 例如，https://&lt;org\_url&gt;/main.aspx?pagetype=entitylist&etn=systemuser&forceUCI=0

4.  在**管理用户角色**对话框中，选择您之前创建的安全角色，然后选择**确定**。

### <a name="share-with-external-users"></a>与外部用户共享

您的门户应该以匿名方式运行，并且外部用户可以访问。 如果要尝试用于管理外部用户的角色和权限的高级功能，请参阅[配置在门户中使用的联系人](configure/configure-contacts.md)、[为门户邀请联系人](configure/invite-contacts.md)、[为门户创建 Web 角色](configure/create-web-roles.md)、[分派实体权限](configure/assign-entity-permissions.md)。  

## <a name="settings"></a>设置

显示门户设置，并可用于更改门户的名称。 也可以执行高级查找，如通过 Power Apps 门户管理中心管理门户和处理站点设置。 设置提供 Power Apps 门户管理中心和站点设置的链接。 详细信息：[高级门户管理](admin/admin-overview.md)和[配置站点设置](configure/configure-site-settings.md)。  

> [!div class=mx-imgBorder]
> ![门户设置](media/portal-settings.png "门户设置")  

## <a name="delete"></a>删除

删除门户和托管资源。 删除门户时，其 URL 将变为不可访问。 删除门户不影响环境中的所有门户配置或解决方案，它们将保持原样。
必须手动删除门户配置，才能从环境中完全删除门户配置。 方法是，使用门户管理应用程序，并删除门户的相应网站记录。

> [!NOTE]
> 如果权限不足，无法删除门户，将显示错误。 您必须具有系统管理员角色才能删除门户。 此外，还必须是 Azure Active Directory 中的门户应用程序负责人。 创建门户的用户默认为负责人，可以删除门户。 有关将自己添加为负责人的信息，请参阅[将自己添加为 Azure AD 应用程序的负责人](admin/admin-overview.md#add-yourself-as-an-owner-of-the-azure-ad-application)。

## <a name="details"></a>详细信息

显示详细信息，如门户的负责人，门户的创建和上次修改日期和时间，以及门户的 URL。

> [!div class=mx-imgBorder]
> ![门户详细信息](media/portal-details.png "门户详细信息")  

