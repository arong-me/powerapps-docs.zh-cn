---
title: RDL 沙盒 | MicrosoftDocs
ms.custom: ''
ms.date: 09/30/2017
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
ms.assetid: 8ec72014-9f0c-4964-ac67-24419b054e91
caps.latest.revision: 13
author: Mattp123
ms.author: matp
manager: amyla
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: f936dc4c6b78096b74b650bf8426ba1d78c41d19
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711375"
---
# <a name="rdl-sandboxing"></a>RDL 沙盒。 

在 Common Data Service 中，报表在沙盒模式下运行。 这是通过在 SQL Server Reporting Services 中启用 报表定义语言 (RDL) 沙盒功能实现的。 RDL 沙盒功能使您能够检测特定类型的资源，并限制其使用。 因此，PowerApps 模型驱动应用程序中的某些功能可能不可用。 有关详细信息，请参阅 [MSDN：启用和禁用 RDL 沙盒](https://msdn.microsoft.com/library/ee210591.aspx)。  
  
 本主题的以下各节介绍 Common Data Service 中的当前 RDL 沙盒配置设置。  
    
<a name="BKMK_Max"></a>   
## <a name="limits-of-the-array-result-length-and-string-result-length"></a>数组结果长度和字符串结果长度的限制  
 RDL 表达式的数组返回值中允许的最大项数已从 250 增加到 102400。 RDL 表达式的字符串返回值中允许的最大项数也已从 250 增加到 102400。 这样就可以包含大小达 75 KB 的图像和徽标，并将存储在使用 Base64 编码的数据库中。  
  
 MaxResourceSize 设置为 2000。 这让您可以在图表中加入最大为1500 KB 的外部图像。 详细信息：[ TechNet：添加外部图像（报表生成器和 SSRS）](https://technet.microsoft.com/library/dd220527.aspx)  
  
<a name="BKMK_Allowed"></a>   
## <a name="allowed-types-and-denied-members"></a>允许的类型和拒绝的成员  
 RDL 沙盒功能使您能够创建批准类型的列表和拒绝成员的列表。 批准类型的列表称为“允许列表”。 RDL 表达式中不允许的拒绝成员的列表称为“阻止列表”。  
  
 下表包含 Common Data Service 的沙盒模式中提供的允许的类型和拒绝的成员的列表。  
  
|允许的类型|拒绝的成员|  
|-------------------|--------------------|  
|`System.Array`|CreateInstance|  
||Finalize|  
||GetType|  
||MemberwiseClone|  
||调整大小|  
|||  
|`System.DateTime`|FromBinary|  
||GetDateTimeFormats|  
||GreaterThan|  
||GreaterThanOrEqual|  
|||  
|||  
|`System.Object`|GetType|  
||MemberwiseClone|  
||ReferenceEquals|  
|||  
|`System.DbNull`|Finalize|  
||MemberwiseClone|  
||GetObjectData|  
||GetTypeCode|  
|||  
|`System.Math`|BigMul|  
||DivRem|  
||IEEERemainder|  
||E|  
||PI|  
||Pow|  
|`System.String`||  
|`System.TimeSpan`|小时数|  
||TicksPerDay|  
||TicksPerHour|  
||TicksPerMillisecond|  
||TicksPerMinute|  
||TicksPerSecond|  
||零|  
||TryParse|  
||TryParseExact|  
|`System.Convert`|ChangeType|  
||IConvertible.ToBoolean|  
||IConvertible.ToByte|  
||IConvertible.ToChar|  
||IConvertible.ToDateTime|  
||IConvertible.ToDecimal|  
||IConvertible.ToDouble|  
||IConvertible.ToInt16|  
||IConvertible.ToInt32|  
||IConvertible.ToInt64|  
||IConvertible.ToSByte|  
||IConvertible.ToSingle|  
||IConvertible.ToType|  
||IConvertible.ToUInt16|  
||IConvertible.ToUInt32|  
||IConvertible.ToUInt64|  
|`System.StringComparer`|创建​​|  
||Finalize|  
|||  
|`System.TimeZone`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`System.Uri`|Unescape|  
||分析|  
||Escape|  
||Finalize|  
|||  
|`System.UriBuilder`|Finalize|  
|||  
|`System.Globalization.CultureInfo`|ClearCachedData|  
|||  
|`System.Text.RegularExpressions.Match`|空|  
||NextMatch|  
||结果|  
||Synchronized|  
|||  
|||  
|`System.Text.RegularExpressions.Regex`|CacheSize|  
||CompileToAssembly|  
||GetGroupNames|  
||GetGroupNumbers|  
||GetHashCode|  
||Unescape|  
||UseOptionC|  
||UseOptionR|  
||capnames|  
||caps|  
||capsize|  
||capslist|  
||roptions|  
||pattern|  
||factory|  
||IsMatch|  
||Matches|  
||Iserializable.GetObjectData|  
||InitializeReferences|  
||RightToLeft|  
||选项​​|  
|||  
|||  
|`Microsoft.VisualBasic.Constants`|vbAbort|  
||vbAbortRetryIgnore|  
||vbApplicationModal|  
||vbArchive|  
||vbBinaryCompare|  
||vbCancel|  
||vbCritical|  
||vbDefaultButton1|  
||vbDefaultButton2|  
||vbDefaultButton3|  
||vbExclamation|  
||vbFormFeed|  
||vbGet|  
||vbHidden|  
||vbHide|  
||vbHiragana|  
||vbIgnore|  
||vbInformation|  
||vbKatakana|  
||vbLet|  
||vbLinguisticCasing|  
||vbMaximizedFocus|  
||vbMinimizedFocus|  
||vbMinimizedNoFocus|  
||vbMsgBoxHelp|  
||vbMsgBoxRight|  
||vbMsgBoxRtlReading|  
||vbMsgBoxSetForeground|  
||vbNo|  
||vbNormal|  
||vbNormalFocus|  
||vbNormalNoFocus|  
||vbObjectError|  
||vbOK|  
||vbOKCancel|  
||vbOKOnly|  
||vbQuestion|  
||vbReadOnly|  
||vbRetry|  
||vbRetryCancel|  
||vbSet|  
||vbSystem|  
||vbSystemModal|  
||VbTypeName|  
||vbVolume|  
||零|  
|`Microsoft.VisualBasic.ControlChars`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Conversion`|Err|  
||ErrorToString|  
||Fix|  
|||  
|`Microsoft.VisualBasic.DateInterval`|Finalize|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Financial`|Finalize|  
||GetType|  
||MemberwiseClone|  
||IRR|  
||NPV|  
||MIRR|  
|||  
|||  
|`Microsoft.VisualBasic.Interaction`|AppActivate|  
||Beep|  
||CallByName|  
||Command|  
||CreateObject|  
||Environ|  
||Finalize|  
||GetAllSettings|  
||GetObject|  
||GetSetting|  
||GetType|  
||InputBox|  
||MemberwiseClone|  
||MsgBox|  
||SaveSetting|  
||Shell|  
||选择|  
||开关|  
|||  
|||  
|`Microsoft.VisualBasic.Information`|Erl|  
||Err|  
||IsError|  
||IsDBNull|  
||Lbound|  
||Ubound|  
||SystemTypeName|  
|||  
|`Microsoft.VisualBasic.Strings`|Finalize|  
||GetType|  
||MemberwiseClone|  
||Lset|  
||Rset|  
|||  
|`Microsoft.Crm.Reporting.RdlHelper`||  
  
<a name="BKMK_Denied"></a>   
## <a name="common-denied-members"></a>常见拒绝的成员  
 下表包含允许的类型中常见的拒绝成员列表：  
  
||  
|-|  
|DateString|  
|持续时间|  
|Equality|  
|Equals|  
|Erl|  
|Filter|  
|GetChar|  
|GroupNameFromNumber|  
|GroupNumberFromName|  
|Int|  
|MaxValue|  
|MinValue|  
|Negate|  
|Timer|  
|TimeString|  
|ToBinary|  
|Finalize|  
|GetType|  
|MemberwiseClone|  
  

