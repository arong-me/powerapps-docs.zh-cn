---
title: 设置 Power BI 与门户的集成 | MicrosoftDocs
description: 了解如何设置 Power BI 与您的门户的集成。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6a471dba2f91ca869ad9ba9da46f6e02cb2a643d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756728"
---
# <a name="set-up-power-bi-integration"></a>设置 Power BI 集成

Power BI 是使用简单的交互式可视化提供见解的最佳工具之一。 若要在门户中的网页上查看 Power BI 的仪表板和报表，您必须从 PowerApps 门户管理中心启用 Power BI 可视化。 您还可以通过启用 Power BI Embedded 服务集成来嵌入在 Power BI 的新工作区中创建的仪表板和报表。

> [!NOTE]
> - 您必须有相应的 Power BI 许可证。
> - 若要使用 Power BI Embedded 服务，您必须有相应的 Power BI Embedded 许可证。 有关详细信息，请参阅[许可](https://docs.microsoft.com/power-bi/developer/embedded-faq#licensing)。

## <a name="enable-power-bi-visualization"></a>启用 Power BI 可视化

启用 Power BI 可视化允许您使用 powerbi Liquid 标记在门户中的网页上嵌入仪表板和报表。

1.  打开 [PowerApps 门户管理中心](admin-overview.md)。

2.  转到**设置 Power BI 集成** > **启用 Power BI 可视化**。

    > [!div class=mx-imgBorder]
    > ![启用 Power BI 可视化](../media/enable-power-bi-visualization.png "启用 Power BI 可视化")

3.  在确认消息中选择**启用**。 在 Power BI 可视化启用后，门户将重启，并且会在几分钟内不可用。 在启用 Power BI 可视化后将显示一条消息。

定制员可以使用 [powerbi](../liquid/portals-entity-tags.md#powerbi) Liquid 标记来在门户中的网页上嵌入 Power BI 仪表板和报表。 在嵌入 Power BI 内容时，定制员可以使用[筛选器参数](https://docs.microsoft.com/power-bi/service-url-filters)创建个性化视图。 详细信息：[powerbi Liquid 标记](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>禁用 Power BI 可视化

1.  打开 [PowerApps 门户管理中心](admin-overview.md)。

2.  转到**设置 Power BI 集成** > **禁用 Power BI 可视化**。

    > [!div class=mx-imgBorder]
    > ![禁用 Power BI 可视化](../media/disable-power-bi-visualization.png "禁用 Power BI 可视化")

3. 在确认消息中选择**禁用**。 在 Power BI 可视化禁用后，门户将重启，并且会在几分钟内不可用。 在禁用 Power BI 可视化后将显示一条消息。

## <a name="enable-power-bi-embedded-service"></a>启用 Power BI Embedded 服务

启用 Power BI Embedded 服务让您可以嵌入在 Power BI 的新工作区中创建的仪表板和报表。 使用 powerbi Liquid 标记在门户中的网页上嵌入仪表板和报表。

**先决条件**：在启用 Power BI Embedded 服务之前，请确保您已在 Power BI 的新工作区创建仪表板和报表。 在创建工作区后，向全局管理员提供管理员访问权限，以使工作区显示在 PowerApps 门户管理中心内。 有关创建新工作区以及向其添加访问权限的详细信息，请参阅[在 Power BI 中创建新工作区](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)。

**Power BI Embedded 服务限制**：有关限制的信息，请参阅[注意事项和限制](https://docs.microsoft.com/power-bi/developer/embed-service-principal#considerations-and-limitations)。

> [!NOTE]
> 请确保为使用 powerbi Liquid 标记启用 Power BI 可视化。

1. 打开 [PowerApps 门户管理中心](admin-overview.md)。

2. 转到**设置 Power BI 集成** > **启用 Power BI Embedded 服务**。

    > [!div class=mx-imgBorder]
    > ![启用 Power BI Embedded 服务](../media/enable-powerbi-embedded-button.png "启用 Power BI Embedded 服务")

3. 在**启用 Power BI Embedded 服务集成**窗口中，从需要在您的门户中显示的仪表板和报表中选择 Power BI 工作区并将其移至**选定工作区**列表。

    > [!div class=mx-imgBorder]
    > ![选择 Power BI 工作区](../media/enable-powerbi-embedded-window.png "选择 Power BI 工作区")
    
    > [!NOTE]
    > 在将工作区添加到**选定工作区**列表后，数据库和报表将在几分钟后呈现。
    

4. 选择**启用**。 在启用 Power BI Embedded 服务时，将重新启动门户，并且门户有几分钟不可用。 在启用 Power BI Embedded 服务后将显示一条消息。

您现在必须创建安全组，并将其添加到您的 Power BI 帐户中。 有关详细信息，请参阅[创建安全组并添加到 Power BI 帐户中](#create-security-group-and-add-to-power-bi-account)。

### <a name="create-security-group-and-add-to-power-bi-account"></a>创建安全组并添加到 Power BI 帐户中

在启用 Power BI Embedded 服务集成后，您必须在 Azure Active Directory 中创建安全组，并向其添加成员，然后通过 Power BI 管理门户在 Power BI 中添加安全组。 这允许在新 Power BI 工作区中创建的仪表板和报表显示在门户中。

> [!NOTE]
> 您必须使用用于启用 Power BI Embedded 服务的同一个全局管理员帐户登录。

**步骤 1：创建安全组**

1. 使用目录的全局管理员帐户登录 [Azure 门户](https://portal.azure.com)。

2. 选择 **Azure Active Directory**、**组**，然后选择**新建组**。

3. 在**组**页面中，输入以下信息：

    - **组类型**：安全组。

    - **组名称**：门户 Power BI Embedded 服务。

    - **组描述**：此安全组用于门户和 Power BI Embedded 服务集成。

    - **成员身份类型**：已分派。

      > [!div class=mx-imgBorder]
      > ![为 Power BI Embedded 服务创建安全组](../media/powerbi-embed-security-group.png "为 Power BI Embedded 服务创建安全组")

4. 选择**创建**。

**步骤 2：添加组成员**

**必备条件**：在将成员添加到安全组前，您必须有门户的应用程序 ID。 门户的应用程序 ID 在 [PowerApps 门户管理中心](admin-overview.md)的**门户详细信息**选项卡提供。

1. 使用目录的全局管理员帐户登录 [Azure 门户](https://portal.azure.com)。

2. 选择 **Azure Active Directory**，然后选择**组**。

3. 从**组 - 所有组**页，搜索**门户 Power BI Embedded 服务**组，并选择它。

    > [!div class=mx-imgBorder]
    > ![索并选择 Power BI Embedded 服务的安全组](../media/search-security-group.png "索并选择 Power BI Embedded 服务的安全组")

4. 从**门户 Power BI Embedded 服务概述**页，从**管理**区域选择**成员**。

5. 选择**添加成员**，在文本框中输入门户的应用程序 ID。

6. 从搜索结果中选择成员，然后选择**选择**。

    > [!div class=mx-imgBorder]
    > ![在 Power BI Embedded 服务的安全组中添加成员](../media/add-member-powerbi-embed.png "在 Power BI Embedded 服务的安全组中添加成员")

**步骤 3：Power BI 设置**

1. 使用目录的全局管理员帐户登录 [Power BI](https://powerbi.microsoft.com)。

2. 在 Power BI 服务的右上角选择**设置**，并选择**管理门户**。

    > [!div class=mx-imgBorder]
    > ![在 Power BI 服务中选择管理门户](../media/select-admin-portal.png "在 Power BI 服务中选择管理门户")

3. 选择**租户设置**。

4. 在**开发人员设置**部分下，选择**允许服务主体使用 Power BI API**。

5. 在**特定安全组**字段中，搜索**门户 Power BI Embedded 服务**组，并选择它。

    > [!div class=mx-imgBorder]
    > ![在 Power BI 管理门户中添加安全组](../media/add-sg-powerbi.png "在 Power BI 管理门户中添加安全组")

6. 选择**应用**。

定制员现在可以使用 [powerbi](../liquid/portals-entity-tags.md#powerbi) Liquid 标记来在门户中网页上的新 Power BI 工作区嵌入 Power BI 仪表板和报表。 若要使用 Power BI Embedded 服务，身份验证类型必须指定为 **powerbiembedded**。 在嵌入 Power BI 内容时，定制员可以使用[筛选器参数](https://docs.microsoft.com/power-bi/service-url-filters)创建个性化视图。 详细信息：[powerbi Liquid 标记](../liquid/portals-entity-tags.md#powerbi)。


### <a name="manage-the-power-bi-embedded-service"></a>管理 Power BI Embedded 服务

1. 打开 [PowerApps 门户管理中心](admin-overview.md)。

2. 转到**设置 Power BI 集成** > **管理 Power BI Embedded 服务**。

    > [!div class=mx-imgBorder]
    > ![管理 Power BI Embedded 服务](../media/manage-powerbi-embedded-button.png "管理 Power BI Embedded 服务")

3. 在**管理 Power BI Embedded 服务集成**窗口中，从需要在您的门户中显示的仪表板和报表中删除 Power BI 工作区或将其移至**选定工作区**列表。

    > [!div class=mx-imgBorder]
    > ![选择 Power BI 工作区](../media/manage-powerbi-embedded-window.png "选择 Power BI 工作区")
    
    > [!NOTE]
    > 在从**选定工作区**列表删除工作区后，最多可能需要 1 小时反映更改。 到时，数据库和报表将呈现在门户上，且没有任何问题。

4. 选择**保存**。

### <a name="disable-the-power-bi-embedded-service"></a>禁用 Power BI Embedded 服务

1.  打开 [PowerApps 门户管理中心](admin-overview.md)。

2.  转到**设置 Power BI 集成** > **管理 Power BI Embedded 服务**。

    > [!div class=mx-imgBorder]
    > ![管理 Power BI Embedded 服务](../media/manage-powerbi-embedded-button.png "管理 Power BI Embedded 服务")

3. 在**管理 Power BI Embedded 服务集成**窗口中，选择**禁用 Power BI Embedded 服务集成**。

    > [!div class=mx-imgBorder]
    > ![禁用 Power BI Embedded 服务](../media/disable-powerbi-embedded-window.png "禁用 Power BI Embedded 服务")

4. 选择**保存**。

5. 在确认消息中选择**确定**。 在禁用 Power BI Embedded 服务时，将重新启动门户，并且门户有几分钟不可用。 在禁用 Power BI Embedded 服务后将显示一条消息。

## <a name="privacy-notice"></a>隐私声明  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>另请参阅

[powerbi Liquid 标记](../liquid/portals-entity-tags.md#powerbi)<br> 
[向门户内的网页添加 Power BI 报表或仪表板](add-powerbi-report.md)
