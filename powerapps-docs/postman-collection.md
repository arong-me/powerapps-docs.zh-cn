---
title: "使用 Postman 描述自定义连接器 | Microsoft 文档"
description: "创建用于注册自定义连接器的 Postman 集合"
services: 
suite: powerapps
documentationcenter: 
author: archnair
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/28/2017
ms.author: archanan
ms.openlocfilehash: fd060ff873ee376b7ca886f721d360372c1d13ed
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2018
---
# <a name="describe-a-custom-connector-with-postman"></a>使用 Postman 描述自定义连接器
[Postman](https://www.getpostman.com/) 是用于加快和简化 API 开发的工具。 本教程介绍了如何创建 Postman 集合，然后你就可以使用此集合在 PowerApps 中轻松创建[自定义连接器](register-custom-api.md)了。

## <a name="prerequisites"></a>先决条件
* 安装 [Postman 应用](https://www.getpostman.com/apps)

## <a name="create-a-postman-collection"></a>创建 Postman 集合
让我们为 Azure 认知服务[文本分析 API](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api) 生成 Postman 集合。 此 API 可以标识向其传递的文本的语言、情绪和关键短语。

1. 创建 Postman 集合的第一步是创建请求。 创建请求时，可以设置 HTTP 谓词、请求 URL、查询或路径参数、标头和正文。 有关详细信息，请参阅 Postman 文档中的[发送请求](https://www.getpostman.com/docs/requests)。 对于检测语言 API 终结点，请按如下所示设置值：
   
    ![Postman 请求](./media/postman-collection/request.png)
   
    所用参数和值的详细信息：
   
   | 参数 | 值 |
   | --- | --- |
   | 谓词 |POST |
   | 请求 URL |https://westus.api.cognitive.microsoft.com/text/analytics/v2.0/languages |
   | 参数 |numberOfLanguagesToDetect |
   | 授权 |“No Auth” |
   | 标头 |Ocp-Apim-Subscription-Key = <your subscription key> <br/>Content-Type = application/json |
   | 正文 |<code>{<br/>&nbsp;&nbsp;&nbsp;"documents": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": "1",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "Hello World"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}<code> |
2. 单击“发送”，生成请求并获取返回的响应。
3. 单击“保存”，将请求保存到 Postman 集合中。
   
    ![Postman 响应](./media/postman-collection/request-response-save.png)
4. 在“保存请求”对话框中，输入“请求名称”和“请求说明”。 这些值将用于自定义连接器。
   
    ![保存 Postman 集合](./media/postman-collection/save-request-note.png)
   
    还可以保存请求响应。 自定义连接器目前仅支持每个请求保存一个响应。 如果每个请求保存了多个响应，只会使用第一个响应。
   
    ![保存 Postman 响应](./media/postman-collection/save-response.png)
5. 创建和保存其他请求和响应，继续生成 Postman 集合。
6. 生成包含所有请求和响应的 Postman 集合后，导出此集合。
   
    ![Postman 导出](./media/postman-collection/export.png)
7. 选择“集合 v1”作为导出格式。
   
    ![Postman 导出](./media/postman-collection/export2.png)

现在可以使用此 Postman 集合在 PowerApps 中创建自定义连接器。 有关详细信息，请参阅[在 PowerApps 中注册和使用自定义连接器](register-custom-api.md)。 

