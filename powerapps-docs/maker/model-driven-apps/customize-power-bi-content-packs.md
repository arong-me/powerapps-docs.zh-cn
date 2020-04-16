---
title: 自定义 Dynamics 365 Power BI 内容包 | MicrosoftDocs
description: 了解如何修改可用 Power BI 内容包以使用 Dynamics 365 数据。
keywords: PBI
ms.date: 09/30/2017
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
ms.assetid: 424d7f29-de44-4ce0-94f1-be8777ad6485
author: Mattp123
ms.author: matp
manager: annbe
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 16
topic-status: Drafting
tags: ''
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: 1fb1c7289e287c96ce53474baba7632106ada79e
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115930"
---
# <a name="customize-dynamics-365-apps-power-bi-content-packs"></a>自定义 Dynamics 365 应用 Power BI 内容包

Power BI 是用于可视化业务数据的一组丰富的服务和工具。  现已提供了内容包，可用于与 Power BI 一起基于标准数据模型分析 Dynamics 365 Sales、Service 和 Marketing 应用数据。 内容包使用对大多数销售。服务或市场营销报告方案都十分有用的一组实体和字段生成。  
  
 Dynamics 365 应用通常使用自定义字段扩展。 这些自定义字段在 Power BI 模型中不自动显示。 本主题介绍可用于编辑或扩展内容包中包含的报表以在 Power BI 模型中添加自定义字段的不同方法。  
    
<a name="PBI_edit_first"></a>   
## <a name="do-this-before-you-customize-a-content-pack-for-power-bi-reports"></a>为 Power BI 报表自定义内容包之前执行此操作  
 
自定义内容包之前，请阅读此处的信息，并在必要时执行各任务。  
  
### <a name="meet-the-requirements"></a>满足要求  
  
- [Power BI 服务注册](https://powerbi.com/)。  
  
- [Power BI Desktop](https://powerbi.microsoft.com/desktop) 应用程序，用于编辑 Power BI 报表。  
  
- 要自定义的内容包的 PBIX 文件。  
  
  -   [下载 Dynamics CRM Online Sales Manager PBIX](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
  -   [下载 Dynamics CRM Online Service Manager PBIX](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  -   [下载 Microsoft Dynamics 365 Process Analyzer PBIX](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Process%20Analyzer%20-1.34b.pbix)  
  
  Dynamics 365 content pack 现在仅支持美国英语。  
  
### <a name="prepare-a-content-pack-for-customization"></a>准备要自定义的内容包  
  
> [!IMPORTANT]
>  若要将 OData 源连接到您的实例，必须在自定义内容包之前执行此处介绍的步骤。  
> 
> 目前 Power BI 服务与 Dynamics 365 版本 9.0 OData 终结点不兼容。 如果尝试使用版本 9.0 OData 终结点和 Power BI 服务，将显示错误消息“此源的元数据文档似乎无效”。 要解决这个不兼容问题，请使用 Dynamics 365 版本 8.2 OData 终结点。有关不同终结点版本的详细信息，请参阅[撰写 HTTP 请求并处理错误](../../developer/common-data-service/webapi/compose-http-requests-handle-errors.md)。
  
1. 启动 Power BI Desktop。  
  
    选择**文件** > **打开**，打开内容包（如 Sales Manager.bpix），然后选择**打开**。  
  
    将加载内容包中的几页报表并在 Power BI Desktop 中显示。  
  
2. 在 Power BI Desktop 功能区中，选择**编辑查询**。  
  
3. 在“编辑查询”窗口左导航窗格中**查询**下，选择 **CRMServiceUrl** 查询，然后选择功能区中的**高级编辑器**。 在源定义中，将 **base.crm.dynamics.com** 替换为应用实例 URL。 例如，如果组织名称为 *Contoso*，该 URL 将如下所示：  
  
    源 = "https://*contoso*.crm.dynamics.com/api/data/v8.0/"  
  
4. 选择**完成**，然后选择“查询编辑器”中的**关闭并应用**。  
  
5. 显示“访问 OData 源”对话框时，选择**组织帐户**，然后选择**登录**。  
  
   ![“访问 Odata 源”对话框](media/pbi-odata-signin.PNG "“访问 Odata 源”对话框")  
  
6. 显示登录页时，输入您的凭据来为您的实例执行身份验证。  
  
7. 在“访问 Odata 源”对话框中，选择**连接**。  
  
    将更新内容包查询。 这可能需要几分钟时间。  
  
<a name="PBI_edit_report"></a>   
## <a name="customize-adynamics-365-content-pack"></a>自定义 Dynamics 365 Content Pack  
 [更改报表中显示的日期格式](#PBI_edit_date)  
  
 [向除“客户”外的任何实体的报表添加自定义字段](#PBI_edit_field)  
  
 [向“客户”实体的报表添加自定义字段](#PBI_field_Account)  
  
 [向报表添加选项集字段](#PBI_optionset_field)  
  
 [提高查询的行数](#BPI_increaserows)  
  
<a name="PBI_edit_date"></a>   
### <a name="convert-a-datetime-field-to-a-date-field-for-reporting"></a>将日期时间字段转换为日期字段以执行报告  
 在 Dynamics 365 应用中，某些日期的保存格式为“日期/时间/时区”，这种格式不太适合聚集报表中的数据。 可以为实体字段转换报表中显示的日期。 例如，可以将“商机创建时间”字段转换为日期以报告“商机创建日期”。  
  
1. 在 Power BI Desktop 中，选择**编辑查询**。  
  
2. 在“查询编辑器”的左导航窗格中的**查询**下，选择要更改其日期字段的查询，如**商机**实体查询中的**预计结束日期**。  
  
3. 右键单击列标题（如*预计结束日期*），指向**更改类型**，然后选择其他日期类型（如**日期**）。  
  
   ![在 Power BI Desktop 中更改数据类型](media/pbi-changeformat.PNG "在 Power BI Desktop 中更改数据类型")  
  
4. 选择**保存并应用**以关闭“查询编辑器”。  
  
5. 在 Power BI 主页中，选择**应用更改**更新关联的报表。  
  
<a name="PBI_edit_field"></a>   
### <a name="add-a-custom-field-to-a-report"></a>向报表添加自定义字段  
 下面的过程介绍如果向除“客户”实体之外的所有可用实体的报表添加日期、字符串或数字类型的自定义字段。  
  
> [!NOTE]
>  若要向“客户”实体添加字段，请参阅[向“客户”实体的报表添加自定义字段](#PBI_field_Account)。 若要添加选项集类型的字段，请参阅[向报表添加选项集字段](#PBI_optionset_field)。  
  
1. 在 Power BI Desktop 中，选择**编辑查询**。  
  
2. 在“查询编辑器”的左导航窗格中的**查询**下，选择要提供给报表使用的自定义字段的查询，如**商机**实体查询。  
  
3. 在右窗格中**应用的步骤**下，选择**已删除的其他列**旁边的设置按钮 ![“设置”按钮](media/mp-ua-r16-settings.png "“设置”按钮")。  
  
4. **选择列**列表将显示实体的所有字段，包括自定义字段。 然后所需自定义字段，然后选择**确定**。  
  
    将更新实体查询，并在实体表中为所选自定义字段添加一列。  
  
5. 在右窗格中**应用的步骤**下，选择**语言 - 重命名的列**，然后选择**高级编辑器**，将字段的映射添加到实体查询。 例如，如果“商机”实体的自定义字段名称为 *int_forecast*，则显示名称为 *Forecast*，而查询应显示为这样。  
  
   ```  
   {"int_forecast","Forecast"}  
   ```  
  
   ![为报表中的自定义字段添加映射](media/pbi-addfieldmapping.png "为报表中的自定义字段添加映射")  
  
6. 添加字段映射之后，请确保“高级编辑器”底部不显示任何语法错误。 此外，还请确保字段名称的显示与其在列标题中的显示一模一样，包括字母的大小写也必须正确。 如果未检测到语法错误或表错误，请选择**完成**。  
  
7. 单击“查询编辑器”中的**关闭并应用**。  
  
    自定义字段现在出现在实体的右窗格中**字段**下，可添加到新报表或现有报表。  
  
<a name="PBI_field_Account"></a>   
## <a name="add-a-custom-field-to-a-report-for-the-account-entity"></a>向“客户”实体的报表添加自定义字段  
 由于“客户”查询使用 Fetch XML 筛选查询，所以用于添加字段的步骤与使用 OData 的其他实体查询有所不同。 若要向 OData 查询实体添加自定义字段，请参阅[向报表添加自定义字段](#PBI_edit_field)。  
  
1. 复制为“客户”实体编码的 Fetch XML 查询。 为此，请按照以下步骤操作：  
  
   1.  在 Power BI Desktop 中，选择**编辑查询**。  
  
   2.  在“查询编辑器”左导航窗格中的**查询**下，选择**客户**实体查询，然后选择功能区中的**高级编辑器**。  
  
   3.  从 %3Cfetch 开始并以 fetch%3E 结束的第一行，复制整个编码的 Fetch XML。  
  
   4.  所复制编码的 Fetch XML 应如下所示：  
  
        %3Cfetch%20version%3D%221.0%22%20output-format%3D%22xml-platform%22%20mapping%3D%22logical%22%20distinct%3D%22true%22%3E%3Centity%20name%3D%22account%22%3E%3Cattribute%20name%3D%22territorycode%22%20%2F%3E%3Cattribute%20name%3D%22customersizecode%22%20%2F%3E%3Cattribute%20name%3D%22owningbusinessunit%22%20%2F%3E%3Cattribute%20name%3D%22ownerid%22%20%2F%3E%3Cattribute%20name%3D%22originatingleadid%22%20%2F%3E%3Cattribute%20name%3D%22revenue%22%20%2F%3E%3Cattribute%20name%3D%22sic%22%20%2F%3E%3Cattribute%20name%3D%22marketcap%22%20%2F%3E%20%3Cattribute%20name%3D%22parentaccountid%22%20%2F%3E%3Cattribute%20name%3D%22owninguser%22%20%2F%3E%3Cattribute%20name%3D%22accountcategorycode%22%20%2F%3E%3Cattribute%20name%3D%22marketcap_base%22%20%2F%3E%3Cattribute%20name%3D%22customertypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_postalcode%22%20%2F%3E%3Cattribute%20name%3D%22numberofemployees%22%20%2F%3E%3Cattribute%20name%3D%22accountratingcode%22%20%2F%3E%3Cattribute%20name%3D%22address1_longitude%22%20%2F%3E%3Cattribute%20name%3D%22revenue_base%22%20%2F%3E%3Cattribute%20name%3D%22createdon%22%20%2F%3E%3Cattribute%20name%3D%22name%22%20%2F%3E%3Cattribute%20name%3D%22address1_stateorprovince%22%20%2F%3E%3Cattribute%20name%3D%22territoryid%22%20%2F%3E%3Cattribute%20name%3D%22accountclassificationcode%22%20%2F%3E%3Cattribute%20name%3D%22businesstypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_country%22%20%2F%3E%3Cattribute%20name%3D%22accountid%22%20%2F%3E%3Cattribute%20name%3D%22address1_latitude%22%20%2F%3E%3Cattribute%20name%3D%22modifiedon%22%20%2F%3E%3Cattribute%20name%3D%22industrycode%22%20%2F%3E%3Clink-entity%20name%3D%22opportunity%22%20from%3D%22parentaccountid%22%20to%3D%22accountid%22%20alias%3D%22ab%22%3E%3Cfilter%20type%3D%22and%22%3E%3Ccondition%20attribute%3D%22opportunityid%22%20operator%3D%22not-null%22%20%2F%3E%3Ccondition%20attribute%3D%22modifiedon%22%20operator%3D%22last-x-days%22%20value%3D%22365%22%20%2F%3E%3C%2Ffilter%3E%3C%2Flink-entity%3E%3C%2Fentity%3E%3C%2Ffetch%3E  
  
2. 解码编码的 Fetch XML。 它必须是有效的编码的 Fetch XML，并且在解码后应如下所示：  
  
    \<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true"> \<entity name="account"> \<attribute name="territorycode" /> \<attribute name="customersizecode" /> \<attribute name="owningbusinessunit" /> \<attribute name="ownerid" /> \<attribute name="originatingleadid" /> \<attribute name="revenue" /> \<attribute name="sic" /> \<attribute name="marketcap" />  \<attribute name="parentaccountid" /> \<attribute name="owninguser" /> \<attribute name="accountcategorycode" /> \<attribute name="marketcap_base" /> \<attribute name="customertypecode" /> \<attribute name="address1_postalcode" /> \<attribute name="numberofemployees" /> \<attribute name="accountratingcode" /> \<attribute name="address1_longitude" /> \<attribute name="revenue_base" /> \<attribute name="createdon" /> \<attribute name="name" /> \<attribute name="address1_stateorprovince" /> \<attribute name="territoryid" /> \<attribute name="accountclassificationcode" /> \<attribute name="businesstypecode" /> \<attribute name="address1_country" /> \<attribute name="accountid" /> \<attribute name="address1_latitude" /> \<attribute name="modifiedon" /> \<attribute name="industrycode" /> \<link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab"> \<filter type="and"> \<condition attribute="opportunityid" operator="not-null" /> \<condition attribute="modifiedon" operator="last-x-days" value="365" /> \</filter> \</link-entity> \</entity> \</fetch>  
  
   > [!TIP]
   >  网上有许多免费提供的 URL 编码器和解码器工具。  
  
3. 在 Fetch XML 中，将您的自定义实体作为属性节点在 \<entity> 节点之间添加。 例如，若要添加名称为 *customclassificationcode* 的自定义字段，请在另一个属性节点（如**industrycode**）后添加该节点。  
  
   ```  
  
   <attribute name="industrycode" />  
   <attribute name=" customclassificationcode "/>  
   <link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab">  
   ```  
  
4. URL 将为更新后的 Fetch XML 编码。 必须为包含新自定义属性的 Fetch XML 编码，然后将其用于替换内容包随附的现有 OData 源查询。 方法是，将更新后的 FetchXML 复制到剪贴板，然后将其粘贴到 URL 编码器中。  
  
5. 将编码的 Fetch XML URL 粘贴到 OData 源中。 方法是，将编码的 URL 粘贴到 **Query=[fetchXml=** 文本后的引号之间以替换现有编码的 FetchXML，然后选择**完成**。  
  
    下面的屏幕截图显示最左的引号的位置。  
  
   ![将编码的 URL 粘贴到 OData 源中](media/pbi-acct-encoded-url.PNG "将编码的 URL 粘贴到 OData 源中")  
  
6. 在右窗格中**应用的步骤**下，选择**已删除的其他列**旁边的设置按钮 ![“设置”按钮](media/mp-ua-r16-settings.png "“设置”按钮")。  
  
7. “选择列”列表将显示实体的所有字段，包括自定义字段。 选择在前面添加到 Fetch XML 查询的自定义字段（如 *customclassificationcode*），然后选择**确定**。  
  
   > [!NOTE]
   >  您在“列选择器”中选择的字段名必须与您添加到 FetchXML 查询的字段名匹配。  
  
    将更新实体查询，并在实体表中为所选自定义字段添加一列。  
  
8. 选择“查询编辑器”中的**关闭并应用**。  
  
    自定义字段现在出现在实体的右窗格中**字段**下，可添加到新报表或现有报表。  
  
<a name="PBI_optionset_field"></a>   
## <a name="add-a-custom-option-set-field-to-a-report"></a>向报表添加自定义选项集字段  
 选项集字段用于从多个值中进行选择。 商机的“等级”和“销售阶段”字段就是现成的选项集字段。 想象以下您在“商机”窗体上有一个自定义选项集字段，并且该字段具有以下值和标签。  
  
 ![自定义选项集示例](media/pbi-custom-option-set-example.PNG "自定义选项集示例")  
  
 若要向报表添加自定义选项集字段，请执行以下步骤。  
  
1. 添加自定义字段列。  
  
   -   在“查询编辑器”左导航窗格中的**查询**下，选择具有关联的自定义选项集的实体，如*商机*实体。  
  
   -   在右窗格中**应用的步骤**下，选择**已删除的其他列**旁边的设置按钮 ![“设置”按钮](media/mp-ua-r16-settings.png "“设置”按钮")。  
  
   -   “选择列”列表将显示实体的所有字段，包括自定义字段。 选择自定义字段（如 *new_customoptionset*），然后选择**确定**。  
  
   -   选择**保存**，然后在系统提示时，选择**应用**。  
  
        将在实体表中显示该自定义字段的列。  
  
2. 创建选项集查询。  
  
   1.  在 Power BI Desktop 中，选择**编辑查询**。  
  
   2.  在“查询编辑器”左导航窗格中的**查询**下，选择**创建表**组下拥有与您要添加到报表的选项集最相似的选项集字段的查询。 对于此示例，**SalesStageOptionSet**查询有四个选项，因此很适合选择。  
  
   3.  选择**高级编辑器**。  
  
        将显示选项集查询。  
  
   ![创建选项集查询](media/pbi-makeoptionsetquery.png "创建选项集查询")  
  
   4.  将整个查询复制到剪贴板。 可以将其粘贴到文本编辑器（如“记事本”）中，供以后参考。  
  
   5.  在“查询编辑器”中，右键单击**创建表**组，选择**新建查询**，然后选择**空白查询**。  
  
   6.  在右窗格中**名称**下，输入一个名称（如 *CustomOptionSet*），然后按 Enter 键。  
  
   7.  选择**高级编辑器**。  
  
   8.  在“高级编辑器”中，粘贴您在前面复制的查询。  
  
   9. 将现有值和选项替换为您的自定义值和选项。 在此示例中，您将把这个  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"Qualify"},{1,"Develop"},{2,"Propose"},{3,"Close"}})  
       in  
           Source  
  
       ```  
  
        更改为这个。  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"A"},{1,"B"},{2,"C"},{3,"D"},{4,"E"}})  
       in  
           Source  
  
       ```  
  
   10. 确保无语法错误，然后选择**完成**关闭“高级编辑器”。 将在“查询编辑器”中显示值和选项的表。  
  
   ![新选项集查询](media/pbi-optionsetquerycreated.png "新选项集查询")  
  
   11. 选择**保存**，然后在系统提示时，选择**应用**。  
  
3. 插入实体和自定义选项集表的合并查询。  
  
   1.  在“查询编辑器”的左窗格中的**实体**下，选择包含自定义选项集的实体。 对于此示例，选择的是**商机**实体查询。  
  
   2.  在功能区中，选择**合并查询**，然后在系统提示插入步骤时，选择**插入**。  
  
   3.  在“合并”对话框中，选择自定义选项集的列标题，如 *new_optionset*。 在下拉列表中，选择前面创建的相应选项集查询。  显示选项集表时，选择**值**列标题将其选中。  
  
   ![合并所选表](media/pbi-merge-tables.png "合并所选表")  
  
   4.  让联接类型保持为**左向外(全部从第一个开始，匹配从第二个开始)**，然后选择**确定**。  
  
       > [!TIP]
       >  重命名合并查询。 在**应用的步骤**下，右键单击您创建的查询，选择**重命名**，然后输入描述性名称，例如 *Merge CustomOptionSet*。  
  
4. 定义列，以便仅显示标签。  
  
   1.  在“查询编辑器”的左窗格中的“实体”下，选择包含自定义选项集的实体。 对于此示例，选择的是**商机**实体查询。  
  
   2.  在右窗格中**应用的步骤**下，选择一个扩展的查询显示合并列，如 **Expanded SalesStage**。  
  
   3.  找到并选择前面的合并查询步骤部分创建的心列的列标题。  
  
   4.  在**转换**选项卡上，选择**展开**。  
  
   5.  在“扩展新列”对话框中，清除与值对应的列（因为列中仅应显示标签）。 选择**完成**。  
  
   ![选择表示标签的列](media/pbi-expand-column.png "选择表示标签的列")  
  
   6.  选择**保存**，然后在系统提示时，选择**应用**。  
  
5. 更改报表生成的列名。  
  
   1.  在“查询编辑器”的左窗格中的**实体**下，选择包含自定义选项集的实体。 对于此示例，选择的是**商机**实体查询。  
  
   2.  选择**高级编辑器**。  
  
   3.  添加重命名的列行项，确保无语法错误，然后选择**完成**。 在此示例中，前面创建的自定义选项集列名为**NewColumn**，该列名将重命名为 *Custom Option Set*。  
  
   ![重命名要在报表中显示的列](media/pbi-rename-column.png "重命名要在报表中显示的列")  
  
   4.  选择**保存**，然后在系统提示时，选择**应用**。  
  
6. 选择**保存并应用**以关闭“查询编辑器”。  
  
    现在可使用自定义选项集生成 Power BI 报表。  
  
<a name="BPI_increaserows"></a>   
## <a name="increase-the-number-of-rows-queried"></a>提高查询的行数  
 默认情况下，内容包中的所有 Power BI 实体查询都不能超过 100,000 行。 若要提高可查询的行数，请执行以下步骤。  
  
> [!IMPORTANT]
>  提高行计数限制可显著影响刷新报表所用时间。 此外，Power BI 服务有 30 分钟的运行查询限制。 提高行计数限制时，请务必小心谨慎。  
  
1. 在 Power BI Desktop 中，选择**编辑查询**。  
  
2. 在“查询编辑器”左导航窗格中的**查询**下，选择要提高其行技术限制的实体查询，如**潜在顾客**实体。  
  
3. 在右窗格中**应用的步骤**下，选择**保留首行**。  
  
4. 提高筛选的行数。 例如，若要提高到 150,000，请将 Table.FirstN(#"Filtered Rows",100001) 更改为 Table.FirstN(#"Filtered Rows",150000)  
  
5. 在右窗格中**应用的步骤**下，选择**检查行计数**。  
  
6. 找到步骤的 **>100,000**部分。  
  
   ![增加行计数值](media/pbi-increaserowcount.png "增加行计数值")  
  
7. 将值提高到更大数字，如 *150,000*。  
  
8. 选择“查询编辑器”中的**关闭并应用**。  
  
<a name="BPI_publish"></a>   
## <a name="publish-your-report-to-the-power-bi-service"></a>将报表发布到 Power BI 服务  
 在几乎任何设备上从任何位置发布报表以实现组织共享和访问。  
  
1. 在 Power BI Desktop 主页**开始**选项卡功能区上，选择**发布**。  
  
2. 如果系统提示您登录 Power BI 服务，选择**登录**。  
  
3. 如果有多个可用目标，请选择需要的目标，然后选择**发布**。  
  
### <a name="see-also"></a>另请参阅  
 [将 Power BI 与 Dynamics 365 Customer Engagement (on-premises) 结合使用](use-power-bi.md)
