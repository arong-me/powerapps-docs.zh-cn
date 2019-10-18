---
title: lookupObjects |Microsoft Docs
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
ms.assetid: d213b401-cfc4-44df-b55c-f040fb6d7072
ms.openlocfilehash: 0dca29df3537389decefe2584d2fc931cea8979c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341141"
---
# <a name="lookupobjects"></a>lookupObjects

[!INCLUDE [lookupobjects-description](includes/lookupobjects-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.utils.lookupObjects(lookupOptions)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|LookupOptions|`UtilityApi.LookupOptions`|是|定义用于打开查找对话框的选项。 LookupOptions 具有以下属性：<br/>- **allowMultiSelect**： `Boolean`。 指示查找是否允许选择多个项。<br/>- **defaultEntityType**： `String`。 要使用的默认实体类型。<br/>- **defaultViewId**： `String`。 要使用的默认视图。<br/>- **entityTypes**： `String[]`。 要显示的实体类型。<br/>- **viewid**： `String[]`。 视图选取器中可用的视图。 仅支持系统视图（而非用户视图）。|

## <a name="return-value"></a>返回值

类型：[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)<[Entityreference](../entityreference.md)[] >


### <a name="related-topics"></a>相关主题

[Utility](../utility.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)