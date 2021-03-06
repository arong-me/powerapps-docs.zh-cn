---
title: 在 Power Apps 门户中创建和管理发布状态 | MicrosoftDocs
description: 了解如何在门户中创建和管理发布状态。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 6daf92aa4d821b66b8388826d69dcb8bbd99ddb4
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980513"
---
# <a name="create-and-manage-publishing-states"></a>创建和管理发布状态

发布状态允许门户网站中内容生命周期的定义。 在基本级别，发布状态可以确定关联的实体是否应在门户中被视为可见/已发布。 在更复杂的配置中，它们可定义内容查看和发布的多阶段流程，每个阶段有安全限制。

发布状态可用于[网页](web-page.md)、[web 文件](web-files.md)、[web 链接](manage-web-links.md)、论坛和广告。

默认情况下，有两个发布状态可用：草稿和已发布。 草稿指定不应向非内容作者用户显示的内容，而已发布指定应对所有门户用户显示的内容（除其他安全限制外）。 如果需要，您可以修改默认配置以满足您的特定要求 – 通过添加新状态或重命名状态。

## <a name="manage-publishing-states"></a>管理发布状态

可在门户中创建、编辑和删除发布状态。

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转到**门户** > **网站**。

3. 选择要管理发布状态的网站。

4. 转到**发布状态**选项卡。将显示可用发布状态列表。

    > [!div class=mx-imgBorder]
    > ![管理发布状态](../media/publishing-states.png "管理发布状态")

5. 若要添加新发布状态，请选择**新发布状态**。

6. 若要编辑现有的发布状态，选择该发布状态的名称。

7. 在“发布状态”窗口中，在字段中输入适当的值。

8. 选择**保存并关闭**。


### <a name="publishing-state-attributes"></a>发布状态属性

|名称|说明|
|-----|--------|
|名称|状态的描述性名称。 此字段为必填字段。|
|网站|状态所属的网站。 此字段为必填字段。|
|默认|如果选中，将指定此状态作为网站的默认状态。 在通过门户前端编辑界面创建新实体时，这将确定选定的默认状态。<br>**注意**：只有给定网站的一个发布状态应标记为默认状态。|
|可公开|如果选中，将指定与此状态关联的实体将在门户上被视为可见（或已发布）。<br>虽然与不可见状态关联的实体将在门户上不可见，与可见状态关联的实体也可能不可见，可能由于安全权限、到期日期或其他可见性规则。<br>具有内容管理权限的用户可以被授予使用“预览模式”的能力，这允许这些用户查看（预览）未发布的内容。|
|显示顺序|表示状态放置顺序的整数值，在用于选择发送状态的菜单和下拉列表中 – 多数时候在门户前端编辑界面中。|
|||

## <a name="publishing-state-transition-rules"></a>发布状态转换规则

发布状态转换规则允许您精细控制哪些 Web 角色有权在门户上进行有关发布状态的内容更改。

为求准确，发布状态转换规则管理发布状态（草稿或已发布）之间的转换。 当用户尝试将项目的发布状态从个切换为另一个时，如果此转换存在规则，那么安全提供程序将断言已登录用户的 Web 角色有权执行此转换。

如果尝试更改的登录用户具有您分派到规则的任何一个角色，转换将会成功。 如果用户不具有将一个规则更改为另一个规则的权限，前端编辑将不允许他们进行该更改。 或者，您可以创建规则；然后当您创建 Web 角色时，将规则添加到 Web 角色。 一个规则可以与任何数量的 Web 角色关联，反之亦然。

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转到**门户** > **发布状态转换规则**。

3. 若要新建规则，请选择**新建**。

4. 若要编辑现有规则，请选择规则名称。

5. 在“发布状态转换规则”窗口中，在字段中输入适当的值。

6. 选择**保存**，以便可以继续将 Web 角色添加到其中。

    > [!div class=mx-imgBorder]
    > ![创建发布状态转换规则](../media/publishing-state-transition-rule.png "创建发布状态转换规则")

7. 在 **Web 角色**选项卡中，选择**添加现有 Web 角色**。 在**查找记录**窗格中，浏览并添加相应的 Web 角色。

8. 选择**保存**。

## <a name="state-based-control-rules"></a>基于状态的控制规则

[网页访问控制规则](webpage-access-control.md)与发布状态链接以允许或拒绝基于网站分支和该分支中内容的发布状态查看或修改内容的权限。 为此，可将网页访问控制规则与发布状态关联。 一旦与发布状态关联，在该发布状态有效时，规则将只能应用于网页。

例如，假设您希望具有内容发布角色的某个人只能在页面处于“草稿”模式时修改该页面的内容。  这将确保对页面的更改在页面“活动”时不执行，并允许对待定更改执行审批流程。

为此，您将使用授予的更改权限创建规则，并将其应用于问题分支（或如果规则应用于整个网站则为主页）。 然后您将此规则与草稿状态关联。

> [!div class=mx-imgBorder]
> ![创建基于状态的控制规则](../media/state-based-control-rule.png "创建基于状态的控制规则")

然后您将此规则与相应的 Web 角色关联，例如，内容发布。 假设此 Web 角色未与更宽限的规则（即无论发布状态如何均准予更改的规则）关联，那么具有内容发布 Web 角色的用户将能够修改草稿状态的页面，但不能修改已发布状态的页面。
