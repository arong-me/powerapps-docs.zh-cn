---
title: SaveData 和 LoadData 函数 | Microsoft 文档
description: PowerApps 中 SaveData 和 LoadData 函数的参考信息（包括语法）
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 8dc68646808e40792d3e55aa9ac547aa43a78efb
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="savedata-and-loaddata-functions-in-powerapps"></a>PowerApps 中的 SaveData 和 LoadData 函数
保存并重新加载[集合](../working-with-data-sources.md#collections)。

## <a name="description"></a>说明
**SaveData** 函数会存储某个集合，以便在将来通过另一个名称来使用。  

**LoadData** 函数使用此前通过 **SaveData** 保存的名称重新加载集合。 不能使用此函数加载另一个源的集合。  

**LoadData** 不创建集合；此函数仅填充现有集合。 必须先通过 **[Collect](function-clear-collect-clearcollect.md)** 使用正确的[列](../working-with-tables.md#columns)创建集合。

存储经过加密，位于本地设备上的专用位置，与其他用户和其他应用隔离。  

## <a name="syntax"></a>语法
**SaveData**( *Collection*, *Name* )<br>**LoadData**( *Collection*, *Name* [, *IgnoreNonexistentFile* ])

* *Collection* - 必需。  要存储或加载的集合。
* *Name* - 必需。  存储的名称。 必须使用同一名称来保存和加载同一数据集。 命名空间不与其他应用或用户共享。
* *IgnoreNonexistentFile* - 可选。 指明 **LoadData** 函数在找不到匹配文件时是应显示还是应忽略错误的布尔值 (**true**/**false**)。 如果指定“false”，将显示错误。 如果指定“true”，将忽略错误，这适用于脱机方案。 如果设备处于脱机状态（即，“Connection.Connected”状态为“false”），**SaveData** 可能会创建文件。

## <a name="examples"></a>示例
| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **If(Connection.Connected, ClearCollect(LocalTweets, Twitter.SearchTweet("PowerApps", {maxResults: 100})),LoadData(LocalTweets, "Tweets", true))** |如果设备处于联机状态，将从 Twitter 服务加载“LocalTweets”集合；否则，将从本地文件缓存加载集合。 |无论设备处于联机状态还是脱机状态，内容都会呈现。 |
| **SaveData(LocalTweets, "Tweets")** |将“LocalTweets”集合另存为设备上的本地文件缓存。 |数据会进行本地保存，以便 **LoadData** 可以将其加载到集合中。 |

