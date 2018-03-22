---
title: 可委托的数据源 | Microsoft 文档
description: 列出了所有受支持的可委托数据源
services: ''
suite: powerapps
documentationcenter: na
author: archnair
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/15/2017
ms.author: archanan
ms.openlocfilehash: e073c0a8c471dc8b863894e2d229b15b66b3ce60
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="delegable-data-sources"></a>可委托的数据源
如[了解委托](delegation-overview.md)一文中所详述，委托是指 PowerApps 将数据处理这项任务委托给数据源，而不是将数据移到应用中进行本地处理。

仅表数据源支持委托。 下面列出了表数据源及其是否支持委托，下一部分将对此进行详细介绍。

* Common Data Service - **是**
* SharePoint - **是**
* SQL Server - **是**
* Dynamics 365 - **是**
* Salesforce - **是**
* Dynamics 365 for Operations - 尚不支持
* Dynamics 365 for Financials - 尚不支持
* Dynamics NAV - 尚不支持
* Google 表格 - 尚不支持

我们将会在此列表中不断补充更多表数据源，并说明其是否支持委托。

本文档列出了每个数据源的委托支持的最新状态。

## <a name="prerequisites"></a>先决条件

* 阅读[了解委托](delegation-overview.md)一文

## <a name="list-of-data-sources-and-supported-delegation"></a>有关数据源及其委托支持的列表
下面的数据源和可委托函数及谓词列表会定期进行更新，以反映 PowerApps 中委托支持的最新状态。

### <a name="top-level-delegable-functions"></a>顶级可委托函数
| &nbsp; | Common Data Service | SharePoint | SQL Server | Dynamics 365 | Salesforce |
| --- | --- | --- | --- | --- | --- |
| Average |否 |否 |是 |否 |否 |
| 筛选 |是 |是 |是 |是 |是 |
| LookUp |是 |是 |是 |是 |是 |
| 最多 |否 |否 |是 |否 |否 |
| Min |否 |否 |是 |否 |否 |
| 搜索 |是<sup>1</sup> |否 |是 |是 |是 |
| 排序 |是 |是 |是 |是 |是 |
| SortByColumns |是 |是 |是 |是 |是 |
| Sum |否 |否 |是 |否 |否 |

<sup>1</sup>仅限字符串字段

### <a name="filter-and-lookup-delegable-predicates"></a>Filter 和 LookUp 可委托谓词
| &nbsp; | Common Data Service | SharePoint | SQL Server | Dynamics 365 | Salesforce |
| --- | --- | --- | --- | --- | --- |
| 否 |是 |否 |是 |是 |是 |
| IsBlank |否 |否 |是 |是 |否 |
| TrimEnds |否 |否 |是 |否 |否 |
| Len |否 |否 |是 |否 |否 |
| +、- |否 |否 |是 |否 |否 |
| <、<=、=、<>、>、>= |是 |是（仅限 =） |是 |是 |是 |
| And (&&)、Or (&#124;&#124;)、Not (!) |是<sup>2</sup> |是（Not(!) 除外） |是 |是 |是 |
| in |否 |否 |是 |否 |是 |
| StartsWith |否 |是 |否 |否 |否 |

<sup>2</sup>仅限运算符。 不委托 And/Or/Not 函数。
