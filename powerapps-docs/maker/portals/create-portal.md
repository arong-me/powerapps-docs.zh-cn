---
title: 在 PowerApps 中创建门户 |Microsoft Docs
description: 在 PowerApps 中创建门户的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b818db8fb72fe36fcc7ea049a4e5b4cfb17eb0d9
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542655"
---
# <a name="create-a-common-data-service-starter-portal"></a>创建 Common Data Service starter 门户

利用在 PowerApps 中生成门户的功能，你可以为外部和内部用户创建网站，使其能够与 Common Data Service 中存储的数据进行交互。

下面是创建门户的一些优点：

- 由于数据存储在 Common Data Service 中，因此您无需从 PowerApps 创建连接，就像在 Dynamics 365 或 Salesforce 中处理 SharePoint、模型驱动应用程序时一样。 只需在门户中指定要显示或管理的实体。

- 可以通过在网页上添加和配置组件，通过 WYSIWYG 门户 Studio 设计门户。

可以在新的环境中或在现有环境中创建门户。

如果选择使用 "**创建新环境**" 链接在新环境中创建门户，则会在创建环境时安装所需的门户必备组件，例如实体、数据和初学者门户模板。 在此方法中，将在几分钟内预配门户。

如果选择在没有门户必备组件的现有环境中创建门户，将首先安装先决条件，然后创建门户。 在此方法中，门户预配可能需要一些时间，并且在设置门户后会收到通知。

基于 PowerApps 中选定的环境，你可以在 Dynamics 365 中包含模型驱动应用的环境中创建 Common Data Service 初学者门户或门户。

有关使用环境的详细信息：使用[环境和 Microsoft PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)

有关可用门户模板的详细信息：[门户模板](portal-templates.md)

创建门户：

1.  登录 [PowerApps](https://make.powerapps.com)。  

2.  在 "**制作自己的应用**" 下，选择 "**门户**"。

3.  如果所选环境不包含门户必备项，则会在**门户**中显示一条消息，提示你选择其他环境或创建一个新环境。

    > [!div class=mx-imgBorder]
    > ![创建新环境消息](media/create-portal-message.png "创建新环境消息")

4.  如果选择继续当前环境，请在窗口中输入所需的信息，如以下步骤中所述。 如果选择创建新的环境，请参阅[创建新环境](#create-new-environment)。

5.  在**门户中**的 "空白" 窗口中，输入门户网站的名称和地址，然后从下拉列表中选择一种语言。 完成后，选择 "**创建**"。

    > [!div class=mx-imgBorder]
    > ![新建门户](media/create-new-portal.png "新建门户")  

选择 "**创建**" 后，门户将开始预配，并通过 "[通知](#portal-provisioning-notifications)" 显示设置状态。

如果在未安装门户必备组件的环境中创建门户，则该设置状态也将显示在网格中：

> [!div class=mx-imgBorder]
> ![网格通知](media/provision-progress-notif.png "网格通知")

成功设置门户后，状态将更新，并在网格中显示门户：

> [!div class=mx-imgBorder]
> ![已预配门户](media/recent-apps.png "已预配门户")

若要在 PowerApps portal Studio 中编辑门户，请参阅[编辑门户](manage-existing-portals.md#edit)。

> [!NOTE]
> - 最多可以在一个租户中创建五个门户。 但是，环境中只能创建每个类型的一个门户。
> - 如果没有足够的特权来预配门户，将显示错误。 你必须具有中的 "系统管理员" 角色才能创建门户 Common Data Service。 还必须在用户记录的 "**客户端访问许可证（CAL）" 信息**中将**访问模式**设置为 "**读写**"。
> - 如果你购买了较旧的门户外接程序，并且想要使用该外接程序预配门户，则必须使用 " **Dynamics 365 管理中心**" 页。 详细信息：[使用旧门户加载项预配门户](provision-portal-add-on.md)
> - 如果已使用旧版门户外接程序预配了门户，则仍可通过[make.powerapps.com](https://make.powerapps.com)对其进行自定义和管理。
> - 从[make.powerapps.com](https://make.powerapps.com)预配门户不会使用较旧的门户加载项。 此外，这些门户未列在**Dynamics 365 管理中心**页面上的 "**应用程序**" 选项卡下。
> - 无法从**Dynamics 365 管理中心**页面创建 Common Data Service starter 门户。
> - PowerApps 门户在法国地区不可用。

## <a name="create-new-environment"></a>创建新环境

使用门户中的 "**空白**" 窗口中提供的选项创建环境时，请遵循以下步骤。

1.  在 "**新建环境**" 窗格中，输入环境的名称，然后从下拉列表中选择 "区域和环境类型"。 环境创建后，将无法更改区域。 完成后，选择 "**创建环境**"。

    > [!div class=mx-imgBorder]
    > ![创建新环境](media/create-new-environment.png "创建新环境")  

2.  创建环境后，会在对话框中收到一条确认消息，并会提示创建数据库。 选择 "**创建数据库**" 以启用对 Common Data Service 的访问。

    > [!NOTE]
    > 可能不会自动显示创建数据库的提示。 在这种情况下，你必须切换到新环境，并再次**从空白**磁贴中选择门户。

    > [!div class=mx-imgBorder]
    > ![已创建新环境](media/new-environment-created.png "已创建新环境")  

3.  为数据库中存储的数据选择货币和语言。 数据库创建后，将无法更改货币或语言。 完成后，选择 "**创建数据库"** 。 该数据库是通过入门门户创建的，它使你可以在设置门户后快速开始处理示例内容。

    > [!NOTE]
    > 仅当使用门户中的 "**空白**" 窗口创建环境时，"**包括初学者门户**" 选项才可用。 从 PowerApps 管理中心创建环境时，此选项不可用。

    > [!div class=mx-imgBorder]
    > ![创建新数据库](media/create-new-database.png "创建新数据库") 

    Common Data Service 上创建数据库可能需要几分钟时间。 创建数据库后，将在 PowerApps 主页上的环境列表中选择新环境，并创建门户管理应用。 此应用并不是实际的门户，而是模型驱动的应用，可用于执行高级配置活动。 现在，你可以继续创建门户来设计面向外部的网站。

    > [!div class=mx-imgBorder]
    > ![门户管理应用](media/portal-mgmt-app.png "门户管理应用")

4. 创建环境和数据库后，在 "**创建自己的应用**" 下，选择 "门户" "**空白**"。 

    > [!NOTE]
    > 如果创建了数据库，但仍收到 "创建数据库" 提示，则必须先刷新 PowerApps 主页，再**从空白**磁贴中选择门户。


## <a name="portal-provisioning-notifications"></a>门户预配通知

选择 "**创建**" 后，门户将开始预配，并通过 "通知" 显示设置状态。

**作为 toast 通知**

选择 "**创建**" 以预配门户时，将显示以下通知。

> [!div class=mx-imgBorder]
> ![Toast 通知](media/toast-notif.png "Toast 通知") 

**通知窗格中的通知**

成功放置预配请求后，**通知**窗格中会显示以下通知。

正在进行预配显示的通知

> [!div class=mx-imgBorder]
> ![窗格通知](media/pane-notif.png "窗格通知") 

已成功完成为设置显示的通知

> [!div class=mx-imgBorder]
> ![预配成功通知](media/provision-complete-notif.png "预配成功通知") 

如果门户预配失败，则通知显示方式类似。
  
**通过电子邮件发送通知**

成功放置预配请求后，将向创建门户的用户发送确认电子邮件通知。 此外，在门户预配完成后，会向用户发送一封电子邮件。

## <a name="disable-portal-creation-in-a-tenant"></a>禁用租户中的门户创建

作为全局管理员，如果要在租户中禁用由非管理员创建的门户，则可以通过 PowerShell 启用 `disablePortalsCreationByNonAdminUsers` 租户级别设置来执行此操作。 若要运行 PowerShell cmdlet，必须先安装所需的模块。 若要了解如何安装所需的 PowerShell 模块，请参阅[安装](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#installation)。

安装这些模块后，在 PowerShell 窗口中运行以下命令（以管理员身份运行 PowerShell）。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

管理员是具有以下 Azure 角色之一的用户：

- 全局管理员
- Dynamics 365 服务管理员
- Power Platform 服务管理员

没有以上提到的任何 Azure 角色的用户被视为非管理员用户。

当在租户中禁用门户创建时，非管理员将看到如下错误：

> [!div class=mx-imgBorder]
> ![已阻止门户创建错误](media/portal-create-blocked-error.png "已阻止门户创建错误")
