---
title: 将数据集成到 Common Data Service for Apps
description: 将来自多个源的数据集成到 Common Data Service for Apps
author: sabinn-msft
ms.service: powerapps
ms.topic: how-to
ms.component: cds
ms.date: 09/19/2018
ms.author: sabinn
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: b8cebc6f9db8a1a7c1a060aad461f4f32fcee05b
ms.sourcegitcommit: 2bcf40aeaa35420dc43f5803f4e57ff0f6afb57b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46468971"
---
# <a name="integrate-data-into-common-data-service-for-apps"></a>将数据集成到 Common Data Service for Apps

<!--note from editor: the style guide says not to use "the" in front of Common Data Service for Apps, so I'm removing that.-->

数据集成器（面向管理员）是用于将数据集成到 Common Data Service for Apps 的点到点集成服务。 它支持将来自多个源（例如，Dynamics 365 for Finance and Operations、Dynamics 365 for Sales and SalesForce (预览版)、SQL (预览版)）的数据集成到 Common Data Service for Apps。 它也支持将数据集成到 Dynamics 365 for Finance and Operations 和 Dynamics 365 for Sales。 自 2017 年 7 月以来，此服务已公开发布。  

我们开始使用第一方应用，例如，Dynamics 365 for Finance and Operations 和 Dynamics 365 for Sales。 借助 Power Query 或基于 M 的连接器，我们现在能够支持其他源，如 SalesForce（预览版）和 SQL（预览版），并且将在不久的将来扩展到 20 个以上的源。 

> [!div class="mx-imgBorder"]
> ![数据源到目标](media/data-integrator/DataIntegratorP2P-new.PNG "数据源到目标")

## <a name="how-can-you-use-the-data-integrator-for-your-business"></a>如何将数据集成器用于你的业务？

数据集成器（面向管理员）还支持基于过程的集成方案，如“从目标客户到现金”提供 Dynamics 365 for Finance and Operations 和 Dynamics 365 for Sales 之间的直接同步。 提供“数据集成”功能的“从目标客户到现金”模板启用 Finance and Operations 和 Sales 之间的帐户、联系人、产品、销售报价、销售订单和销售发票的数据流。 当数据在 Finance and Operations 和 Sales 之间流动时，你可以在 Sales 中执行销售和市场营销活动，并可以使用 Finance and Operations 中的库存管理处理订单履行。 

> [!div class="mx-imgBorder"]
> ![从目标客户到现金](media/data-integrator/ProspectToCash631.png "从目标客户到现金")

“从目标客户到现金”集成可让销售人员凭借 Dynamics 365 for Sales 的优势处理并监视其销售过程，同时使用 Finance and Operations 中的丰富功能完成履行和开票的各个方面。 借助 Microsoft Dynamics 365“从目标客户到现金”集成，可以获得两个系统结合起来的能力。 

请观看视频：[“从目标客户到现金”集成](https://www.youtube.com/watch?v=AVV9x5x-XCg)

有关“从目标客户到现金”集成的详细信息，请参阅有关[从目标客户到现金解决方案](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/prospect-to-cash)的文档。

我们还支持到 Dynamics 365 for Finance and Operations 的 [Field Service 集成](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/sales-marketing/field-service-work-order)和 [PSA (Project Service Automation) 集成](https://docs.microsoft.com/dynamics365/unified-operations/financials/project-management/psa-integration?toc=/fin-and-ops/toc.json)。

## <a name="data-integrator-platform"></a>数据集成器平台

数据集成器（面向管理员）包含数据集成平台、由应用程序团队（例如，Dynamics 365 for Finance and Operations 和 Dynamics 365 for Sales）提供的现成模板以及由客户和合作伙伴创建的自定义模板。 我们已构建可跨各种源扩展的应用程序不可知的平台。 在最核心的部分中，创建连接（到集成端点），选择具有预定义映射的可自定义模板之一（可以进一步自定义），创建并执行数据集成项目。  

集成模板充当具有预定义实体和字段映射的蓝图，以便启用从源到目标的数据流。 它还能够在导入数据之前对其进行转换。 在大多数情况下，源和目标应用之间的架构可能截然不同，并且具有预定义实体和字段映射的模板充当集成项目的良好开端。  

> [!div class="mx-imgBorder"]
> ![数据集成平台](media/data-integrator/DIPlatform.PNG "数据集成平台")

## <a name="how-to-set-up-a-data-integration-project"></a>如何设置数据集成项目

有以下三个主要步骤：

1. 创建连接（提供数据源的凭据）。

2. 创建连接集（标识上一步中创建的连接的环境）。

3. 使用模板创建数据集成项目（为一个或多个实体创建或使用预定义的映射）。

创建集成项目后，可以选择手动运行该项目，也可以为未来设置基于计划的刷新。 本文的其余部分详细介绍了这三个步骤。

### <a name="how-to-create-a-connection"></a>如何创建连接

在可以创建数据集成项目之前，必须为计划在 Microsoft PowerApps 门户中使用的每个系统预配连接。 将这些连接视为集成点。

**创建连接**

1. 转到 [PowerApps 管理中心](https://admin.powerapps.com)。

2. 在“数据”下，选择“连接”，然后选择“新建连接”。

3. 可以从连接列表中选择连接，也可以搜索连接。

    > [!div class="mx-imgBorder"] 
    > ![创建连接](media/data-integrator/CreateConnection780.png "创建连接")

4. 选择连接后，选择“创建”。 然后，系统将提示你提供凭据。

5. 提供凭据后，将在你的连接下列出连接。

    > [!div class="mx-imgBorder"] 
    > ![连接列表](media/data-integrator/CreateConnection1780.png "连接列表")

### <a name="how-to-create-a-connection-set"></a>如何创建连接集

连接集是两个连接、连接的环境、组织映射信息以及可在项目之间重复使用的集成密钥的集合。 可以先使用一个用于开发的连接集，然后再切换到另一个用于生产的连接集。 与连接集存储在一起的一个重要信息是组织单位映射，例如，Finance and Operations 法人（或公司）与 Dynamics 365 for Sales 组织或业务部门之间的映射。 可以将多个组织映射存储在连接集中。

**创建连接集**

1. 转到 [PowerApps 管理中心](https://admin.powerapps.com)。

2. 在左侧导航窗格中选择“数据集成”选项卡。

3. 选择“连接集”选项卡，然后选择“新建连接集”。

4. 提供连接集的名称。
  
    > [!div class="mx-imgBorder"] 
    > ![创建连接集](media/data-integrator/CreateConnectionSet1780.png "创建连接集")
  
5. 选择之前创建的连接并选择适当的环境。

6. 选择下一个连接并重复上述步骤（将这些连接视为不按特定顺序排列的源和目标）。

7. 指定组织到业务部门的映射（如果在 Finance and Operations 和 Sales 系统之间集成）。
  
    > [!NOTE]
    > 可以为每个连接集指定多个映射。
  
8. 填写所有字段后，选择“创建”。

9. 将在“连接集列表”页下显示刚创建的新连接集。
    
    > [!div class="mx-imgBorder"] 
    > ![连接集列表](media/data-integrator/CreateConnectionSet2780.png "连接集列表")

连接集已准备好跨各种集成项目使用。

### <a name="how-to-create-a-data-integration-project"></a>如何创建数据集成项目

项目启用系统之间的数据流。 项目包含一个或多个实体的映射。 映射指示哪些字段映射到哪些其他字段。

**创建数据集成项目**

1. 转到 [PowerApps 管理中心](https://admin.powerapps.com)。

2. 在左侧导航窗格中选择“数据集成”选项卡。

3. 在“项目”选项卡中，选择右上角的“新建项目”。

    > [!div class="mx-imgBorder"] 
    > ![创建项目](media/data-integrator/CreateNewProject780.png "创建项目")

4. 提供集成项目的名称。

5. 选择其中一个可用模板（或[创建你自己的模板](#how-to-customize-or-create-your-own-template)）。 在这种情况下，我们会将产品实体从 Finance and Operations 移动到 Sales。

    > [!div class="mx-imgBorder"] 
    > ![选择模板以创建新项目](media/data-integrator/CreateNewProjectSelectTemplate780.png "选择模板以创建新项目")

6. 选择“下一步”，然后选择之前创建的连接集（或[创建新连接集](#how-to-create-a-connection-set)）。

7. 通过确认连接和环境名称来确保已选择正确的连接集。

    > [!div class="mx-imgBorder"] 
    > ![创建新连接集](media/data-integrator/CreateNewProjectSelectConnectionSet780.png "创建新连接集")

8. 选择“下一步”，然后选择法人到业务部门的映射。

    > [!div class="mx-imgBorder"] 
    > ![创建新的法人映射](media/data-integrator/CreateNewProjectLegalEntityMapping780.png "创建新的法人映射")

9. 在下一个屏幕上查看并接受隐私声明和同意。

10. 继续创建项目，然后运行项目，进而执行项目。

    > [!div class="mx-imgBorder"] 
    > ![运行项目](media/data-integrator/RunProject780.png "运行项目")

    在此屏幕上，你会看到几个选项卡（“计划”和“执行历史记录”）以及一些按钮（“添加任务”、“刷新实体”和“高级查询”），本文稍后将对此进行介绍。

### <a name="execution-history"></a>执行历史记录

<!--note from editor: Do you think most people reading this will know what "upsert" means?-->

执行历史记录显示具有项目名称的所有项目执行的历史记录、执行项目的时间戳、执行的状态以及 Upsert 和/或错误的数量。

-   项目执行历史记录的示例。

    > [!div class="mx-imgBorder"] 
    > ![项目执行历史记录](media/data-integrator/ExecutionHistorySuccessFailures4780.png "项目执行历史记录")

-   成功执行的示例，状态显示为已完成 \# 个 Upsert。 （更新 Upsert 是用来更新记录（如果记录已存在）或者插入新记录的逻辑。）

    > [!div class="mx-imgBorder"] 
    > ![执行成功](media/data-integrator/ExecutionHistorySuccess2780.png "执行成功")

-   对于执行失败，可以向下钻取以查看根本原因。

    下面是失败并显示项目验证错误的示例。 在这种情况下，项目验证错误是由于实体映射中缺少源字段。

    > [!div class="mx-imgBorder"] 
    > ![执行历史记录失败](media/data-integrator/ExecutionHistoryFailures3780.png "执行历史记录失败")

-   如果项目执行处于“错误”状态，则将在下一次计划运行时重试执行。

-   如果项目执行处于“警告”状态，则需要在源上解决问题。 将在下一次计划运行时重试执行。

    在任何一种情况下，还可以选择手动“重新运行执行”。

### <a name="how-to-set-up-a-schedule-based-refresh"></a>如何设置基于计划的刷新

我们目前支持两种类型的执行/写入：

-   手动写入（手动执行和刷新项目）

-   基于计划的写入（自动刷新）

创建集成项目后，可以选择手动运行该项目或配置基于计划的写入，后者可以为你的项目设置自动刷新。

**设置基于计划的写入**

1. 转到 [PowerApps 管理中心](https://admin.powerapps.com)。

2. 可以采用两种不同的方式计划项目。<br>

    选择项目并选择“计划”选项卡或通过单击项目名称旁边的省略号，从“项目列表”页启动计划程序。

    > [!div class="mx-imgBorder"] 
    > ![基于计划的写入](media/data-integrator/Schedulebasedwrites780.png "基于计划的写入")

3. 选择“重复间隔”，并在填写所有字段后，选择“保存计划”。

    > [!div class="mx-imgBorder"] 
    > ![基于计划的写入](media/data-integrator/Schedulebasedwrites1780.png "基于计划的写入")

可以将频率设置为 1 分钟，也可以将重复间隔设置为特定的小时数、天数、周数或月数。 请注意，在上一个项目任务完成其运行之前，不会开始下一次刷新。

另请注意，在“通知”下，你可以选择基于电子邮件的警报通知，这些通知将向你发送有关作业执行（已完成并显示警告和/或由于出现错误而失败）的警报。 你可以提供多个收件人，包括以逗号分隔的组。

> [!div class="mx-imgBorder"] 
> ![电子邮件通知](media/data-integrator/EmailNotification780.png "电子邮件通知")

## <a name="customizing-projects-templates-and-mappings"></a>自定义项目、模板和映射 

使用模板创建数据集成项目。 模板可使数据移动商业化，进而帮助业务用户或管理员将数据从源加速集成到目标，并减少总体负担和成本。 业务用户或管理员可以开始使用由 Microsoft 或其合作伙伴发布的现成模板，然后对其进行进一步自定义，再创建项目。 然后，可以将该项目另存为模板并与组织共享和/或创建新项目。 

模板可向你提供源、目标和数据流的方向。 自定义和/或创建你自己的模板时，需要记住这一点。  

可以采用以下方式自定义项目和模板：

-   自定义字段映射。

-   通过添加所选的实体来自定义模板。

### <a name="how-to-customize-field-mappings"></a>如何自定义字段映射

**创建连接集**

1. 转到 [PowerApps 管理中心](https://admin.powerapps.com)。

2. 选择要为其自定义字段映射的项目，然后选择源和目标字段之间的箭头。

    > [!div class="mx-imgBorder"] 
    > ![字段映射](media/data-integrator/FieldMapping780.png "字段映射")

3. 这样会转到“映射”屏幕，你可以在其中通过选择右上角的“添加映射”或从下拉列表中选择“自定义现有映射”来添加新映射。

    > [!div class="mx-imgBorder"] 
    > ![字段映射自定义](media/data-integrator/FieldMappingCustomize780.png "字段映射自定义")

4. 自定义字段映射后，选择“保存”。

### <a name="how-to-customize-or-create-your-own-template"></a>如何自定义或创建你自己的模板 

**创建你自己的模板**

1. 转到 [PowerApps 管理中心](https://admin.powerapps.com)。

2. 为你的新模板标识源和目标以及流方向。

3. 通过选择与所选的源和目标以及流方向匹配的现有模板来创建项目。

<!--note from editor: Didn't we create the project in step 3? Step 4 tells us to create the project.-->

4. 选择适当的连接后创建项目。

5. 在保存和/或运行项目之前，选择右上角的“添加任务”。

    > [!div class="mx-imgBorder"] 
    > ![自定义模板](media/data-integrator/CustomizeTemplate780.png "自定义模板")

    这将启动“添加任务”对话框。

6. 提供有意义的任务名称并添加所选的源和目标实体。

    > [!div class="mx-imgBorder"] 
    > ![自定义模板添加任务](media/data-integrator/CustomizeTemplateAddtask75.png "自定义模板添加任务")

7. 下拉列表向你显示所有源和目标实体。

    > [!div class="mx-imgBorder"] 
    > ![自定义模板添加任务](media/data-integrator/CustomizeTemplateAddtask175.png "自定义模板添加任务")

    在这种情况下，创建了新任务以将 SalesForce 中的用户实体同步到 Common Data Service for Apps 中的用户实体。

    > [!div class="mx-imgBorder"] 
    > ![自定义模板添加任务](media/data-integrator/CustomizeTemplateAddtask275.png "自定义模板添加任务")

8. 创建任务后，你将看到列出的新任务，并且可以删除原始任务。

    > [!div class="mx-imgBorder"] 
    > ![自定义模板添加任务](media/data-integrator/CustomizeTemplateAddtask3780.png "自定义模板添加任务")

9. 你刚创建了新模板，在这种情况下，该模板用于将用户实体数据从 SalesForce 提取到 Common Data Service。 选择“保存”以保存自定义。

10. 按照这些步骤为此新模板自定义字段映射。 可以在“项目列表”页中运行此项目和/或将此项目另存为模板。

    > [!div class="mx-imgBorder"] 
    > ![自定义模板另存为模板](media/data-integrator/CustomizeTemplateSaveAsTemplate780.png "自定义模板另存为模板")

11. 提供名称和说明和/或与组织中的其他人共享。

    > [!div class="mx-imgBorder"] 
    > ![自定义模板另存为模板](media/data-integrator/CustomizeTemplateSaveAsTemplate175.png "自定义模板另存为模板")

## <a name="advanced-data-transformation-and-filtering"></a>高级数据转换和筛选 

借助 Power Query 支持，我们现在提供源数据的高级筛选和数据转换功能。 Power Query 可让用户重塑数据以满足其需求，并打造易于使用、具有吸引力且无代码的用户体验。 可以逐个项目启用此功能。 

### <a name="how-to-enable-advanced-query-and-filtering"></a>如何启用高级查询和筛选

**设置高级筛选和数据转换**

1. 转到 [PowerApps 管理中心](https://admin.powerapps.com)。

2. 选择要启用高级查询的项目，然后选择“高级查询”。

    > [!div class="mx-imgBorder"] 
    > ![选择高级查询](media/data-integrator/EnablePQ1780.png "选择高级查询")

3. 你将收到一条警告，指示启用高级查询是单向操作，且无法撤消。 选择“确定”以继续，然后选择源和目标映射箭头。

    > [!div class="mx-imgBorder"] 
    > ![警告](media/data-integrator/EnablePQ275.png "警告")

4. 现在会向你显示熟悉的实体映射页面，其中包含用于启动高级查询和筛选的链接。

    > [!div class="mx-imgBorder"] 
    > ![高级查询和筛选](media/data-integrator/EnablePQ3780.png "高级查询和筛选")

5. 选择“链接”以启动“高级查询和筛选”用户界面，从而为你提供 Microsoft Excel 类型列中的源字段数据。

    > [!div class="mx-imgBorder"] 
    > ![高级查询和筛选](media/data-integrator/EnablePQ4780.png "高级查询和筛选")

6. 从顶部菜单中，获取用于转换数据的多个选项，如“添加条件列”、“复制列”和“提取”。

    > [!div class="mx-imgBorder"] 
    > ![添加列](media/data-integrator/EnablePQAddColumn75.png "添加列")

7. 也可以右键单击任何列以获取更多选项，如“删除列”、“删除重复项”和“拆分列”。

    > [!div class="mx-imgBorder"] 
    > ![右键单击列](media/data-integrator/EnablePQAddColumn180.png "右键单击列")

8. 此外，还可以通过单击每个列并使用 Excel 类型筛选器进行筛选。

    > [!div class="mx-imgBorder"] 
    > ![启用筛选](media/data-integrator/EnablePQFiltering80.png "启用筛选")

<!--note from editor: I don't see an "otherwise" in the screenshot. I see "else".-->

9. 可以使用条件列实现默认值转换。 为此，请从“添加列”下拉列表中选择“添加条件列”并输入新列的名称。 使用 If 和 equal to 的任何字段和值，用默认值填充 Then 和 Otherwise。

    > [!div class="mx-imgBorder"] 
    > ![添加条件列](media/data-integrator/EnablePQDefaultValueTransforms2780.png "添加条件列")

10. 注意顶部 fx 编辑器中的 each 子句。

    > [!div class="mx-imgBorder"] 
    > ![fx 编辑器](media/data-integrator/EnablePQDefaultValueTransforms2780.png "fx 编辑器")

11. 修复 fx 编辑器中的 each 子句，然后选择“确定”。

    > [!div class="mx-imgBorder"] 
    > ![修复 each 子句](media/data-integrator/EnablePQDefaultValueTransforms5780.png "修复 each 子句")

<!--note from editor: The sentence that starts with "Additionally" is confusing - not sure where the "same steps" fit in.-->

12. 每次进行更改时，会应用一个步骤。 你可以在右侧窗格中看到应用的步骤（滚动到底部才能看到最新步骤）。 需要编辑时可以撤消步骤。 此外，还可以通过右键单击左侧顶部窗格中的 QrySourceData 以查看使用相同步骤在后台执行的 M 语言来转到高级编辑器。

    > [!div class="mx-imgBorder"] 
    > ![高级编辑器](media/data-integrator/EnablePQDefaultValueTransforms4780.png "高级编辑器")

13. 选择“确定”以关闭“高级查询和筛选”界面，然后在“映射任务”页上，选择新创建的列作为源以相应地创建映射。

    > [!div class="mx-imgBorder"] 
    > ![选择新列](media/data-integrator/EnablePQDefaultValueTransforms6780.png "选择新列")

有关 Power Query 的详细信息，请参阅 [Power Query 文档](https://docs.microsoft.com/power-query/)。
