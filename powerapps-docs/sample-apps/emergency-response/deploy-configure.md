---
title: 部署和配置“医院应急响应”应用 | Microsoft Docs
description: 详细介绍医院 IT 管理员如何为组织部署和配置示例应用。
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/07/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 97de25b8c1f80ad4bd89242a2c71f97eeec1c9aa
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80871640"
---
# <a name="deploy-and-configure-the-hospital-emergency-response-app"></a>部署和配置“医院应急响应”应用

为了适应你的需求，需要对“医院应急响应”应用进行少量的设置。 本文为医院 IT 管理员提供为其组织部署和配置应用程序的分步说明。

上述步骤预计完成时间：35-40 分钟  。

## <a name="demo-deploy-and-configure-the-hospital-emergency-response-app"></a>演示：部署和配置“医院应急响应”应用

观看如何部署和配置“医院应急响应”应用。

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="service-urls-for-us-government-customers"></a>面向 US Government 客户的服务 URL

US Government 客户也可以使用“医院应急响应”解决方案。 有一组用于访问 Power Apps US Government 环境和 Power BI 的 URL，它们与商业版不同。

本文通篇使用的是商业版服务 URL。 如果你是 US Government 客户，请使用相应的 US Government URL 进行部署，如下所述：


| **商业版 URL**                | **US Government 版本 URL**  |
|-------------------------------------------|--------------------------------|
| https://make.powerapps.com                | https://make.gov.powerapps.us (GCC)<br/><br/>https://make.high.powerapps.us (GCC High)                |
| https://admin.powerplatform.microsoft.com | https://gcc.admin.powerplatform.microsoft.us (GCC)<br/><br/>https://high.admin.powerplatform.microsoft.us (GCC High) |
| https://app.powerbi.com/                  | <https://app.powerbigov.us> (GCC)<br/><br/>https://app.high.powerbigov.us (GCC High)                  |

若要详细了解 Power Apps 和 Power BI 的 US Government 计划，请参阅：
- [Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI US Government](https://docs.microsoft.com/power-bi/service-govus-overview)


## <a name="deploy-the-hospital-emergency-response-app"></a>部署“医院应急响应”应用

若要为组织部署“医院应急响应”示例应用，请按照以下步骤操作。

- [步骤 1：注册 Power Apps 并创建环境](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [步骤 2：下载部署包](#step-2-download-the-deployment-package)
- [步骤 3：将解决方案文件导入到环境中](#step-3-import-the-solution-file-into-your-environment)
- [步骤 4：为组织加载配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)
    - [步骤 4.1：加载必需的配置数据](#step-41-load-mandatory-configuration-data)
    - [步骤 4.2：加载主数据](#step-42-load-master-data)
- [步骤 5：更新移动应用品牌](#step-5-update-the-mobile-app-branding)
- [步骤 6：为移动应用设置绕过同意](#step-6-bypass-consent-for-mobile-apps)
- [步骤 7：将 Azure Application Insights 密钥添加到移动应用以用于遥测（可选）](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional)
- [步骤 8：与组织中的用户共享画布应用](#step-8-share-canvas-apps-with-users-in-your-organization)
- [步骤 9：将移动应用设置为首推应用和特色应用](#step-9-set-your-mobile-app-as-hero-and-featured-app)
- [步骤 10：与组织中的管理员共享模型驱动应用](#step-10-share-model-driven-app-with-admins-in-your-organization)

### <a name="step-1-sign-up-for-power-apps-and-create-an-environment"></a>步骤 1：注册 Power Apps 并创建环境

如果你还没有 Power Apps，请注册 Power Apps 并购买适当的许可证。

更多信息：

-   [Power Apps 定价](https://powerapps.microsoft.com/pricing/)
-   [购买 Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

购买 Power Apps 后，请创建具有 Common Data Service 数据库的环境。

1.  登录到 [Power Platform 管理中心](https://aka.ms/ppac)。

2.  创建具有数据库的 Common Data Service 环境。 更多信息：[创建和管理环境](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT]
    > 创建数据库时，如果为数据库选择了安全组，则只能与属于该安全组的用户共享应用  。

3.  在环境中创建相应的用户。 更多信息：[创建用户并分配安全角色](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

### <a name="step-2-download-the-deployment-package"></a>步骤 2：下载部署包

从 <https://aka.ms/emergency-response-solution> 获取最新的部署包 (.zip)，其中包含解决方案文件、映像和数据文件，用于设置“医院应急响应”应用的应用和业务逻辑。

> [!IMPORTANT]
> 请务必先解除阻止部署包（.zip 文件），再解压缩此文件。 若要解除阻止，请执行以下操作：
> 1. 右键单击 .zip 文件，然后选择“属性”  。
> 2. 在“属性”对话框中，依次选择“解除阻止”  、“应用”  和“确定”  。

<br/>

在解除阻止部署文件（.zip 文件）后，将此文件解压缩到计算机上的某个位置。 提取的文件夹将包含下列文件夹：

| **文件夹/文件**       | **说明**  |
|-----------------------|------------------|
| **应用图标**         | 包含移动应用（画布应用）的默认应用图标|
| **数据文件**        | 包含使解决方案/应用正常运行的主数据文件和示例数据文件 (.xlsx)。 可以从这些文件导入数据，以便开始使用应用。 有关详细信息，请参阅[步骤 4：为组织加载配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Power BI 模板** | 包含将用于为组织配置报表的 Power BI 报表模板文件 (.pbit)。 详细信息：[使用 Power BI 仪表板获取见解](#get-insights-using-power-bi-dashboards)|
| **PowerShell**        | 包含用于配置移动应用（画布应用）的脚本。 |
| **解决方案文件**     | 包含创建“医院应急响应”应用所需的应用和元数据的 Common Data Service 解决方案文件。  |

### <a name="step-3-import-the-solution-file-into-your-environment"></a>步骤 3：将解决方案文件导入到环境中

1.  导航到你提取部署文件 (.zip) 的位置；你会找到“解决方案文件”  文件夹。 我们会将“解决方案文件”文件夹下的托管解决方案 (.zip) 文件导入到我们的环境中  。

2.  登录到 [Power Apps](https://make.powerapps.com)。

3.  从右上角选择环境。

4.  在左侧窗格中选择“解决方案”  ，然后选择“导入”  。

    > [!div class="mx-imgBorder"] 
    > ![导入解决方案](media/conf-import-solution.png "导入解决方案")

5.  在“导入解决方案”  对话框中，选择步骤 1 中提到的解决方案文件，然后按照向导中的步骤导入解决方案。

6.  成功导入解决方案后，在“导入”对话框中选择“关闭”  。

现在，你将在“应用”**下看到新应用**：

> [!div class="mx-imgBorder"] 
> ![新应用](media/conf-apps-new-apps.png "新应用")

选择“管理应用”  以打开模型驱动应用，通过该应用可以配置部署设置的其余部分。 更多信息：[什么是模型驱动应用？](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

> [!div class="mx-imgBorder"] 
> ![打开管理应用](media/conf-admin-app-open.png "打开管理应用")

管理应用具有许多实体，你可以在其中添加和管理医院系统的数据。 可以使用左侧导航窗格下半部分中的区域选取器来选择其他区域。

### <a name="step-4-load-configuration-and-master-data-for-your-organization"></a>步骤 4：为组织加载配置和主数据

“医院应急响应”应用所需的全部数据都可以在解压缩的部署文件夹下的“数据文件”  文件夹下找到。

“数据文件”  文件夹包含以下文件和文件夹：

<table style="width:100%">
<tr>
<th>名称</th>
<th>说明</th>
</tr>
<tr>
<td>根文件夹；其中包含以下文件：
<ul>
<li>00 - Acuities Import.xlsx</li>
<li>00 - App Config Import.xlsx</li>
<li>00 - App Import.xlsx</li>
<li>00 - Request Roles Import.xlsx</li>
<li>00 - Supplies Import.xlsx</li>
</ul>
</td>
<td>这些文件是配置数据文件，必须使用管理应用将其导入以下实体：
<ul>
<li>视敏度</li>
<li>应用配置</li>
<li>应用</li>
<li>请求角色</li>
<li>供应导入</li>
</ul>
<br/>将数据导入这些实体会为这些实体创建“医院应急响应”应用正常运行所需的记录。
<br/>
<br/>注意
<strong></strong>：请确保你没有更新这些实体中的配置值，但稍后将说明的“应用”<strong></strong>和“应用配置”<strong></strong>实体除外。</td>
</tr>
<tr>
<td>“示例数据”文件夹</td>
<td><p>此文件夹包含示例数据文件 (.xlsx)，可以将其导入以在应用程序中填充示例数据。 这些文件的命名表示应将数据导入到应用中的顺序。 </p>
<p>为以下包含“医院应急响应”应用的主示例数据的实体导入数据：
<ul>
<li>系统</li>
<li>大区</li>
<li>机构</li>
<li>位置</li>
<li>部门</li>
</ul>
<p>如果要导入组织数据而不是示例数据，可以将这些 Excel 文件中的示例数据替换为组织数据，然后将数据导入应用。</p>
<p>还可以为这些实体手动输入数据。 有关这些实体中的每个实体和字段的信息，请参阅<a href="#manually-configure-and-manage-master-data-for-your-organization">为组织手动配置和管理主数据</a></p></td>
</tr>
<tr>
<td>“主数据”文件夹的数据模板文件</td>
<td><p>此文件夹包含用于主实体的“空”数据文件 (.xlsx)，可用于填充组织数据，然后将其导入到应用中。</p>
<p>这些文件的命名表示应将数据导入到应用中的顺序。 它与前面提到的“示例数据”文件夹中的实体列表相同。</p>
<p>还可以为这些实体手动输入数据。 有关这些实体中的每个实体和字段的信息，请参阅<a href="#manually-configure-and-manage-master-data-for-your-organization">为组织手动配置和管理主数据</a></p>
</td>
</tr>
</table>

#### <a name="step-41-load-mandatory-configuration-data"></a>步骤 4.1：加载必需的配置数据

在进入下一步之前，必须在管理应用中的以下实体下导入配置数据  ：

| 区域名称 | 实体名称| 文件名
|-|-|-
| 位置 | 视敏度 | 00 - Acuities Import.xlsx
| 管理 | 应用配置 | 00 - App Config Import.xlsx
| 管理 | 应用 | 00 - App Import.xlsx
| 人员配备 | 请求角色 | 00 - Request Roles Import.xlsx
| 位置 | 供应 | 00 - Supplies Import.xlsx

##### <a name="how-to-load-data-from-data-files"></a>如何从数据文件加载数据？

要将数据从其中一个数据文件导入到实体，请执行以下步骤：

1.  在管理应用的左侧导航窗格中，选择要为其加载数据的实体。 例如，从区域选取器中选择“管理”，然后选择“视敏度”   。

2.  选择“从 Excel 导入”，然后从“数据文件”文件夹中选择“00 - Acuities Import.xlsx”文件    。

    > [!div class="mx-imgBorder"]
    > ![从 Excel 导入](media/conf-import-from-excel.png "从 Excel 导入")

3.  继续执行导入向导步骤以导入数据。

4.  导入数据后，你将在实体中看到导入的记录：

    > [!div class="mx-imgBorder"] 
    > ![实体记录](media/conf-entity-record.png "导入后的实体中的记录")

对其他配置数据实体重复上述步骤。

或者，如果要手动输入主数据，请参阅[为组织手动配置和管理主数据](#manually-configure-and-manage-master-data-for-your-organization)。

#### <a name="step-42-load-master-data"></a>步骤 4.2：加载主数据

如前文所述：
- 可使用“数据文件/示例数据”文件夹下主数据实体的示例数据文件将示例数据导入到所需实体中  。 

- 可使用“数据文件/主数据的数据模板文件”文件夹下主实体的“空”数据文件来填充组织数据，然后导入所需实体中的数据  。

还可在以后手动添加主数据。 更多信息：[为组织手动配置和管理主数据](#manually-configure-and-manage-master-data-for-your-organization)

### <a name="step-5-update-the-mobile-app-branding"></a>步骤 5：更新移动应用品牌

可更改移动应用的图标、配色方案或显示名称，使其与组织的品牌保持一致。

为此，可使用“管理”区域中的“应用”和“应用配置”实体，方式是从“数据文件”文件夹下提供的 Excel 文件以及部署包下“应用图标”文件夹中的图标文件导入应用和应用配置数据，这在[步骤 2：      下载部署包](#step-2-download-the-deployment-package)中有所介绍。

> [!div class="mx-imgBorder"] 
> ![“应用”和“应用配置”实体](media/conf-app-app-config-entities.png "“应用”和“应用配置”实体")

1.  确保分别使用“App Import.xlsx”和“App Config Import.xlsx”文件导入了“应用”和“应用配置”实体的配置数据     。

1.  下面将复制画布应用的应用 ID，以便可以在导入的“应用”  记录中填充它。 登录到 [Power Apps](https://make.powerapps.com)。

1.  从右上角选择环境。

1.  在左窗格中，选择“应用”，为画布应用选择省略号 (…)，然后选择“详细信息”   。

    > [!div class="mx-imgBorder"] 
    > ![应用详细信息](media/conf-environments-apps-details.png "应用详细信息")

1.  此应用 ID 将显示在该应用的“详细信息”窗格的底部。 ****   将应用 ID 及其名称复制到记事本文件中。

    > [!div class="mx-imgBorder"] 
    > ![“详细信息”中的“应用 ID”](media/conf-details-app-id.png "“详细信息”中的“应用 ID”")

1.  对每个画布应用重复执行步骤 4 和 5。

1.  打开“管理应用”，在管理应用的左侧导航窗格中，从区域选取器中选择“管理”  ，然后选择“应用”  。 随即显示从“App Import.xlsx”  文件导入的所有画布应用记录。

    > [!div class="mx-imgBorder"] 
    > ![管理应用](media/conf-admin-app-records.png "管理应用")

1.  选择其中一个应用记录将其打开。 请注意，“Power App ID”  字段是空的。

    > [!div class="mx-imgBorder"] 
    > ![Power App ID 字段 ](media/conf-powerapp-id-field.png "Power App ID 字段")

1.  在应用详细信息页面中：

    1. 将（之前复制的）记事本的应用 ID 复制到“Power App ID”字段  。

    2. 双击应用图标，然后从“应用图标”文件夹中为该应用选择一个图标文件  。 图像文件是直观命名的，因此你很容易就能选择正确的图标。 例如，为“紧急响应应用”选择“Emergency Response App.png”文件  。 你还可以根据组织品牌选择自定义图像。

    3. 视需要更新此应用的“说明”  或“显示名称”  。

    4. 视需要更新“从菜单隐藏应用”  值，以设置是否应在应用列表中显示此应用。 由于“紧急响应应用”是一个容器应用，因此该值默认设置为“否”   。

    5. 视需要更新“应用显示排名”  值，以设置此应用在应用列表中的显示位置。

    6. 选择“保存”。 

1.  对“应用”下的每条画布应用记录重复步骤 8 和 9  。

1.  在左窗格中，选择“应用配置”  。

1.  选择“紧急响应应用”  记录，将其打开以进行编辑。

    1.  视需要更新应用的颜色。

    2.  在“已启用设备共享”  字段中，选择“是”  或“否”  ，以指定“注销”  选项是否在移动应用中可用。 如果选择“是”，将可以使用“注销”   选项。 更多信息：用户指南中的[“结束班次 - 注销”](use.md#end-shift---sign-out)。

    > [!div class="mx-imgBorder"] 
    > ![“已启用设备共享”字段](media/conf-device-sharing-enabled-field.png "“已启用设备共享”字段")

1.  选择右下角的“保存”以保存更改  。

### <a name="step-6-bypass-consent-for-mobile-apps"></a>步骤 6：为移动应用设置绕过同意

只有租户管理员才能完成此步骤。 另外，在执行此步骤之前，需要每个移动应用（画布应用）的应用 ID。

若要获取应用的应用 ID，在管理应用的左侧导航窗格中，从区域选取器中选择“管理”  ，然后选择“应用”  。 随即显示所有移动应用（画布应用）。 选择一个移动应用以查看其应用 ID。 将每个应用的应用 ID 复制到记事本文件中。

> [!div class="mx-imgBorder"] 
> ![获取应用 ID](media/conf-admin-get-app-id.png "获取应用 ID")

接下来，请执行以下操作：

1.  打开记事本，并复制以下 PowerShell 脚本：

    ```powershell
    # MUST BE A TENANT ADMIN TO RUN THIS
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    Import-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Import-Module -Name Microsoft.PowerApps.PowerShell
    
    # This call opens prompt to collect credentials 
    # (Azure Active Directory account and password) 
    # used by the commands
    Add-PowerAppsAccount
    
    # Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppApisToBypassConsent -AppName APPGUIDHERE
    ```

2.  将 `APPGUIDHERE` 值替换为画布应用的实际应用 ID。

3.  将文件另存为 .ps 文件。

4.  以管理员身份运行 PowerShell 并执行刚刚创建的 .ps 文件。

5.  对每个画布应用重复执行步骤 2-4。

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional"></a>步骤 7：将 Azure Application Insights 密钥添加到移动应用以用于遥测（可选）

（可选）可以使用 Azure Application Insights 来收集移动应用（画布应用）的详细遥测，以获取有关应用使用情况的见解。 有关此内容的详细信息，请参阅[使用 Application Insights 分析应用遥测](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights)

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>步骤 8：与组织中的用户共享画布应用

为了使前端用户能够借助其移动设备中的画布应用使用数据，必须与他们共享这些应用。 使用 Azure AD 组可以更轻松地与用户组共享应用。

> [!IMPORTANT]
> 请确保你计划与之共享这些应用的用户或组已  有权访问你的环境。 通常，在[设置环境](#step-1-sign-up-for-power-apps-and-create-an-environment)时，你已添加用户或组。 也可以按照此处的步骤操作，先将用户添加到你的环境，并授予相应访问权限，再与用户共享这些应用：[创建用户并分配安全角色](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)。

1.  登录到 [Power Apps](https://make.powerapps.com)

2.  在左侧导航窗格中，选择“应用”  以查看所有应用的列表。

3.  选择移动应用（画布应用），并在横幅中选择“共享”  。

    > [!div class="mx-imgBorder"] 
    > ![共享画布应用](media/conf-share-canvas-apps.png "共享画布应用")

4.  指定要与哪些 Azure AD 组或用户共享此应用。 当应用连接到 Common Data Service 数据时，你还需要提供对实体的权限。 共享面板会提示你管理实体的安全性。 将“紧急响应用户”和“Common Data Service 用户”安全角色分配给此应用使用的实体，然后选择“共享”    。

    > [!div class="mx-imgBorder"] 
    > ![与 Azure AD 组或用户共享应用](media/conf-share-app-groups-users.png "与 Azure AD 组或用户共享应用")

5.  对每个移动应用重复执行步骤 3 和 4。

要详细了解如何共享应用，请参阅：[共享画布应用](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app)

### <a name="step-9-set-your-mobile-app-as-hero-and-featured-app"></a>步骤 9：将移动应用设置为首推应用和特色应用

通过此步骤，可以将移动应用设置为 Power Apps  移动应用中的首推应用和特色应用。 只有租户管理员才能完成此步骤。

在执行此步骤之前，需要获得要设置为首推应用和特色应用的每个移动应用（画布应用）的应用 ID。 要了解如何获取画布应用的应用 ID，请参阅[步骤 6：为移动应用设置绕过同意](#step-6-bypass-consent-for-mobile-apps)

接下来，请执行以下操作：

1.  打开记事本，并复制以下 PowerShell 脚本：


    ```powershell
    # MUST BE A TENANT ADMIN TO RUN THIS
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    Import-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Import-Module -Name Microsoft.PowerApps.PowerShell

    # This call opens prompt to collect credentials 
    # (Azure Active Directory account and password) 
    # used by the commands
    Add-PowerAppsAccount

    # Use the "Emergency Response App" App ID
    # To clear a featured app use Clear-AdminPowerAppAsFeatured

    #Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppAsFeatured -AppName APPGUIDHERE

    # To clear a hero app use Clear-AdminPowerAppAsHero
    # Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppAsHero -AppName APPGUIDHERE
    ```

2.  将脚本中的 `APPGUIDHERE` 值替换为需要分别设置为首推应用和特色应用的实际应用 ID。

3.  将文件另存为 .ps 文件。

4.  以管理员身份运行 PowerShell 并执行刚刚创建的 .ps 文件。
 

### <a name="step-10-share-model-driven-app-with-admins-in-your-organization"></a>步骤 10：与组织中的管理员共享模型驱动应用

为了让管理员用户能够使用管理员应用（模型驱动应用），必须与他们共享这些应用。 使用 Azure AD 组可以更轻松地与管理员用户组共享应用。

> [!IMPORTANT]
> 请确保你计划与之共享此应用的用户或组已  有权访问你的环境。 通常，在[设置环境](#step-1-sign-up-for-power-apps-and-create-an-environment)时，你已添加用户或组。 也可以按照此处的步骤操作，先将用户添加到你的环境，并授予相应访问权限，再与用户共享此应用：[创建用户并分配安全角色](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)。

1. 登录到 [Power Apps](https://make.powerapps.com)。

2. 在左侧导航窗格中，选择“应用”以查看所有应用的列表。

3. 选择模型驱动应用（“管理应用”-“紧急响应应用”  ），然后在横幅中选择“共享”  。

4. 指定要与哪些 Azure AD 组或管理员用户共享此应用，分配“紧急响应管理员”  安全角色，然后选择“共享”  。


## <a name="manually-configure-and-manage-master-data-for-your-organization"></a>为组织手动配置和管理主数据

管理员可以在 [Power Apps](https://make.powerapps.com) 中使用模型驱动应用来创建和管理其组织的主数据。 此数据是“医院应急响应”应用正常运行所需的。

> [!NOTE]
> 还可以将组织数据导入部署包中可用的数据文件，然后将其导入下面的实体。 更多信息：[步骤 4：为组织加载配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)

必须按以下顺序将主数据添加到下面的实体中：

1. [系统](#systems-data)

1. [区域](#regions-data)

1. [机构](#facilities-data)

1. [位置](#locations-data)

1. [科室](#departments-data)

从管理应用左侧导航的“位置”  区域中管理主数据：

> [!div class="mx-imgBorder"]
> ![locations-area](media/locations-area.png)

“层次结构”  区域下的各实体按应填充数据的顺序列出。

### <a name="systems-data"></a>系统数据

使用“系统”  实体可以创建和管理医院系统的条目。 这样就可以管理同一组织内的多个医院系统。

创建记录的步骤如下：

1. 在左窗格中选择“系统”  ，然后选择“新建”  ：  
    > [!div class="mx-imgBorder"]
    > ![select-systems-new](media/select-systems-new.png)

2. 在“新建系统”  页中，指定适当的值：  
   > [!div class="mx-imgBorder"]
   > ![enter-details-new-system](media/enter-details-new-system.png)

   | **字段**            | **说明**                                    |
   |----------------------|----------------------------------------------------|
   | 系统名称          | 键入医院的名称。                     |
   | 说明          | 键入可选说明。                      |
   | 生效开始日期 | 键入此医院系统的开始日期和时间。 |
   | 生效结束日期   | 键入此医院系统的结束日期和时间。   |

3. 选择“保存并关闭”。  新创建的记录将显示在“系统”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

### <a name="regions-data"></a>区域数据

使用“区域”  实体可以管理医院系统的地理区域。

创建记录的步骤如下：

1. 在左窗格中选择“区域”  ，然后选择“新建”  ：

2. 在“新建区域”  页中，指定适当的值：  

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-region](media/enter-details-new-region.png)

    | **字段**            | **说明**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | 系统               | 选择一个医院系统。 此列表是根据之前创建的“系统”数据  填充的。 |
    | 区域名称          | 键入区域名称。 例如，“西雅图”。                                                              |
    | 说明          | 键入可选说明。                                                                            |
    | 生效开始日期 | 键入此区域的开始日期和时间。                                                       |
    | 生效结束日期   | 键入此区域的结束日期和时间。                                                         |

3. 选择“保存并关闭”。  新创建的记录将显示在“区域”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

### <a name="facilities-data"></a>机构数据

使用“机构”  实体可以管理每个区域中的医院位置。 例如，“西雅图”区域内的“雷德蒙德”和“贝尔维尤”的机构    。

创建记录的步骤如下：

1. 在左窗格中选择“机构”  ，然后选择“新建”  。

2. 在“新建机构”  页中，指定适当的值： 

    > [!div class="mx-imgBorder"] 
    > ![enter-details-new-facility](media/enter-details-new-facility.png)

    | **字段**            | **说明**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | 区域               | 选择区域。 此列表是根据之前创建的“区域”数据  填充的。 |
    | 机构名称        | 键入机构名称。 例如，“贝尔维尤”。                                                  |
    | 说明          | 键入可选说明。                                                                   |
    | 呼吸机总数          | 键入机构可用的呼吸机总数                                  |
    | 生效开始日期 | 键入此机构的开始日期和时间。                                                     |
    | 生效结束日期   | 键入此机构的结束日期和时间。                                                       |

    如果需要，请输入机构地址。

3. 选择“保存并关闭”。  新创建的记录将显示在“机构”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

### <a name="locations-data"></a>位置数据

使用“位置”  实体可以管理每个医院机构的特定位置。

> [!NOTE]
> 在创建“位置”  记录之前，请确保已使用“00 - Acuities Import.xlsx”  文件导入视敏度数据（前面的[步骤 4：为组织加载配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)中说明的步骤）。 这是因为创建“位置”  记录需要视敏度信息。

创建记录的步骤如下：

1. 在左窗格中选择“位置”  ，然后选择“新建”  。

2. 在“新建位置”  页中，指定适当的值：  
 
    > [!div class="mx-imgBorder"]
    > ![enter-details-new-location](media/enter-details-new-location.png)

    | **字段**            | **说明**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | 位置名称        | 键入位置的名称。                                                                       |
    | 设施             | 选择机构。 此列表是根据之前创建的“机构”数据  填充的。 |
    | 层                | 键入机构的楼层信息。                                                         |
    | 单位                 | 键入机构的单位信息                                                           |
    | 急症      | 选择与此位置关联的视敏度记录。                                                                                                     |
    | COVID 位置      | 选择是否将此位置用于处理 COVID 患者（“是”  或“否”  。）                                                                                                      |
    | 总床位数           | 键入机构中的床位总数。                                                       |
    | 波动床位           | 键入机构中的波动床位数。 波动床位是指超出许可的床位容量时提供的床位（如果患者需要住院的话）。                                                      |
    | 阻止的床位数         | 键入机构中已阻止的床位数。                                                     |
    | 上次统计数量          | 根据创建的上次统计记录进行填充。                                             |
    | 占用率 | 基于上次统计数量和床位总数自动计算                                         |
    | 生效开始日期 | 键入此位置的开始日期和时间。                                                   |
    | 生效结束日期   | 键入此位置的结束日期和时间。                                                     |
    | 位置顺序       | 键入一个数字，用于对位置下拉列表中的位置进行排序。                               |
    | 备用场地标志  | 供内部使用。                                                                                     |

3. 选择“保存并关闭”。  新创建的记录将显示在“位置”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

### <a name="departments-data"></a>科室数据

使用“科室”  实体可以管理医院的科室信息。

创建记录的步骤如下：

1. 在左窗格中选择“科室”  ，然后选择“新建”  。

2. 在“新建科室”  页中，指定适当的值：

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-department](media/enter-details-new-department.png)

    | **字段**            | **说明**                                    |
    |----------------------|----------------------------------------------------|
    | Department Name      | 键入科室名称。                            |
    | 说明          | 键入可选说明。                      |
    | 生效开始日期 | 键入此科室的开始日期和时间。 |
    | 生效结束日期   | 键入此科室的结束日期和时间。   |

3. 选择“保存并关闭”。  新创建的记录将显示在“科室”  列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”  。

## <a name="get-insights-using-common-data-service-dashboards"></a>使用 Common Data Service 仪表板获取见解

默认情况下，“医院应急响应”管理（模型驱动）应用中提供以下仪表板：

- **床位管理**

   显示各机构可用的床位、占用率以及床位总数。

- **设备和供应**

  显示正在使用中的关键设备，以及不同机构中的供应情况。

- **员工管理**

  显示在不同机构中请求、分配和可用的员工数。

- **COVID 患者**

  显示不同机构中接受检测并且 COVID-19 呈阳性的患者数量。

- **出院**

  显示预计出院患者数量和实际出院数量。

除了默认提供的仪表板外，还可以创建自己的仪表板。

### <a name="manage-dashboards"></a>管理仪表板

管理仪表板的步骤如下：

1. 登录到 [Power Apps](https://make.powerapps.com) 并浏览到管理应用。

2. 在左侧导航窗格中，从区域选取器中选择“仪表板”  ：

    > [!div class="mx-imgBorder"]
    > ![select-dashboards](media/select-dashboards.png)

3. 选择左侧导航栏中的仪表板名称以查看图表：

    > [!div class="mx-imgBorder"]
    > ![view-charts](media/view-charts.png)

    > [!NOTE]
    > 可以在屏幕底部筛选数据，并使用筛选后的值自动更新顶部的图表。

4. 选择“展开”  选项，以全屏模式查看图表：

    > [!div class="mx-imgBorder"]
    > ![select-expand](media/select-expand.png)

### <a name="additional-analysis"></a>其他分析

- **向下钻取**：可以选择图表区域以进一步细化实体的其他属性（字段）：

    > [!div class="mx-imgBorder"]
    > ![select-chart-area-drill-down](media/select-chart-area-drill-down.png)

- **刷新**：可以刷新仪表板来反映更新后的数据。 可以单击“全部刷新”刷新特定仪表板上的所有图表，  ，也可以单击“刷新”来刷新  选定的图表：

    > [!div class="mx-imgBorder"]
    > ![refresh-dashboards](media/refresh-dashboards.png)

- **查看记录**：选择“更多命令(…  )”  ，然后选择“查看记录”  查看与给定图表相关联的所有记录：

    > [!div class="mx-imgBorder"]
    > ![select-more-commands](media/select-more-commands.png)

    > [!NOTE] 
    > 选择“查看记录”  时，你将看到图表和记录之间的实体拆分视图。 在右侧对记录的筛选器所做的任何更改都会通过自动更新反映到屏幕左侧的图表中。

若要详细了解如何编辑现有仪表板和更新图表的属性，请阅读[编辑现有仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard)。

### <a name="create-new-dashboards"></a>创建新仪表板

还可以创建自己的仪表板，并对其进行自定义以适应你的需求。 要创建新仪表板，请选择“新建”，然后选择“Dynamics 365 仪表板”   ：

> [!div class="mx-imgBorder"]
> ![select-new-dynamics-dashboard](media/select-new-dynamics-dashboard.png)

有关创建新仪表板的详细信息，请阅读[创建新仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard)。

## <a name="get-insights-using-power-bi-dashboards"></a>使用 Power BI 仪表板获取见解

发布 Power BI 仪表板并将其与组织中的用户共享，让他们可以使用仪表板获取见解并制定决策。

### <a name="prerequisites"></a>先决条件

- 已为访问报表的用户分配 Power BI Premium 容量或 Power BI Pro 许可证。 

- 在 Power BI 中创建一个用于发布报表的工作区。 登录 Power BI 并创建工作区。 更多信息：[在 Power BI 中创建新工作区](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- 从 Windows 应用商店中安装 Power BI Desktop：<https://aka.ms/pbidesktop>

   > [!NOTE] 
   > 如果你过去通过直接从“下载中心”页下载可执行文件来安装 Power BI Desktop，请删除它，并使用从 Microsoft Store 获取的 Power BI Desktop。 Microsoft Store 版本会随着新版本的发布而自动更新。
   >
   > 如果无法从 Microsoft Store 安装，请从[“下载中心”页](https://www.microsoft.com/download/details.aspx?id=58494)安装最新的非 Microsoft Store 版本。

- 从应用商店安装 Power BI Desktop 后，请运行它，使用有权在组织中发布 Power BI 应用的帐户登录。

### <a name="publish-the-power-bi-dashboard"></a>发布 Power BI 仪表板

1. 导航到你提取部署包的位置。 在“Power BI 模板”  文件夹下将能够找到 Emergency Response App.pbit  文件。

2. 在 Power BI Desktop 中打开“Emergency Response App.pbit”  文件。 系统会提示你键入以下值：

    - **Organization_name**：键入将在每个报表页的左上角填充的组织名称。
    - **CDS_base_solution_URL**：键入 Common Data Service 环境实例的 URL。 例如： https://[myenv]  .crm.dynamics.com

    > [!div class="mx-imgBorder"]
    > ![指定组织名称和基 URL](media/pbi-pub-rep1.png)

    选择“加载”  。

3. 系统将提示你输入凭据以连接到 Common Data Service 环境。 选择“组织帐户”   >  **“登录”** ，指定你的 Common Data Service 凭据。  

    > [!div class="mx-imgBorder"]
    > ![select-organizational-account](media/select-organizational-account.png)

4. 登录后，选择“连接”  ，以连接到 Common Data Service 中的数据。

5. 成功连接后，你的数据就会显示在 Power BI 报表中。 系统会提示你将挂起的更改应用于查询；选择“应用更改”  。

6. 选择“发布”  将数据发布到 Power BI 工作区。 系统会提示你保存更改；选择“保存”  。

    > [!div class="mx-imgBorder"]
    > ![select-refresh-publish](media/select-refresh-publish.png)

7. 系统会提示你将文件另存为 .pbix 文件（与 Common Data Service 环境信息一起保存）。 提供一个名称并将其保存在计算机上。

8. 保存 .pbix 文件后，系统会提示你发布报表。 在“发布到 Power BI”  页上，选择要发布到哪个工作区，然后单击“选择”  。

12. 在你的工作区中可以使用此报表了。 现在要配置数据集的数据刷新设置。 选择工作区中的数据集，并选择“计划刷新”  图标。  
    
    > [!div class="mx-imgBorder"]
    > ![schedule-refresh](media/schedule-refresh.png)

13. 首次尝试设置数据刷新设置时，你会看到“设置”  页，其中包含指明凭据无效的消息。 在“数据源凭据”  下，选择“编辑凭据”  ，以指定你的凭据。  

    > [!div class="mx-imgBorder"]
    > ![select-edit-credentials](media/select-edit-credentials.png)

14. 在下一个屏幕中：
    - 选择“OAuth2”  作为“身份验证方法”  。
    - 选择“组织”  作为“此数据源的隐私级别设置”  。
    - 选择“登录”  。

    系统会提示你指定凭据并登录。 成功登录后，你便会返回到“设置”  页。

15. 在“设置”  页中，展开“计划的刷新”  ，并指定根据计划来刷新数据所需的详细信息。 选择**应用**。

    > [!div class="mx-imgBorder"]
    > ![计划的刷新](media/refresh-schedule.png)

    > [!NOTE] 
    > 对数据刷新次数存在限制。 Power BI 将共享容量上的数据集限制为每天最多刷新 8 次。 如果数据集驻留在 Premium 容量上，则每天最多可在数据集设置中计划 48 次刷新。 更多信息：[刷新数据](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

16. 在左侧窗格中选择工作区名称，然后选择右上角的“创建应用”  。  

    > [!div class="mx-imgBorder"]
    > ![select-create-app](media/select-create-app.png)

17. 在应用发布页上，执行以下操作：

    1. 在“设置”  选项卡上，指定应用的名称和描述。

    2. 在“导航”  选项卡上，指定要将应用发布到哪个仪表板。

    3. 在“权限”  选项卡上，指定将能够查看此应用的用户或组。 请务必选中“自动安装此应用”  复选框，以便自动为最终用户安装此应用。 更多信息：[自动为最终用户安装应用](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![select-install-apps-automatically](media/select-install-apps-automatically.png)

18. 选择“发布应用”  。 有关在 Power BI 中发布应用的详细信息，请参阅[发布应用](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app)。

### <a name="view-the-power-bi-dashboard"></a>查看 Power BI 仪表板

登录 [Power BI](https://apps.powerbi.com) 即可访问和查看 Power BI 仪表板。

> [!div class="mx-imgBorder"]
> ![查看 Power BI 仪表板](media/view-power-dashboard.png)

可以使用报表顶部的筛选器来筛选医院系统、区域和机构的数据。 还可以筛选 COVID 位置。

> [!div class="mx-imgBorder"]
> ![报表筛选器](media/report-filters.png)

#### <a name="system-at-a-glance-page"></a>“系统概览”页 

“系统概览”页  是提供概述的默认页或顶级页。  

此页显示以下内容的汇总视图： 

- **COVID 患者**：显示 COVID 患者总数、COVID-19 检测呈阳性患者数以及疑似患者数。 

- **床位管理**：显示可用床位数、占用率、波动床位数以及床位总数。 还可以使用下面的网格按急症单位查看数字。 

- **护士人员配备管理**：显示 ICU 中的患者数、已分配的护士数，以及护士与患者的比例。  

- **出院**：显示长期住院患者总数、预计出院患者数和实际出院患者数。 

- **设备**：显示呼吸机总数、正在使用中的呼吸机数和可用呼吸机数。 

- **供应品**：按天显示现有供应品数。

> [!NOTE]
> - 选择任何汇总区域中的信息图标 (i) 会转到区域的相应详细信息页。 
> - 还可以对报表执行其他操作，如对数据进行筛选和排序、将报表导出为 PDF 和 PowerPoint、添加聚焦等。 若要详细了解 Power BI 中的报表功能，请参阅 [Power BI 中的报表](https://docs.microsoft.com/power-bi/consumer/end-user-reports)
> - 其中一些报表的最新或上次更新列显示数据上次刷新日期和时间。 通过查看这些列中的日期和时间值的颜色，也很容易识别新鲜度：
>    - 黑色：数据在不到 20 小时前刷新
>    - 灰色：数据在 20-24 小时前刷新
>    - 红色：数据在超过 24 小时前刷新 
 
#### <a name="system-view-page"></a>“系统视图”页

“系统视图”  页显示包含以下医院系统信息的图表：
- 正在使用中的呼吸机数和可用呼吸机数
- 可用床位数、急症护理床位数以及占用率
- 请求获取的员工总数、患者数（统计数字）、护士与患者的比例。
- 按天统计的现有供应品数

> [!div class="mx-imgBorder"]
> ![系统视图](media/report-system-view.png)

#### <a name="location-details-page"></a>“位置详细信息”页 

若要按位置向下钻取报表，请单击右上角的“位置详细信息”  。 “位置详细信息”  页显示按位置划分的数据，如床位总数、可用床位数、波动床位数、COVID 患者数等。 

> [!div class="mx-imgBorder"]
> ![位置详细信息](media/report-location-details.png) 

#### <a name="covid-patient-details-page"></a>“COVID 患者详细信息”页 

“COVID 患者详细信息”  页提供了关于 COVID 患者的向下钻取信息，如每个位置的患者数、一段时间内的患者数趋势（显示疑似患者 (PUI) 数和检测呈阳性的患者数的波峰和波谷），以及患者在医院中的位置。

> [!div class="mx-imgBorder"]
> ![COVID 患者详细信息](media/report-covid-details.png)

#### <a name="bed-management-page"></a>“床位管理”页 

“床位管理”  页提供了按位置划分的向下钻取信息，如可用床位总数和占用率。

> [!div class="mx-imgBorder"]
> ![床位管理](media/report-bed-details.png)

#### <a name="staff-details-page"></a>“员工详细信息”页  

“员工详细信息”  页提供了按位置划分的员工详细信息，如已分配的护士数、患者总数和 COVID 患者数。 它还显示一段时间内的护士与患者的比例和 ICU 护士与患者的比例。

> [!div class="mx-imgBorder"]
> ![员工详细信息](media/report-staff-details.png)

#### <a name="equipment-details-page"></a>“设备详细信息”页 

“设备详细信息”  页提供了按位置划分的设备详细信息，如正在使用中的呼吸机总数、COVID 患者数，以及正在使用中的其他设备（如腰带、充电器和风帽）数。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-equipment-details.png)

#### <a name="discharge-details-page"></a>“出院详细信息”页 

“出院详细信息”  页提供了以下详细信息：长期住院患者数、一段时间内的出院障碍数，以及实际出院数和预计出院数之间的差异。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-discharge-details.png)

#### <a name="supplies-on-hand-details-page"></a>“现有供应品详细信息”页 

“现有供应品详细信息”  页提供了按位置和供应品划分的供应品详细信息；它还提供了一段时间内现有可用供应品的数据。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-discharge-details.png)

## <a name="view-and-manage-app-feedback"></a>查看和管理应用反馈

一线员工在其移动设备上使用画布应用提供的所有反馈都存储在“应用反馈”  实体中，管理员可以使用管理应用左侧导航窗格中的“管理”  区域来查看和管理反馈。

要查看和管理应用反馈，请执行以下操作：

1. 登录到 [Power Apps](https://make.powerapps.com) 并浏览到管理应用。

2. 在左侧导航窗格中，从区域选取器中选择“管理”  。

3. 选择“应用反馈”  以查看用户提交的应用反馈的列表。 可以单击一条记录以查看详细信息，并可以选择是否将其标记为“已查看”。  

    > [!div class="mx-imgBorder"]
    > ![select-app-feedback](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>问题和反馈

- 若要报告“医院应急响应”示例应用存在的问题，请访问 <https://aka.ms/emergency-response-issues>。

- 若要提供关于“医院应急响应”示例应用的反馈，请访问 <https://aka.ms/emergency-response-feedback>。

## <a name="next-step"></a>下一步

[使用“医院应急响应”应用](use.md)
