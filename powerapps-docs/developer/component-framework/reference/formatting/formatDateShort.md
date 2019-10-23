---
title: formatDateShort |Microsoft Docs
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
ms.assetid: e69a9b6c-f737-4ebb-a9c1-901923b85358
ms.openlocfilehash: d9dd72ffdcb9ad69b3aae767effd14f617c0cba9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343556"
---
# <a name="formatdateshort"></a>formatDateShort

[!INCLUDE [formatdateshort-description](includes/formatdateshort-description.md)]

## <a name="syntax"></a>语法

`context.formatting.formatDateShort(value, includeTime);`

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览）

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|值|`Date`|是|要设置格式的值日期。|
|includeTime|`boolean`|是|是否在格式化值中显示时间。|

## <a name="return-value"></a>返回值

类型： `string`


### <a name="related-topics"></a>相关主题

[格式设置](../formatting.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)