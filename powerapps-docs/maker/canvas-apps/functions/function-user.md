---
title: User 函数 | Microsoft 文档
description: PowerApps 中 User 函数的引用信息（包括语法）
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2016
ms.author: gregli
ms.openlocfilehash: 4bb19496ef1dbd89c52048161e325a7fab496d3e
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="user-function-in-powerapps"></a>PowerApps 中的 User 函数
返回当前用户的相关信息。

## <a name="description"></a>说明
**User** 函数返回当前用户的相关信息[记录](../working-with-tables.md#records)：

| 属性 | 说明 |
| --- | --- |
| **User().Email** |当前用户的电子邮件地址。 |
| **User().FullName** |当前用户的全名（包括姓和名）。 |
| **User().Image** |当前用户的图像。 此为 "blob:*identifier*" 形式的图像 URL。 将 **[Image](../controls/control-image.md)** 控件的 **[Image](../controls/properties-visual.md)** 属性设置为此值可以在应用中显示用户图像。 |

> [!NOTE]
> 返回的是当前 PowerApps 用户的相关信息。  该信息与 PowerApps 播放器和 PowerApps Studio 中显示的“帐户”信息一致，可在任何已创作的应用范围外找到。  该信息可能与当前用户在 Office 365 或其他服务中的信息不一致。

## <a name="syntax"></a>语法
**User**()

## <a name="examples"></a>示例
当前 PowerApps 用户的信息如下：

* 全名：**"John Doe"**
* 电子邮件地址：**“john.doe@contoso.com”**
* 图像：![](media/function-user/john-doe-picture.png) 

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **User()** |当前 PowerApps 用户的所有信息记录。 |{ FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" } |
| **User().Email** |当前 PowerApps 用户的电子邮件地址。 |"john.doe@contoso.com" |
| **User().FullName** |当前 PowerApps 用户的全名。 |"John Doe" |
| **User().Image** |当前 PowerApps 用户的图像 URL。  将 **Image** 控件的 **Image** 属性设置为此值可以在应用中显示用户图像。 |"blob:1234...5678"<br><br>使用 **ImageControl.Image**：<br>![](media/function-user/john-doe-picture.png) |
