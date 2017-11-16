---
title: "使用环境 | Microsoft 文档"
description: "切换环境并了解如何更改页面上的内容。"
services: 
suite: powerapps
documentationcenter: na
author: linhtranms
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/14/2016
ms.author: litran
ms.openlocfilehash: e7252415f6f5839a7531f1264615dc5ed39dca10
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="working-with-environments-and-microsoft-powerapps"></a>使用环境和 Microsoft PowerApps
通过 PowerApps，你可以在不同的环境中工作，并在它们之间轻松切换。 有关环境的概述，请参阅 [环境概述](environments-overview.md)，该文章详细介绍了使用环境的原因以及如何创建和管理环境。 本文的范围将涵盖有关环境的以下主题：

* 如何在 powerapps.com 上切换环境
* 如何在正确的环境中创建应用
* 如何在正确的环境中查看应用

## <a name="switch-the-environment"></a>切换环境
注册并首次登录到 powerapps.com 时，你很可能会登录到默认环境。 通过查看页面的右上角即可对此进行验证。

![默认环境](./media/working-with-environments/env-dropdown.png)

每个人均可访问*默认环境*。 你可以开始在此环境中创建应用并与其他用户共享。 你还可以访问其他环境，如那些 [自己创建](environments-administration.md)的或他人创建但你有权访问的环境。 通过单击右上角中的“环境”下拉菜单，然后选择不同的环境即可切换环境。 在此示例中，我正从*默认环境*切换到*环境 1*。

![切换环境](./media/working-with-environments/switch-env.png)

一旦切换到另一个环境（例如环境 1），你会在此新环境中看到你所创建的或有权访问的所有应用。

## <a name="create-apps-in-the-right-environment"></a>在正确的环境中创建应用
你可以在有权访问的现有环境或新环境中创建应用。 但创建自己的环境需要使用特定计划。 有关详细信息，请参阅 [本主题](pricing-billing-skus.md)。 创建应用前，始终**确保你选择是要在其中创建应用的环境**。 否则，你必须在环境之间移动应用。

1. 如果你在访问 [powerapps.com](http://web.powerapps.com)，则选择要在其中创建应用的环境。 如果你在访问 *PowerApps Studio* 或 *适用于 Web 的 PowerApps Studio*，请跳到步骤 4。
2. 选择“**+ 新应用**”
3. 选择“**打开 PowerApps Studio**”或“**适用于 Web 的 PowerApps Studio**”
4. *PowerApps Studio* 或 *适用于 Web 的 PowerApps Studio* 打开后，再次在右上角选择环境。 我们将在以后改进这种体验，但在当前版本中，每次在新环境中创建应用时必须执行上述操作。
   
   ![Studio 切换环境](./media/working-with-environments/studio-switch-env.PNG)
5. 在“**帐户**”页上，选择当前环境名称旁的“**更改**”。
   
   ![Studio 切换环境](./media/working-with-environments/studio-env-dropdown.PNG)
6. 选择要在其中创建应用的环境。
   
   ![Studio 切换环境](./media/working-with-environments/studio-env-dropdown2.PNG)
7. 选择“**新建**”开始创建应用。 你的应用现在将驻留在第 6 步所选的环境中。
   
   ![Studio 切换环境](./media/working-with-environments/new-app.PNG)

## <a name="view-apps-in-the-right-environment"></a>在正确的环境中查看应用
无论你使用的是 [powerapps.com](http://web.powerapps.com)、适用于 Windows 的 PowerApps Studio 还是适用于 Web 的 PowerApps Studio，你所看到的应用、连接列表等始终根据在下拉菜单中选择的环境进行筛选。 如果未看到所查找的应用，则请始终确认是否选择了正确的环境。

同样，要在 [powerapps.com](http://web.powerapps.com) 中切换环境：

![切换环境](./media/working-with-environments/switch-env.png)

要在适用于 Windows 的 PowerApps Studio 或适用于 Web 的 PowerApps Studio 中切换环境：

  ![Studio 切换环境](./media/working-with-environments/studio-switch-env.PNG)

有关环境的详细信息，请参阅 [概述](environments-overview.md)。
