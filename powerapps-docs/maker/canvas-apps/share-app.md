---
title: 共享画布应用 | Microsoft Docs
description: 通过授予其他用户运行或修改应用的权限来共享画布应用
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/18/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 75157ecd3921476d7b527dfc5b87b0efbd308f71
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75203964"
---
# <a name="share-a-canvas-app-in-power-apps"></a>在 Power Apps 中共享画布应用

生成满足业务需求的画布应用后，指定组织中哪些用户可以运行应用，哪些用户可以修改并重新共享应用。 按姓名指定每个用户或在 Azure Active Directory 中指定安全组。 如果每个人都可利用你的应用，则指定整个组织可以运行应用。

> [!IMPORTANT]
> 要使共享应用按预期运行，还必须管理应用所基于的数据源或源的权限，如[Common Data Service](#common-data-service)或[Excel](share-app-data.md)。 可能还需要共享应用依赖的[其他资源](share-app-resources.md)，例如流、网关或连接。

## <a name="prerequisites"></a>必备组件

共享应用前，必须将其保存至云（而非本地），然后发布应用。

- 为应用提供有意义的名称和明确说明，以便人们了解应用的功能并且可在列表中轻松找到该应用。 在 Power Apps Studio 的 "**文件**" 菜单上，选择 "**应用设置**"，指定名称，然后键入或粘贴说明。

- 无论何时进行更改，如果想要其他人看到这些更改，必须保存并重新发布应用。

## <a name="share-an-app"></a>共享应用

1. [登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 Power Apps，然后选择左边缘附近的 "**应用**"。

    ![显示应用列表](./media/share-app/file-apps.png)

1. 选择要共享的应用，方法是选择其图标。

    ![选择应用](./media/share-app/select-app.png)

1. 在横幅中选择 "**共享**"。

    ![打开共享屏幕](./media/share-app/banner-share.png)

1. 按名称或别名指定 Azure Active Directory 要与之共享应用的用户或安全组。

    - 若要允许整个组织运行应用（但不修改或共享），请在 "共享" 面板中键入**Everyone** 。
    - 如果项由分号分隔，则可以使用别名列表、友好名称或这些项的组合（例如， **Jane Doe &lt;jane.doe@contoso.com**）来共享应用。 如果有多个用户具有相同名称但具有不同的别名，则会将找到的第一个人员添加到列表。 如果名称或别名已经有权限或无法解析，则会出现工具提示。 

    ![指定用户和共同所有者](./media/share-app/share-everyone.png)

    > [!NOTE]
    > 无法将应用与组织中的通讯组或组织外的组共享。

1. 如果要允许与之共享应用的用户对其进行编辑和共享（除了运行该应用），请选中 "**共同所有者**" 复选框。

    如果在[解决方案中创建了应用程序](add-app-solution.md)，则无法向该安全组授予**共同所有者**权限。

    > [!NOTE]
    > 无论权限如何，都不能同时编辑应用。 如果一个人打开应用进行编辑，则其他人可以运行它，但不能对其进行编辑。

1. 如果你的应用连接到用户需要其访问权限的数据，请指定这些数据。

    例如，你的应用可能会连接到 Common Data Service 数据库中的实体。 共享此类应用程序时，"共享" 面板会提示您管理该实体的安全性。

    > [!div class="mx-imgBorder"]
    > ![分配安全角色](media/share-app/cds-assign-security-role.png)

    有关为实体管理安全的详细信息，请参阅本主题后面的[管理实体权限](share-app.md#manage-entity-permissions)。

1. 若要帮助用户查找你的应用，请选中 "向**新用户发送电子邮件邀请**" 复选框。

1. 在 "共享" 面板的底部，选择 "**共享**"。

    共享应用的每个人都可以在移动设备上的 Power Apps Mobile 中或在浏览器的[Dynamics 365](https://home.dynamics.com)上的 AppSource 中运行该应用。 共同所有者可以在[Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)中编辑并共享应用。

    如果你发送了电子邮件邀请，则与你共享该应用程序的所有人都可以通过选择邀请中的链接来运行它。

    - 如果用户在移动设备上选择链接，应用会在 Power Apps Mobile 中打开。
    - 如果用户选择台式计算机上的链接，则会在浏览器中打开该应用。

    收到邀请的共同所有者会获得另一个链接，该链接打开应用程序以在 Power Apps Studio 中进行编辑。

通过选择用户或安全组的名称，然后执行以下步骤之一，可以更改该用户或安全组的权限：

- 若要允许共同所有者运行应用，但不能再对其进行编辑或共享，请清除 "**共同所有者**" 复选框。
- 若要停止与该用户或组共享应用，请选择 "删除（x）" 图标。

## <a name="security-group-considerations"></a>安全组注意事项

- 如果与某个安全组共享应用，则该组的现有成员和加入该组的任何人都将具有你为该组所指定的权限。 退出该组的任何人将失去该权限，除非他们属于有访问权限的其他组或你为他们提供个人身份的权限。

- 每个安全组成员都具有与整个组相同的应用权限。 但是，可以为该组的一个或多个成员指定更高的权限，以允许他们具有更高的访问级别。 例如，你可以授予安全组运行应用程序的权限，但你也可以为属于该组的用户 B 授予 "**共同所有者**" 权限。 安全组中的每个成员都可以运行该应用，但是只有用户 B 可以编辑它。 如果向安全组授予**共同所有者**权限和用户 B 运行应用程序的权限，则该用户仍可以编辑该应用程序。

## <a name="manage-entity-permissions"></a>管理实体权限

### <a name="common-data-service"></a>Common Data Service

如果创建基于 Common Data Service 的应用，则还必须确保共享该应用的用户对该应用所依赖的一个或哪些实体具有适当的权限。 具体而言，这些用户必须属于一个安全角色，该安全角色可以执行创建、读取、写入和删除相关记录等任务。 在许多情况下，你需要创建一个或多个自定义安全角色，该角色具有用户运行该应用程序所需的确切权限。 然后，可以根据需要向每个用户分配一个角色。

> [!NOTE]
> 在撰写本文时，可以将安全角色分配给 Azure Active Directory 中的单个用户和安全组，但不能分配给 Office 组。

#### <a name="prerequisite"></a>先决条件

若要分配角色，您必须对 Common Data Service 数据库具有**系统管理员**权限。

#### <a name="assign-a-security-group-in-azure-ad-to-a-role"></a>将 Azure AD 中的安全组分配给角色

1. 在 "共享" 面板中，选择 "**数据权限**" 下**的 "分配安全角色**"。

1. 在 Common Data Service 中选择要分配给用户的角色或角色，或要与之共享应用的 Azure AD 中的安全组。
     > [!div class="mx-imgBorder"] 
     > ![安全角色列表](media/share-app/cds-assign-security-role-list.png "安全角色列表")

### <a name="common-data-service-previous-version"></a>Common Data Service（上一版本）

当您共享基于 Common Data Service 的旧版本的应用程序时，您必须对该服务单独共享运行时权限。 如果你没有执行此操作的权限，请参阅你的环境管理员。

## <a name="share-with-guests"></a>与来宾共享
 
可以与 Azure Active Directory 租户的来宾用户共享 Power Apps 画布应用。 这使得邀请外部业务合作伙伴、承包商和第三方能够运行公司的画布应用。 

> [!NOTE]
> 只能为与他们共享的应用分配**用户**角色，而不能为其分配**共同所有者**角色。

### <a name="prerequisites"></a>必备组件
- 在 Azure Active Directory （Azure AD）中，为租户启用 B2B 外部协作。 详细信息：[启用 B2B 外部协作并管理可以邀请来宾的人员](/azure/active-directory/b2b/delegate-invitations)
    - 默认情况下启用 B2B 外部协作。 但是，租户管理员可以更改这些设置。 有关 Azure AD B2B 的详细信息，请参阅[什么是来宾用户在 AZURE AD B2B 中的访问权限？](/azure/active-directory/b2b/what-is-b2b)  
- 对可将来宾用户添加到 Azure AD 租户的帐户的访问权限。 具有来宾邀请者角色的管理员和用户可以将来宾添加到租户。   
- 来宾用户必须拥有一个许可证，其中的 Power Apps 使用的权限与通过以下租户之一分配的应用功能匹配：
    - 托管要共享的应用的租户。
    - 来宾用户的主租户。

> [!NOTE]
> 每个应用计划的电源应用的范围限定为特定环境中的应用，因此无法跨租户识别它们。 Office 和 Power Apps 随附的每个用户计划的 power Apps 不会绑定到特定环境，因此，它们可在来宾方案中跨租户识别。 

### <a name="steps-to-grant-guest-access"></a>授权来宾访问的步骤
1. 选择 "**新来宾用户**"，在 Azure AD 中添加来宾用户。 详细信息：[快速入门：在 Azure AD 中添加新的来宾用户](/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal)。
    > [!div class="mx-imgBorder"] 
    > ![在 Azure AD 中添加来宾](media/share-app/guest_access_doc_1.png "在 Azure AD 中添加来宾")
2. 如果来宾用户在其主租户中没有许可证，则为来宾用户分配许可证。
   - 若要从 admin.microsoft.com 分配来宾用户，请参阅向[一个用户分配许可证](/office365/admin/subscriptions-and-billing/assign-licenses-to-users)。
   - 若要从 portal.azure.com 分配来宾用户，请参阅[分配或删除许可证](/azure/active-directory/fundamentals/license-users-groups)。
 
   > [!IMPORTANT]
   > 可能需要禁用 Microsoft 365 管理中心预览才能将许可证分配给来宾。 

3. 共享画布应用。 
    1. 登录到 https://make.powerapps.com  
    2. 单击 "**应用**"，选择一个画布应用，然后在命令栏上选择 "**共享**"。 
    3. 输入 Azure AD 租户的来宾用户的电子邮件地址。 详细信息：[什么是来宾用户在 AZURE AD B2B 中的访问权限？](/azure/active-directory/b2b/what-is-b2b)
          > [!div class="mx-imgBorder"] 
          > ![与来宾共享](media/share-app/guest_access_doc_2.png "与来宾共享")
 
共享应用以进行来宾访问后，来宾可以通过在共享过程中发送给他们的电子邮件发现和访问与他们共享的应用。

> [!div class="mx-imgBorder"]  
> ![来宾接收应用共享电子邮件](media/share-app/guest_access_doc_4.png "来宾接收应用共享电子邮件")

### <a name="frequently-asked-questions"></a>常见问题

#### <a name="whats-the-difference-between-canvas-app-guest-access-and-power-apps-portals"></a>画布应用来宾访问和电源应用门户之间的区别是什么？ 
画布应用支持构建一个应用，用于对业务流程进行数字化处理，而无需以传统编程语言（例如C#）编写代码。 对于画布应用的来宾访问，使由不同组织参与共同业务流程的人员团队能够访问与各种 Microsoft 和第三方源集成的相同应用资源。 详细信息：[画布的概述-适用于电源应用的应用连接器](/powerapps/maker/canvas-apps/connections-list)。

利用[Power Apps 门户](/powerapps/maker/portals/overview) 提供生成低代码的响应式网站的功能，使外部用户能够与 Common Data Service 中存储的数据进行交互。 它允许组织创建可通过匿名方式或通过其所选的登录提供者（如 LinkedIn、Microsoft 帐户或其他商业登录提供商）与组织外部的用户共享的网站。 

下表概述了 Power Apps 门户和画布应用之间的一些核心功能差异。  

| | 界面 | 身份验证 | 可访问的数据源 |
|------|--------|----------|-------------------|
| Power Apps 门户 | 仅浏览器体验 | 允许匿名访问和经过身份验证的访问 | Common Data Service |
| 画布应用 | 浏览器和移动应用 | 需要通过 Azure AD 进行身份验证 | 任何 ~ 150 的现成连接器和任何自定义连接器  |
||

#### <a name="can-guests-access-customized-forms-in-sharepoint"></a>来宾是否可以访问 SharePoint 中的自定义表单？
可以。 可以使用自定义窗体访问 SharePoint 列表的任何用户都可以使用窗体创建和编辑列表中的项，而无需任何 Power Apps 许可证。

#### <a name="can-guests-access-apps-embedded-in-sharepoint"></a>来宾是否可以访问嵌入在 SharePoint 中的应用？ 
可以。 但是，访问画布独立应用需要使用与应用功能（包括嵌入的应用）相匹配的权限的 Power Apps 的许可。 通过 Microsoft Power Apps 嵌入控件在 SharePoint 中嵌入画布应用时，请输入应用 id。为此，请在 "**应用程序 web 链接" 或 "ID** " 框中输入应用 ID。 

> [!div class="mx-imgBorder"]  
> ![在 SharePoint 中为来宾嵌入画布应用](media/share-app/guest_access_doc_5.PNG "在 SharePoint 中为来宾嵌入画布应用")

通过 iFrame HTML 标记在 SharePoint 中嵌入画布应用时，请使用完整 web URL 引用应用。 若要查找 URL，请参阅 "https://make.powerapps.com"，选择应用，选择 "**详细信息**" 选项卡，URL 将显示在 " **Web 链接**" 下。

> [!div class="mx-imgBorder"]  
> ![画布应用详细信息](media/share-app/guest_access_doc_6.PNG "画布应用详细信息")

#### <a name="how-come-guests-can-launch-the-app-shared-with-them-but-connections-fail-to-be-created"></a>来宾如何启动与他们共享的应用程序，但无法创建连接？
与非来宾一样，应用访问的基础数据源还必须可供来宾访问。

#### <a name="what-license-must-be-assigned-to-my-guest-so-they-can-run-an-app-shared-with-them"></a>必须将哪些许可证分配给来宾，才能运行与他们共享的应用？
运行应用程序所需的与非来宾相同的许可证。 例如，如果应用使用高级 connecters，则每个应用计划的每个应用计划或每个用户的电源应用计划必须分配给来宾。  

|                                 | SharePoint 自定义窗体 | 使用非高级连接器的独立画布应用 | 使用高级连接器的独立画布应用 | 模型驱动应用 |
|---------------------------------|----------------------------|----------------------------------------------------|------------------------------------------------|------------------|
| SharePoint 用户（无 PA 许可证） | x                          |                                                    |                                                |                  |
| 带/办公室的 Power Apps    | x                          | x                                                  |                                                |                  |
| 每个应用计划的电源应用          | x                          | x                                                  | x                                              | x                |
| 每个用户的电源应用计划         | x                          | x                                                  | x                                              | x                |

有关各种计划的定价和功能的更多详细信息，请参阅[Microsoft Power Apps 和 Power 自动许可指南](https://go.microsoft.com/fwlink/?linkid=2085130)。

#### <a name="in-power-apps-mobile-how-does-a-guest-see-apps-for-their-home-tenant"></a>在 Power Apps Mobile 中，来宾如何查看其 home 租户的应用？
访问了移动设备上的移动设备上发布的画布应用的任何用户，这些应用在不是其主租户的 Azure AD 租户中发布，必须注销电源应用并重新登录到 Power Apps Mobile。  

#### <a name="must-a-guest-accept-the-azure-ad-guest-invitation-prior-to-sharing-an-app-with-the-guest"></a>在与来宾共享应用之前，来宾是否必须接受 Azure AD 来宾邀请？
不。 如果来宾在接受来宾邀请之前启动与他们共享的应用程序，则在启动应用程序时，会提示来宾接受邀请作为登录体验的一部分。  

#### <a name="what-azure-ad-tenant-are-connections-for-a-guest-user-created-in"></a>哪个 Azure AD 租户是在中创建的来宾用户的连接？
应用的连接始终在应用关联的 Azure AD 租户的上下文中进行。 例如，如果在 Contoso 租户中创建了一个应用，则会在 Contoso 租户的上下文中建立 Contoso 内部用户和来宾用户的连接。

#### <a name="can-guests-use-microsoft-graph-via-microsoft-security-graph-connector-or-a-custom-connector-using-microsoft-graph-apis"></a>来宾可以使用 Microsoft Graph 通过 Microsoft 安全图形连接器还是使用 Microsoft Graph Api 的自定义连接器？
不需要，Azure AD 来宾无法查询 Microsoft Graph 来检索他们是来宾的租户的信息。

#### <a name="what-intune-policies-apply-to-guests-using-my-power-apps"></a>哪些 InTune 策略适用于使用我的 Power Apps 的来宾？
InTune 仅应用用户的主租户的策略。 例如，如果 Alice@Contoso.com 与 Vikram@Fabrikam.com共享应用，则 InTune 将继续在 Virkam 的设备上应用 Fabrikam.com 策略，而不考虑该用户运行的电源应用。

#### <a name="what-connectors-support-guest-access"></a>哪些连接器支持来宾访问？
不执行任何类型的 Azure AD 身份验证的所有连接器都支持来宾访问。 下表列举了所有执行 Azure AD 身份验证的连接器，以及哪些连接器当前支持来宾访问。 其中的许多都将更新为最新版本。

| **Connector**                                     | **支持来宾访问**                                              |
|---------------------------------------------------|------------------------------------------------------------------------|
| 10to8 预约计划                      | 否                                                                     |
| Adobe Creative Cloud                              | 否                                                                     |
| Adobe 登录                                        | 否                                                                     |
| Asana                                             | 否                                                                     |
| AtBot 管理员                                       | 否                                                                     |
| AtBot 逻辑                                       | 否                                                                     |
| Azure AD                                          | 是                                                                    |
| Azure 自动化                                  | 是                                                                    |
| Azure 容器实例                          | 是                                                                    |
| Azure 数据工厂                                | 是                                                                    |
| Azure Data Lake                                   | 是                                                                    |
| Azure DevOps                                      | 否                                                                     |
| Azure 事件网格                                  | 否                                                                     |
| Azure IoT Central                                 | 是                                                                    |
| Azure Key Vault                                   | 否                                                                     |
| Azure Kusto                                       | 是                                                                    |
| Azure Log Analytics                               | 是                                                                    |
| Azure 资源管理器                            | 是                                                                    |
| Basecamp 2                                        | 否                                                                     |
| Bitbucket                                         | 否                                                                     |
| Bitly                                             | 否                                                                     |
| bttn                                              | 否                                                                     |
| 缓冲区                                            | 否                                                                     |
| 业务中心                                  | 否                                                                     |
| CandidateZip                                      | 否                                                                     |
| Capsule CRM                                       | 否                                                                     |
| 云 PKI 管理                              | 否                                                                     |
| Cognito Forms                                     | 否                                                                     |
| Common Data Service                               | 否                                                                     |
| Common Data Service （旧版）                      | 否                                                                     |
| D & B 优化器                                     | 否                                                                     |
| Derdack SIGNL4                                    | 否                                                                     |
| Disqus                                            | 否                                                                     |
| 文档合并                                    | 否                                                                     |
| Dynamics 365                                      | 否                                                                     |
| 用于销售的 Dynamics 365 AI                         | 是                                                                    |
| 适用于 Fin & Ops 的 Dynamics 365                        | 否                                                                     |
| Enadoc                                            | 否                                                                     |
| Eventbrite                                        | 否                                                                     |
| Excel Online （Business）                           | 否                                                                     |
| Excel Online （OneDrive）                           | 否                                                                     |
| 过期提醒                               | 否                                                                     |
| FreshBooks                                        | 否                                                                     |
| GoToMeeting                                       | 否                                                                     |
| GoToTraining                                      | 否                                                                     |
| GoToWebinar                                       | 否                                                                     |
| Harvest                                           | 否                                                                     |
| 使用 Azure AD 的 HTTP                                | 否                                                                     |
| Infusionsoft                                      | 否                                                                     |
| Inoreader                                         | 否                                                                     |
| Intercom                                          | 否                                                                     |
| JotForm                                           | 否                                                                     |
| kintone                                           | 否                                                                     |
| LinkedIn                                          | 否                                                                     |
| 营销内容中心                             | 否                                                                     |
| 中型                                            | 否                                                                     |
| Metatask                                          | 否                                                                     |
| Microsoft Forms                                   | 否                                                                     |
| Microsoft Forms Pro                               | 否                                                                     |
| Microsoft Graph 安全性                          | 否                                                                     |
| Microsoft Kaizala                                 | 否                                                                     |
| Microsoft 学校数据同步                        | 否                                                                     |
| Microsoft StaffHub                                | 否                                                                     |
| Microsoft Teams                                   | 是                                                                    |
| Microsoft 待办事项（商业）                        | 否                                                                     |
| Muhimbi PDF                                       | 否                                                                     |
| NetDocuments                                      | 否                                                                     |
| Office 365 组                                 | 是                                                                    |
| Office 365 Outlook                                | 否                                                                     |
| Office 365 用户                                  | 是                                                                    |
| Office 365 视频                                  | 否                                                                     |
| OneDrive                                          | 否                                                                     |
| OneDrive for Business                             | 否                                                                     |
| OneNote（企业版）                                | 否                                                                     |
| Outlook Customer Manager                          | 否                                                                     |
| Outlook 任务                                     | 是                                                                    |
| Outlook.com                                       | 否                                                                     |
| Paylocity                                         | 否                                                                     |
| Planner                                           | 否                                                                     |
| Plumsail 窗体                                    | 否                                                                     |
| Power BI                                          | 是                                                                    |
| Project Online                                    | 否                                                                     |
| ProjectWise 设计集成                    | 否                                                                     |
| Projectwise 共享                                 | 否                                                                     |
| SharePoint                                        | 是                                                                    |
| SignNow                                           | 否                                                                     |
| Skype for Business Online                         | 否                                                                     |
| Soft1                                             | 否                                                                     |
| Stormboard                                        | 否                                                                     |
| Survey123                                         | 否                                                                     |
| SurveyMonkey                                      | 否                                                                     |
| Toodledo                                          | 否                                                                     |
| Typeform                                          | 否                                                                     |
| Vimeo                                             | 否                                                                     |
| Webex 团队                                       | 否                                                                     |
| Windows Defender 高级威胁防护（ATP） | 否                                                                     |
| Word Online （商业）                            | 否                                                                     |
