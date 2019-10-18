---
title: setControlState |Microsoft Docs
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
ms.assetid: 1052db82-7002-44ca-ad1f-9d3d4c311817
ms.openlocfilehash: 56c2221916781db646d27b131dfc00e61e742be3
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342659"
---
# <a name="setcontrolstate"></a>setControlState

[!INCLUDE [setcontrolstate-description](includes/setcontrolstate-description.md)]

## <a name="syntax"></a>语法

`context.mode.setControlState(state);`

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览） 

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|状态|`Dictionary`|是|单个用户在一个会话中保留的数据。|

## <a name="return-value"></a>返回值

类型： `boolean`


### <a name="related-topics"></a>相关主题

[Mode](../mode.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)