---
title: setFullScreen |Microsoft Docs
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
ms.assetid: 1faf3e79-969e-4c1e-ac01-8e2155c609fa
ms.openlocfilehash: b7fb38bcb0102356d8d1ea2540edf0dd1f845cbd
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342613"
---
# <a name="setfullscreen"></a>setFullScreen

[!INCLUDE [setfullscreen-description](includes/setfullscreen-description.md)]

## <a name="syntax"></a>语法

`context.mode.setControlState(mode);`

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|值|`Boolean`|是|`True` 组件是否需要自动调整为全屏。 如果组件需要自动调整为分配的宽度，则 `False`。|


### <a name="related-topics"></a>相关主题

[Mode](../mode.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)