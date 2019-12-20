---
title: 在模型驱动系统窗体中嵌入 Power BI 报表 | MicrosoftDocs
ms.custom: ''
ms.date: 03/05/2019
ms.reviewer: matp
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 1
author: prsi-msft
ms.author: prsi
manager: kvivek
tags:
- Links to topic not migrated
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5ea6ed1011ce9d21c78adf6beed9a2943c9f4cd0
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860443"
---
# <a name="embed-a-power-bi-report-in-a-model-driven-system-form"></a>在模型驱动系统窗体中嵌入 Power BI 报表
您可以使用 Power Apps 模型驱动应用中的 Power BI 报表将丰富的报表和分析带入您的系统窗体，让用户完成更多任务。 这可以解锁跨系统聚合数据的能力，并将其自定义到单个记录的上下文。
 
## <a name="prerequisites"></a>必备条件 
嵌入 Power BI 内容是一个可选功能，默认情况下所有环境均禁用。 在嵌入 Power BI 内容之前，必须将其启用。 详细信息：[在组织中启用 Power BI 可视化效果化](https://docs.microsoft.com/dynamics365/customer-engagement/admin/use-power-bi?#enable--visualizations-in-the-organization)。

此功能需要导出解决方案、进行修改以添加 XML 片段，然后重新导入到环境。 请务必仅通过托管解决方案在您的目标环境中导入所做的更改。 请参阅[导入、更新和导出解决方案](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions)获取为现有托管解决方案安装更新的指导。

## <a name="embed-without-contextual-filtering"></a>不使用上下文筛选嵌入
您通过嵌入 Power BI 报表和磁贴即可使用它们，并获取完全相同的报表。 这不会将它们置于当前模型驱动窗体的上下文中，因此，您将在实体的所有记录中获取相同报表或磁贴。 例如，下列报表一次可以显示所有客户的地理位置，对于显示摘要信息很有用。

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-unfiltered.png "Embed-powerbi-report-in-system-form-unfiltered")

您可以通过添加窗体 XML 的 `<sections>` 块内的以下代码段来在您的系统窗体中嵌入承载 Power BI 报表和磁贴的部分。 然后，在目标环境中导入解决方案。 

```xml
<section id="{d411658c-7450-e1e3-bc80-07021a04bcc2}" locklevel="0" showlabel="true" IsUserDefined="0" name="tab_4_section_1" labelwidth="115" columns="1" layout="varwidth" showbar="false">
    <labels>
        <label languagecode="1033" description="Unfiltered Power BI embedding demo"/>
    </labels>
    <rows>
        <row>
            <cell id="{7d18b61c-c588-136c-aee7-03e5e74a09a1}" showlabel="true" rowspan="20" colspan="1" auto="false">
                <labels>
                    <label languagecode="1033" description="Accounts (Parent Account)"/>
                </labels>
                <control id="unfilteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
                    <parameters>
                        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
                        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
                        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
                    </parameters>
                </control>
            </cell>
        </row>
        <row/>
    </rows>
</section>
```
> [!IMPORTANT]
> 请务必使用 XML 示例中所示的控件 `classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}"`。

 此表介绍前一个示例中的属性。

|                                                 属性                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIGroupId**                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Power BI 工作区 ID。用户的默认工作区始终是 00000000-0000-0000-0000-000000000000。 可以通过查看 URL 检查任何工作区的 ID。 例如，https://xyz.powerbi.com/groups/0ddbe381-256d-44bc-93de-34e47f3d9ab4/。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                               **PowerBIReportId**                                |                             Power BI 报表 ID。将此替换为要嵌入的报表。 可以通过查看 URL 检查任何报表的 ID。 例如，https://xyz.powerbi.com/groups/me/reports/544c4162-6773-4944-900c-abfd075f6081。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                                       **TileUrl**                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        您要嵌入的 Power BI 报表或磁贴 URL。 请确保使用正确的 Power BI 实例名称（将 msit.powerbi.com 替换为您自己的名称）和报表 ID（将 reportId=544c4162-6773-4944-900c-abfd075f6081 替换为您自己的信息）。 例如，https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

## <a name="embed-with-contextual-filtering"></a>使用上下文筛选嵌入
您可以通过对当前的模型驱动窗体应用上下文筛选器来使 Power BI 报表和磁贴更有意义，以使报表或磁贴根据当前记录的属性进行筛选。 例如，通过使用客户名称筛选 Power BI 报表，以下报表显示客户的地理位置。 此选项允许单个报表显示实体的所有记录的加入上下文的信息。

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-filtered.png "Embed-powerbi-report-in-system-form-filtered")

筛选通过在 `<parameter>` 块中添加 `<PowerBIFilter>` 元素进行，如此处所示。 您可以使用窗体实体的任何属性来构造筛选器表达式。 详细信息：通过[构造筛选器](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters)了解如何创建您自己的筛选器。
    
```xml
<control id="filteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
    <parameters>
        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
        <PowerBIFilter>{"Filter": "[{\"$schema\":\"basic\",\"target\":{\"table\":\"My Active Accounts\",\"column\":\"Account Name\"},\"operator\":\"In\",\"values\":[$a],\"filterType\":1}]", "Alias": {"$a": "name"}}</PowerBIFilter>
    </parameters>
</control>
```

请注意，这使用与未筛选的报表嵌入相同的控件，因此控件类 ID 保持不变。 

此表介绍前一个示例中使用的所有其他属性。

|                                                 属性                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIFilter**                          |        通过作为参数传递窗体属性将 Power BI 报表置于上下文的筛选器表达式。 为了更加易读，筛选器按如下方式构造。    |

```json
    {
            "Filter": "[{
                    \"$schema\":\"basic\",
                    \"target\":{
                            \"table\":\"My Active Accounts\",
                            \"column\":\"Account Name\"
                    },
                    \"operator\":\"In\",
                    \"values\":[$a, $b],
                    \"filterType\":1
            }]",
            "Alias": {
                    "$a": "firstname",
                    "$b":"lastname"
            }
    }
```

前一个表达式的目标部分标识应用筛选器的表和列。 运算符标识确定从 Power Apps 模型驱动型应用传递的数据的逻辑和值。 若要以通用方式参数化，通过使用别名构造值。 在上一个表达式中，传递了客户的 **firstname** 和 **lastname**，二者都在 Power BI 报表中的**客户名称**列搜索。 请注意 **firstname** 和 **lastname** 是客户实体的属性的唯一名称，其值将在此处传递。 

可以通过查看[构造筛选器](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters)中的示例并为 $schema 和 filterType 提供适当的值来创建更复杂的筛选器表达式。 请确保使用 *\"* 转义筛选器中的每个文字，以便可以正确生成 JSON。

## <a name="known-issues-and-limitations"></a>已知问题和限制
1. 此集成只在统一接口客户端可用，并且在支持的 Web 浏览器和移动设备上。
2. 在 Power Apps 窗体设计器中打开此窗体将不会以有意义的方式显示控件。 这是因为此控件在窗体设计器外自定义。
3. 系统将使用用户的 Power Apps 用户名和密码自动进行身份验证后进入 Power BI。 如果具有匹配凭据的 Power BI 客户不存在，登录提示将显示，如此处所述。 

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-1.png "Embed-powerbi-report-in-system-form-auth-1")

4. 如果使用了不正确的客户登录 Power BI，数据将不会显示。 若要使用正确的凭据登录，请先注销，然后再次登录。

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-2.png "Embed-powerbi-report-in-system-form-auth-2")

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-3.png "Embed-powerbi-report-in-system-form-auth-3")

5. 显示在 Power Apps 内的报表数据的视图与 Power BI 中的相同，Power Apps 安全角色和权限不会影响显示的数据。 因此，数据基本上与 Power BI 数据集创建者看到的相同。 若要应用类似于 Power Apps 安全角色和团队的数据访问限制，请使用[使用 Power BI 的行级安全性 (RLS)](https://docs.microsoft.com/power-bi/service-admin-rls)。
6. 如果窗体在导入解决方案并发布自定义项之后未显示 Power BI 报表，请在模型驱动窗体编辑器中打开它并保存，以便窗体 JSON 重新生成。


### <a name="see-also"></a>另请参阅

[在 Power Apps 模型驱动的个人仪表板中嵌入 Power BI 仪表板](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard)

[将 Power BI 与 Dynamics 365 应用结合使用](https://docs.microsoft.com/dynamics365/customer-engagement/admin/use-power-bi)

[导入、更新和导出解决方案](../common-data-service/import-update-export-solutions.md)
