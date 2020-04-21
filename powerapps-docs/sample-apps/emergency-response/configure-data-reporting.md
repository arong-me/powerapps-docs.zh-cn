---
title: 在医院应急响应应用中配置主数据和查看仪表板 | Microsoft Docs
description: 提供有关医院 IT 管理员为其组织部署和配置示例应用的详细说明。
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/15/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 5a622a7d945fa78536c3addb75cfa64d327c7c90
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "3265393"
---
# <a name="configure-master-data-and-view-dashboards"></a>配置主数据和查看仪表板

本文提供有关如何使用管理应用（模型驱动应用）添加和管理解决方案的主数据，以及如何使用 Power BI 仪表板查看关键见解和指标的信息。

这些任务通常由您的组织中的业务管理员执行。

## <a name="configure-and-manage-master-data-for-your-organization"></a>为您的组织配置和管理主数据

使用管理应用创建和管理组织的主数据。 此数据是让医院应急响应应用运行所必需的。

> [!IMPORTANT]
> - 确保您的 IT 管理员已在您的组织中部署解决方案，并已授予业务管理员使用管理应用的适当权限。 详细信息：[部署医院应急响应应用](deploy-configure.md#deploy-the-hospital-emergency-response-app)
> 
> - 您也可以从部署包所提供的数据文件中导入数据。 详细信息：[步骤 4：加载您的组织的配置和主数据](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

您必须按以下顺序在这些实体中添加主数据：

1. [系统](#systems-data)

1. [区域](#regions-data)

1. [Facilities](#facilities-data)

1. [位置](#locations-data)

1. [部门](#departments-data)

从管理应用中左侧导航的**位置**区域管理主数据：

> [!div class="mx-imgBorder"]
> ![位置区域](media/locations-area.png)

**层次结构**区域下的实体按照您填充数据应该采取的顺序列出。

> [!NOTE]
> 视觉数据在解决方案部署期间导入。 详细信息：[步骤 4：加载您的组织的配置和主数据](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

### <a name="systems-data"></a>系统数据

通过**系统**实体，您可以创建和管理医院系统的条目。 这使您可以在同一组织中管理多个医院系统。

要创建记录：

1. 使用您的 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左侧窗格中选择**系统**，然后选择**新建**：  
    > [!div class="mx-imgBorder"]
    > ![选择-系统-新建](media/select-systems-new.png)

1. 在**新建系统**页上，指定适当的值：  
   > [!div class="mx-imgBorder"]
   > ![输入-详细信息-新建-系统](media/enter-details-new-system.png)

   | **字段**            | **说明**                                    |
   |----------------------|----------------------------------------------------|
   | 系统名称          | 键入医院的名称。                     |
   | 说明          | 键入可选说明。                      |
   | 生效日期 | 键入此医院系统的开始日期和时间。 |
   | 失效日期   | 键入此医院系统的结束日期和时间。   |

1. 选择**保存并关闭**。 新创建的记录将显示在**系统**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

### <a name="regions-data"></a>区域数据

通过**区域**实体，您可以管理医院系统的地理区域。

要创建记录：

1. 使用您的 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左侧窗格中选择**区域**，然后选择**新建**。

1. 在**新建区域**页上，指定适当的值：  

    > [!div class="mx-imgBorder"]
    > ![输入-详细信息-新建-区域](media/enter-details-new-region.png)

    | **字段**            | **说明**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | 系统               | 选择医院系统。 此列表基于您先前创建的**系统**数据填充。 |
    | 区域名称          | 键入区域名称。 例如，西雅图。                                                              |
    | 说明          | 键入可选说明。                                                                            |
    | 生效日期 | 键入此区域的开始日期和时间。                                                       |
    | 失效日期   | 键入此区域的结束日期和时间。                                                         |

1. 选择**保存并关闭**。 新创建的记录将显示在**区域**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

### <a name="facilities-data"></a>设施数据

通过**设施**实体，您可以管理每个区域中的医院位置。 例如，**西雅图**区域的**雷蒙德**和**贝尔维尤**设施。

要创建记录：

1. 使用您的 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左侧窗格中选择**设施**，然后选择**新建**。

1. 在**新建设施**页上，指定适当的值： 

    > [!div class="mx-imgBorder"] 
    > ![输入-详细信息-新建-设施](media/enter-details-new-facility.png)

    | **字段**            | **说明**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | 地区               | 选择此设施所关联的区域。 此列表基于您先前创建的**区域**数据填充。 |
    | 设施名称        | 键入设施名称。 例如，贝尔维尤。                                                  |
    | 呼吸机总数          | 键入设施中提供的呼吸机总数。                                  |
    | 说明          | 键入可选说明。                                                                   |
    | 生效日期 | 键入此设施的开始日期和时间。                                                     |
    | 失效日期   | 键入此设施的结束日期和时间。                                                       |
    |床位总数      | 自动计算。|
    |占用总数      | 自动计算。|
    |设施地址      | 键入设施的街道、市、县、省/市/自治区、邮政编码、纬度和经度。|

    如果需要，输入设施地址。

1. 选择**保存并关闭**。 新创建的记录将显示在**设施**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

### <a name="locations-data"></a>位置数据

通过**位置**实体，您可以管理每个医院设施内的特定位置。

> [!NOTE]
> 在创建**位置**记录之前，请确保您已按照前面在[步骤 4：加载您的组织的配置和主数据](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)中说明的步骤，使用 **00 - Acuities Import.xlsx** 文件导入了锐器数据。 这是因为创建**位置**记录需要用到锐器信息。

要创建记录：

1. 使用您的 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左侧窗格中选择**位置**，然后选择**新建**。

1. 在**新建位置**页上，指定适当的值：  
 
    > [!div class="mx-imgBorder"]
    > ![输入-详细信息-新建-位置](media/enter-details-new-location.png)

    | **字段**            | **说明**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | 位置名称        | 键入位置的名称。                                                                       |
    | 设施             | 选择一个设施。 此列表基于您先前创建的**设施**数据填充。 |
    | 楼层                | 键入设施的楼层信息。                                                         |
    | 单位                 | 键入设施的单元信息。                                                           |
    | 占用率 | 根据上次统计和床位总数值自动计算。                                         |
    | 锐器      | 选择与此位置关联的锐器记录。                                                                                                     |
    | 冠状病毒位置      | 选择此位置是否用于处置冠状病毒患者（**是**或**否**）。                                                                                                      |
    | 床位总数           | 键入设施中的床位总数。                                                       |
    | 加床数           | 键入设施中的加床数量。 加床数是指如果患者需要收治，可以配备的超过许可床位的床位数。                                                      |
    | 冻结床位数         | 键入设施中冻结的床位数量。                                                     |
    | 上次人数统计          | 根据创建的上一次人数统计记录填充。                                             |
    | 生效日期 | 键入此位置的开始日期和时间。                                                   |
    | 失效日期   | 键入此位置的结束日期和时间。                                                     |
    | 位置顺序       | 键入位置在位置下拉列表中所排顺序的数字。                               |
    | 替换站点标志  | 供内部使用。                                                                                     |

1. 选择**保存并关闭**。 新创建的记录将显示在**位置**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

通过打开现有位置记录并选择各自的选项卡，您可以查看某个位置的关联数据，如**统计数据**、**冠状病毒追踪**、**设备需求**。 关联数据由前线员工使用[移动应用](use.md)输入。

> [!div class="mx-imgBorder"]
> ![位置相关记录](media/location-related-records.png)


### <a name="departments-data"></a>部门数据

通过**部门**实体，您可以管理医院的部门信息。

要创建记录：

1. 使用您的 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左侧窗格中选择**部门**，然后选择**新建**。

1. 在**新建部门**页上，指定适当的值：

    > [!div class="mx-imgBorder"]
    > ![输入-详细信息-新建-部门](media/enter-details-new-department.png)

    | **字段**            | **说明**                                    |
    |----------------------|----------------------------------------------------|
    | 部门名称      | 键入部门名称。                            |
    | 说明          | 键入可选说明。                      |
    | 生效日期 | 键入此部门的开始日期和时间。 |
    | 失效日期   | 键入此部门的结束日期和时间。   |

1. 选择**保存并关闭**。 新创建的记录将显示在**部门**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

## <a name="manage-tracking-level-for-mobile-apps"></a>管理移动应用的跟踪级别

前线工作人员可以使用移动应用（画布应用）按*位置*或*设施*跟踪信息。 下面是每个移动应用的默认跟踪级别： 

|App  |默认跟踪级别  |
|--|--|
|冠状病毒追踪|位置|
|员工|位置|
|设备|位置|
|床位容量|设施|
|用品|设施|
|人员需求|设施|
|出院跟踪|设施|

作为管理员，您可以更改移动应用的默认跟踪级别。

1. 使用您的 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左侧导航中，选择**管理**区域，然后选择**应用**。 

    > [!div class="mx-imgBorder"]
    > ![配置管理应用记录](media/admin-apps.png)

1. 选择其中一个画布应用打开记录。

1. 在应用记录中，从**跟踪级别**字段中选择适当的值。

    > [!div class="mx-imgBorder"]
    > ![应用跟踪级别](media/app-tracking-level.png)

    - 如果为某个应用选择了**位置**，使用移动应用创建的记录将包含位置和设施信息以及其他数据。 此外，移动应用程序中将提供**位置**下拉列表，供用户选择位置以跟踪数据。

    - 如果为某个应用选择了**设施**，使用移动应用创建的记录仅包含设施信息以及其他数据。

    - 如果您未为**跟踪级别**字段选择任何值，前面说明的*默认*跟踪级别将应用于移动应用。

1. 选择右下角的**保存**以保存您的更改。

## <a name="view-common-data-service-dashboards"></a>查看 Common Data Service 仪表板

在医院应急响应管理（模型驱动）应用中，默认提供以下仪表板：

- **床位管理**

   跨不同设施显示床位可用情况、占有率和床位总数。

- **设备和用品**

  跨不同设施显示正在使用的关键设备和可用的用品。

- **人员管理**

  跨不同设施显示申请、分配和可用的人员数量。

- **冠状病毒患者**

  显示不同设施正在接受调查以及已发现 2019 冠状病毒病呈阳性的患者数量。

- **出院**

  显示预期出院和实际出院的患者人数。

除了默认提供的仪表板之外，您还可以创建自己的仪表板。

### <a name="manage-dashboards"></a>管理仪表板

要管理仪表板：

1. 登录 [Power Apps](https://make.powerapps.com)，浏览到您的管理应用。

2. 在左侧导航窗格中，从区域选取器中选择**仪表板**：

    > [!div class="mx-imgBorder"]
    > ![选择-仪表板](media/select-dashboards.png)

3. 在左侧导航窗格中选择仪表板名称查看图表：

    > [!div class="mx-imgBorder"]
    > ![查看-图表](media/view-charts.png)

    > [!NOTE]
    > 您可以在屏幕底部筛选数据，顶部的图表会自动更新为筛选出的值。

4. 选择**展开**选项可在全屏模式下查看图表：

    > [!div class="mx-imgBorder"]
    > ![选择-展开](media/select-expand.png)

### <a name="additional-analysis"></a>其他分析

- **向下钻取**：您可以选择图表区域来通过实体的其他属性（字段）进一步向下钻取：

    > [!div class="mx-imgBorder"]
    > ![选择-图表区域-向下钻取](media/select-chart-area-drill-down.png)

- **刷新**：您可以刷新仪表板来反映更新的数据。 您可以使用**全部刷新**刷新特定仪表板上的所有图表，也可以使用**刷新**刷新所选图表：

    > [!div class="mx-imgBorder"]
    > ![刷新-仪表板](media/refresh-dashboards.png)

- **查看记录**：选择**更多命令** (**…**)，然后选择**查看记录**查看与给定图表相关联的所有记录：

    > [!div class="mx-imgBorder"]
    > ![选择-更多-命令](media/select-more-commands.png)

    > [!NOTE] 
    > 当您选择**查看记录**时，您将看到在图表和记录之间进行拆分的实体视图。 对右侧记录的筛选器所做的任何更改都会经过自动更新反映到屏幕左侧的图表中。

有关编辑现有仪表板和更新图表属性的详细信息，请阅读[编辑现有仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard)。

### <a name="create-new-dashboards"></a>创建新仪表板

您还可以创建自己的仪表板，并进行自定义来满足您的需求。 若要创建新仪表板，请选择**新建**，然后选择 **Dynamics 365 仪表板**：

> [!div class="mx-imgBorder"]
> ![选择-新建-dynamics-仪表板](media/select-new-dynamics-dashboard.png)

有关创建新仪表板的详细信息，请阅读[创建新仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard)。

## <a name="view-power-bi-dashboard"></a>查看 Power BI 仪表板

查看 Power BI 仪表板以获取见解、制定决策。

### <a name="prerequisites"></a>先决条件

- 分配给访问报表的用户的 Power BI 高级容量或 Power BI Pro 许可证。 

- 您的 IT 管理员必须已发布 Power BI 报表，并授予您对其进行访问的权限。 详细信息：[发布 Power BI 仪表板](deploy-configure.md#publish-the-power-bi-dashboard) 

### <a name="view-the-dashboard"></a>查看仪表板

登录到 [Power BI](https://apps.powerbi.com) 访问和查看 Power BI 仪表板。

> [!div class="mx-imgBorder"]
> ![查看 Power BI 仪表板](media/view-powerbi-dashboard.png)

您可以使用右侧的筛选器来筛选冠状病毒位置、设施、区域和医院系统的数据。

#### <a name="system-at-a-glance-page"></a>系统概览页 

**系统概览页**是提供整体视图的默认页面或顶层页面。  

此页面显示以下信息的摘要视图： 

- **冠状病毒患者信息**：显示冠状病毒患者总数、发现 COVID-19 呈阳性的患者人数，以及正在接受调查的患者人数 (PUI)。

- **床位管理**：显示床位可用情况、占有率、加床数量和床位总数。 您也可以使用下面的网格以锐音符的单位查看数字。

- **人员配备信息**：显示 ICU 中患者的数量、护士的分配情况以及护士与患者的比率。  

- **患者出院信息**：显示长期住院患者总数、预计出院的患者人数和实际出院人数。

- **设备信息**：显示呼吸机总数、正在使用的呼吸机数量以及可用呼吸机。 

- **用品信息**：按天显示现有的用品数量。

> [!NOTE]
> - 在任何一个汇总区域选择标题将会带您进入该区域的相应详细信息页面。 
> - 您还可以对报表执行其他操作，如筛选和排序数据、将报表导出到 PDF 和 PowerPoint、添加聚焦等。 有关 Power BI 中的报表功能的详细信息，请参阅 [Power BI 中的报表](https://docs.microsoft.com/power-bi/consumer/end-user-reports)
> - 其中的某些报表的最新或上次更新列显示上次刷新数据的日期和时间。 通过查看以下列中的日期和时间值的颜色，可以轻松识别数据的新旧：
>    - 黑色：数据刷新不超过 20 小时
>    - 灰色：数据在 20 - 24 小时以前刷新
>    - 红色：数据刷新超过 24 小时 
 
#### <a name="system-view-page"></a>系统视图页面

**系统视图**页显示包含以下医院系统信息的图表：
- 正在使用的呼吸机和可用呼吸机
- 床位和急症护理床位可用情况和占用率
- 请求的人员总数、患者（统计）人数和护士与患者比率
- 一段时间内的现有用品

> [!div class="mx-imgBorder"]
> ![系统视图](media/report-system-view.png)

#### <a name="location-details-page"></a>位置详细信息页 

在**系统概览**页上，选择右上角的 **i**。 **位置详细信息**页面按位置显示数据，如床位总数、可用床位数、加床数量、冠状病毒患者等。 

> [!div class="mx-imgBorder"]
> ![位置详细信息](media/report-location-details.png) 

#### <a name="covid-patients-page"></a>冠状病毒患者页 

此页提供有关冠状病毒患者的向下钻取信息，如每个位置的患者，显示正在接受调查的患者 (PUI) 人数的峰值和谷值的随时间推移的患者趋势，以及发现阳性的患者人数，并可以了解患者位于医院内的哪个位置。

> [!div class="mx-imgBorder"]
> ![冠状病毒患者详细信息](media/report-covid-details.png)

#### <a name="bed-management-page"></a>床位管理页 

此页面按位置提供向下钻取信息，如可用床位总数、可用的急诊床位和占用率。

> [!div class="mx-imgBorder"]
> ![床位管理](media/report-bed-details.png)

#### <a name="staffing-details-page"></a>人员配备详细信息页  

此页面提供按位置显示的人员、分配的护士人数、患者总数和冠状病毒患者人数的详细信息。 另外还会显示一段时间内护士与患者的比例和 ICU 护士与患者的比例。

> [!div class="mx-imgBorder"]
> ![人员详细信息](media/report-staff-details.png)

#### <a name="equipment-page"></a>设备页 

此页面按位置、正在使用的呼吸机总数、被冠状病毒患者人数覆盖的情况，以及设备的其他部件，如正在使用的呼吸器带、充电器和面罩。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-equipment-details.png)

#### <a name="discharges-page"></a>出院页 

此页面提供有关长期患者、一段时间内的出院障碍以及实际和预期出院的差异的详细信息。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-discharge-details.png)

#### <a name="supplies-page"></a>用品页 

此页面按位置提供有关用品的详细信息。 另外还按用品和设施提供库存持有天数的图表，以及一段时间内现有的可用用品。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-supplies.png)

## <a name="view-and-manage-app-feedback"></a>查看和管理应用反馈

在移动设备上使用画布应用的前线人员提供的所有反馈都存储在**应用反馈**实体中，管理员可以使用管理应用中左侧导航窗格的**管理**区域查看和管理这些反馈。

若要查看和管理应用反馈：

1. 登录 [Power Apps](https://make.powerapps.com)，浏览到您的管理应用。

2. 在左侧导航窗格中，从区域选取器中选择**管理**。

3. 选择**应用反馈**查看用户提交的应用反馈列表。 您可以单击一条记录来查看详细信息，并标记是否审阅。  

    > [!div class="mx-imgBorder"]
    > ![选择-应用反馈](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>问题和反馈

- 若要报告有关医院应急响应示例应用的问题，请访问 <https://aka.ms/emergency-response-issues>。

- 有关医院应急响应示例应用的反馈，请访问 <https://aka.ms/emergency-response-feedback>。

## <a name="next-step"></a>下一步

[使用医院应急响应移动应用](use.md)
