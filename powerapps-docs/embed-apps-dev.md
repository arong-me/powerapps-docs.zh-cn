---
title: "将 PowerApps 集成到网站和其他服务中 | Microsoft 文档"
description: "在网站和其他服务中嵌入应用。"
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/12/2017
ms.author: mblythe
ms.openlocfilehash: 541de1bcea9b76262d4f2d1cbe79c76b1c117245
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="integrate-powerapps-into-websites-and-other-services"></a>将 PowerApps 集成到网站和其他服务中
如果能够直接将生成的应用集成到用户工作时使用的工具中，通常最为实用。 借助 PowerApps，可以将应用嵌入 iframe，以便于将这些应用集成到网站和其他服务中（如 Power BI 或 SharePoint）。

本主题先会介绍如何设置应用嵌入参数；然后，我们将会把资产订购应用嵌入网站。

![嵌入了应用的 Power BI 仪表板](media/embed-apps-dev/embed-dashboard.png)

请记住以下限制：

* 只有同一租户中的 PowerApps 用户，才能访问嵌入应用。
* PowerApps 仅支持关闭兼容性视图的 Internet Explorer 11。

还可以将 PowerApps 集成到 SharePoint Online 中（不使用 iframe）。 有关详细信息，请参阅[使用 PowerApps 从 SharePoint 中生成应用](generate-app-from-sharepoint-list-interface.md)。

## <a name="set-uri-parameters-for-your-app"></a>设置应用 URI 参数
若有要嵌入的应用，第一步是设置统一资源标识符 (URI) 参数，以便 iframe 知道在何处查找应用。 URI 的格式如下：

```
https://web.powerapps.com/webplayer/iframeapp?source=iframe
&appId=/providers/Microsoft.PowerApps/apps/[AppID]
```

**注意**：为了提升 URI 在页面上的显示效果，我们添加了换行符。

只需将 URI 中的 [AppID] 替换成应用 ID（包括 '[' & ']'）。 稍后，我们将介绍如何获取此值，而现在将先介绍 URI 中的所有参数：

* **[appID]** - 格式为 `/providers/Microsoft.PowerApps/apps/[AppID]`。 用于提供要运行的应用的 ID。
* **screenColor** - 用于为用户提供更好的应用加载体验。 此参数的格式为 [RGBA (red value, green value, blue value, alpha)](functions/function-colors.md)，用于控制应用加载时的屏幕颜色。 最好将此参数设置为与应用图标的颜色相同。
* **source** - 虽然不影响应用，但建议添加描述性名称来指代嵌入来源。
* 最后，可以使用 [Param() 函数](functions/function-param.md)添加所需的任何自定义参数，并且这些值可供应用使用。 这些参数添加到 URI 的末尾，如 `[AppID]&amp;param1=value1`。 在应用的启动阶段，这些参数为只读；如果需要更改它们，必须重启应用。

### <a name="get-the-app-id"></a>获取应用 ID
可以在 powerapps.com 上获取应用 ID。对于要嵌入的应用，请执行以下操作：

1. 在 [powerapps.com](https://powerapps.microsoft.com) 中，依次单击或点击“应用”选项卡上的省略号（“...” ）和“详细信息”。
   
    ![转到应用详细信息](media/embed-apps-dev/details.png)
2. 复制“应用 ID”。
   
    ![从“详细信息”中复制应用 ID](media/embed-apps-dev/app-id.png)
3. 替换 URI 中的 `[AppID]` 值。 对于资产订购应用，URI 如下所示：
   
    ```
    https://web.powerapps.com/webplayer/iframeapp?hideNavBar=true&
    source=iframe&appId=/providers/Microsoft.PowerApps/apps/76897698-91a8-b2de-756e-fe2774f114f2
    ```

## <a name="embed-your-app-in-a-website"></a>将应用嵌入网站
嵌入应用现在与向网站的 HTML 代码添加 iframe（或支持 iframe 的任何其他服务，如 Power BI 或 SharePoint）一样简单：

```
<iframe width="[W]" height="[H]" src="https://web.powerapps.com/webplayer/iframeapp?hideNavBar=true&
source=website&screenColor=rgba(165,34,55,1)&appId=/providers/Microsoft.PowerApps/apps/[AppID]"/>
```

指定 iframe 宽度和高度值，然后将 `[AppID]` 替换成应用 ID。

下图展示了嵌入 Contoso 示例网站的资产订购应用。

![嵌入了应用的 Contoso 网站](media/embed-apps-dev/contoso-website.png)

对应用用户进行身份验证时，请注意以下几点：

* 如果网站使用 Azure Active Directory (AAD) 身份验证，用户无需额外登录。
* 如果网站使用其他任何登录机制或网站未经身份验证，用户将会在 iframe 上看到登录提示。 登录后，用户便可以运行应用，但前提是应用的作者已与其共享应用。

如你所见，嵌入应用不仅操作简单，而且还能提供非常强大的功能。 通过嵌入应用，可以将应用直接集成到你和客户工作时使用的工具（网站、Power BI 仪表板、SharePoint 页面等）。

