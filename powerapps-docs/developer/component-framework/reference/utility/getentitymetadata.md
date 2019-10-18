---
title: getEntityMetadata |Microsoft Docs
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
ms.assetid: 6a334af7-ca5b-449c-b90f-0901824654d2
ms.openlocfilehash: 89dc2e9d567b8ff38c41df2074d2a85d6bcaf467
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340957"
---
# <a name="getentitymetadata"></a>getEntityMetadata

[!INCLUDE [getentitymetadata-description](includes/getentitymetadata-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.utils.getEntityMetadata(entityName, attributes)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|entityName|`String`|是|实体的逻辑名称。|
|属性|`String[]`|否|要获取其元数据的特性。|

## <a name="return-value"></a>返回值

类型： `Promise<EntityMetadata>`


### <a name="related-topics"></a>相关主题

[Utility](../utility.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)