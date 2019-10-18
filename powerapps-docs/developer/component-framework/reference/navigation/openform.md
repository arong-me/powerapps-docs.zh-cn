---
title: openForm |Microsoft Docs
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
ms.assetid: bea56947-d976-4974-9ac7-2d5f5c7b6732
ms.openlocfilehash: d0754030de4880f0ad693105e96b47d785f1561b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342360"
---
# <a name="openform"></a>openForm

[!INCLUDE [openform-description](includes/openform-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.navigation.openForm(options, parameters)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|选项|`EntityFormOptions`|是|用于打开窗体的实体窗体选项。 EntityFormOptions 具有以下属性：<br/>- **createFromEntity**： `Lookup`。 指定将基于映射的属性值提供默认值的记录。 Lookup 对象具有以下字符串属性： `entityType`、`id` 和 `name`。 <br/>- **entityId**： `String`。 要为其显示窗体的实体记录的 ID。<br/>- **entityName**： `String`。 要为其显示窗体的实体的逻辑名称。<br/>- **formId**： `String`。 要显示的窗体实例的 ID。<br/>- **高度**： `Number`。 要以像素为单位显示的窗体窗口高度。<br/>- **openInNewWindow**： `boolean`。 是否在新窗口中显示窗体。<br/>- **useQuickCreateForm**： `Boolean`。 是否打开 "快速创建" 窗体。 如果不指定此值，则默认情况下将传递 `false`。<br/>- **width**： `Number`。 要以像素为单位显示的窗体窗口宽度。<br/>- **windowPosition**： `Number`。 在屏幕上为窗体的窗口位置指定下列值之一： `1:center` <br/> `2:side`|
|Parameters|`Object`|否|将额外参数传递给窗体的字典对象。 无效参数将导致错误。 详细信息，[请参阅使用传递给窗体的参数的字段值](https://docs.microsoft.com/en-us/powerapps/developer/model-driven-apps/set-field-values-using-parameters-passed-form)和[将窗体配置为接受自定义查询字符串参数](https://docs.microsoft.com/en-us/powerapps/developer/component-framework/sample-controls/navigation-api-control)|

## <a name="return-value"></a>返回值

类型： `Promise<OpenFormSuccessResponse>`

## <a name="remarks"></a>标记

请参阅[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)

### <a name="related-topics"></a>相关主题

[导航](../navigation.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)