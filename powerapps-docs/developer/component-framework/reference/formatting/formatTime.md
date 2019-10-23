---
title: formatTime |Microsoft Docs
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
ms.assetid: 148964b5-106e-4f2e-8038-9086d29dc54f
ms.openlocfilehash: cc2c7dfdbe9952d69dcda9fdd4c813965f539478
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343326"
---
# <a name="formattime"></a>formatTime

[!INCLUDE [formattime-description](includes/formattime-description.md)]

## <a name="syntax"></a>语法

`context.formatting.formatTime(value, behavior);`

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览）

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|值|`Date`|是|要设置格式的日期。|
|操作|`DateTimeFieldBehavior`|是|要设置格式的 datetime 对象的行为。 @No__t_0 具有以下属性：<br/>-  `None =0`：未知的日期时间行为 <br/>-  `UserLocal =1`：与用户本地时间有关。 以 UTC 形式存储的日期<br/>-  `TimeZoneIndependent =3`：不转换到 UTC 的存储日期和时间|

## <a name="return-value"></a>返回值

类型： `string`


### <a name="related-topics"></a>相关主题

[格式设置](../formatting.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)