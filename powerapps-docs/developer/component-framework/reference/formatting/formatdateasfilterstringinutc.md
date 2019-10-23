---
title: formatDateAsFilterStringUTC |Microsoft Docs
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
ms.assetid: a604fbbf-6d09-450d-b686-7a5cb3f3a2bc
ms.openlocfilehash: 2242e1badabd740bf414340ae3d11b29e6000ebb
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343142"
---
# <a name="formatdateasfilterstringinutc"></a>formatDateAsFilterStringInUTC

[!INCLUDE [formatdateasfilterstringinutc-description](includes/formatdateasfilterstringinutc-description.md)]

## <a name="syntax"></a>语法

`context.formatting.formatDateAsFilterStringInUTC(value, includeTime)`

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览）

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|值|`Date`|是|要设置格式的日期。|
|includeTime|`boolean`|是| 如果应在返回值中包含时间部分，则为。|

## <a name="return-value"></a>返回值

类型： `string`


### <a name="related-topics"></a>相关主题

[格式设置](../formatting.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)