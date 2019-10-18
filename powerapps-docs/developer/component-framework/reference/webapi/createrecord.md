---
title: createRecord |Microsoft Docs
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
ms.assetid: 9179f03b-9d26-4253-9535-13ab544d58ac
ms.openlocfilehash: f3a2b860f17d7efaaf8efebcf2418aef04478947
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340819"
---
# <a name="createrecord"></a>createRecord

[!INCLUDE [createrecord-description](includes/createrecord-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.webAPI.createRecord(entityLogicalName, data).then(successCallback, errorCallback);`

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
<td>要创建的实体的逻辑名称。 例如： &quot;account &quot;。</td>
</tr>
<tr>
<td>数据</td>
<td>对象</td>
<td>是</td>
<td><p>一个 JSON 对象，用于定义新实体记录的属性和值。</p>
<p>请参阅本主题后面的示例，了解如何为各种创建方案定义 <code>data</code> 对象。</td>
</tr>
<tr>
<td>successCallback</td>
<td>函数</td>
<td>否</td>
<td><p>创建记录时要调用的函数。 将传递具有以下属性的对象以标识新记录：</p>
<ul>
<li><b>entityType</b>： String。 新记录的实体逻辑名称。</li>
<li><b>id</b>： String。 新记录的 GUID。</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>函数</td>
<td>否</td>
<td>操作失败时要调用的函数。 将传递具有以下属性的对象：
<ul>
<li><b>errorCode</b>： Number。 错误代码。</li>
<li><b>message</b>： String。 描述问题的错误消息。</li>
</ul></td>
</tr>
</table>

## <a name="return-value"></a>返回值

类型：[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)<[Entityreference](../entityreference.md) >

说明：成功后，将返回一个承诺对象，其中包含在**successCallback**参数的说明中前面指定的属性。

### <a name="related-topics"></a>相关主题

[Web API](../webapi.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)