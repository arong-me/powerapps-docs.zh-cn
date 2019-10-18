---
title: 类型表 |Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 41ea27ac-65b6-45a4-ae03-5f8d02dfc67b
ms.openlocfilehash: 058580b8f39417ccc5e77e7ac96a51bfc95939a1
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "72338749"
---
|Value|描述|
|--|--|
|`Currency`|介于-922337203685477 和922337203685477之间的货币值可以在此字段中。 您可以设置精度级别或选择以特定货币或组织使用的单个标准精度作为精度。|
|`DateAndTime.DateAndTime`|显示日期和时间。|
|`DateAndTime.DateOnly`|仅显示日期。|
|`Decimal`|对于-100000000000 和-100000000000 之间的值，最多可使用10个小数位数。 可以指定精度级别和最大值和最小值。|
|`Enum`|枚举数据类型。|
|`FP`|对于-100000000000 和-100000000000 之间的值，最多可使用5个小数位数。 可以指定精度级别和最大值和最小值。 |
|`Multiple`|此字段最多可包含1048576个文本字符。 您可以将最大长度设置为小于此长度。 将此字段添加到窗体时，可以指定字段的大小。|
|`OptionSet`|此字段提供一组选项。 每个选项都有一个数值和标签。 添加到窗体时，此字段显示一个控件，以便用户仅选择一个选项。 |
|`SingleLine.Email`|此文本提供了一个用于打开用户的电子邮件应用程序的 mailto 链接。|
|`SingleLine.Phone`|在 web 应用程序中，如果计算机上已安装客户端，则字段将为 "已启用"，以便使用 Skype 或 Lync 启动调用。 电话服务提供程序选择位于 "系统设置" 的 "常规" 选项卡的底部。对于平板电脑的 Dynamics 365，Skype 是唯一可用的电话服务提供程序。|
|`SingleLine.Text`|此选项只显示文本。|
|`SingleLine.TextArea`|此格式选项可用于显示多行文本。 但对于超过4000个字符，如果需要大量文本，则 "多行文本" 字段是更好的选择。|
|`SingleLine.Ticker`|对于大多数语言，将启用文本作为打开 MSN Money 网站的链接，以显示有关股票行情所代表股票价格的详细信息。对于某些东亚语言，该窗口将打开该股票代号的 Bing 搜索结果。|
|`SingleLine.URL`|此文本提供了一个用于打开指定页面的超链接。 任何不以有效协议开头的文本都将有 "http://"。此字段仅允许使用 HTTP、HTTPS、FTP、FTPS、ONENOTE 和电话协议。|
|`TwoOptions`|此字段提供两个选项。 每个选项的数值均为0或1，对应于 false 或 true 值。 每个选项还有一个标签，以便 true 或 false 值可以表示为 "是" 和 "否"、"热"、"已关闭"、"关闭" 或要显示的任何一对标签。|
|`Whole.None`|此选项只显示数字。|

## <a name="value-elements-that-are-not-supported"></a>不支持的值元素

当前不支持以下 `of-type` 特性值：

|Value|描述|
|-----|------|
|`Whole.Duration`|此 format 选项可用于显示持续时间选项的列表。 但数据库中存储的数据始终是几分钟的时间。 此字段的外观类似于下拉列表，提供了建议的选项，如1分钟、15分钟、30分钟，一直到3天。 用户可以选择这些选项。 但是，用户还可以只键入几分钟的时间，并将其解析为该时间段。|
|`Whole.Timezone`|此选项显示时区的选择列表，如（GMT-12:00）国际日期行西部和（GMT-08:00）太平洋时间（美国 &）。 其中每个区域都存储为一个数字。 例如，对于时区（GMT-08:00）太平洋时间（美国 & 加拿大），TimeZoneCode 为4。 详细信息： [TimeZoneCode 类（Sdk 程序集）](https://docs.microsoft.com/en-us/previous-versions/dynamics-crm4/developers-guide/bb959779(v=msdn.10))|
|`Whole.Language`|此选项显示为你的组织设置的语言列表。 这些值显示为语言名称的下拉列表，但使用 LCID 代码将数据存储为数值。 语言代码是四位数或五位数区域设置 ID。 有效区域设置 ID 值可以在[区域设置 ID (LCID) 图表](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms912047(v=winembedded.10))中找到。|
|`Lookup.Simple`|允许对特定实体进行单一引用。 所有自定义查找都是此类型。|
|`Lookup.Customer`|允许单个引用帐户或联系人记录。 这些查找可用于 "机会"、"案例"、"报价单"、"订单" 和 "发票" 实体。 这些实体还具有单独的帐户和联系人查找，如果客户始终是一种类型，则可以使用它们。 您也可以同时包含这两者，而不是使用客户查找。|
|`Lookup.Owner`|允许单个引用团队或用户记录。 所有团队或用户拥有的实体都有其中的一个。|
|`Lookup.PartyList`|允许多个实体引用多个实体。 可在电子邮件实体的 "**收件人**" 和 **"抄送"** 字段中找到这些查找。 它们还用于电话和约会实体。|
|`Lookup.Regarding`|允许单个引用多个实体。 在活动中使用的 "关于" 字段中可以找到这些查找。|
|`MultiSelectOptionSet`|可以通过添加多选字段来自定义表单（主视图、快速创建和快速视图）和电子邮件模板。 添加多选选项集字段时，可以指定将可供用户选择的多个值。 用户填写表单时，他们可以选择一个、多个或所有显示在下拉列表中的值。|
