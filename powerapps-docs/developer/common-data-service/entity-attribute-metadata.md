---
title: 特性元数据 | Microsoft Docs
description: 了解如何在 Common Data Service for Apps 中使用特性元数据。
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/12/2018
ms.author: jdaly
ms.openlocfilehash: efe04d9bd9c761f432d16d4c9304c52e55503aeb
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="attribute-metadata"></a>特性元数据

实体包含特性的集合，这些特性表示可在每条记录中包含的数据。 开发人员需要了解不同类型的特性以及如何使用它们。 

详细信息：[Dynamics 365 客户参与开发人员指南：实体特性介绍](/dynamics365/customer-engagement/developer/introduction-entity-attributes)

## <a name="attribute-names"></a>特性名称

与实体一样，每个特性在创建后具有唯一的名称。 此名称以多种方式表示：


|名称 |说明  |
|---------|---------|
|`SchemaName`|通常情况下，是逻辑名称的帕斯卡拼写版本。 例如，`AccountNumber`|
|`LogicalName`|全部小写的名称。 例如，`accountnumber`|

创建自定义特性时，所选名称前将添加解决方案发布者的自定义前缀值，该发布者与其中创建了该特性的解决方案相关联。

特性创建后，无法更改其名称。

每个特性还具有两个属性，可显示已经过本地化的值。 这些值用于引用应用中的特性。

|名称 |说明  |
|---------|---------|
|`DisplayName`|通常与架构名称相同，但可以包含空格。 也即，帐号|
|`Description`|描述特性或为用户提供指导的短句。 例如，输入账户的 ID 号或代码，用于快速搜索和识别系统视图中的帐户。<br />在模型驱动的应用中，当用户将鼠标悬停在窗体中此特性的字段上时，将显示此信息。|


这些是用于引用应用中特性的可本地化的值。 可随时更改这些值。 要添加或编辑本地化的值，请参阅 [Dynamics 365 客户参与自定义指南：将自定义实体和字段文本翻译成其他语言](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation)。

## <a name="attribute-types"></a>特性类型

`AttributeTypeName` 属性描述特性的类型。 此属性包含类型 `AttributeTypeDisplayName` 的值，该值为现有的每个不同类型的特性提供标签。 

> [!NOTE]
> 不要与 `AttributeType` 属性混淆。 此旧属性中的值大多与 `AttributeTypeName` 一致，除了一点，它将 `ImageType` 特性显示为 `Virtual`。 应指示为 `AttributeTypeName` 属性而非 `AttributeType` 属性。

在下表中：

- 这些类型按类别分组以供比较。
- 对于每个 `AttributeTypeDisplayName` 值，只要可行，均包含相应的 .NET 程序集 [AttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.attributemetadata) 派生类。 这些类型与 `AttributeTypeDisplayName` 标签间不存在 1:1 的关系。
- 那些可创建为自定义特性的特性类型包括 UI 中显示的相应标签。


|类别|AttributeTypeDisplayName/<br />AttributeMetadata 类型|可创建/<br />标签|说明  |
|---------|---------|---------|---------|
|类别|`BooleanType`<br />[BooleanAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.booleanattributemetadata)|是<br />**两个选项**|包含两个选项中的选定选项值，这两个选项通常指示 true 或 false 值。<br />详细信息：[选项集](#option-sets)|
|类别|`EntityNameType`<br />[EntityNameAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitynameattributemetadata)|否|包含与系统中的实体相对应的选项值。 仅供内部使用。|
|类别|`MultiSelectPicklistType`<br />[MultiSelectPicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.multiselectpicklistattributemetadata)|是<br />**多选选项集**|包含可选多个选项的多选选项值。<br />详细信息： <br />[选项集](#option-sets)<br />[Dynamics 365 客户参与开发人员指南：多选列表特性](/dynamics365/customer-engagement/developer/multi-select-picklist)|
|类别|`PicklistType`<br />[PicklistAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.picklistattributemetadata)|是<br />**选项集**|包含可选择一个选项的选定选项值。<br />详细信息：[选项集](#option-sets)|
|类别|`StateType`<br />[StateAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stateattributemetadata)|否|包含描述实体记录状态的选项值。<br />详细信息：[选项集](#option-sets)|
|类别|`StatusType`<br />[StatusAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.statusattributemetadata)|否|包含描述实体记录状态原因的选项值。<br />详细信息：[选项集](#option-sets)|
|集合|`CalendarRulesType`|否|包含 `CalendarRules` 实体记录的集合。<br />无使用此类型的特性。 生成代理时，代码生成工具将创建元数据中不存在的两个模拟特性。 这些特性表示与实体记录具有一对多关系的日历规则记录的视图。|
|集合|`PartyListType`|否|包含 `ActivityParty` 实体记录的集合。<br />详细信息：[ActivityParty 实体](#activityparty-entity)|
|日期和时间|`DateTimeType`<br />[DateTimeAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.datetimeattributemetadata)|是<br />**日期和时间**|包含日期和时间值。<br />所有日期和时间特性支持的最早值为 1753 年 1 月 1 日中午 12 点。|
|图像|`ImageType`<br />[ImageAttributeMetadata]()|是<br />**图像**|包含用于支持检索实体记录图像数据的数据。<br />详细信息：[实体图像](entity-metadata.md#entity-images)|
|托管的属性|`ManagedPropertyType`<br />[ManagedPropertyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.imageattributemetadata)|否|包含的数据描述当存储在实体记录中的解决方案组件包含在托管解决方案中时，是否可自定义。<br />详细信息：[托管的属性](introduction-solutions.md#managed-properties)|
|数量|`BigIntType`<br />[BigIntAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.bigintattributemetadata)|否|包含 `BigInt` 值。 仅供内部使用。|
|数量|`DecimalType`<br />[DecimalAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.decimalattributemetadata)|是<br />**十进制数字**|包含 `Decimal` 值。 `Precision` 属性设置精度级别。|
|数量|`DoubleType`<br />[DoubleAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.doubleattributemetadata)|是<br />**浮点数**|包含 `Double` 值。 `Precision` 属性设置精度级别。|
|数量|`IntegerType`<br />[IntegerAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.integerattributemetadata)|是<br />**整数**|包含 `Int` 值|
|数量|`MoneyType`<br />[MoneyAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.moneyattributemetadata)|是<br />**货币**|包含 `Decimal` 值。 `PrecisionSource` 属性确定设置精度级别的位置。<br />0：`Precision` 属性<br />1：`Organization.PricingDecimalPrecision` 特性<br />2：实体记录中的 `TransactionCurrency.CurrencyPrecision` 特性|
|参考|`CustomerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|是<br />**客户**|包含对帐户或联系人实体记录的引用。|
|参考|`LookupType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|是<br />**查找**|包含对实体记录的引用。 有效记录的逻辑名称通常存储在特性的 `Targets` 属性中。|
|参考|`OwnerType`<br />[LookupAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.lookupattributemetadata)|否|包含对用户或团队实体记录的引用。|
|String|`MemoType`<br />[MemoAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.memoattributemetadata)|是<br />**多行文本**|包含要显示在多行文本框中的字符串值。|
|String|`StringType`<br />[StringAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.stringattributemetadata)|是<br />**单行文本**|包含要显示在单行文本框中的字符串值。|
|唯一标识符|`UniqueidentifierType`<br />[UniqueIdentifierAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.uniqueidentifierattributemetadata)|否|包含 GUID 唯一标识符值。|
|虚拟|`VirtualType`|否|这些特性不能在代码中使用，且通常可以忽略。|


## <a name="supported-operations-and-form-usage-for-attributes"></a>支持的特性操作和窗体用法

每个特性都包含布尔属性，这些属性描述特性可参与的操作类型以及在窗体中的存在形式。

|属性|说明|
|--|--|
|`IsRequiredForForm`|特性是否必须作为窗体中的字段包含在内。|
|`IsValidForCreate`|是否可在创建操作中设置特性值。|
|`IsValidForForm`|特性是否可作为窗体中的字段包含在内。|
|`IsValidForRead`|是否可检索特性值。|
|`IsValidForUpdate`|是否可在更新操作中设置特性值。|

如果尝试在创建或更新操作中为某个对该操作无效的特性设置值，将忽略该值。
如果尝试检索对读取操作无效的特性，将返回 null 值。


## <a name="attribute-requirement-level"></a>特性要求级别

`RequiredLevel` 属性是一个布尔托管属性，用于描述是否需要特性值。

此属性可设置以下值：

|名称|值|UI 标签|说明|
|--|--|--|--|
|`None`|0|**可选**|未指定要求。|
|`SystemRequired`|1|**系统必需**|该特性必须具有值。|
|`ApplicationRequired`|2|**业务必需**|业务要求该属性须具有值。|
|`Recommended`|3|**业务建议**|建议特性具有值。|

Common Data Service 仅对系统创建的特性强制执行 `SystemRequired` 选项。 无法将自定义特性设置为使用 `SystemRequired` 选项。 

模型驱动的应用强制执行 `ApplicationRequired` 选项，并为 `Recommended` 选项使用另一种表示形式。 自定义客户端的创建者可使用此信息来要求类似的验证或表示形式选项。

因为这是一个托管属性，所以作为托管解决方案的发布者，你可以决定解决方案的使用者是否可以更改解决方案中特性的这些设置。

详细信息：[托管的属性](introduction-solutions.md#managed-properties)


## <a name="rollup-and-calculated-attributes"></a>汇总和计算特性

借助计算和汇总属性，用户无需手动执行计算，这样便可专注于工作。 系统管理员可以定义一个字段来包含许多常见计算的值，而无需开发人员的协助。 开发人员也可以利用平台功能（而不是在其代码中）执行这些计算。

详细信息： 
- [Dynamics 365 客户参与自定义指南：定义用于聚合值的汇总字段](/dynamics365/customer-engagement/customize/define-rollup-fields)
- [Dynamics 365 客户参与自定义指南：计算和汇总特性](/dynamics365/customer-engagement/customize/define-calculated-fields)
- [Dynamics 365 客户参与开发人员指南：计算和汇总特性](/dynamics365/customer-engagement/developer/calculated-rollup-attributes)

## <a name="attribute-format"></a>特性格式

特性的格式值控制其在模型驱动的应用中的显示方式。 自定义应用的开发人员可使用此信息来创建类似体验。

### <a name="integer-formats"></a>整数格式

结合使用 `Format` 属性和整数特性来显示此类型的备选用户体验。

|选项|说明|
|--|--|
|`None`|显示文本框以编辑数值|
|`Duration`|显示包含时间间隔的下拉列表。 用户可从列表中选择一个值或键入一个表示分钟数的整数值。|
|`TimeZone`|显示包含时区列表的下拉列表。|
|`Language`|显示下拉列表，其中包含已为组织启用的语言列表。 如果未启用其他语言，则只有基本语言这一个选项。 保存的值为该语言的 LCID 值。|

### <a name="string-formats"></a>字符串格式

结合使用 `FormatName` 属性和字符串特性来设置 [StringFormatName 类](/dotnet/api/microsoft.xrm.sdk.metadata.stringformatname)中的值，用于控制字符串特性的格式设置方式。

|名称|说明|
|--|--|
|`Email`|该窗体字段将文本值作为电子邮件地址进行验证并在该字段中创建一个 mailto 链接。|
|`PhoneNumber`|该窗体字段包含一个链接，用于使用 Skype 发起电话呼叫。|
|`PhoneticGuide`|仅供内部使用。|
|`Text`|该窗体显示一个文本框。|
|`TextArea`|该窗体显示一个文本区域字段。|
|`TickerSymbol`|该窗体显示一个链接，该链接打开后会显示一个证券股票代号的引文。|
|`URL`|该窗体显示一个用于打开该 URL 的链接。|
|`VersionNumber`|仅供内部使用。|

### <a name="date-and-time-formats"></a>日期和时间格式

`DateTimeBehavior` 属性，用于控制日期和时间特性的行为。
有三个选项：

|选项|简短说明|
|--|--|
|`UserLocal`|在系统中将日期和时间值存储为 UTC 值。|
|`DateOnly`|在系统中将实际日期和时间值按 12:00 AM (00:00:00) 的形式进行存储。|
|`TimeZoneIndependent`|将实际日期和时间值存储在系统中，而不考虑用户时区。|

使用 `Format` 属性控制模型驱动的应用中值的显示方式，而不考虑 `DateTimeBehavior`。

|选项|说明|
|--|--|
|DateAndTime|显示完整的日期和时间|
|DateOnly|仅显示日期。|

详细信息：[Dynamics 365 客户参与开发人员指南：日期和时间特性的行为和格式](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute)

## <a name="auto-number-attributes"></a>自动编号特性

可为任何实体添加自动编号特性。 目前，可通过编程方式添加该特性。 没有要添加此类型特性的用户界面。
详细信息：[Dynamics 365 客户参与开发人员指南：创建自动编号特性](/dynamics365/customer-engagement/developer/create-auto-number-attributes)

## <a name="option-sets"></a>选项集

显示一组选项的特性可以引用由属性定义的一组选项，也可以引用可由多个属性共享的单独一组选项。 当一个特性中的值也适用于其他特性时，这尤其有用。 通过引用一组常用选项，可将这些选项保留在同一位置。 这些可共享的选项集是全局选项集。 那些在特性中定义的选项集是本地选项集。

### <a name="retrieve-options-data"></a>检索选项数据
组织服务提供请求类，可用于检索供特性使用的选项。

#### <a name="use-the-organization-service-to-retrieve-options"></a>使用组织服务检索选项

每个具有选项的特性继承自 [EnumAttributeMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata)，并包含[选项集属性](/dotnet/api/microsoft.xrm.sdk.metadata.enumattributemetadata.optionset)。 该属性包含 [OptionSetMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata)，其中包含[选项属性](/dotnet/api/microsoft.xrm.sdk.metadata.optionsetmetadata.options)中的选项。 

借助组织服务，可使用以下消息来检索有关选项集的信息：
|请求类|说明|
|--|--|
|[RetrieveAllOptionSetsRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest) |检索有关所有全局选项集的数据|
|[RetrieveAttributeRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveattributerequest) |检索包含任何本地选项集的特性的相关数据|
|[RetrieveMetadataChangesRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrievemetadatachangesrequest) |基于可包含本地选项集的查询来检索元数据<br />详细信息：[检索和检测对元数据的更改](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata)|
|[RetrieveOptionSetRequest](/dotnet/api/microsoft.xrm.sdk.messages.retrieveoptionsetrequest) |检索有关全局选项集的数据。|

详细信息： 
- [示例：将特性选择列表元数据转储到文件](/dynamics365/customer-engagement/developer/org-service/sample-dump-attribute-picklist-metadata-file)
- [Dynamics 365 客户参与开发人员指南：自定义全局选项集](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)

#### <a name="use-the-web-api-to-retrieve-options"></a>使用 Web API 检索选项

Web API 为选项值查询提供一种 RESTful 样式。 通过检索实体中的属性，可检索本地或全局选项。 以下示例为 [Account](reference/entities/account.md).[AccountCategoryCode property](reference/entities/account.md#BKMK_AccountCategoryCode) 中包含的选项返回 [OptionSetMetadata](/dynamics365/customer-engagement/web-api/optionsetmetadata)。

`GET <organization url>/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(LogicalName='accountcategorycode')/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet`

借助 Web API 还可使用 [RetrieveMetadataChanges 函数](/dynamics365/customer-engagement/web-api/retrievemetadatachanges)。

详细信息：[Dynamics 365 客户参与开发人员指南：使用 Web API 查询元数据 > 查询 EntityMetadata 特性](/dynamics365/customer-engagement/developer/webapi/query-metadata-web-api#querying-entitymetadata-attributes)



## <a name="attribute-mapping"></a>属性映射

在现有实体记录的上下文中创建新实体记录时，可以自动将现有实体记录中的某些值作为新实体记录的默认值进行传输。 这简化了模型驱动应用用户的数据输入。 应用程序用户可查看映射的值，并可在保存实体前对其进行编辑。

对于创建自定义客户端的开发人员，实现同一行为的方法是使用 `InitializeFrom` 消息（组织服务 [InitializeFromRequest 类](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest)或 Web API [ InitializeFrom 函数](/dynamics365/customer-engagement/web-api/initializefrom)）获取配置了默认值的实体数据。

详细信息 
- [Dynamics 365 客户参与自定义指南：映射实体字段](/dynamics365/customer-engagement/customize/map-entity-fields#BKMK_mappingEntityFields)
- [Dynamics 365 客户参与开发人员指南自定义实体和特性映射](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)

### <a name="see-also"></a>另请参阅

[Common Data Service for Apps 实体](entities.md)