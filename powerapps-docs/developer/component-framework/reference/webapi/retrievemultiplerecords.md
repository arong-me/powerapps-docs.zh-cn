---
title: retrieveMultipleRecords |Microsoft Docs
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
ms.assetid: 824a53f9-c743-435a-9de2-8128846f3191
ms.openlocfilehash: d708596e9b8e12ead8f84d31d3b35fb5b27843f8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340796"
---
# <a name="retrievemultiplerecords"></a>retrieveMultipleRecords

[!INCLUDE [retrievemultiplerecords-description](includes/retrievemultiplerecords-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.webAPI.retrieveMultipleRecords(entityLogicalName, options, maxPageSize).then(successCallback, errorCallback);`

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
<td>选项</td>
<td>String</td>
<td>否</td>
<td><p>OData 系统查询选项或 FetchXML 查询来检索数据。 </p> 
<ul>
<li>支持以下系统查询选项： <b>$select</b>、 <b>$top</b>、 <b>$filter</b>、 <b>$expand</b>和<b>$orderby</b>。</li>
<li>若要指定 FetchXML 查询，请使用 <code>fetchXml</code> 特性来指定查询。</li>
</ul>
<p>注意：必须始终使用<b>$select</b>系统查询选项，通过包含以逗号分隔的属性名称列表来限制为实体记录返回的属性。 这是一项重要的性能最佳实践。 如果未使用<b>$select</b>指定属性，则将返回所有属性。</li>
<p>指定从 <code>?</code> 开始的查询选项。 还可以通过使用 <code>&amp;</code> 分隔查询选项来指定多个系统查询选项。
<p>请参阅本主题后面的示例，了解如何为各种检索多个方案定义 <code>options</code> 参数。</td>
</tr>
<tr>
<td>maxPageSize</td>
<td>Number</td>
<td>否</td>
<td><p>指定一个正数，该数字表示每页返回的实体记录数。 如果未指定此参数，则默认值将作为5000传递。</p>
<p>如果要检索的记录数大于指定的 <code>maxPageSize</code> 值，则返回的承诺对象中的 <code>nextLink</code> 属性将包含用于检索下一组实体的链接。 </td>
</tr>
<tr>
<td>successCallback</td>
<td>函数</td>
<td>否</td>
<td><p>检索实体记录时要调用的函数。 具有以下属性的对象将传递给函数：</p>
<ul>
<li><b>实体</b>： JSON 对象的数组，其中每个对象均表示检索到的实体记录，其中包含作为 <code>key: value</code> 对的属性及其值。 默认情况下，会检索实体记录的 Id。</li>
<li><b>nextLink</b>：字符串。 如果要检索的记录数多于请求中 <code>maxPageSize</code> 参数中指定的值，则此属性返回 URL 以返回下一组记录。</li>
</ul>
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

类型：[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)<RetrieveMultipleResponse>

说明：该 `RetrieveMultipleResponse` 返回一个承诺，其中包含包含检索到的实体记录的 JSON 对象数组和**nextLink**属性，其中 URL 指向下一组记录（如果在请求中指定了分页（`maxPageSize`））和返回的记录计数超出了分页值。 它具有以下参数：

|参数|返回值|描述|
|----|------|-------|
|条目|`Entity[]`|JSON 对象的数组，其中每个对象都表示检索到的实体记录，其中包含特性及其值。|
|nextLink|`string`|如果要检索的记录数多于请求的 "maxPageSize" 参数中指定的值，此属性将返回 URL 以返回下一组记录。|


### <a name="related-topics"></a>相关主题

[Web API](../webapi.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)