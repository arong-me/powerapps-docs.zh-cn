---
title: 在 PowerApps 中创建门户 | MicrosoftDocs
description: 有关在 PowerApps 中创建门户的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 10/02/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-a-common-data-service-starter-portal"></a>创建 Common Data Service 起点门户

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

借助在 PowerApps 中构建门户的功能，您可以为外部和内部用户创建一个网站，使他们能够与存储在 Common Data Service 中的数据进行交互。

这些是创建门户网站的一些好处：

- 由于数据存储在 Common Data Service 中，因此您无需像使用 SharePoint、Dynamics 365 模型驱动应用程序或 Salesforce 等数据源那样，通过 PowerApps 创建连接。 您只需要指定要在门户中显示或管理的实体。

- 您可以在 WYSIWYG 门户设计器中通过在网页上添加和配置组件来设计门户。

您可以在新环境或现有环境中创建门户。

如果您选择使用**创建新环境**链接在新环境中创建门户，则在创建环境时会安装必需的门户先决条件，例如实体、数据和起点门户模板。 使用这种方法，几分钟后即可配置门户。

如果选择在没有门户先决条件的现有环境中创建门户，则首先安装先决条件，然后再创建门户。 采用这种方法，门户配置可能会花费一些时间，并且在配置门户后会通知您。

您可以根据所选环境在 PowerApps 中创建 Common Data Service 起点门户或 Dynamics 365 门户。

有关使用环境的详细信息：[使用环境和 Microsoft PowerApps](https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/working-with-environments)

有关可用门户网站模板的详细信息：[门户模板](portal-templates.md)

要创建门户：

1.  登录到 [PowerApps](http://web.powerapps.com)。  

2.  在**制作您自己的应用**下，选择**从空白门户开始(预览)**。

3.  如果所选环境不包含门户先决条件，则将在**从空白门户开始(预览)** 窗口中显示一条消息，建议您选择另一个环境或创建一个新环境。

    > [!div class=mx-imgBorder]
    > ![创建新环境消息](media/create-portal-message.png "创建新环境消息")

4.  如果选择继续使用当前环境，请按照以下步骤在窗口中输入所需信息。 如果选择创建新环境，请参阅[创建新环境](#create-new-environment)。

5.  在**从空白门户开始(预览)** 窗口中，输入门户的名称和网站的地址，然后从下拉列表中选择一种语言。 完成后，选择**创建**。

    > [!div class=mx-imgBorder]
    > ![创建新门户](media/create-new-portal.png "创建新门户")  

选择**创建**后，门户将开始配置，配置状态通过[通知](#portal-provisioning-notifications)显示。

如果您在没有安装门户先决条件的环境中创建了门户，那么配置状态也会显示在网格中：

> [!div class=mx-imgBorder]
> ![网格通知](media/provision-progress-notif.png "网格通知")

成功配置门户后，状态将更新，门户将显示在网格中：

> [!div class=mx-imgBorder]
> ![已配置的门户](media/recent-apps.png "已配置的门户")

要在门户设计器中编辑门户，请参阅[编辑门户](manage-existing-portals.md#edit)。

> [!NOTE]
> - 您最多可以在一个租户中创建五个门户。 但是，在环境中每种类型只能创建一个门户。
> - 如果权限不足，无法配置门户，将显示错误。 您必须在 Common Data Service 中具有系统管理员或至少具有系统定制员角色才能创建门户。 您还必须在用户记录的**客户端访问许可证(CAL)信息**下将**访问模式**设置为**读写**。

## <a name="create-new-environment"></a>创建新环境

使用**从空白门户开始(预览)** 窗口中提供的选项创建环境时，请执行以下步骤。

1.  在**新环境**窗格中，输入环境名称，然后从下拉列表中选择区域和环境类型。 创建环境后，您将无法更改区域。 完成后，选择**创建环境**。

    > [!div class=mx-imgBorder]
    > ![创建新环境](media/create-new-environment.png "创建新环境")  

2.  创建环境后，将在对话框中收到确认消息，并提示您创建数据库。 选择**创建数据库**以允许对 Common Data Service 的访问。

    > [!NOTE]
    > 创建数据库的提示可能不会自动显示。 在这种情况下，您必须转到新环境并再次选择**从空白门户开始**磁贴。

    > [!div class=mx-imgBorder]
    > ![已创建新环境](media/new-environment-created.png "已创建新环境")  

3.  选择数据库中存储的数据的货币和语言。 创建数据库后，您将无法更改货币或语言。 完成后，选择**创建我的数据库**。 数据库是通过起点门户创建的，一旦配置了门户，您便可以快速开始示例内容。

    > [!NOTE]
    > **包含起点门户**选项仅在您使用**从空白门户开始(预览)** 窗口中提供的选项创建环境时可用。 从 PowerApps 管理中心创建环境时，此选项不可用。

    > [!div class=mx-imgBorder]
    > ![创建新数据库](media/create-new-database.png "创建新数据库") 

    在 Common Data Service 上创建数据库可能需要几分钟。 创建数据库后，将在 PowerApps 主页上的环境列表中选择新环境，并创建门户管理应用。 该应用不是实际的门户，而是模型驱动的配套应用，可让您执行高级管理活动。 现在，您可以继续创建用于设计面向外部的网站的门户。

    > [!div class=mx-imgBorder]
    > ![门户管理应用](media/portal-mgmt-app.png "门户管理应用")

4. 创建环境和数据库后，在**制作您自己的应用**下，选择**从空白门户开始(预览)**。 

    > [!NOTE]
    > 如果已创建数据库，但仍显示创建数据库提示，则必须刷新 PowerApps 主页，然后再选择**从空白门户开始(预览)** 磁贴。


## <a name="portal-provisioning-notifications"></a>门户配置通知

选择**创建**后，门户将开始配置，配置状态通过通知显示。

**Toast 形式的通知**

当您选择**创建**来配置门户时，将显示以下通知。

> [!div class=mx-imgBorder]
> ![Toast 通知](media/toast-notif.png "Toast 通知") 

**通知窗格中的通知**

成功下达配置请求后，以下通知将显示在**通知**窗格中。

为正在进行的配置显示的通知

> [!div class=mx-imgBorder]
> ![窗格通知](media/pane-notif.png "窗格通知") 

为成功完成的配置显示的通知

> [!div class=mx-imgBorder]
> ![配置成功通知](media/provision-complete-notif.png "配置成功通知") 

如果门户配置失败，则显示类似通知。
  
## <a name="disable-portal-creation-in-a-tenant"></a>在租户中禁用门户创建

作为全局管理员，如果要禁止非管理员在租户中创建门户，可以通过 PowerShell 启用 `disablePortalsCreationByNonAdminUsers` 租户级别设置来实现。 若要运行 PowerShell cmdlet，必须首先安装必需的模块。 有关安装必需的 PowerShell 模块的信息，请参阅[安装](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-powershell#installation)。

安装模块后，在 PowerShell 窗口中运行以下命令（以管理员身份运行 PowerShell）。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

管理员是具有以下 Azure 角色之一的用户：

-  全局管理员
- Dynamics 365 服务管理员
- Power Platform 服务管理员

没有任何上述 Azure 角色的用户被视为非管理员。

在租户中禁用门户创建时，非管理员将看到以下错误：

> [!div class=mx-imgBorder]
> ![门户创建被阻止错误](media/portal-create-blocked-error.png "门户创建被阻止错误")

