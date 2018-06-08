---
title: 使用环境 | Microsoft 文档
description: 切换环境并了解如何更改页面上的内容。
documentationcenter: na
author: linhtranms
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 10/14/2016
ms.author: litran
ms.openlocfilehash: 4bf196041853e9f88c97aabcd3ff1c234b2608be
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "32329470"
---
# <a name="working-with-environments-and-microsoft-powerapps"></a>使用环境和 Microsoft PowerApps
通过 PowerApps，你可以在不同的环境中工作，并在它们之间轻松切换。 有关环境的概述，请参阅 [环境概述](../../administrator/environments-overview.md)，该文章详细介绍了使用环境的原因以及如何创建和管理环境。 本文的范围将涵盖有关环境的以下主题：

* 如何在 powerapps.com 上切换环境
* 如何在正确的环境中创建应用
* 如何在正确的环境中查看应用

## <a name="switch-the-environment"></a>切换环境
注册并首次登录到 powerapps.com 时，你很可能会登录到默认环境。 通过查看页面的右上角即可对此进行验证。

![默认环境](./media/working-with-environments/env-dropdown.png)

每个人均可访问*默认环境*。 你可以开始在此环境中创建应用并与其他用户共享。 你还可以访问其他环境，如那些 [自己创建](../../administrator/environments-administration.md)的或他人创建但你有权访问的环境。 通过单击右上角中的“环境”下拉菜单，然后选择不同的环境即可切换环境。 此示例演示了从“默认环境”切换到“环境 1”的过程。

![切换环境](./media/working-with-environments/switch-env.png)

一旦切换到另一个环境（例如环境 1），你会在此新环境中看到你所创建的或有权访问的所有应用。

## <a name="create-apps-in-the-right-environment"></a>在正确的环境中创建应用
可在你创建的环境中或已获得访问权限的环境中创建应用。 但创建自己的环境需要使用[特定计划](../../administrator/pricing-billing-skus.md)。 创建应用前，始终**确保你选择是要在其中创建应用的环境**。 否则，你必须在环境之间移动应用。

若要在合适的环境中创建应用，请执行以下任一项：

- 如果 PowerApps Studio 没有打开，先[登录](http://web.powerapps.com)，选择想要在其中创建应用的环境，然后选择靠近左侧边缘的“应用”，再选择“创建应用”。

- 如果 PowerApps Studio 打开，则在右上角角落再次选择环境。

5. 在“**帐户**”页上，选择当前环境名称旁的“**更改**”。

6. 选择要在其中创建应用的环境。

    ![Studio 切换环境](./media/working-with-environments/studio-env-dropdown2.PNG)

7. 选择“**新建**”开始创建应用。 你的应用现在将驻留在第 6 步所选的环境中。

    ![Studio 切换环境](./media/working-with-environments/new-app.PNG)

## <a name="view-apps-in-the-right-environment"></a>在正确的环境中查看应用
无论你使用的是 [powerapps.com](http://web.powerapps.com) 还是 PowerApps Studio，你所看到的应用、连接列表等始终根据在下拉菜单中选择的环境进行筛选。 如果未看到所查找的应用，则请始终确认是否选择了正确的环境。

有关环境的详细信息，请参阅 [概述](../../administrator/environments-overview.md)。
