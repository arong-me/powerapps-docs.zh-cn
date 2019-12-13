---
title: 在 Web 浏览器中运行应用 | Microsoft Docs
description: 本主题介绍如何在 Web 浏览器中运行应用
author: mduelae
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 12/05/2019
ms.author: mkaur
manager: kvivek
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8ce6cfe213817cd603857bb5ea2735b188f8cb6c
ms.sourcegitcommit: 15c6b26ff085928459ad9b3f52fb607fae4a997d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74956775"
---
# <a name="run-an-app-in-a-web-browser"></a>在 Web 浏览器中运行应用
当你创建应用，或者有人与你共享应用时，你可以在 Dynamics 365 移动应用或 tablet 上的 web 浏览器中运行该应用。 在本主题中，你将了解如何在 web 浏览器中从[Dynamics 365 主页](https://home.dynamics.com)运行画布或模型驱动应用。

若要获得完整的功能和优化的体验，强烈建议使用适用于手机和平板电脑移动应用的 Dynamics 365。 如果你没有安装适用于手机和平板电脑应用的 Dynamics 365，则你仍可以在平板电脑上使用 web 浏览器，前提是你的设备具有足够高的屏幕分辨率。 有关详细信息，请查看[支持的内容](https://docs.microsoft.com/dynamics365/mobile-app/support-phones-tablets#supported-devices-for-the-mobile-app)。

> [!NOTE]
> 不支持使用手机上的 web 浏览器运行模型驱动的应用;必须使用适用于手机的 Dynamics 365 应用。

要按本快速入门教程操作，需要以下内容：
- Power Apps 许可证。 此功能适用于电源应用计划，例如[Power Apps 计划2试用版](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps)，或包含 power apps 的任何[Microsoft Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1)或[Dynamics 365](https://dynamics.microsoft.com/pricing/)计划。 
- 对你生成的或其他人生成并与你共享的应用的访问权限。
- 对受支持的 Web 浏览器和操作系统的访问权限。
   - 对于画布应用，请参阅：[系统要求、限制和配置值](../maker/canvas-apps/limits-and-config.md)
   - 对于模型驱动应用，请参阅：[支持的 Web 浏览器和移动设备](https://docs.microsoft.com/dynamics365/customer-engagement/admin/supported-web-browsers-and-mobile-devices)


## <a name="sign-in-to-dynamics-365"></a>登录到 Dynamics 365
在 [https://home.dynamics.com](https://home.dynamics.com) 上登录到 Dynamics 365。

## <a name="find-an-app-on-the-home-page"></a>在主页上查找应用
主页上可能显示多种类型的商业应用，可通过在搜索框中键入一部分名称来找到特定应用。 你还可以筛选此列表，以仅显示由特定源（如电源应用）创建的应用。 为此，请选择 "**筛选**"，然后选择 "源"。

如果最近安装了应用，该应用可能不会立即显示在应用列表中。 选择 "**同步**" 以显示所有应用。 此过程可能需要一分钟。

![](./media/run-app-browser/dynamics-365-home.png)


## <a name="run-an-app-from-a-url"></a>从 URL 中运行应用
可以在 tablet 的浏览器中将应用的 URL 另存为书签，并通过选择书签来运行该 URL，也可以通过电子邮件发送 URL 作为链接。 如果其他人创建了一个应用并将其与你的电子邮件共享，则可以通过选择电子邮件中的链接来运行该应用。 使用 URL 运行应用时，系统可能提示使用 Azure Active Directory 凭据登录。

![](./media/run-app-browser/web-login.png)

## <a name="connect-to-data"></a>连接到数据
如果应用需要连接数据源，或必须征得同意才能使用设备功能（例如照相机或定位服务），必须先确认连接或予以同意，然后才能使用应用。 通常情况下，只会在首次连接时看到提示。

![Connection](./media/run-app-browser/app-connection.png)

## <a name="close-an-app"></a>关闭应用
若要关闭应用，请退出 Dynamics 365 主页，或打开其他应用。

## <a name="next-steps"></a>后续步骤
本主题介绍如何在 Web 浏览器中运行画布或模型驱动应用。 了解如何执行以下操作：
- 在移动设备上运行画布应用，请参阅[在移动设备上运行画布应用](run-app-client.md)
- 在移动设备上运行模型驱动的应用，请参阅[在移动设备上运行模型驱动的应用](run-app-client-model-driven.md)
- 使用模型驱动的应用，请参阅[使用模型驱动的应用](use-model-driven-apps.md)

