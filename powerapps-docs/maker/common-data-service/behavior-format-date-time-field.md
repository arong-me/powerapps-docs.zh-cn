---
title: Common Data Service 中的“日期和时间”字段的行为和格式 | MicrosoftDocs
ms.custom: ''
ms.date: 05/25/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 73d691c7-344e-4c96-8979-c661c290bf81
caps.latest.revision: 47
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cbb327956558e57713040ec8ab1a26d3af78c6c7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711815"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>“日期和时间”字段的行为和格式

在 Common Data Service 中，日期和时间数据类型在许多标准实体字段中使用。 根据字段表示的日期类型，可以选择不同的字段行为：**用户当地时间**、**仅限日期**或**时区无关**。  
  
<a name="Behavior"></a>   

## <a name="date-and-time-field-behavior-and-format"></a>日期及时间字段的行为和格式  

下表包含有关日期和时间字段的行为和格式的信息。  
  
|行为|格式|说明|  
|--------------|------------|-------------------------------|  
|**用户当地时间** |**仅限日期**<br />- 或 -<br />**日期和时间**|这是自定义日期和时间字段的默认行为。<br /><br />字段值在当前用户的当地时间中显示。<br />在 Web 服务中，这些值使用常见的 UTC 时区格式返回。<br /><br />如果选择默认行为，您可以更改此信息一次。 详细信息[更改用户当地时间行为](#change-user-local-behavior)|  
|**仅限日期**|**仅限日期**|无时区转换。<br /><br />值的时间部分始终为 12:00AM。<br />值的日期部分按照 UI 和 Web 服务中指定的方式存储和检索。|  
|**时区无关**|**仅限日期**<br />- 或 -<br />**日期和时间**|无时区转换。<br /><br />日期和时间值按照 UI 和 Web 服务中指定的方式存储和检索。|  

## <a name="change-user-local-behavior"></a>更改用户当地时间行为：

除非托管解决方案发布商阻止此行为，否则您可以将现有的自定义“日期”字段的行为从**用户当地时间**更改为**仅限日期**或**时区无关**。 这是一次性的更改。

更改字段行为将影响字段行为更改后添加或修改的字段值。 数据库中的现有字段值仍然是 UTC 时区格式。 若要将现有字段值的行为从 UTC 更改为“仅限日期”，您可能需要借助开发人员以编程方式进行更改。 详细信息：[转换数据库中的现有日期和时间值的行为](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#convert-behavior-of-existing-date-and-time-values-in-the-database)。 

> [!WARNING]
> 在更改现有日期和时间字段的行为之前，应查看字段的所有依赖项，如业务规则、工作流和计算或汇总字段，确保行为更改没有导致出现问题。 在更改日期和时间字段的行为后，您应该打开依赖于更改的字段的每个业务规则、工作流、计算字段和汇总字段，查看信息，然后保存记录以确保使用了最新的日期和时间字段的行为和值。 

### <a name="change-behavior-during-a-solution-import"></a>在解决方案导入期间更改行为

在使用**用户当地时间**行为导入包含“日期”字段的解决方案时，您可能可以选择将行为更改为**仅限日期**或**时区无关**。  

### <a name="prevent-changing-behavior"></a>阻止更改行为

如果您在托管解决方案中分发自定义日期字段，您可以阻止使用您的解决方案的用户通过将 **CanChangeDateTimeBehavior** 托管属性设置为 **False** 来更改行为。 详细信息：[字段托管属性](set-managed-properties-metadata.md#field-managed-properties)
  
## <a name="use-cases"></a>使用案例

请考虑以下**仅限日期**和**时区无关**行为的使用案例。

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>仅限日期情形：生日和纪念日

仅限日期行为适用于不需要有关一天的时间和时区的信息的情况，如生日或纪念日。 使用此选择，全球所有应用用户将看到完全相同的日期值。  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>时区无关情形：酒店入住登记

如果不需要时区信息（如酒店入住登记时间），您可以使用此行为。 使用此选择，全球所有应用用户将看到相同的日期和时间值。  


## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>“仅限日期”行为不支持的日期和时间查询运算符  

以下与日期和时间相关的查询运算符对**仅限日期**行为是无效的。 当这些运算符之一用于查询时，会引发无效运算符异常错误。  
  
- X 分钟以前  
- X 小时以前  
- 最近 X 小时  
- 今后 X 小时  

  
### <a name="see-also"></a>另请参阅

[创建和编辑字段](create-edit-fields.md)<br />
[定义计算字段以自动化手动计算](define-calculated-fields.md)<br />
[字段托管属性](set-managed-properties-metadata.md#field-managed-properties)<br />
[托管属性](solutions-overview.md#managed-properties)

