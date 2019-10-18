---
title: updateRecord |Microsoft Docs
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
ms.assetid: 179ced61-ff0f-45ef-aa14-835ce99532cf
ms.openlocfilehash: 96037bcd8ca43448e928abef714ae031222d8e98
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340681"
---
# <a name="updaterecord"></a>updateRecord

[!INCLUDE [updaterecord-description](includes/updaterecord-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.webAPI.updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>要更新的记录的实体逻辑名称。 例如： &quot;account &quot;。</td>
</tr>
<tr>
<td>id</td>
<td>String</td>
<td>是</td>
<td>要更新的实体记录的 GUID。</td>
</tr>
<tr>
<td>数据</td>
<td>对象</td>
<td>是</td>
<td><p>一个包含 <code>key: value</code> 对的 JSON 对象，其中 <code>key</code> 是实体的属性， <code>value</code> 要更新的属性的值。</p>
<p>请参阅本主题后面的示例，了解如何为各种更新方案定义 <code>data</code> 对象。</td>
</tr>
<tr>
<td>successCallback</td>
<td>函数</td>
<td>否</td>
<td><p>更新记录时要调用的函数。 将传递具有以下属性的对象以标识更新的记录：</p>
<ul>
<li><b>entityType</b>： String。 已更新记录的实体类型。</li>
<li><b>id</b>： String。 已更新记录的 GUID。</li>
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

类型： [承诺] （（dateformattinginfo） <[Entityreference](../entityreference.md) >

说明：成功后，将返回一个承诺对象，其中包含在**successCallback**参数的说明中前面指定的属性。


### <a name="related-topics"></a>相关主题

[Web API](../webapi.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)