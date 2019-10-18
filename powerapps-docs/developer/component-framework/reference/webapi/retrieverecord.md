---
title: RetrieveRecord |Microsoft Docs
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
ms.assetid: dddeecc9-5067-420d-8bd7-4c914218e969
ms.openlocfilehash: 9c77bf9975bd1f1f115df9385061c008975cc184
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341693"
---
# <a name="retrieverecord"></a>retrieveRecord

[!INCLUDE [retrieverecord-description](includes/retrieverecord-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.webAPI.retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

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
<td>要检索的记录的实体逻辑名称。 例如： &quot;account &quot;。</td>
</tr>
<tr>
<td>id</td>
<td>String</td>
<td>是</td>
<td>要检索的实体记录的 GUID。</td>
</tr>
<tr>
<td>选项</td>
<td>String</td>
<td>否</td>
<td><p>OData 系统查询选项， <b>$select</b>和<b>$expand</b>检索数据。</p>
<ul><li>使用<b>$select</b>系统查询选项可以限制返回的属性，包括以逗号分隔的属性名称列表。 这是一项重要的性能最佳实践。 如果未使用<b>$select</b>指定属性，则将返回所有属性。</li>
<li>使用<b>$expand</b>系统查询选项可以控制从相关实体返回的数据。 如果只是包含导航属性的名称，则将接收到相关记录的所有属性。 可以使用导航属性名称后面的括号中的<b>$select</b>系统查询选项来限制为相关记录返回的属性。 将此用于<i>单值</i>和<i>集合值</i>导航属性。</li>
</ul>
<p>指定从 <code>?</code> 开始的查询选项。 还可以通过使用 <code>&amp;</code> 分隔查询选项来指定多个查询选项。 例如：</p>
<code>?$select=name&amp;$expand=primarycontactid($select=contactid,fullname)</code>
<p>请参阅本主题后面的示例，了解如何为各种检索方案定义 <code>options</code> 参数。</td>
</tr>
<tr>
<td>successCallback</td>
<td>函数</td>
<td>否</td>
<td><p>检索记录时要调用的函数。 带有检索到的属性和值的 JSON 对象将传递给函数。</p>
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>函数</td>
<td>否</td>
<td>操作失败时要调用的函数。</td>
</tr>
</table>

## <a name="return-value"></a>返回值

类型：[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)<[实体](../entity.md)>



### <a name="related-topics"></a>相关主题

[Web API](../webapi.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)