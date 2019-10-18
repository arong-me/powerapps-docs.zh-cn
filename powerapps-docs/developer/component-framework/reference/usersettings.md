---
title: UserSettings | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c237ff96-9268-4068-9d61-aea0bdc79fc2
ms.openlocfilehash: 5325091d8f82ffd98cfc4e5fdab4e0228a5d541e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341026"
---
# <a name="usersettings"></a>UserSettings

[!INCLUDE [usersettings-description](includes/usersettings-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="dateformattinginfo"></a>dateFormattingInfo

从服务器检索的日期格式设置信息。

**类型**： [DateFormattingInfo](dateformattinginfo.md)

### <a name="isrtl"></a>isRTL

如果语言为从右到左，则返回 true。

**类型**： `boolean`

### <a name="languageid"></a>languageId

当前用户的语言 id。

**类型**： `number`

### <a name="numberformattinginfo"></a>numberFormattingInfo

从服务器检索的数字格式设置信息。

**类型**： [NumberFormattingInfo](numberformattinginfo.md)

### <a name="securityroles"></a>securityRoles

当前用户角色。

**类型**： `string[]`

### <a name="userid"></a>Id

当前用户的 id。

**类型**： `string`

### <a name="username"></a>userName

当前用户的用户名。

**类型**： `string`

## <a name="methods"></a>方法

|付款方式 | 描述 | 
| ------|-------------|
|[getTimeZoneOffsetMinutes](usersettings/gettimezoneoffsetminutes.md)|[!INCLUDE [gettimezoneoffsetminutes-description](usersettings/includes/gettimezoneoffsetminutes-description.md)]|

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)