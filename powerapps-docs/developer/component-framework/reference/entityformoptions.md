---
title: EntityFormOptions |Microsoft Docs
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
ms.assetid: 418871c0-59dc-4a7c-a8f9-9364a19f7662
ms.openlocfilehash: 7429a5bac040e3c20412ac0916743a57d9d5710f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344361"
---
# <a name="entityformoptions"></a>EntityFormOptions

提供对实体窗体的所有信息的访问。

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="createfromentity"></a>createFromEntity

指定将基于映射的属性值提供默认值的记录。 Lookup 对象具有以下属性：实体类型、id 和名称。

**类型**： [Entityreference](entityreference.md)

### <a name="entityid"></a>entityId

要为其显示窗体的实体记录的唯一 Id。 

**类型**： `string`

### <a name="entityname"></a>entityName

要为其显示窗体的实体的逻辑名称。 

**类型**： `string`

### <a name="formid"></a>formId

要显示的窗体实例的 ID。

**类型**： `string`

### <a name="height"></a>height

要以像素为单位显示的窗体窗口高度。

**类型**： `number`

### <a name="openinnewwindow"></a>openInNewWindow

是否在新窗口中显示窗体。

**类型**： `boolean`

### <a name="usequickcreateform"></a>useQuickCreateForm

是否打开 "快速创建" 窗体。 如果不指定此参数，则默认情况下将传递 false。 

**类型**： `boolean`

### <a name="width"></a>width

要以像素为单位显示的窗体窗口宽度。

**类型**： `boolean`

### <a name="windowposition"></a>windowPosition

指定屏幕上的窗口位置。

**类型**： `number`

WindowPosition 值是具有以下可能值的数字

|Value|位置|
|---|---|
|1|Center|
|2|反面|


### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)