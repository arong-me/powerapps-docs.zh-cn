---
title: 重定向到门户的新 URL | MicrosoftDocs
description: 有关如何创建重定向 URL 以将用户重定向到站点中的其他页面的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 63cec47042cee4c29e225f33f1678261da3a01ca
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760138"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>将重定向 URL 添加到门户的新 URL

客户经常希望有重定向到网站深入页面的简单 URL，或者希望允许旧 URL 用于网站并自动重定向到网站中的新 URL。 页面重定向允许内容作者指定请求的 URL 将永久或暂时重定向到特定网页或 Web 文件。 这些重定向 URL 从页面内容单独管理，以便它们不必直接适应 Web 层次结构。

## <a name="create-a-redirect"></a>创建重定向

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转到**门户** > **网站** > **重定向**。

3. 选择**新建**。

4. 按照下面的说明输入重定向信息。

| 名称        | 说明                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 客户        | 重定向的易记名称。 （可以是任何内容。 能够轻松识别。）                                                              |
| 网站     | 重定向与之关联的网站。 （用户的重定向起始站点。）                                                         |
| 入站 URL | 将重定向的部分 URL。 （用户的重定向起始页面。）                                                            |
| 状态代码 | 以下代码之一：**302（暂时重定向）**：返回暂时重定向状态。 这是默认情况。                                               -   **301（永久重定向）**：返回指示资源已永久移动的永久重定向状态。                          |
| URL         | 将重定向到的目标外部 URL。 （如果用户重定向到对于上方指定的网站是内部的链接则使用此方法。）                            |
| 网页    | 将重定向到的目标内部网页。 （如果用户重定向到对于上方指定的网站是内部的页面则使用此方法。） |
| 站点标记 | 将重定向到的内部网站标记。                                                                                           |

4. 在输入必填字段并为 URL、网页或网站标记字段中的至少一个指定值后，选择**保存**。

    ![重定向客户调查](../media/redirect-customer-survey.png "重定向客户调查")  

## <a name="use-the-redirect"></a>使用重定向

在请求入站 URL时，浏览器重定向到目标网页的 URL 以匹配重定向项。

例如，对于目标网页设置为“客户支持调查”页的 cs-survey 的入站 URL 值，下列请求：

https://customerportal.contoso.com/cs-survey

生成请求以下 URL 的浏览器：

https://customerportal.contoso.com/surveys/customer-service-survey/

