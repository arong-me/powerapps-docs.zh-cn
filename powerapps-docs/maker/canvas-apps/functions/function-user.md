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
ms.openlocfilehash: 75b7b4e1f4c66745bdbddebb30c0e4ca45dfeb2b
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845344"
---
# <a name="user-function-in-power-apps"></a>Power Apps 中的用户函数
返回当前用户的相关信息。

## <a name="description"></a>说明
**User** 函数返回当前用户的相关信息[记录](../working-with-tables.md#records)：

| 属性 | 说明 |
| --- | --- |
| **User().Email** |当前用户的电子邮件地址。 |
| **User().FullName** |当前用户的全名（包括姓和名）。 |
| **User().Image** |当前用户的图像。 此为 "blob:*identifier*" 形式的图像 URL。 将 **[Image](../controls/properties-visual.md)** 控件的 **[Image](../controls/control-image.md)** 属性设置为此值可以在应用中显示用户图像。 |

> [!NOTE]
> 返回的信息适用于当前的 Power Apps 用户。  它将与 Power Apps 播放机和工作室中显示的 "帐户" 信息匹配，在任何创作的应用程序中都可以找到此信息。  该信息可能与当前用户在 Office 365 或其他服务中的信息不一致。

> [!NOTE]
> 如果在2020年3月之前使用用户函数发布了应用程序，则可能会发现该应用程序 intermitently 不会检索照片。 此问题已在2020年3月发布版本中得到解决。  若要利用更新后的实现，只需重新打开应用程序，保存并重新发布。  

## <a name="syntax"></a>语法
**User**()

## <a name="examples"></a>示例
当前的 Power Apps 用户具有以下信息：

* 全名： **"John Doe"**
* 电子邮件地址： **“john.doe@contoso.com”**
* 图像：![](media/function-user/john-doe-picture.png) 

|       公式       |                                                                    说明                                                                    |                                                 结果                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             当前 Power Apps 用户的所有信息的记录。                                             |    { FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678" }    |
|  **User().Email**   |                                                 当前 Power Apps 用户的电子邮件地址。                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   当前 Power Apps 用户的完整名称。                                                    |                                               "John Doe"                                                |
|  **User().Image**   | 当前 Power Apps 用户的图像 URL。  将 **Image** 控件的 **Image** 属性设置为此值可以在应用中显示用户图像。 | "blob:1234...5678"<br><br>使用 **ImageControl.Image**：<br>![](media/function-user/john-doe-picture.png) |

