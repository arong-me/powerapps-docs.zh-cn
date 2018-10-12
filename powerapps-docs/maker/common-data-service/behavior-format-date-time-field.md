---
title: Common Data Service for Apps 中“日期和时间”字段的行为和格式 | Microsoft Docs
ms.custom: ''
ms.date: 05/25/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 2f62f2433fe959e3713df544628db186b801731e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669275"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>“日期和时间”字段的行为和格式

在 Common Data Service for Apps 中，很多标准实体字段都使用了“日期和时间”数据类型。 根据字段代表的日期类型，可以选择不同的字段行为：“用户当地时间”、“仅日期”或“时区无关”。  
  
<a name="Behavior"></a>   

## <a name="date-and-time-field-behavior-and-format"></a>“日期和时间”字段的行为和格式  

下表包含“日期和时间”字段的行为和格式的相关信息。  
  
|行为|格式|描述|  
|--------------|------------|-------------------------------|  
|**用户当地时间** |**仅日期**<br />- 或 -<br />**日期和时间**|这是自定义日期和时间字段的默认行为。<br /><br />字段值显示为当前用户的当地时间。<br />在 Web 服务中，使用常规的 UTC 时区格式返回这些值。<br /><br />如果选择默认行为，可对此进行一次更改。 详细信息：[更改用户当地时间行为](#change-user-local-behavior)|  
|**仅日期**|**仅日期**|不存在时区转换。<br /><br />该值的时间部分始终为上午 12:00。<br />将按 UI 和 Web 服务中的指定内容存储和检索该值的日期部分。|  
|**时区无关**|**仅日期**<br />- 或 -<br />**日期和时间**|不存在时区转换。<br /><br />将按 UI 和 Web 服务中的指定内容存储和检索日期和时间值。|  

## <a name="change-user-local-behavior"></a>更改用户当地时间行为：

只要托管解决方案的发布者未阻止此操作，即可将现有自定义“日期”字段的行为从“用户当地时间”更改为“仅日期”或“时区无关”。 这种更改是一次性的。

更改字段行为会影响在此次更改后添加或修改的字段值。 现有字段值以 UTC 时区格式保留在数据库中。 若要将现有字段值的行为从 UTC 更改为“仅日期”，可能需要向开发人员寻求编程帮助。 详细信息：[转换数据库中现有日期和时间值的行为](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#convert-behavior-of-existing-date-and-time-values-in-the-database)。 

> [!WARNING]
> 在更改现有日期和时间字段的行为之前，应查看该字段的所有依赖项，例如业务规则、工作流、计算字段或汇总字段，以便确保更改该行为不会带来任何问题。 在更改日期和时间字段的行为后，应打开依赖于该更改字段的各个业务规则、工作流、计算字段和汇总字段，检查这些信息并进行保存，以便确保使用最新的日期和时间字段行为和值。 

### <a name="change-behavior-during-a-solution-import"></a>在导入解决方案的过程中更改行为

若导入的解决方案包含使用“用户当地时间”行为的日期字段，可选择将该行为更改为“仅日期”或“时区无关”。  

### <a name="prevent-changing-behavior"></a>阻止更改行为

如果要在托管解决方案中分发自定义日期字段，可以通过将“CanChangeDateTimeBehavior”托管属性设置为“False”来阻止使用该解决方案的人员更改行为。 详细信息：[字段托管属性](set-managed-properties-metadata.md#field-managed-properties)
  
## <a name="use-cases"></a>用例

请思考以下“仅日期”和“时区无关”行为的用例。

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>“仅日期”方案：生日和纪念日

“仅日期”行为适合用于无需当天具体时间和时区信息的情况与，例如生日和纪念日。 选择此行为后，世界各地所有应用用户都会看到完全相同的日期值。  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>“时区无关”方案：酒店入住

此行为适用于不需要时区信息的情况，例如酒店入住时间。 选择此行为后，世界各地所有应用用户都会看到相同的日期和时间值。  


## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>“仅日期”行为不支持日期和时间查询运算符  

以下与日期和时间相关的查询运算符对于“仅日期”行为无效。 若在查询中使用了其中某个运算符，则会引发无效运算符异常错误。  
  
- Older Than X Minutes  
- Older Than X Hours  
- Last X Hours  
- Next X Hours  

  
### <a name="see-also"></a>另请参阅

[创建并编辑字段](create-edit-fields.md)<br />
[定义计算字段以自动化手动计算](define-calculated-fields.md)<br />
[字段托管属性](set-managed-properties-metadata.md#field-managed-properties)<br />
[托管​​属性](solutions-overview.md#managed-properties)

