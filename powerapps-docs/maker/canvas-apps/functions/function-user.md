---
title: User 函数 | Microsoft 文档
description: Power Apps 中用户函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d4c558e40b9bb351f3ea6b4d202ef4849cb4e85d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729873"
---
# <a name="user-function-in-power-apps"></a>Power Apps 中的用户函数
返回当前用户的相关信息。

## <a name="description"></a>描述
**User** 函数返回当前用户的相关信息[记录](../working-with-tables.md#records)：

| 属性 | 描述 |
| --- | --- |
| **User().Email** |当前用户的电子邮件地址。 |
| **User().FullName** |当前用户的全名（包括姓和名）。 |
| **User().Image** |当前用户的图像。 此为 "blob:*identifier*" 形式的图像 URL。 将 **[Image](../controls/control-image.md)** 控件的 **[Image](../controls/properties-visual.md)** 属性设置为此值可以在应用中显示用户图像。 |

> [!NOTE]
> 返回的信息适用于当前的 Power Apps 用户。  它将与 Power Apps 播放机和工作室中显示的 "帐户" 信息匹配，在任何创作的应用程序中都可以找到此信息。  该信息可能与当前用户在 Office 365 或其他服务中的信息不一致。

## <a name="syntax"></a>语法
**User**()

## <a name="examples"></a>示例
当前的 Power Apps 用户具有以下信息：

* 全名： **"John Doe"**
* 电子邮件地址： **“john.doe@contoso.com”**
* 图像：![](media/function-user/john-doe-picture.png) 

|       公式       |                                                                    描述                                                                    |                                                 结果                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             当前 Power Apps 用户的所有信息的记录。                                             |    { FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" }    |
|  **User().Email**   |                                                 当前 Power Apps 用户的电子邮件地址。                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   当前 Power Apps 用户的完整名称。                                                    |                                               "John Doe"                                                |
|  **User().Image**   | 当前 Power Apps 用户的图像 URL。  将 **Image** 控件的 **Image** 属性设置为此值可以在应用中显示用户图像。 | "blob:1234...5678"<br><br>使用 **ImageControl.Image**：<br>![](media/function-user/john-doe-picture.png) |

