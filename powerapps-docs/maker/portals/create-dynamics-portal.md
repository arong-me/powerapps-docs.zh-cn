---
title: 使用 Dynamics 365 环境创建门户 |Microsoft Docs
description: 使用 Dynamics 365 环境创建门户的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e81fde2c5f756c9a7f08bfcd6438efca6321a420
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975486"
---
# <a name="create-a-portal-with-dynamics-365-environment"></a>创建使用 Dynamics 365 环境的门户

如果在 Dynamics 365 中选择包含模型驱动应用的环境，则可以创建[门户模板](portal-templates.md)中所述的门户。

1.  登录 [PowerApps](http://web.powerapps.com)。

2.  选择左窗格中的 "**创建**"，然后在 "**搜索模板**" 字段中输入**门户**，以显示所有 Dynamics 365 门户模板。

    > [!div class=mx-imgBorder]
    > ![Dynamics 365 门户模板](media/dynamics-portals.png "Dynamics 365 门户模板")  

3.  选择所需的门户模板。

4.  在 "创建门户" 窗口中，输入门户网站的名称和地址，然后从下拉列表中选择一种语言。 完成后，选择 "**创建**"。 创建过程与[创建 Common Data Service 的入门门户](create-portal.md)部分中所述的过程相同。

> [!NOTE]
> - 如果你购买了较旧的门户外接程序，并且想要使用该外接程序预配门户，则必须使用 " **Dynamics 365 管理中心**" 页。 详细信息：[预配门户](https://docs.microsoft.com/en-gb/dynamics365/customer-engagement/portals/provision-portal)
> - 如果已使用旧版门户外接程序预配了门户，则仍可通过[make.powerapps.com](https://make.powerapps.com)对其进行自定义和管理。
> - 从[make.powerapps.com](https://make.powerapps.com)预配门户不会使用较旧的门户加载项。 此外，这些门户未列在**Dynamics 365 管理中心**页面上的 "**应用程序**" 选项卡下。
> - 无法从**Dynamics 365 管理中心**页面创建 Common Data Service starter 门户。
> - 若要禁用在租户中创建门户，请参阅[禁用在租户中创建门户](create-portal.md#disable-portal-creation-in-a-tenant)。

