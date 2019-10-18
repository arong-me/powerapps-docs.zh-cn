---
title: deleteRecord |Microsoft Docs
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
ms.assetid: 5c9968bf-d535-425c-b1f1-0db6b7822de1
ms.openlocfilehash: f6c8dd6ea7d156e28ab3ae54d7fe37dad6c4546a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340750"
---
# <a name="deleterecord"></a>deleteRecord

[!INCLUDE [deleterecord-description](includes/deleterecord-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.webAPI.deleteRecord(entityLogicalName, id).then(successCallback, errorCallback);`

## <a name="parameters"></a>参数

<table style="width:100%">
<tr>
<th>名称</th>
<th>类型</th>
<th>需要</th>
<th>描述</th>
</tr>
<tr>
<td>entityLogicalName</td>
<td>String</td>
<td>是</td>
<td>要删除的记录的实体逻辑名称。 例如： &quot;account &quot;。 </td>
</tr>
<tr>
<td>id</td>
<td>String</td>
<td>是</td>
<td>要删除的实体记录的 GUID。</td>
</tr>
<tr>
<td>successCallback</td>
<td>函数</td>
<td>否</td>
<td><p>要在删除记录时调用的函数。 将传递具有以下属性的对象以标识删除的记录：</p>
<ul>
<li><b>entityType</b>： String。 记录的实体类型。</li>
<li><b>id</b>： String。 记录的 GUID。</li>
<li><b>name</b>： String。 记录的名称。</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>函数</td>
<td>否</td>
<td>操作失败时要调用的函数。</td>
</tr>
</table>

## <a name="return-value"></a>返回值

类型：[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)<[Entityreference](../entityreference.md) >

### <a name="related-topics"></a>相关主题

[Web API](../webapi.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)