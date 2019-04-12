---
title: 通过 Common Data Service 定义引用记录的备用键 | MicrosoftDocs
description: 了解如何在 Common Data Service 中定义可用于引用记录的备用键
ms.custom: ''
ms.date: 06/06/2018
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
ms.assetid: 29e53691-0b18-4fde-a1d0-7490aa227898
caps.latest.revision: 10
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="define-alternate-keys-to-reference-records"></a>定义引用记录的备用键

*备用键*提供准确有效的方式将数据与外部系统集成。 当外部系统不存储在 Common Data Service 中唯一标识记录的全局唯一标识符 (GUID) ID 时这非常重要。 

数据集成系统将使用备用键来使用表示唯一组合的一个或多个实体字段值唯一标识记录。 每个备用键都有一个唯一名称。 

例如，若要使用备用键标识客户记录，您可以使用客户编号或客户编号字段并结合其他一些字段（包含不应更改的值）。

> [!NOTE]
> 尽管您可以通过 PowerApps 定义备用键，在代码中，它们只能通过编程方式使用。 若要了解以编程方式使用备用键的详细信息，请参阅：   
> - [开发人员文档：使用备用键创建记录](/dynamics365/customer-engagement/developer/use-alternate-key-create-record) 
> - [开发人员文档：使用备用键通过 Web API 检索记录](/dynamics365/customer-engagement/developer/webapi/retrieve-entity-using-web-api#retrieve-using-an-alternate-key)

备用键功能的一些好处包括：  
  
- 更快地查找记录。  
- 更可靠的批量数据操作。  
- 利用从不含记录 ID 的外部系统导入的数据简化编程。  
  

## <a name="creating-an-alternate-key"></a>创建备用键

有两个设计器可以用来创建备用键：

|设计器| 说明|
|--|--|
|[PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|提供简单的简化体验，但是有些选项不可用。<br />详细信息：[使用 PowerApps 门户定义备用键](define-alternate-keys-portal.md)|
|解决方案资源管理器|不那么简单，但提供更多灵活性可减少常见要求。<br />详细信息：[使用解决方案资源管理器定义备用键](define-alternate-keys-solution-explorer.md) |

> [!NOTE]
> 您还可以使用以下方法在您的环境中创建备用键：
> - 导入包含备用键定义的解决方案。
> - 开发人员还可以编写代码来创建备用键。 详细信息：[开发人员文档：定义实体的备用键](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)

本主题中的信息将帮助您选择可以使用的设计器。 

除非您需要满足下列要求中的任何一个，否则您应该使用 [PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)创建备用键。

- 在 Common Data Service 默认解决方案以外的解决方案中创建备用键
- 您希望轻松跟踪所创建的跟踪支持索引创建进度的系统作业


## <a name="limits-in-creating-alternate-keys"></a>创建备用键的限制

备用键创建存在一些约束。

### <a name="fields-that-can-be-used-for-alternate-keys"></a>可以用于备用键的字段

仅以下这些字段类型可以用于创建备用键：
 - 十进制
 - 整数
 - 单行文本（字符串）

### <a name="number-of-keys"></a>键数

您最多可以为一个实体定义五个不同的键密钥。
 
### <a name="valid-key-size"></a>有效的键大小

当创建键时，系统会验证该键是否受平台支持，包括键总大小不能违反基于 SQL 的索引约束，如每个键 900 个字节和 16 列。 如果键大小不满足约束，将显示一条错误消息。

### <a name="unicode-characters-in-key-value"></a>键值中的 Unicode 字符

如果用于备用键的字段内的数据将包含以下字符之一 `<`、`>`、`*`、`%`、`&`、`:`、`/`、`\\`，那么修补程序或 upsert 操作将无法运行。 

如果只需要唯一性，此方法没问题，但如果需要在数据集成中使用这些键，那么最好在不包含具有这些字符的数据的字段中创建键。

## <a name="track-the-status-of-the-creation-of-the-alternate-key"></a>跟踪备用键的创建状态。

当创建备用键时，它将启动系统作业来在数据库表上创建索引以对备用键使用的字段强制执行唯一约束。 在这些索引创建前，备用键不会生效。 创建这些索引可能需要花费一些时间，具体取决于系统中的数据量。 

系统作业的状态确定备用键的状态。 备用键可能具有以下状态：
- **挂起**
- **正在进行**
- **Active**
- **失败**

在系统作业完成时，备用键的状态为**可用**，其可以使用。

如果系统作业失败，请找到系统作业查看错误。 系统作业将有一个这样格式的名称：`Create index for {0} for entity {1}`，其中 `0` 是备用键的**显示名称**，`1` 是实体的名称。


> [!NOTE]
> 如果要监视系统作业的状态，应该使用解决方案资源管理器来创建索引。 它将包含系统作业的链接，以便您可以进行监视。 详细信息：[（可选）查看跟踪索引创建的系统作用](define-alternate-keys-solution-explorer.md#optional-view-the-system-job-tracking-creation-of-indexes)
  
  
### <a name="see-also"></a>另请参阅  

[使用 PowerApps 门户定义备用键](define-alternate-keys-portal.md)<br />
[使用解决方案资源管理器定义备用键](define-alternate-keys-solution-explorer.md)<br />
[开发人员文档：定义实体的备用键](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)<br />
[开发人员文档：使用备用键创建记录](/dynamics365/customer-engagement/developer/use-alternate-key-create-record)
