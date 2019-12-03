---
title: SaveData 和 LoadData 函数 | Microsoft 文档
description: PowerApps 中 SaveData 和 LoadData 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1be652ef905d73baeeafd9ddf06f74584851b457
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678295"
---
# <a name="savedata-and-loaddata-functions-in-powerapps"></a>PowerApps 中的 SaveData 和 LoadData 函数
保存并重新加载[集合](../working-with-data-sources.md#collections)。

## <a name="description"></a>描述
**SaveData** 函数会存储某个集合，以便在将来通过另一个名称来使用。  

**LoadData** 函数使用此前通过 **SaveData** 保存的名称重新加载集合。 不能使用此函数加载另一个源的集合。  

使用这些函数可以通过在第一次运行时在 **[app.config](../controls/control-screen.md#additional-properties)** 公式中缓存数据来提高应用程序启动性能，然后在后续运行时重新加载本地缓存。 你还可以使用这些函数向应用添加[简单的脱机功能](../offline-apps.md)。

不能在浏览器中使用这些函数（在 Power Apps Studio 中创作应用程序时）或在 web 播放器中运行应用程序时使用。 若要测试你的应用，请在 iPhone 或 Android 设备上的 Power Apps Mobile 中运行它。

这些函数受可用应用内存量的限制，因为它们对内存中集合进行操作。 可用内存可能因设备和操作系统、Power Apps 使用的内存和应用对屏幕和控件的复杂性而异。 如果存储的数据量超过了几 mb，请在预期应用程序运行的设备上测试应用程序。 通常预计有30到 70 mb 的可用内存。  

**LoadData** 不创建集合；此函数仅填充现有集合。 必须先通过 **[Collect](function-clear-collect-clearcollect.md)** 使用正确的[列](../working-with-tables.md#columns)创建集合。 加载的数据将追加到集合;如果要从空集合开始，请首先使用 **[Clear](function-clear-collect-clearcollect.md)** 函数。

存储经过加密，位于本地设备上的专用位置，与其他用户和其他应用隔离。

## <a name="syntax"></a>语法
**SaveData**( *Collection*, *Name* )<br>**LoadData**( *Collection*, *Name* [, *IgnoreNonexistentFile* ])

* *Collection* - 必需。  要存储或加载的集合。
* *Name* - 必需。  存储的名称。 必须使用同一名称来保存和加载同一数据集。 命名空间不与其他应用或用户共享。
* *IgnoreNonexistentFile* - 可选。 指明 **LoadData** 函数在找不到匹配文件时是应显示还是应忽略错误的布尔值 (**true**/**false**)。 如果指定“false”，将显示错误。 如果指定“true”，将忽略错误，这适用于脱机方案。 如果设备处于脱机状态（即，“Connection.Connected”状态为“false”），**SaveData** 可能会创建文件。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **If(Connection.Connected, ClearCollect(LocalTweets, Twitter.SearchTweet("PowerApps", {maxResults: 100})),LoadData(LocalTweets, "Tweets", true))** |如果设备处于联机状态，将从 Twitter 服务加载“LocalTweets”集合；否则，将从本地文件缓存加载集合。 |无论设备处于联机状态还是脱机状态，内容都会呈现。 |
| **SaveData(LocalTweets, "Tweets")** |将“LocalTweets”集合另存为设备上的本地文件缓存。 |数据会进行本地保存，以便 **LoadData** 可以将其加载到集合中。 |

