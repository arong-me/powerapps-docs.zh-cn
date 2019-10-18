---
title: getTimeZoneOffsetMinutes |Microsoft Docs
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
ms.assetid: 86290d20-7dbb-4932-adaa-31121ae7a3f6
ms.openlocfilehash: bc621299b19b1387225b8532ee03ff65e0e6471f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341003"
---
# <a name="gettimezoneoffsetminutes"></a>getTimeZoneOffsetMinutes

[!INCLUDE [gettimezoneoffsetminutes-description](includes/gettimezoneoffsetminutes-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.usersettings.getTimeZoneOffsetMinutes(date)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|日期|`Date`|是|要获取其相对于 utc 的偏移量的日期。|

## <a name="return-value"></a>返回值

类型： `Number` 说明：时区偏移量（分钟）。


### <a name="related-topics"></a>相关主题

[用户设置](../usersettings.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)