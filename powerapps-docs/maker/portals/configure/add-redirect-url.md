---
title: 重定向到门户上的新 URL |MicrosoftDocs
description: 说明如何创建重定向 URL 以将用户重定向到站点中的其他页面。
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553408"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>将重定向 URL 添加到门户中的新 URL

客户经常想要有一个简单的 URL，该 URL 将重定向到站点中的更深层页，或者他们想要允许将旧版 URL 与站点一起使用，并自动重定向到站点中的新 URL。 页面重定向允许内容作者指定一个 URL，该 URL 在被请求时将永久重定向到特定网页或 web 文件。 这些重定向 Url 与页面内容分开管理，因此它们不必直接在 web 层次结构中适应。

## <a name="create-a-redirect"></a>创建重定向

1. 打开[门户管理应用](configure-portal.md)。

2. 请参阅**门户** > **网站** > **重定向**。

3. 选择 "**新建**"。

4. 输入重定向信息，如下所述。

| 名称        | 描述                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 名称        | 重定向的友好名称。 （可以是任何内容。 便于识别。）                                                              |
| 网站     | 与重定向关联的网站。 （用户重定向到的站点。）                                                         |
| 入站 URL | 要重定向的部分 URL。 （用户重定向到的页面。）                                                            |
| 状态代码 | 以下项之一： **302 （临时重定向）** ：返回临时重定向状态。 这是默认值。                                               -   **301 （永久重定向）** ：返回永久重定向状态，指示资源已永久移动。                          |
| 链接         | 要重定向到的目标外部 URL。 （如果将用户重定向到上面指定网站的外部链接，请使用此链接。）                            |
| 网页    | 要重定向到的目标内部网页。 （如果要将用户重定向到上面指定网站的内部页面，请使用此页。） |
| 站点标记 | 要重定向到的目标内部站点标记。                                                                                           |

4. 输入必填字段并为至少一个 URL、网页或网站标记字段指定一个值后，请选择 "**保存**"。

    ![重定向客户调查](../media/redirect-customer-survey.png "重定向客户调查")  

## <a name="use-the-redirect"></a>使用重定向

请求入站 URL 后，浏览器将重定向到匹配的重定向条目的目标网页的 URL。

例如，对于 "cs-调查" 的入站 URL 值，目标网页设置为 "客户支持调查" 页，以下请求：

https://customerportal.contoso.com/cs-survey

在浏览器中生成请求以下 URL 的结果：

https://customerportal.contoso.com/surveys/customer-service-survey/

