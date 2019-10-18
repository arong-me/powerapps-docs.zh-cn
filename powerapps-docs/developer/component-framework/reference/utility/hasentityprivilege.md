---
title: hasEntityPrivilege |Microsoft Docs
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: f22723f0-c606-465c-abba-0a8c46a10e32
ms.openlocfilehash: f370d14f0b978d7ac4b6e6535677e06e7cf3f86e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340888"
---
# <a name="hasentityprivilege"></a>hasEntityPrivilege

[!INCLUDE [hasentityprivilege-description](includes/hasentityprivilege-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.utils.hasEntityPrivilege(entityTypeName, privilegeType, privilegeDepth)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|entityTypeName|`string`|是|实体类型名称|
|privilegeType|`enum`|否|实体特权类型。 它具有以下属性：<br/>- `None = 0`<br/>- `Create = 1` <br/>- `Read = 2`<br/>- `Write = 3`<br/>- `Delete = 4`<br/>- `Assign =5`<br/>- `Share =6`<br/>- `Append =7`<br/>- `AppendTo =8`|
|privilegeDepth|`enum`|否|实体权限深度。 它具有以下特性： <br/>- `None = -1`<br/>- `Basic = 0`<br/>- `Local = 1`<br/>- `Deep = 2`<br/>- `Global = 3`|

## <a name="return-value"></a>返回值

**类型**： `boolean`

### <a name="related-topics"></a>相关主题

[Utility](../utility.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)