---
title: 获取会话 ID 或画布应用 ID | Microsoft Docs
description: 如何获取会话 ID 或画布应用 ID 以在 Power Apps 中进行故障排除
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bad3f118da62d0c4eb6c0873aa6aed03516a9085
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729620"
---
# <a name="get-a-session-id-or-a-canvas-app-id"></a>获取会话 ID 或画布应用 ID
如果你遇到在 Power Apps 中创建的画布应用的问题，你可以帮助 Microsoft 更有效地解决问题，因为你为这些问题提供了会话 ID 和/或应用 ID。

## <a name="get-the-session-id"></a>获取会话 ID

### <a name="when-editing-an-app"></a>编辑应用时
1. 在左上角选择“文件”。

1. 选择“帐户”。

1. 在“诊断”下选择“会话详细信息”。

    ![从 Power Apps Studio 获取会话 ID](media/get-sessionid/studio.png)

### <a name="when-running-an-app-in-a-browser"></a>在浏览器中运行应用时
1. 在右上角，选择齿轮图标。

1. 选择“会话详细信息”。

    ![从浏览器中获取会话 ID](media/get-sessionid/browser.png)

### <a name="when-running-an-app-on-a-phone-or-a-tablet"></a>在手机或平板电脑上运行应用时
1. 向右轻扫。

1. 点击“会话详细信息”。

    ![从浏览器中获取会话 ID](media/get-sessionid/mobile.png)

### <a name="when-running-an-embedded-app-or-form"></a>运行嵌入的应用或窗体时
1. 执行以下步骤之一：

    - 按住 Alt 键，并右键单击应用或窗体。
    - 用两个手指点击应用或窗体 1-2 秒，然后释放。

1. 选择“会话详细信息”。

    ![从嵌入的应用中获取会话 ID](media/get-sessionid/embedded.png)

## <a name="get-an-app-id"></a>获取应用 ID
1. [登录到 Power Apps](https://powerapps.microsoft.com)。

1. 在左边缘附近，选择“应用”。

1. 对要进行故障排除的应用选择省略号 (. . .)， 然后选择“详细信息”。

    ![转到应用详细信息](./media/get-sessionid/details.png)

    将在该应用的“详细信息”窗格底部显示应用 ID。

    ![从“详细信息”中复制应用 ID](./media/get-sessionid/app-id.png)
