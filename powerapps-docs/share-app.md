---
title: "共享应用 | Microsoft 文档"
description: "通过授予其他用户运行或修改应用的权限来共享应用"
services: 
suite: powerapps
documentationcenter: na
author: linhtranms
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/28/2016
ms.author: litran
ms.openlocfilehash: 1d32873009c337a835a047df38b9ef18d5bf2064
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="share-an-app-in-powerapps"></a>在 PowerApps 中共享应用
虽然可以使用 PowerApps 轻松生成可满足你自己的业务需求的应用，但能够与其他人共享这些应用才是它的真正魅力所在。 在本主题中，你将了解如何与指定用户或安全组共享应用，或与整个组织共享应用。

## <a name="open-the-share-app-screen"></a>打开共享应用屏幕
若要共享应用，必须打开 powerapps.com。我们不再支持在 PowerApps Studio 或 PowerApps Mobile 上共享应用。

**从 PowerApps Studio 开始**

* 选项 1 - 在“文件”菜单上，单击或点击“共享”。
  
    ![文件和共享](./media/share-app/studio-share.png)
* 选项 2 - 在“文件”菜单上，单击或点击“打开”，然后单击或点击应用的共享图标。
  
    ![省略号和共享](./media/share-app/studio-share-icon.png)

**从 [powerapps.com](http://web.powerapps.com) 开始**

* 在左侧的导航栏中，单击或点击“应用”，然后单击或点击省略号 (...)，再单击或点击“共享”。
  
   ![门户上的省略号](./media/share-app/portal-share.png)

## <a name="share-an-app"></a>共享应用
从此处可通过执行下列步骤来共享应用。

1. 指定 Azure Active Directory 中一个或多个用户或安全组的名称，或指定要与整个组织共享应用。 请注意，当向整个组织进行共享时，只能使用**用户**权限共享。
   
    ![在 powerapps.com 中指定用户](./media/share-app/portal-users.png)
2. 指定权限级别：
   
   * **用户**：用户或组可以运行应用，但无法共享应用。
   * **参与者**：用户或组可以运行、自定义该应用，并可对其他用户共享自定义版本。
     
       ![共享应用门户](./media/share-app/portal-permissions.png)
3. 单击或点击“**保存**”。

要更改用户或组的权限，请重复此过程的步骤 1，然后在权限列表中为相应用户或组指定一个不同的选项。 要删除用户或组的所有权限，请单击或点击相应用户或组的 **x** 图标。

### <a name="send-email-notification"></a>发送电子邮件通知
在共享应用时，可选择是否通过电子邮件通知用户或安全组。 如果选择此选项，将发送一封电子邮件来通知用户或安全组。 该电子邮件包含用于访问应用的链接。 如适用，系统将提示用户注册并安装 PowerApps。

请注意，所发送的电子邮件模板各不相同，具体取决于共享应用所用的权限。 如果以**用户**权限共享应用，则电子邮件将包含运行该应用的链接。 如果以**参与者**权限共享应用，则电子邮件将包含在 PowerApps Studio 中编辑应用，或运行应用的链接。

### <a name="how-do-my-users-see-the-app-i-shared"></a>用户应如何查看我所共享的应用？
在与一个或多个用户、安全组共享应用后，他们查看该应用的方式将取决于你共享应用所用的权限。

##### <a name="if-you-shared-app-with-user-permission"></a>如果以用户权限共享应用
如果在应用共享屏幕中选择该复选框，则获得共享应用的人将收到一封电子邮件通知。 在电子邮件中，他们可以单击或点击链接，在 [Dynamics 365](http://home.dynamics.com) 上运行应用。 我们将在不久之后支持通用链接，这意味着如果你已安装 PowerApps Studio 或 PowerApps Mobile，该应用将在 PowerApps Studio 或 PowerApps Mobile 中打开。

用户还可在 [Dynamics 365](http://home.dynamics.com) 的 AppSource 中发现应用（例如，如果你未发送电子邮件）。 [阅读更多](app-source.md)有关用户如何通过 AppSource 获取应用的内容。

##### <a name="if-you-shared-an-app-with-contributor-permission"></a>如果以参与者权限共享应用
如果在应用共享屏幕中选择该复选框，则获得共享应用的人将收到一封电子邮件通知。 在电子邮件中，他们可以通过单击或点击链接直接打开应用，然后在适用于 Web 的 PowerApps Studio 中进行编辑。 此外，还有一个链接可用于在 [Dynamics 365](http://home.dynamics.com) 上运行应用。 我们将在不久之后支持通用链接，这意味着如果你已安装 PowerApps Studio 或 PowerApps Mobile，该应用将在 PowerApps Studio 或 PowerApps Mobile 中打开。

用户还可在 [powerapps.com](http://web.powerapps.com) 中发现应用（例如，如果你未发送电子邮件）。 在该主页中，应用创建者可以浏览已创建的所有应用，或浏览以**参与者**权限共享的应用。 与之相反，在 [Dynamics 365](http://home.dynamics.com) 中，用户可以从 PowerApps 和其他商业应用快速运行应用。

## <a name="other-things-to-know"></a>其他须知要点
* 若要共享应用，必须将其保存至云，而非本地。
* 在共享应用之前，请考虑你要与哪个用户和安全组进行共享，以及它们各种所承担的角色 - 用户还是参与者。 如果与某个组共享应用，则该组的现有成员和加入该组的任何人都具有你所指定的权限。 除非是具有访问权限的其他组的成员或者你明确指定权限的人，否则离开该组的任何人都将失去这些权限。
* 每个组成员具有与整个组相同的应用权限。 但是，可以为该组的一个或多个成员指定更高的权限，以允许他们具有更高的访问级别。 例如，你能够以用户权限与安全组 A 共享一个应用。 安全组 A 的每个成员都能运行该应用。 现在，你与用户 B 共享应用，该用户属于安全组 A，具有参与者权限。 用户 B 现在可以编辑应用，同时安全组 A 中的其他成员仅能使用应用。 如果对一个或多个组成员指定较少的权限，则他们仍将具有已授予整个组的所有权限。
* 你可以与整个组织共享应用，但请考虑清楚是否人人都需要访问你的应用。
* 请注意，你对共享应用做出的任何更改一经保存，便会与共享对象同步。 如果你改进应用，便会发现这样非常棒；但如果你删除或大幅改动相关功能，也可能会对其他人造成影响。
* 在共享应用前，为应用指定一个有意义的名称和提要，让其他人知道这是一个什么应用，并能在列表中快速找到它。 在 PowerApps Studio 的“文件”菜单中，单击或点击“应用设置”，然后输入提要。
  
  ![应用提要](./media/share-app/description.png)

### <a name="app-sharing-and-the-resources-the-app-uses"></a>应用共享和应用所使用的资源
大多数应用至少依赖于以下资源类型中的一个：

* 到数据源的连接
* 本地数据网关
* 自定义连接器
* Excel 工作簿或其他服务
* 流

用户和参与者需要获得对应用使用的任何数据连接和网关的访问权限。 虽然应用隐式附带某些权限，但仍必须明确授予其他权限。 有关详细信息，请参阅 [共享应用资源](share-app-resources.md)。

在共享一个使用 Common Data Service 的应用时，请注意信息栏的指示，它要求必须单独对 Common Data Service 共享运行时权限。 如果缺少执行此操作的权限，请查看环境管理。[阅读更多](database-security.md)有关 Common Data Service 的安全性的内容。

![共享时的应用资源](./media/share-app/app-sharing-resources.png)

### <a name="what-isnt-supported"></a>不支持哪些功能？
* 可共享至安全组，但无法共享至分发组。
* 可以与组织中的用户共享应用，但无法与其他租户中的用户共享应用。
* 可以共享来自 [powerapps.com](http://web.powerapps.com) 的应用，但无法共享来自 PowerApps Studio 的应用。 （单击或点击 PowerApps Studio 中的共享图标，打开 [powerapps.com](http://web.powerapps.com)）。
* 如果对某个应用具有参与者（而非用户）权限，则可以重新共享该应用。

