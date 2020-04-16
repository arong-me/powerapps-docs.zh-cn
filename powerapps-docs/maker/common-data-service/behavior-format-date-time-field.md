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
ms.openlocfilehash: d89f040bf7030706f9f7288021249e3b78dcd3e5
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "3167046"
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

如果您在托管解决方案中分发自定义日期字段，您可以阻止使用您的解决方案的用户通过将 **CanChangeDateTimeBehavior** 托管属性设置为 **False** 来更改行为。 详细信息：[设置字段的托管属性](set-managed-properties-for-field.md)
  
## <a name="use-cases"></a>使用案例 

请考虑以下**仅限日期**和**时区无关**行为的使用案例。

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>仅限日期情形：生日和纪念日

仅限日期行为适用于不需要有关一天的时间和时区的信息的情况，如生日或纪念日。 使用此选择，全球所有应用用户将看到完全相同的日期值。  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>时区无关情形：酒店入住登记

如果不需要时区信息（如酒店入住登记时间），您可以使用此行为。 使用此选择，全球所有应用用户将看到相同的日期和时间值。  


## <a name="best-practices-for-using-time-zone"></a>使用时区的最佳实践

### <a name="for-my-datetime-field-i-was-expecting-utclocal-and-i-am-seeing-the-opposite-value"></a>对于我的“日期/时间”字段，我预期的是（UTC/当地），却看到了相反的值

这是由于实体字段设置和应用窗体设置之间缺少一致性引起的。 将实体字段配置为“时区无关”或“用户当地时间”时，将确定从存储中检索数据时是否遵守时区偏移。 但是，应用窗体还具有 UTC 或“当地”设置。 
 
这将告诉窗体如何解释它从 Common Data Service 接收的数据。 如果从存储中检索的数据与时区无关，但窗体设置为“当地”，UTC 数据将根据用户在其配置文件中的时区以用户当时间显示。 反之亦然，如果将窗体设置为 UTC，来自存储的用户当地值将显示为 UTC。 幸运的是，可以在不破坏现有记录的情况下修改窗体的日期时区值。

### <a name="i-picked-date-only-in-my-entity-field-but-my-form-is-showing-a-time-picker-along-with-the-date"></a>我在实体字段中选择了“仅限日期”，但是我的窗体显示了时间选取器以及日期

如果您为“仅限日期”字段选择了时区无关或用户当地时间的行为，则会发生这种情况。 在 Common Data Service 中，默认情况下它将存储 00:00:00 时间，但是如果您将字段添加到窗体中，它将假定您还需要设置时间。 如果您将时间选取器保留在窗体中，用户可以输入时间，该时间将被保存为 00:00:00 以外的其他值。 如何解决此问题
* 编辑窗体，删除时间选取器和关联的公式。 这会将时间保存为 00:00:00，但仍会允许基于时区的日期计算。
* 如果您的字段当前已设置为用户当地时间，并且您不需要按时区计算日期，您可以将其更改为“仅限日期”。 这是一项永久性的更改，无法撤消。 不能对时区无关的行为字段进行此更改。 请始终小心更改行为，因为其他应用、插件或工作流可能依赖于此数据。

### <a name="i-have-a-date-only-field-but-it-is-showing-the-wrong-date-for-some-users"></a>我有一个“仅限日期”字段，但是它为某些用户显示了错误的日期
如果出现这种情况，请检查为“仅限日期”字段设置的行为。 如果该字段设置为时区无关或用户当地时间，所包含的时间戳将导致日期对不同用户显示不同值。 UTC 或“当地”的窗体显示设置将确定显示的日期是使用用户的时区设置计算，还是显示为 UTC 值。 将窗体值更改为 UTC 而不是用户当地时间会阻止时区偏移的计算，并将为已保存记录显示 UTC 日期。 或者，如果您需要此值为不改变的静态日期，并且字段当前是用户当地时间，您可以将字段行为更改为“仅限日期”。 请谨慎操作，此更改不可撤消。

### <a name="my-scriptplug-in-is-supposed-to-intercept-the-date-submitted-using-the-universal-client-before-the-user-local-conversion-occurs-but-instead-it-is-being-treated-as-user-local-data"></a>我的（脚本/插件）应该在用户当地时间转换发生之前拦截使用通用客户端提交的日期，但却将其视为用户当地时间数据 

当在 UTC 和用户当地时间之间转换数据时，Web 客户端和通用客户端的行为略有不同。 在 Web 客户端中，日期被输入到客户端中，传递到提供的 API，之后被转换为用户当地时间。 这允许脚本/插件检索数据，并在将数据传递到平台服务并转换为用户当地时间之前执行操作。 在通用客户端中，将日期转换为用户当地时间值的过程发生在将数据传递到 API 之前，因此，提供的数据将不是 UTC 日期，而是基于检索或发布数据的用户的用户当地日期。 若要解决此问题，用户可以执行下列操作之一：

* 将窗体更改为时区无关，这将保留 UTC 值。 仅当用户不需要窗体以用户当地时间显示时，此方法才有效。
* 修改其脚本以检测使用的时区偏移，在脚本中重新计算回 UTC，然后执行操作。

## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>“仅限日期”行为不支持的日期和时间查询运算符  

以下与日期和时间相关的查询运算符对**仅限日期**行为是无效的。 当这些运算符之一用于查询时，会引发无效运算符异常错误。  
  
- X 分钟以前  
- X 小时以前  
- 最近 X 小时  
- 今后 X 小时  

  
### <a name="see-also"></a>另请参阅

[创建和编辑字段](create-edit-fields.md)<br />
[定义计算字段以自动化手动计算](define-calculated-fields.md)<br />
[字段托管属性](set-managed-properties-metadata.md#view-and-edit-field-managed-properties)<br />
[托管属性](solutions-overview.md#managed-properties)  
[博客：在 Common Data Service 中处理时区](https://powerapps.microsoft.com/en-us/blog/working-with-time-zones-in-the-common-data-service/)


