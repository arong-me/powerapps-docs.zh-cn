---
title: DataSet | Microsoft Docs
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
ms.assetid: 0202d51f-e9a9-4a2e-b3e9-0bfd7f6afb86
ms.openlocfilehash: 5e9408c81fc9587b9dec30f18fc68c3112ba6125
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345304"
---
# <a name="dataset"></a>DataSet

[!INCLUDE [dataset-description](includes/dataset-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="addcolumn"></a>addColumn （）

向列集添加列

### <a name="remarks"></a>标记

此方法接受两个参数。

|名称|类型|需要|描述|
|------|-----|------|-----|
|路径名|`string`|是|要添加到数据集的列名称。|
|entityAlias|`string`|否| 需要为其添加列名称的实体别名。|

### <a name="columns"></a>表列

此数据集中可用的一组列。

**类型**： [Column](column.md)[]

### <a name="error"></a>条

数据检索是否出错。

**类型**： `boolean`

### <a name="errormessage"></a>errorMessage

与最后遇到的错误关联的错误消息（如果适用）。

**类型**： `string`

### <a name="filtering"></a>滤除

当前查询的列筛选。

**类型**：[筛选](filtering.md)

### <a name="linking"></a>链接

定义链接实体信息。

**类型**：[链接](linking.md)

### <a name="loading"></a>加载

指示是否正在加载数据集。

**类型**： `boolean`

### <a name="paging"></a>分页

分页状态和操作。

**类型**：[分页](paging.md)

### <a name="records"></a>记录

Id 映射到完整记录对象。

**类型**： [EntityRecord](entityrecord.md)

### <a name="sortedrecordids"></a>sortedRecordIds

数据集中的记录的 Id，按查询响应结果排序。

**类型**： `string[]`

### <a name="sorting"></a>排序

当前查询的排序状态。

**类型**： [SortStatus](sortstatus.md)

## <a name="methods"></a>方法

|付款方式 | 描述 | 
| ------------- |-------------|
|[clearSelectedRecordIds](dataset/clearselectedrecordids.md)|[!INCLUDE [clearselectedrecordids-description](dataset/includes/clearselectedrecordids-description.md)]| 
|[getSelectedRecordIds](dataset/getselectedrecordids.md)|[!INCLUDE [getselectedrecordids-description](dataset/includes/getselectedrecordids-description.md)]| 
|[getTargetEntityType](dataset/gettargetentitytype.md)|[!INCLUDE [gettargetentitytype-description](dataset/includes/gettargetentitytype-description.md)]| 
|[getTitle](dataset/gettitle.md)|[!INCLUDE [gettitle-description](dataset/includes/gettitle-description.md)]| 
|[getViewId](dataset/getviewid.md)|[!INCLUDE [getviewid-description](dataset/includes/getviewid-description.md)]| 
|[openDatasetItem](dataset/opendatasetitem.md)|[!INCLUDE [opendatasetitem-description](dataset/includes/opendatasetitem-description.md)]| 
|[刷新](dataset/refresh.md)|[!INCLUDE [refresh-description](dataset/includes/refresh-description.md)]| 
|[setSelectedRecordIds](dataset/setselectedrecordids.md)|[!INCLUDE [setselectedrecordids-description](dataset/includes/setselectedrecordids-description.md)]| 

## <a name="example"></a>示例

若要了解有关如何实现 dataset 方法的详细信息，请参阅[数据集网格组件](../sample-controls/data-set-grid-control.md)

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)