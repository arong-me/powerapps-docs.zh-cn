---
title: 将应用添加到 Microsoft Teams | Microsoft Docs
description: 了解如何将应用添加到 Microsoft Teams 频道，以便你与之共享应用的用户可以在此频道中打开该应用。
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: mduelae
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 97be49797df13b82901425ae9389e85538068f5d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74726223"
---
# <a name="add-an-app-to-microsoft-teams"></a>将应用添加到 Microsoft Teams

Microsoft Teams 是基于 Office 365 技术构建的聊天协作平台。 你可以通过将 Power Apps 画布应用添加到团队中的渠道来自定义团队经验。 本主题介绍如何将产品展示示例应用添加到 Teams 频道，然后从该频道打开应用。 

![嵌入 Microsoft Teams 的应用](./media/open-app-embedded-in-teams/embedded-app.png)

如果尚未注册 Power Apps，请在开始之前[免费注册](https://make.powerapps.com/signup?redirect=marketing&email=)。

## <a name="prerequisites"></a>必备组件

若要按照此步骤操作，需要 [Office 365 订阅](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1)和 [Teams 中的频道](https://www.youtube.com/watch?v=he2f1quaR7M)。

## <a name="sign-in-to-power-apps"></a>登录到 Power Apps

在[https://make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)登录到 Power Apps。

## <a name="add-an-app"></a>添加应用

1. 在 Microsoft Teams 中，选择一个团队及该团队下的一个频道。 本例选择了“业务开发”团队下的“常规”频道。

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. 选择 + 添加选项卡。

    ![](./media/open-app-embedded-in-teams/teams-add-tab.png)

3. 在“添加选项卡”对话框中，选择“PowerApps”。

    ![](./media/open-app-embedded-in-teams/add-a-tab.png)

4. 选择“示例应用” > “产品展示” > “保存”。

    ![](./media/open-app-embedded-in-teams/select-an-app.png)

    此时，可以在频道中使用应用了。

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

> [!NOTE]
> 在将应用添加到 Teams 之前，请[共享](../maker/canvas-apps/share-app.md)自己的应用（默认情况下共享示例应用）。

## <a name="open-an-app"></a>打开应用

1. 在 Microsoft Teams 中，选择团队以及包含此应用的频道。

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. 选择“产品展示”选项卡。

    ![](./media/open-app-embedded-in-teams/open-tab.png)

    在频道中打开应用。

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

## <a name="known-issues"></a>已知问题

在 Microsoft Teams 相关桌面应用中：

* 应用必须通过安全 (https) 连接加载图像和 .pdf 文件等内容。
* 并不是所有传感器（如“Acceleration”、“Compass”和“Location”）都受支持。
* 仅支持下面这些音频格式：AAC、H264、OGG Vorbis 和 WAV。

## <a name="clean-up-resources"></a>清理资源

若要从频道中删除应用，选择“产品展示”选项卡 >“删除”。

## <a name="next-steps"></a>后续步骤

在本主题中，你将产品展示示例应用添加到了 Teams 频道，然后从该频道打开了应用。 若要了解有关电源应用的详细信息，请继续阅读 Power Apps 教程。

> [!div class="nextstepaction"]
> [Power Apps 教程](../maker/canvas-apps/get-started-create-from-blank.md)
