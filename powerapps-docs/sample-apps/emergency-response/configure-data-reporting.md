---
title: 在“医院应急响应”应用中配置主数据并查看仪表板 | Microsoft Docs
description: 详细介绍医院 IT 管理员如何为组织部署和配置示例应用。
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
ms.locfileid: "81448264"
---
# <a name="configure-master-data-and-view-dashboards"></a>配置主数据并查看仪表板

本文介绍了如何使用管理应用（模型驱动应用）来添加和管理解决方案的主数据，并使用 Power BI 仪表板查看主要见解和指标。

这些任务通常由组织中的业务管理员执行。

## <a name="configure-and-manage-master-data-for-your-organization"></a>为组织配置和管理主数据

使用管理应用为组织创建和管理主数据。 此数据是“医院应急响应”应用正常运行所需的。

> [!IMPORTANT]
> - 确保 IT 管理员已在组织中部署了解决方案，并为业务管理员授予了相应的权限来使用管理应用。 更多信息：[部署“医院应急响应”应用](deploy-configure.md#deploy-the-hospital-emergency-response-app)
> 
> - 还可以从部署包中提供的数据文件导入数据。 更多信息：[步骤 4：为组织加载配置和主数据](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

必须按以下顺序将主数据添加到下面的实体中：

1. [系统](#systems-data)

1. [区域](#regions-data)

1. [机构](#facilities-data)

1. [位置](#locations-data)

1. [科室](#departments-data)

从管理应用左侧导航的“位置”  区域中管理主数据：

> [!div class="mx-imgBorder"]
> ![locations-area](media/locations-area.png)

“层次结构”  区域下的各实体按应填充数据的顺序列出。

> [!NOTE]
> 在部署解决方案的过程中，会导入视敏度数据。 更多信息：[步骤 4：为组织加载配置和主数据](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)

### <a name="systems-data"></a>系统数据

使用“系统”  实体可以创建和管理医院系统的条目。 这样就可以管理同一组织内的多个医院系统。

创建记录的步骤如下：

1. 使用 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左窗格中选择“系统”  ，然后选择“新建”  ：  
    > [!div class="mx-imgBorder"]
    > ![select-systems-new](media/select-systems-new.png)

1. 在“新建系统”  页中，指定适当的值：  
   > [!div class="mx-imgBorder"]
   > ![enter-details-new-system](media/enter-details-new-system.png)

   | **字段**            | **说明**                                    |
   |----------------------|----------------------------------------------------|
   | 系统名称          | 键入医院的名称。                     |
   | 说明          | 键入可选说明。                      |
   | 生效开始日期 | 键入此医院系统的开始日期和时间。 |
   | 生效结束日期   | 键入此医院系统的结束日期和时间。   |

1. 选择“保存并关闭”。  新创建的记录将显示在“系统”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

### <a name="regions-data"></a>区域数据

使用“区域”  实体可以管理医院系统的地理区域。

创建记录的步骤如下：

1. 使用 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左窗格中选择“区域”  ，然后选择“新建”  ：

1. 在“新建区域”  页中，指定适当的值：  

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-region](media/enter-details-new-region.png)

    | **字段**            | **说明**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | 系统               | 选择一个医院系统。 此列表是根据之前创建的“系统”数据  填充的。 |
    | 区域名称          | 键入区域名称。 例如，“西雅图”。                                                              |
    | 说明          | 键入可选说明。                                                                            |
    | 生效开始日期 | 键入此区域的开始日期和时间。                                                       |
    | 生效结束日期   | 键入此区域的结束日期和时间。                                                         |

1. 选择“保存并关闭”。  新创建的记录将显示在“区域”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

### <a name="facilities-data"></a>机构数据

使用“机构”  实体可以管理每个区域中的医院位置。 例如，“西雅图”区域内的“雷德蒙德”和“贝尔维尤”的机构    。

创建记录的步骤如下：

1. 使用 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左窗格中选择“机构”  ，然后选择“新建”  。

1. 在“新建机构”  页中，指定适当的值： 

    > [!div class="mx-imgBorder"] 
    > ![enter-details-new-facility](media/enter-details-new-facility.png)

    | **字段**            | **说明**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | 区域               | 选择与此机构关联的区域。 此列表是根据之前创建的“区域”数据  填充的。 |
    | 机构名称        | 键入机构名称。 例如，“贝尔维尤”。                                                  |
    | 呼吸机总数          | 键入机构可用的呼吸机总数。                                  |
    | 说明          | 键入可选说明。                                                                   |
    | 生效开始日期 | 键入此机构的开始日期和时间。                                                     |
    | 生效结束日期   | 键入此机构的结束日期和时间。                                                       |
    |总床位数      | 自动计算。|
    |已占用总数      | 自动计算。|
    |机构地址      | 键入机构的街道、城市、县、省/市/自治区、邮政编码、纬度和经度。|

    如果需要，请输入机构地址。

1. 选择“保存并关闭”。  新创建的记录将显示在“机构”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

### <a name="locations-data"></a>位置数据

使用“位置”  实体可以管理每个医院机构的特定位置。

> [!NOTE]
> 在创建“位置”  记录之前，请确保已使用“00 - Acuities Import.xlsx”  文件导入视敏度数据（前面的[步骤 4：为组织加载配置和主数据](deploy-configure.md#step-4-load-configuration-and-master-data-for-your-organization)中说明的步骤）。 这是因为创建“位置”  记录需要视敏度信息。

创建记录的步骤如下：

1. 使用 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左窗格中选择“位置”  ，然后选择“新建”  。

1. 在“新建位置”  页中，指定适当的值：  
 
    > [!div class="mx-imgBorder"]
    > ![enter-details-new-location](media/enter-details-new-location.png)

    | **字段**            | **说明**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | 位置名称        | 键入位置的名称。                                                                       |
    | 设施             | 选择机构。 此列表是根据之前创建的“机构”数据  填充的。 |
    | 层                | 键入机构的楼层信息。                                                         |
    | 单位                 | 键入机构的单位信息。                                                           |
    | 占用率 | 基于上次统计数量和床位总数自动计算。                                         |
    | 急症      | 选择与此位置关联的视敏度记录。                                                                                                     |
    | COVID 位置      | 选择是否将此位置用于治疗 COVID 患者（“是”  或“否”  ）。                                                                                                      |
    | 总床位数           | 键入机构中的床位总数。                                                       |
    | 波动床位           | 键入机构中的波动床位数。 波动床位是指超出许可的床位容量时提供的床位（如果患者需要住院的话）。                                                      |
    | 阻止的床位数         | 键入机构中已阻止的床位数。                                                     |
    | 上次统计数量          | 根据创建的上次统计记录进行填充。                                             |
    | 生效开始日期 | 键入此位置的开始日期和时间。                                                   |
    | 生效结束日期   | 键入此位置的结束日期和时间。                                                     |
    | 位置顺序       | 键入一个数字，用于对位置下拉列表中的位置进行排序。                               |
    | 备用场地标志  | 供内部使用。                                                                                     |

1. 选择“保存并关闭”。  新创建的记录将显示在“位置”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

通过打开现有位置记录并选择相应的选项卡，可以查看该位置的关联数据，如“统计数量”  、“COVID 追踪”  和“设备需要”  。 相关数据由一线员工使用[移动应用](use.md)输入。

> [!div class="mx-imgBorder"]
> ![与位置相关的记录](media/location-related-records.png)


### <a name="departments-data"></a>科室数据

使用“科室”  实体可以管理医院的科室信息。

创建记录的步骤如下：

1. 使用 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左窗格中选择“科室”  ，然后选择“新建”  。

1. 在“新建科室”  页中，指定适当的值：

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-department](media/enter-details-new-department.png)

    | **字段**            | **说明**                                    |
    |----------------------|----------------------------------------------------|
    | Department Name      | 键入科室名称。                            |
    | 说明          | 键入可选说明。                      |
    | 生效开始日期 | 键入此科室的开始日期和时间。 |
    | 生效结束日期   | 键入此科室的结束日期和时间。   |

1. 选择“保存并关闭”。  新创建的记录将显示在“科室”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

## <a name="manage-tracking-level-for-mobile-apps"></a>管理移动应用的跟踪级别

一线工作人员可以使用移动应用（画布应用），根据“位置”  或“机构”  来跟踪信息。 下面是每个移动应用的默认跟踪级别： 

|应用  |默认跟踪级别  |
|--|--|
|COVID 追踪|位置|
|人员|位置|
|设备|位置|
|床位容量|设施|
|供应|设施|
|人员配备需求|设施|
|出院跟踪|设施|

作为管理员，你可以更改移动应用的默认跟踪级别。

1. 使用 IT 管理员提供的 URL 登录管理应用（模型驱动应用）。

1. 在左侧导航窗格中，选择“管理”  区域，然后选择“应用”  。 

    > [!div class="mx-imgBorder"]
    > ![配置管理应用记录](media/admin-apps.png)

1. 选择其中一个画布应用以打开记录。

1. 在应用记录中，在“跟踪级别”  字段中选择合适的值。

    > [!div class="mx-imgBorder"]
    > ![应用跟踪级别](media/app-tracking-level.png)

    - 如果为应用选择“位置”  ，则使用移动应用创建的记录将包含位置和机构信息及其他数据。 此外，用户可以在移动应用中使用“位置”  下拉列表，以便选择要跟踪数据的位置。

    - 如果为应用选择“机构”  ，则使用移动应用创建的记录将仅包含机构信息及其他数据。

    - 如果未选择“跟踪级别”  字段的任何值，则前面所述的默认  跟踪级别将应用于移动应用。

1. 选择右下角的“保存”以保存更改  。

## <a name="view-common-data-service-dashboards"></a>查看 Common Data Service 仪表板

默认情况下，“医院应急响应”管理（模型驱动）应用中提供以下仪表板：

- **床位管理**

   显示各机构可用的床位、占用率以及床位总数。

- **设备和供应**

  显示正在使用中的关键设备，以及不同机构中的供应情况。

- **员工管理**

  显示在不同机构中请求、分配和可用的员工数。

- **COVID 患者**

  显示不同机构中接受检测并且 COVID-19 呈阳性的患者数量。

- **出院**

  显示预计出院患者数量和实际出院数量。

除了默认提供的仪表板外，还可以创建自己的仪表板。

### <a name="manage-dashboards"></a>管理仪表板

管理仪表板的步骤如下：

1. 登录到 [Power Apps](https://make.powerapps.com) 并浏览到管理应用。

2. 在左侧导航窗格中，从区域选取器中选择“仪表板”  ：

    > [!div class="mx-imgBorder"]
    > ![select-dashboards](media/select-dashboards.png)

3. 选择左侧导航栏中的仪表板名称以查看图表：

    > [!div class="mx-imgBorder"]
    > ![view-charts](media/view-charts.png)

    > [!NOTE]
    > 可以在屏幕底部筛选数据，并使用筛选后的值自动更新顶部的图表。

4. 选择“展开”  选项，以全屏模式查看图表：

    > [!div class="mx-imgBorder"]
    > ![select-expand](media/select-expand.png)

### <a name="additional-analysis"></a>其他分析

- **向下钻取**：可以选择图表区域以进一步细化实体的其他属性（字段）：

    > [!div class="mx-imgBorder"]
    > ![select-chart-area-drill-down](media/select-chart-area-drill-down.png)

- **刷新**：可以刷新仪表板来反映更新后的数据。 可以单击“全部刷新”刷新特定仪表板上的所有图表，  ，也可以单击“刷新”来刷新  选定的图表：

    > [!div class="mx-imgBorder"]
    > ![refresh-dashboards](media/refresh-dashboards.png)

- **查看记录**：选择“更多命令(…  )”  ，然后选择“查看记录”  查看与给定图表相关联的所有记录：

    > [!div class="mx-imgBorder"]
    > ![select-more-commands](media/select-more-commands.png)

    > [!NOTE] 
    > 选择“查看记录”  时，你将看到图表和记录之间的实体拆分视图。 在右侧对记录的筛选器所做的任何更改都会通过自动更新反映到屏幕左侧的图表中。

若要详细了解如何编辑现有仪表板和更新图表的属性，请阅读[编辑现有仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard)。

### <a name="create-new-dashboards"></a>创建新仪表板

还可以创建自己的仪表板，并对其进行自定义以适应你的需求。 要创建新仪表板，请选择“新建”，然后选择“Dynamics 365 仪表板”   ：

> [!div class="mx-imgBorder"]
> ![select-new-dynamics-dashboard](media/select-new-dynamics-dashboard.png)

有关创建新仪表板的详细信息，请阅读[创建新仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard)。

## <a name="view-power-bi-dashboard"></a>查看 Power BI 仪表板

查看 Power BI 仪表板以获取见解并做出决策。

### <a name="prerequisites"></a>先决条件

- 已为访问报表的用户分配 Power BI Premium 容量或 Power BI Pro 许可证。 

- IT 管理员必须已发布 Power BI 报表，并授予你访问报表的权限。 更多信息：[发布 Power BI 仪表板](deploy-configure.md#publish-the-power-bi-dashboard) 

### <a name="view-the-dashboard"></a>查看仪表板

登录 [Power BI](https://apps.powerbi.com) 即可访问和查看 Power BI 仪表板。

> [!div class="mx-imgBorder"]
> ![查看 Power BI 仪表板](media/view-powerbi-dashboard.png)

可以使用右侧的筛选器来筛选 COVID 位置、机构、区域和医院系统的数据。

#### <a name="system-at-a-glance-page"></a>“系统概览”页 

“系统概览”页  是提供概述的默认页或顶级页。  

此页显示以下内容的汇总视图： 

- COVID 患者信息  ：显示 COVID 患者总数、COVID-19 检测呈阳性患者数以及疑似患者数 (PUI)。

- **床位管理**：显示可用床位数、占用率、波动床位数以及床位总数。 还可以使用下面的网格按急症单位查看数字。

- 人员配备信息  ：显示 ICU 中的患者数、已分配的护士数，以及护士与患者的比例。  

- 患者出院信息  ：显示长期住院患者总数、预计出院患者数和实际出院患者数。

- 设备信息  ：显示呼吸机总数、正在使用中的呼吸机数和可用呼吸机数。 

- 供应品信息  ：按天显示现有供应品数。

> [!NOTE]
> - 选择任何汇总区域中的标题会转到区域的相应详细信息页。 
> - 还可以对报表执行其他操作，如对数据进行筛选和排序、将报表导出为 PDF 和 PowerPoint、添加聚焦等。 若要详细了解 Power BI 中的报表功能，请参阅 [Power BI 中的报表](https://docs.microsoft.com/power-bi/consumer/end-user-reports)
> - 其中一些报表的最新或上次更新列显示数据上次刷新日期和时间。 通过查看这些列中的日期和时间值的颜色，也很容易识别新鲜度：
>    - 黑色：数据在不到 20 小时前刷新
>    - 灰色：数据在 20-24 小时前刷新
>    - 红色：数据在超过 24 小时前刷新 
 
#### <a name="system-view-page"></a>“系统视图”页

“系统视图”  页显示包含以下医院系统信息的图表：
- 正在使用中的呼吸机数和可用呼吸机数
- 可用床位数、急症护理床位数以及占用率
- 请求获取的员工总数、患者数（统计数字）以及护士与患者的比例
- 在一段时间内的先用供应品数

> [!div class="mx-imgBorder"]
> ![系统视图](media/report-system-view.png)

#### <a name="location-details-page"></a>“位置详细信息”页 

从“系统概览”  页中，选择右上角的“i”  。 “位置详细信息”  页显示按位置划分的数据，如床位总数、可用床位数、波动床位数、COVID 患者数等。 

> [!div class="mx-imgBorder"]
> ![位置详细信息](media/report-location-details.png) 

#### <a name="covid-patients-page"></a>“COVID 患者”页 

此页提供了关于 COVID 患者的向下钻取信息，如每个位置的患者数、一段时间内的患者数趋势（显示疑似患者 (PUI) 数和检测呈阳性的患者数的波峰和波谷），以及患者在医院中的位置。

> [!div class="mx-imgBorder"]
> ![COVID 患者详细信息](media/report-covid-details.png)

#### <a name="bed-management-page"></a>“床位管理”页 

此页提供了按位置划分的向下钻取信息，如可用床位总数、急症护理床位数以及占用率。

> [!div class="mx-imgBorder"]
> ![床位管理](media/report-bed-details.png)

#### <a name="staffing-details-page"></a>“人员配备详细信息”页  

此页提供了按位置划分的员工详细信息，如已分配的护士数、患者总数和 COVID 患者数。 它还显示一段时间内的护士与患者的比例和 ICU 护士与患者的比例。

> [!div class="mx-imgBorder"]
> ![员工详细信息](media/report-staff-details.png)

#### <a name="equipment-page"></a>“设备”页 

此页提供了按位置划分的设备详细信息，如正在使用中的呼吸机总数、COVID 患者数，以及正在使用中的其他设备数（如皮带、充电器和风帽）。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-equipment-details.png)

#### <a name="discharges-page"></a>“出院”页 

此页提供了以下详细信息：长期住院患者数、一段时间内的出院障碍数，以及实际出院数和预计出院数之间的差异。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-discharge-details.png)

#### <a name="supplies-page"></a>“供应品”页 

此页提供了按位置划分的供应品详细信息。 它还提供了一个图表，其中按天显示现有供应品和设施，以及一段时间内可用的现有供应品。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-supplies.png)

## <a name="view-and-manage-app-feedback"></a>查看和管理应用反馈

一线员工在其移动设备上使用画布应用提供的所有反馈都存储在“应用反馈”  实体中，管理员可以使用管理应用左侧导航窗格中的“管理”  区域来查看和管理反馈。

要查看和管理应用反馈，请执行以下操作：

1. 登录到 [Power Apps](https://make.powerapps.com) 并浏览到管理应用。

2. 在左侧导航窗格中，从区域选取器中选择“管理”  。

3. 选择“应用反馈”  以查看用户提交的应用反馈的列表。 可以单击一条记录以查看详细信息，并可以选择是否将其标记为“已查看”。  

    > [!div class="mx-imgBorder"]
    > ![select-app-feedback](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>问题和反馈

- 若要报告“医院应急响应”示例应用存在的问题，请访问 <https://aka.ms/emergency-response-issues>。

- 若要提供关于“医院应急响应”示例应用的反馈，请访问 <https://aka.ms/emergency-response-feedback>。

## <a name="next-step"></a>下一步

[使用“医院应急响应”移动应用](use.md)
