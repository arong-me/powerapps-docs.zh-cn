---
title: 在 Teams 中嵌入的 PowerApps 应用程序 |Microsoft Docs
description: 可以嵌入在 PowerApps 中共享它的 Microsoft Teams 中创建的应用。
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/29/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d17b02cc87bb219474aade955a2910f12fcf7f27
ms.sourcegitcommit: 2376c1f1f3431bca52a8deb9b966ce1fe9f88da0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66381377"
---
# <a name="embed-a-powerapps-app-in-teams"></a>在 Teams 中嵌入的 PowerApps 应用 

你可以共享它直接嵌入到 Microsoft Teams 创建 PowerApps。 完成后，用户可以选择 **+** 若要将您的应用程序添加到任何**你**team 通道或在的团队中的会话。 应用会显示为磁贴下**选项卡为你的团队**。 

管理员可以让它显示了上传应用程序**所有**在租户中的团队**所有选项卡部分**。 请参阅[共享中 Microsoft Teams 应用](https://review.docs.microsoft.com/en-us/power-platform/admin/embed-app-teams?branch=JimHoltzWorkBranch)。

> [!NOTE]
> 团队的自定义应用策略必须设置为允许上传自定义应用。 如果无法在 Teams 中嵌入您的应用程序，请与管理员联系，请参阅如果它们已安装程序[自定义应用设置](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)。 

## <a name="prerequisites"></a>先决条件

- [拥有 PowerApps 许可证](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- 创建画布应用

## <a name="locate-your-powerapps-guid"></a>找到 PowerApp 的 GUID

找到并记下的 PowerApp 的 GUID，以便在稍后的步骤使用。

1. 登录到[ https://web.powerapps.com ](https://web.powerapps.com)，然后选择**应用**菜单中。

   > [!div class="mx-imgBorder"] 
   > ![显示的应用列表](./media/embed-teams-app/file-apps2.png "显示的应用列表")

2. 选择**更多命令**（...） 应用程序想要在团队中共享，然后选择**详细信息**。

   > [!div class="mx-imgBorder"] 
   > ![应用详细信息](./media/embed-teams-app/app-details.png "应用详细信息")

3. 记录**应用程序 ID**以供将来使用。

   > [!div class="mx-imgBorder"] 
   > ![应用详细信息](./media/embed-teams-app/app-details2.png "应用详细信息")

## <a name="install-app-studio"></a>安装 App Studio

如果尚未安装 App Studio，则可以跳过这些步骤。 

1. 在 Teams 中，选择**应用程序**左下角的团队菜单中 (![应用图标](./media/embed-teams-app/apps-icon.png "应用图标"))。

2. 在搜索框中搜索"应用程序 Studio"，然后选择它。

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. 选择**安装**。 

   > [!div class="mx-imgBorder"] 
   > ![安装的应用程序 Studio](./media/embed-teams-app/install-app-studio.png "安装的应用程序 Studio")

4. 选择**打开**应用功能。

   > [!div class="mx-imgBorder"] 
   > ![打开应用 Studio](./media/embed-teams-app/open-app-studio.png "打开应用 Studio")

## <a name="create-a-teams-app-for-your-powerapp"></a>创建你的 PowerApp 的团队应用

1. 在 Teams 中，打开 App Studio。

   > [!div class="mx-imgBorder"] 
   > ![打开应用 Studio](./media/embed-teams-app/open-app-studio2.png "打开应用 Studio")

2. 选择**清单编辑器**选项卡，然后选择**创建新的应用**欢迎使用下。

   > [!div class="mx-imgBorder"] 
   > ![创建新应用](./media/embed-teams-app/create-new-app.png "创建新应用")

3. 有关在应用中的信息填充**应用的详细信息**页。  对于应用程序 ID GUID，应使用上述记录的 PowerApp 的应用程序 ID GUID。  这可以避免重复的团队应用特定的 PowerApp。
 
   > [!div class="mx-imgBorder"] 
   > ![填写信息](./media/embed-teams-app/fill-in-info-about-app.png "中填写信息")

   |字段  |描述  |
   |---------|---------|
   |**应用名称** |    |
   |短名称     | 必填。 应用程序短显示名称。 30 个字符限制。        |
   |长名称     | 应用程序中，使用完整的应用名称超过 30 个字符的全名。       | 
   |**标识**     |         |
   |应用程序 ID     | 必填。 Microsoft 生成的唯一标识符此应用。        |
   |包名称     | 必填。 此应用程序的唯一标识符。 我们建议使用反向域十进制表示法。例如，com.example.<AppName>。       |
   |版本     | 必填。 特定应用程序的版本。 如果在清单中更新的内容，版本必须也增加。     |
   |**说明**    |     |
   | 简短说明    | 必填。 你的应用体验，当空间有限制时，使用简短说明。 80 字符限制。   |
   | 详细说明    | 必填。 您的应用程序的完整说明。     |
   | **开发人员信息**    |     |
   | 名称    | 必填。 公司或开发人员的显示名称。     |
   | 网站    | 必填。 通过 powerapps.com 应用网站 https:// URL。 当有人安装您的应用程序，会显示"关于您的应用程序"页。 它应链接到你的应用在 powerapps.com 上的 web 版本。   |
   | **应用 Url**    | 下面的链接将显示在**有关**页以及网站的 URL。     |
   | 隐私声明    | 必填。 开发人员的隐私策略 https:// URL。 [示例](https://go.microsoft.com/fwlink/p/?LinkID=698505)。   |
   | 使用条款    | 必填。 开发人员的使用条款 https:// URL。  [示例](https://go.microsoft.com/fwlink/p/?LinkID=698507)。  |
   | **品牌**    |     |
   | 完整的颜色    | 为全彩色 192 x 192 PNG 图标是相对文件路径。    |
   | 透明大纲    |为透明 32 x 32 PNG 大纲图标是相对文件路径。     |
   | 强调文字颜色    | 要用于轮廓图标将结合使用和作为背景的颜色。     |

有关详细信息，请参阅[清单编辑器](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor)并[清单架构](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema)。

4. 向下滚动到品牌部分并添加徽标和您的应用程序所需的强调文字颜色。  这些是将为您在团队中的应用程序显示的徽标。 

   > [!div class="mx-imgBorder"] 
   > ![品牌和选项卡](./media/embed-teams-app/branding-tabs.png "品牌和选项卡")

5. 下**功能**，选择**选项卡**。

6. 下**团队选项卡**选择**添加**。

   > [!div class="mx-imgBorder"] 
   > ![团队选项卡上添加](./media/embed-teams-app/team-tab-add.png "团队选项卡添加")

7. 在"配置 URL"输入字段中，使用以下格式添加您的应用程序配置 URL: `https://web.powerapps.com/webplayer/teamsapptabsettings?appid=<PowerApp ID>`

   替换为`<PowerApp ID>`与上述记录的应用程序 ID GUID。

   选择[作用域](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope)为你的应用中显示。 请确保**更新配置**已选中，然后选择**保存**。

   > [!div class="mx-imgBorder"] 
   > ![配置 URL](./media/embed-teams-app/configuration-url.png "配置 URL")

8. 下**完成**，选择**有效域**。 添加**apps.powerapps.com**并**apps.preview.powerapps.com**为团队应用程序的有效域。

   > [!div class="mx-imgBorder"] 
   > ![添加有效的域](./media/embed-teams-app/add-valid-domains.png "添加有效的域")

9. 下**完成**，选择**测试和分发**。 下**安装**，选择**安装**。

   > [!div class="mx-imgBorder"] 
   > ![选择安装](./media/embed-teams-app/test-distribute-app.png "选择安装")

10. 选择你想在中，安装的应用程序的团队，然后选择**安装**。

    > [!div class="mx-imgBorder"] 
    > ![添加到团队安装](./media/embed-teams-app/new-app-add-to-team.png "添加到团队安装")

11. 如果你想要立即将该应用的实例添加到频道，选择你想要使用在和选择的应用的频道**设置**。

    > [!div class="mx-imgBorder"] 
    > ![选择设置](./media/embed-teams-app/app-now-available.png "选择设置")

12. 选择“保存”。 

## <a name="add-the-app-as-a-tab"></a>将应用添加为一个选项卡

若要将应用程序作为一个选项卡添加到任何通道或会话，请选择 **+** ，然后在**选项卡为你的团队**选择你的应用。 

> [!div class="mx-imgBorder"] 
> ![为选项卡添加应用](./media/embed-teams-app/add-app-as-tab.png "为选项卡添加应用")

应用程序现在显示为一个选项卡。

> [!div class="mx-imgBorder"] 
> ![为选项卡的应用](./media/embed-teams-app/app-as-tab.png "应用作为选项卡")

### <a name="see-also"></a>另请参阅
[欢迎使用 Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[管理员：在 Microsoft Teams 中嵌入应用](https://docs.microsoft.com/power-platform/admin/share-app-teams)