---
title: 在团队中嵌入应用 |Microsoft Docs
description: 你可以在 Microsoft 团队中嵌入 PowerApps 中创建的应用进行共享。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 42075fbaee40ec98bec0d47e6bfd3c00dc6f9ef6
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182505"
---
# <a name="embed-an-app-in-teams"></a>在团队中嵌入应用

你可以共享已创建的 PowerApps，只需要将其直接嵌入 Microsoft 团队即可。 完成后，用户可以选择 **+** 将你的应用添加到你所在团队中的**任意团队频道**或会话。 应用在**你的团队的选项卡**下显示为磁贴。

管理员可以上传应用程序，使其显示在 "**所有选项卡" 部分**下的租户中的**所有**团队。 请参阅[在 Microsoft 团队中共享应用](https://docs.microsoft.com/power-platform/admin/embed-app-teams)。

> [!NOTE]
> 团队自定义应用策略必须设置为允许上传自定义应用。 如果无法在团队中嵌入你的应用，请与管理员联系，查看他们是否已设置[自定义应用设置](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)。

## <a name="prerequisites"></a>必备组件

- 你需要有效的[PowerApps 许可证](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)。
- 若要将应用嵌入到团队中，需要[使用 PowerApps 创建](data-platform-create-app.md)的现有应用。

## <a name="download-the-app"></a>下载应用程序

1. 登录到[web.powerapps.com](https://web.powerapps.com)，然后在菜单中选择 "**应用**"。

    ![显示应用列表](./media/embed-teams-app/file-apps2.png "显示应用列表")

2. 选择要在团队中共享的应用的 "**更多操作**（...）"，然后选择 "**添加到团队**"。

    ![应用详细信息](./media/embed-teams-app/add-to-teams.png "添加到团队")

3. 在 "添加到团队" 面板中，选择 "**下载**"。 然后，PowerApps 将使用已在应用程序中设置的应用程序说明和徽标生成团队清单文件。

    ![应用详细信息](./media/embed-teams-app/download-app.png "下载应用")

## <a name="add-the-app-as-a-personal-app"></a>将应用添加为个人应用

1. 若要将应用作为个人应用或选项卡添加到任何频道或会话，请在左侧导航栏中选择 "**应用**"，并选择 "**上传自定义应用**"。

    > [!NOTE]
    > 仅当团队管理员创建了[自定义应用策略](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies)并启用了 "**允许上传自定义**应用" 时，才会显示 "**上载自定义应用**"。

    ![添加应用作为选项卡](./media/embed-teams-app/upload-custom-app.png "上传自定义应用")

2. 选择 "**添加**" 以将应用添加为个人应用，或选择 "**添加到团队**"，将应用添加为现有通道或会话中的选项卡。

## <a name="publish-the-app-to-the-teams-catalogue"></a>将应用发布到团队目录

如果你是管理员，则还可以将[应用发布](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams)到 Microsoft 团队目录。

### <a name="see-also"></a>另请参阅

[欢迎使用 Microsoft 团队](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
