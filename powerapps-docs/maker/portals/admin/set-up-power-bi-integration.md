---
title: 设置与门户 Power BI 集成 |MicrosoftDocs
description: 了解如何设置与门户 Power BI 集成。
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543036"
---
# <a name="set-up-power-bi-integration"></a>设置 Power BI 集成

Power BI 是一种用于通过简单的交互式可视化效果提供见解的最佳工具之一。 若要从门户中的网页 Power BI 查看仪表板和报表，必须从 PowerApps 门户管理中心启用 Power BI 可视化。 通过启用 Power BI Embedded 服务集成，还可以嵌入在 Power BI 的新工作区中创建的仪表板和报表。

> [!NOTE]
> - 您必须具有相应的 Power BI 许可证。
> - 若要使用 Power BI Embedded 服务，必须具有相应的 Power BI Embedded 许可证。 有关详细信息，请参阅[许可](https://docs.microsoft.com/power-bi/developer/embedded-faq#licensing)。

## <a name="enable-power-bi-visualization"></a>启用 Power BI 可视化

启用 Power BI 可视化功能后，可以通过使用 powerbi 液体标记将仪表板和报表嵌入到门户中的网页上。

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  请参阅**设置 Power BI 集成** > **启用 Power BI 可视化**。

    > [!div class=mx-imgBorder]
    > ![启用 Power BI 可视化](../media/enable-power-bi-visualization.png "启用 Power BI 可视化")

3.  在确认消息中选择 "**启用**"。 当启用 Power BI 可视化效果时，门户将重新启动，并将在几分钟内不可用。 启用 Power BI 可视化效果时，将显示一条消息。

定制员可以使用[powerbi](../liquid/portals-entity-tags.md#powerbi)液体标记将仪表板和报表 Power BI 嵌入到门户中的网页上。 嵌入 Power BI 内容时，定制员可以使用[筛选器参数](https://docs.microsoft.com/power-bi/service-url-filters)来创建个性化视图。 详细信息： [Powerbi 液体标记](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>禁用 Power BI 可视化

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  请参阅**设置 Power BI 集成** > **禁用 Power BI 可视化**。

    > [!div class=mx-imgBorder]
    > ![禁用 Power BI 可视化](../media/disable-power-bi-visualization.png "禁用 Power BI 可视化")

3. 在确认消息中选择 "**禁用**"。 尽管 Power BI 可视化功能处于禁用状态，但门户在几分钟内就会重新启动并不可用。 禁用 Power BI 可视化效果时，会显示一条消息。

## <a name="enable-power-bi-embedded-service"></a>启用 Power BI Embedded 服务

启用 Power BI Embedded 服务后，你可以嵌入在 Power BI 的新工作区中创建的仪表板和报表。 使用 power 液标记将仪表板和报表嵌入到门户中的网页上。

**先决条件**：在启用 Power BI Embedded 服务之前，请确保已在 Power BI 的新工作区中创建仪表板和报表。 创建工作区后，提供对全局管理员的管理员访问权限，使工作区显示在 PowerApps 门户管理中心。 若要详细了解如何创建新工作区并添加对它们的访问权限，请参阅[在 Power BI 中创建新工作区](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)。

**Power BI Embedded 服务限制**：有关限制的详细信息，请参阅[注意事项和限制](https://docs.microsoft.com/power-bi/developer/embed-service-principal#considerations-and-limitations)。

> [!NOTE]
> 确保启用要使用的 powerbi 液体标记 Power BI 可视化。

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2. 请参阅**设置 Power BI 集成** > **启用 Power BI Embedded 服务**。

    > [!div class=mx-imgBorder]
    > ![启用 Power BI Embedded 服务](../media/enable-powerbi-embedded-button.png "启用 Power BI Embedded 服务")

3. 在 "**启用 Power BI Embedded 服务集成**" 窗口中，选择 ""，并将需要在门户中显示仪表板和报表的 Power BI 工作区移动到 "**所选工作区**" 列表。

    > [!div class=mx-imgBorder]
    > ![选择 Power BI 工作区](../media/enable-powerbi-embedded-window.png "选择 Power BI 工作区")
    
    > [!NOTE]
    > 向**所选工作区**列表添加工作区后，将在几分钟后呈现数据库和报表。
    

4. 选择 "**启用**"。 当启用 Power BI Embedded 服务时，门户将重新启动并在几分钟内不可用。 启用 Power BI Embedded 服务时，将显示一条消息。

你现在必须创建一个安全组，并将其添加到你的 Power BI 帐户。 有关详细信息，请参阅[创建安全组和添加到 Power BI 帐户](#create-security-group-and-add-to-power-bi-account)。

### <a name="create-security-group-and-add-to-power-bi-account"></a>创建安全组并添加到 Power BI 帐户

启用 Power BI Embedded 服务集成后，你必须在 Azure Active Directory 中创建一个安全组，将一个成员添加到该安全组，然后通过 Power BI 管理门户将该安全组添加到 Power BI 中。 这允许在门户中显示新 Power BI 工作区中创建的仪表板和报表。

> [!NOTE]
> 必须使用用于启用 Power BI Embedded 服务的同一全局管理员帐户登录。

**步骤1：创建安全组**

1. 使用目录的全局管理员帐户登录到[Azure 门户](https://portal.azure.com)。

2. 依次选择 " **Azure Active Directory**" 和 "**组**"，然后选择 "**新建组**"。

3. 在 "**组**" 页上，输入以下信息：

    - **组类型**：安全。

    - **组名称**：门户 Power BI Embedded 服务。

    - **组说明**：此安全组用于门户和 Power BI Embedded 服务集成。

    - **成员资格类型**：已分配。

      > [!div class=mx-imgBorder]
      > ![为 Power BI Embedded 服务创建安全组](../media/powerbi-embed-security-group.png "为 Power BI Embedded 服务创建安全组")

4. 选择“创建”。

**步骤2：添加组成员**

**先决条件**：在将成员添加到安全组之前，你必须具有门户的应用程序 ID。 门户的 "应用程序 ID" 位于[PowerApps 门户管理中心](admin-overview.md)中的 "**门户详细信息**" 选项卡上。

1. 使用目录的全局管理员帐户登录到[Azure 门户](https://portal.azure.com)。

2. 选择 " **Azure Active Directory**"，然后选择 "**组**"。

3. 在 "**组-所有组**" 页上，搜索**门户 Power BI Embedded 服务**组，然后选择它。

    > [!div class=mx-imgBorder]
    > ![搜索并选择 Power BI Embedded 服务的安全组](../media/search-security-group.png "搜索并选择 Power BI Embedded 服务的安全组")

4. 从**门户 Power BI Embedded 服务概述**"页中，从"**管理**"区域中选择"**成员**"。

5. 选择 "**添加成员**"，然后在文本框中输入门户的 "应用程序 ID"。

6. 从搜索结果中选择成员，然后选择 "**选择**"。

    > [!div class=mx-imgBorder]
    > ![为 Power BI Embedded 服务添加安全组中的成员](../media/add-member-powerbi-embed.png "为 Power BI Embedded 服务添加安全组中的成员")

**步骤3： Power BI 安装程序**

1. 使用目录的全局管理员帐户登录到[Power BI](https://powerbi.microsoft.com) 。

2. 选择 Power BI 服务右上方的 "**设置**"，然后选择 "**管理门户**"。

    > [!div class=mx-imgBorder]
    > ![在 Power BI 服务中选择管理门户](../media/select-admin-portal.png "在 Power BI 服务中选择管理门户")

3. 选择 "**租户设置**"。

4. 在 "**开发人员设置**" 部分下，选择 "**允许服务主体使用 Power BI api**"。

5. 在 "**特定安全组**" 字段中，搜索**门户 Power BI Embedded 服务**组，然后选择它。

    > [!div class=mx-imgBorder]
    > ![在 Power BI 管理门户中添加安全组](../media/add-sg-powerbi.png "在 Power BI 管理门户中添加安全组")

6. 选择 "**应用**"。

定制员现在可以使用[powerbi](../liquid/portals-entity-tags.md#powerbi)液标记嵌入门户中网页上新的 Power BI 工作区 Power BI 的仪表板和报表。 若要使用 Power BI Embedded 服务，则必须将身份验证类型指定为**powerbiembedded**。 嵌入 Power BI 内容时，定制员可以使用[筛选器参数](https://docs.microsoft.com/power-bi/service-url-filters)来创建个性化视图。 详细信息： [Powerbi 液体标记](../liquid/portals-entity-tags.md#powerbi)。


### <a name="manage-the-power-bi-embedded-service"></a>管理 Power BI Embedded 服务

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2. 请参阅**设置 Power BI 集成** > **管理 Power BI Embedded 服务**。

    > [!div class=mx-imgBorder]
    > ![管理 Power BI Embedded 服务](../media/manage-powerbi-embedded-button.png "管理 Power BI Embedded 服务")

3. 在 "**管理 Power BI Embedded 服务集成**" 窗口中，删除或移动要从中将仪表板和报表显示到**所选工作区**列表的 Power BI 工作区。

    > [!div class=mx-imgBorder]
    > ![选择 Power BI 工作区](../media/manage-powerbi-embedded-window.png "选择 Power BI 工作区")
    
    > [!NOTE]
    > 从**所选工作区**列表中删除工作区后，最长可能需要1小时才能反映更改。 在此之前，数据库和报表将呈现在门户上，而不会出现任何问题。

4. 选择“保存”。

### <a name="disable-the-power-bi-embedded-service"></a>禁用 Power BI Embedded 服务

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  请参阅**设置 Power BI 集成** > **管理 Power BI Embedded 服务**。

    > [!div class=mx-imgBorder]
    > ![管理 Power BI Embedded 服务](../media/manage-powerbi-embedded-button.png "管理 Power BI Embedded 服务")

3. 在 "**管理 Power BI Embedded 服务集成**" 窗口中，选择 "**禁用 Power BI Embedded 服务集成**"。

    > [!div class=mx-imgBorder]
    > ![禁用 Power BI Embedded 服务](../media/disable-powerbi-embedded-window.png "禁用 Power BI Embedded 服务")

4. 选择“保存”。

5. 在确认消息中选择 **"确定"** 。 Power BI Embedded 服务处于禁用状态时，门户会重新启动，并在几分钟内不可用。 禁用 Power BI Embedded 服务时，将显示一条消息。

## <a name="privacy-notice"></a>隐私声明  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>另请参阅

[powerbi 液体标记](../liquid/portals-entity-tags.md#powerbi)<br> 
[在门户中将 Power BI 报表或仪表板添加到网页](add-powerbi-report.md)
