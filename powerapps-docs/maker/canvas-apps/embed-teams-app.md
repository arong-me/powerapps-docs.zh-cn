---
title: 在团队中嵌入 PowerApps 应用 |Microsoft Docs
description: 你可以在 Microsoft 团队中嵌入 PowerApps 中创建的应用进行共享。
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/09/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba08437dc144fc81aa9748163b1005222735cb69
ms.sourcegitcommit: 86ed3ad487f31721155758aa9d87134bb10f8437
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2019
ms.locfileid: "70842238"
---
# <a name="embed-a-powerapps-app-in-teams"></a>在团队中嵌入 PowerApps 应用 

你可以共享已创建的 PowerApps，只需要将其直接嵌入 Microsoft 团队即可。 完成后，用户可以选择 **+** 将你的应用添加到你所在团队中的**任意团队通道**或会话。 应用在**你的团队的选项卡**下显示为磁贴。 

管理员可以上传应用程序，使其显示在 "**所有选项卡" 部分**下的租户中的**所有**团队。 请参阅[在 Microsoft 团队中共享应用](https://docs.microsoft.com/en-us/power-platform/admin/embed-app-teams)。

> [!NOTE]
> 团队自定义应用策略必须设置为允许上传自定义应用。 如果无法在团队中嵌入你的应用，请与管理员联系，查看他们是否已设置[自定义应用设置](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)。 

## <a name="prerequisites"></a>先决条件

- [拥有 PowerApps 许可证](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- 创建了画布应用

## <a name="locate-your-powerapps-guid"></a>查找 PowerApp 的 GUID

查找并记下 PowerApp 的 GUID，以便在后面的步骤中使用。

1. 登录到[https://web.powerapps.com](https://web.powerapps.com)，然后选择菜单中的 "**应用**"。

   > [!div class="mx-imgBorder"] 
   > ![显示应用列表](./media/embed-teams-app/file-apps2.png "显示应用列表")

2. 选择要在团队中共享的应用的**更多命令**（...），然后选择 "**详细信息**"。

   > [!div class="mx-imgBorder"] 
   > ![应用详细信息](./media/embed-teams-app/app-details.png "应用详细信息")


3. 记录**应用 ID**供以后使用。

   > [!div class="mx-imgBorder"] 
   > ![应用详细信息](./media/embed-teams-app/app-details2.png "应用详细信息")

## <a name="install-app-studio"></a>安装 App Studio

如果已安装 App Studio，则可以跳过这些步骤。 

1. 在 "团队" 中，选择 "团队" 菜单左下角的 "**应用**" （![应用图标](./media/embed-teams-app/apps-icon.png "应用图标")）。

2. 在搜索框中搜索 "App Studio"，然后选择它。

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. 选择 "**安装**"。 

   > [!div class="mx-imgBorder"] 
   > ![安装 App Studio](./media/embed-teams-app/install-app-studio.png "安装 App Studio")

4. 为应用功能选择 "**打开**"。

   > [!div class="mx-imgBorder"] 
   > ![打开 App Studio](./media/embed-teams-app/open-app-studio.png "打开 App Studio")

## <a name="create-a-teams-app-for-your-powerapp"></a>为你的 PowerApp 创建团队应用

1. 在团队中，打开 App Studio。

   > [!div class="mx-imgBorder"] 
   > ![打开 App Studio](./media/embed-teams-app/open-app-studio2.png "打开 App Studio")

2. 选择 "**清单编辑器**" 选项卡，然后在 "欢迎" 下选择 "**创建新应用**"。

   > [!div class="mx-imgBorder"] 
   > ![创建新应用](./media/embed-teams-app/create-new-app.png "创建新应用")

3. 在**应用程序详细信息**页中填写有关应用程序的信息。  对于应用 ID GUID，应使用前面记录的 PowerApp 应用 ID GUID。  这将避免特定 PowerApp 的团队应用的重复。
 
   > [!div class="mx-imgBorder"] 
   > ![填写信息](./media/embed-teams-app/fill-in-info-about-app.png "填写信息")

   |字段  |描述  |
   |---------|---------|
   |**应用名称** |    |
   |短名称     | 必需。 应用程序的简短显示名称。 超过30个字符。        |
   |长名称     | 应用的全名，如果完整应用名称超过30个字符，则使用此名称。       | 
   |**标识**     |         |
   |应用 ID     | 必需。 此应用程序的唯一 Microsoft 生成的标识符。        |
   |包名称     | 必需。 此应用的唯一标识符。 建议使用反向域表示法;例如，.com.<AppName>.       |
   |Version     | 必需。 特定应用的版本。 如果在清单中更新某些内容，则版本也必须递增。     |
   |**说明**    |     |
   | 简短说明    | 必需。 应用体验的简短说明，在空间有限时使用。 80字符限制。   |
   | 详细说明    | 必需。 应用的完整说明。     |
   | **开发人员信息**    |     |
   | 名称    | 必需。 公司或开发人员的显示名称。     |
   | 网站    | 必需。 指向应用程序的网站的 https://URL 通过 powerapps.com。 当某个用户安装你的应用时，将显示 "关于你的应用" 页面。 它应链接到 powerapps.com 上的应用程序的 web 版本。   |
   | **应用 Url**    | 这些链接将显示在 "**关于**" 页和 "网站 URL" 中。     |
   | 隐私声明    | 必需。 开发人员的隐私策略的 https://URL。 [示例](https://go.microsoft.com/fwlink/p/?LinkID=698505)。   |
   | 使用条款    | 必需。 开发人员使用条款的 https://URL。  [示例](https://go.microsoft.com/fwlink/p/?LinkID=698507)。  |
   | **品牌**    |     |
   | 完整颜色    | 完整颜色 192x192 PNG 图标的相对文件路径。    |
   | 透明边框    |透明 32x32 PNG 轮廓图标的相对文件路径。     |
   | 强调颜色    | 与和一起用作大纲图标背景的颜色。     |

有关详细信息，请参阅[清单编辑器](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor)和[清单架构](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema)。

4. 向下滚动到 "品牌" 部分，并添加你的徽标和应用所需的个性色。  这些是将在团队中为你的应用程序显示的徽标。 

   > [!div class="mx-imgBorder"] 
   > ![品牌和选项卡](./media/embed-teams-app/branding-tabs.png "品牌和选项卡")

5. 在 "**功能**" 下，选择 "**选项卡**"。

6. 在 "**团队" 选项卡**下选择 "**添加**"。

   > [!div class="mx-imgBorder"] 
   > ![团队选项卡添加](./media/embed-teams-app/team-tab-add.png "团队选项卡添加")

7. 使用以下格式在 "配置 URL" 输入字段中添加应用的配置 URL：`https://apps.powerapps.com/teams/settings/<PowerApp ID>`

   将`<PowerApp ID>`替换为前面记录的应用 ID GUID。

   选择要在其中显示应用的[范围](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope)。 确保已选中 "**可以更新配置**"，然后选择 "**保存**"。

   > [!div class="mx-imgBorder"] 
   > ![配置 URL](./media/embed-teams-app/configuration-url.png "配置 URL")

8. 在 "**完成**" 下，选择**有效域**。 将**apps.powerapps.com**和**Apps.preview.powerapps.com**添加为团队应用程序的有效域。

   > [!div class="mx-imgBorder"] 
   > ![添加有效域](./media/embed-teams-app/add-valid-domains.png "添加有效域")

9. **完成**后，选择 "**测试和分发**"。 在 "**安装**" 下，选择 "**安装**"。

   > [!div class="mx-imgBorder"] 
   > ![选择安装](./media/embed-teams-app/test-distribute-app.png "选择安装")

10. 选择要在其中安装应用的团队，然后选择 "**安装**"。

    > [!div class="mx-imgBorder"] 
    > ![添加到团队安装](./media/embed-teams-app/new-app-add-to-team.png "添加到团队安装")
11. 如果要立即将该应用程序的实例添加到通道，请选择要在其中使用该应用的通道，然后选择 "**设置**"。

    > [!div class="mx-imgBorder"] 
    > ![选择设置](./media/embed-teams-app/app-now-available.png "选择设置")

12. 选择**保存**。

## <a name="add-the-app-as-a-tab"></a>将该应用添加为选项卡

若要将应用作为选项卡添加到任何通道或会话， **+** 请选择 ""，然后在**你的团队的 "选项卡**" 下选择你的应用。 

> [!div class="mx-imgBorder"] 
> ![添加应用作为选项卡](./media/embed-teams-app/add-app-as-tab.png "添加应用作为选项卡")

应用现在显示为一个选项卡。

> [!div class="mx-imgBorder"] 
> ![应用作为选项卡](./media/embed-teams-app/app-as-tab.png "应用作为选项卡")

### <a name="see-also"></a>另请参阅
[欢迎使用 Microsoft 团队](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[对于管理员：在 Microsoft 团队中嵌入应用](https://docs.microsoft.com/power-platform/admin/share-app-teams)
