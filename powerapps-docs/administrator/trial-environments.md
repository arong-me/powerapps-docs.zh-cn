---
title: 试用环境 | Microsoft Docs
description: 通过 PowerApps 预览版程序提前获得功能
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 01/09/2019
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: bd05c4c1251058d464034de71d9b1c287e714190
ms.sourcegitcommit: 170deba334c922157bbb826c795bed3fa858b85e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2019
ms.locfileid: "54196068"
---
# <a name="about-trial-environments"></a>关于试用环境

目前可创建两种面向应用程序的 Common Data Service (CDS) 环境：试用或生成环境。 试用环境对于免费试用 Dynamics 365 for Customer Engagement 应用非常有用。 试用环境在 30 天后过期。

打开“环境”页面，查看你拥有的环境类型以及试用环境即将到期的日期：

> [!div class="mx-imgBorder"] 
> ![PowerApps 环境](media/powerapps-environments75b.png "PowerApps environments")

## <a name="convert-a-trial-environment-to-production"></a>将试用环境转换为生产环境

使用试用环境时，如果希望将所创建的资源保留超过 30 天，请将试用环境转换为生产环境。

必须满足以下条件才能转换为生产环境：

**具有合适的 PowerApps 计划**。 一种使你能够创建生产环境的计划，例如，PowerApps 计划 2。 有关包含生产环境的 PowerApps 计划的信息，请参阅[为团队选择适合的计划](https://powerapps.microsoft.com/pricing/)。 请参阅[如何确定计划](#how-do-i-identify-my-plans)以确定你的 PowerApps 计划。
**具有可用的生产配额**。 可以使用计划创建固定数量的生产环境。 例如，使用 PowerApps 计划 2，可以创建两个生产环境。 如果已经创建了两个生产环境，则只能在删除一个现有环境之后才能再进行创建。 有关详细信息，请参阅[创建环境](environments-overview.md#creating-an-environment)。

请按照以下步骤将试用环境转换为生产环境：

1. 转到 [https://admin.powerapps.com/environments](https://admin.powerapps.com/environments)，并以管理员身份登录。
 
2. 打开“环境”页，然后选择你想要转换到生产环境的试用环境：

    > [!div class="mx-imgBorder"] 
    > ![选择试用环境](media/powerapps-environments75b-select-trial.png "Select trial environment")

3. 在“详细信息”标签上，选择“转换”：

    > [!div class="mx-imgBorder"] 
    > ![选择转换](media/powerapps-trial-select-convert.png "Select Convert")

4. 选择“确认”：

    > [!div class="mx-imgBorder"] 
    > ![选择确认](media/powerapps-trial-select-confirm.png "Select Confirm")

如果你的环境有一个数据库，则转换为生产环境可能需要几个小时。 可以通过“详细信息”标签上的通知来监控进度：

  > [!div class="mx-imgBorder"] 
  > ![转换开始时间](media/powerapps-trial-conversion-started.png "Conversion started")

## <a name="frequently-asked-questions"></a>常见问题

### <a name="who-can-convert-a-trial-environment-to-a-production-environment"></a>谁可以将试用环境转换为生产环境？

需要满足以下条件才能将试用环境转换为生产环境：

**具有合适的 PowerApps 计划**。 需要一种使你能够创建生产环境的计划，例如，PowerApps 计划 2。 有关包含生产环境的 PowerApps 计划的信息，请参阅[为团队选择适合的计划](https://powerapps.microsoft.com/pricing/)。 请参阅[如何确定计划](#how-do-i-identify-my-plans)以确定你的 PowerApps 计划。
**具有可用的生产配额**。 可以使用计划创建固定数量的生产环境。 例如，使用 PowerApps 计划 2，可以创建两个生产环境。 如果已经创建了两个生产环境，则只能在删除一个现有环境之后才能再进行创建。

### <a name="what-if-i-dont-have-available-quota-for-production-environments"></a>如果没有生产环境的可用配额怎么办？

请与 Office 365 全局管理员或 Azure Active Directory (Azure AD) 租户管理员联系，以便：
- 将 PowerApps 计划 2 分配给你。 
- 找到具有可用生产环境配额的其他用户。

还可以购买 PowerApps 计划。

### <a name="can-every-office-365-global-admin-or-azure-ad-tenant-admin-convert-a-trial-environment-to-a-production-environment"></a>每个 Office 365 全局管理员或 Azure AD 租户管理员都可以将试用环境转换为生产环境吗？

不。 全局管理员和 Azure AD 租户管理员需要具有生产环境的可用配额才能将试用环境转换为生产环境。

### <a name="is-there-a-way-to-recover-a-deleted-trial-environment"></a>有没有办法恢复已删除的试用环境？

我们无法保证恢复已删除的试用环境，但我们会尽力在删除后的 7 天内恢复它。 我们无法恢复环境的数据库，但可以恢复应用（使用 PowerApps 创建）和流。

### <a name="how-can-i-retain-my-data-and-resources-if-i-dont-have-a-way-to-convert-the-trial-environment-to-a-production-environment"></a>如果我无法将试用环境转换为生产环境，如何保留数据和资源？

可以将你的资源和数据导出到其他环境。 如果想要将其保留更长时间，建议创建生产环境或单个环境（使用 PowerApps 社区计划）并将资源导出到该环境。 

以下是一些导出资源的指南。

|环境中的资源类型  |如何将其导出？  |
|---------|---------|
|应用（画布和模型驱动）和流     |可以使用[打包](environment-and-tenant-migration.md)从其中一个环境导出应用和流。         |
|数据库中的数据（面向应用程序的 Common Data Service (CDS) 环境）     |可以使用多个选项：<br/><ul><li>[导出到 Excel](../user/export-data-excel.md) 并保存数据。 可以[将数据导入](../user/import-data.md)到另一个环境。</li><br/><li>可以使用 [Data Integrator 服务](data-integrator.md)和 API 将数据导出到另一个环境中。</li></ul> |

我们将删除环境数据库中 30 天内没有任何活动的试用环境。

### <a name="how-can-i-create-a-production-or-an-individual-environment"></a>如何创建生产或个人环境？

需要具有提供生产环境创建的 PowerApps 计划。 有关详细信息，请参阅[创建环境](environments-overview.md#creating-an-environment)。

可以通过注册 [PowerApps 社区计划](https://powerapps.microsoft.com/communityplan/)来创建个人环境。 请注意，在个人环境中共享应用存在限制 - 这些环境仅供个人使用。

### <a name="how-do-i-identify-my-plans"></a>如何确定我的计划？

要确定你的计划，请选择 PowerApps 站点右上角的齿轮图标，然后选择“计划”。

> [!div class="mx-imgBorder"] 
> ![选择计划](media/powerapps-plans.png "Select Plans")

### <a name="see-also"></a>另请参阅
[管理 PowerApps 中的环境](environments-administration.md)<br/>
[环境概述](environments-overview.md)<br/>
[为团队选择适合的计划](https://powerapps.microsoft.com/pricing/)<br/>
[许可概述](pricing-billing-skus.md)<br/>
