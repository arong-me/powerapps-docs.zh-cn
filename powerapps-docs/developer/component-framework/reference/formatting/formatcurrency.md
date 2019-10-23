---
title: FormatCurrency |Microsoft Docs
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
ms.assetid: 87e433e6-573f-414f-b49d-1213f2bd8cf4
ms.openlocfilehash: 6089e88ce5814ca24c8310435726bff07cc97894
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343234"
---
# <a name="formatcurrency"></a>formatCurrency

[!INCLUDE [formatcurrency-description](includes/formatcurrency-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览）

## <a name="syntax"></a>语法

`context.formatting.formatCurrency(value, precision, symbol)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|值|`number`|是| 要设置格式的值。|
|precision|`number`|是| 小数点后的位数。|
|代号|`string`|是| 要添加货币值的货币符号/代码。|

## <a name="return-value"></a>返回值

类型： `string`


### <a name="related-topics"></a>相关主题

[格式设置](../formatting.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)