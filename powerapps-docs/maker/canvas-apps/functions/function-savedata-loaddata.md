---
title: SaveData 和 LoadData 函数 | Microsoft 文档
description: PowerApps 中 SaveData 和 LoadData 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3fb23fec6f6885a55b054889b90fed0c5efafd5e
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61520481"
---
# <a name="savedata-and-loaddata-functions-in-powerapps"></a>PowerApps 中的 SaveData 和 LoadData 函数
保存并重新加载[集合](../working-with-data-sources.md#collections)。

## <a name="description"></a>描述
**SaveData** 函数会存储某个集合，以便在将来通过另一个名称来使用。  

**LoadData** 函数使用此前通过 **SaveData** 保存的名称重新加载集合。 不能使用此函数加载另一个源的集合。  

使用这些函数通过缓存中的数据来提高应用程序启动性能 **[App.OnStart](../controls/control-screen.md#additional-properties)** 公式上首次运行并将其重新加载在后续运行的本地缓存。 也可以使用这些函数将添加[简单的离线功能](../offline-apps.md)到您的应用程序。

创作 PowerApps Studio 中的应用程序或 web 播放机中运行应用程序时，不能使用在浏览器中，这些函数。 若要测试您的应用程序，它在 PowerApps Mobile 中上运行的 iPhone 或 Android 设备。

这些函数都受可用的应用的内存量，因为它们在内存中集合上运行。 具体取决于设备和操作系统，使用 PowerApps 播放器，内存和应用程序在屏幕和控件方面的复杂性而异的可用内存。 如果存储超过几兆字节的数据，请测试预期方案要运行的应用在其上的设备上使用对应用程序。 您通常应该会有 30 和 70 兆字节的可用内存。  

**LoadData** 不创建集合；此函数仅填充现有集合。 必须先通过 **[Collect](function-clear-collect-clearcollect.md)** 使用正确的[列](../working-with-tables.md#columns)创建集合。 加载的数据将追加到集合;使用 **[清除](function-clear-collect-clearcollect.md)** 首先函数，如果你想要开始使用一个空集合。

存储经过加密，位于本地设备上的专用位置，与其他用户和其他应用隔离。

## <a name="syntax"></a>语法
**SaveData**( *Collection*, *Name* )<br>**LoadData**( *Collection*, *Name* [, *IgnoreNonexistentFile* ])

* *Collection* - 必需。  要存储或加载的集合。
* *Name* - 必需。  存储的名称。 必须使用同一名称来保存和加载同一数据集。 命名空间不与其他应用或用户共享。
* *IgnoreNonexistentFile* - 可选。 指明 **LoadData** 函数在找不到匹配文件时是应显示还是应忽略错误的布尔值 (**true**/**false**)。 如果指定“false”，将显示错误。 如果指定“true”，将忽略错误，这适用于脱机方案。 如果设备处于脱机状态（即，“Connection.Connected”状态为“false”），**SaveData** 可能会创建文件。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **If(Connection.Connected, ClearCollect(LocalTweets, Twitter.SearchTweet("PowerApps", {maxResults:100})),LoadData(LocalTweets, "Tweets", true))** |如果设备处于联机状态，将从 Twitter 服务加载“LocalTweets”集合；否则，将从本地文件缓存加载集合。 |无论设备处于联机状态还是脱机状态，内容都会呈现。 |
| **SaveData(LocalTweets, "Tweets")** |将“LocalTweets”集合另存为设备上的本地文件缓存。 |数据会进行本地保存，以便 **LoadData** 可以将其加载到集合中。 |

