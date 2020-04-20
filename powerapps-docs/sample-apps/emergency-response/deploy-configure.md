---
title: 部署“医院应急响应”应用 | Microsoft Docs
description: 详细介绍医院 IT 管理员如何为组织部署和配置示例应用。
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/15/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: bfe52ba868c23e54ed3f8b183e7fd4dfa96ffafc
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81441628"
---
# <a name="deploy-the-hospital-emergency-response-app"></a>部署“医院应急响应”应用

为了适应你的需求，需要对“医院应急响应”应用进行少量的设置。 本文为医院 IT 管理员提供为其组织部署和配置应用程序的分步说明。

上述步骤预计完成时间：35-40 分钟  。

## <a name="demo-deploy-the-hospital-emergency-response-app"></a>演示：部署“医院应急响应”应用

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
| **Power BI 模板** | 包含将用于为组织配置报表的 Power BI 报表模板文件 (.pbit)。 详细信息：[发布 Power BI 仪表板](#publish-the-power-bi-dashboard)|
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
<p>还可以为这些实体手动输入数据。 有关这些实体中的每个实体和字段的信息，请参阅<a href="configure-data-reporting.md#configure-and-manage-master-data-for-your-organization">为组织配置和管理主数据</a></p></td>
</tr>
<tr>
<td>“主数据”文件夹的数据模板文件</td>
<td><p>此文件夹包含用于主实体的“空”数据文件 (.xlsx)，可用于填充组织数据，然后将其导入到应用中。</p>
<p>这些文件的命名表示应将数据导入到应用中的顺序。 它与前面提到的“示例数据”文件夹中的实体列表相同。</p>
<p>还可以为这些实体手动输入数据。 有关这些实体中的每个实体和字段的信息，请参阅<a href="configure-data-reporting.md#configure-and-manage-master-data-for-your-organization">为组织配置和管理主数据</a></p>
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

或者，如果要手动输入主数据，请参阅[为组织配置和管理主数据](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization)。

#### <a name="step-42-load-master-data"></a>步骤 4.2：加载主数据

如前文所述：
- 可使用“数据文件/示例数据”文件夹下主数据实体的示例数据文件将示例数据导入到所需实体中  。 

- 可使用“数据文件/主数据的数据模板文件”文件夹下主实体的“空”数据文件来填充组织数据，然后导入所需实体中的数据  。

还可在以后手动添加主数据。 更多信息：[为组织配置和管理主数据](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization)

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
    > ![Power App ID 字段 ](media/conf-powerapp-id-field.png "更新应用信息")

1.  在应用详细信息页面中：

    1. 将（之前复制的）记事本的应用 ID 复制到“Power App ID”字段  。

    2. 双击应用图标，然后从“应用图标”文件夹中为该应用选择一个图标文件  。 图像文件是直观命名的，因此你很容易就能选择正确的图标。 例如，为“紧急响应应用”选择“Emergency Response App.png”文件  。 你还可以根据组织品牌选择自定义图像。

    3. 视需要更新此应用的“说明”  或“显示名称”  。

    4. 视需要更新“从菜单隐藏应用”  值，以设置是否应在应用列表中显示此应用。 由于“紧急响应应用”是一个容器应用，因此该值默认设置为“否”   。

    5. 视需要更新“应用显示排名”  值，以设置此应用在应用列表中的显示位置。

    6. 如有必要，在“跟踪级别”  字段中选择一个值，以指定是否要在“位置”  或“机构”  级别跟踪此移动应用中的数据。 更多信息：[管理移动应用的跟踪级别](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

    7. 选择“保存”。 

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

## <a name="publish-the-power-bi-dashboard"></a>发布 Power BI 仪表板

发布 Power BI 仪表板并将其与组织中的用户共享，让他们可以使用仪表板获取见解并制定决策。

可以使用以下任一选项发布 Power BI 仪表板：使用 AppSource 中的模板应用，或  使用部署包中提供的 .pbit  文件。

### <a name="option-a-publish-using-the-template-app-from-appsource"></a>选项 A：使用 AppSource 中的模板应用进行发布

有关使用 AppSource 中的模板应用的详细信息，请参阅：[连接到医院应急响应决策支持仪表板](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-health-emergency-response)

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>选项 B：使用部署包中的 .pbit 文件进行发布

本部分介绍了如何使用部署包中提供的 Emergency Response App.pbit  以便发布仪表板。

#### <a name="prerequisites"></a>先决条件

- 已为访问报表的用户分配 Power BI Premium 容量或 Power BI Pro 许可证。 

- 在 Power BI 中创建一个用于发布报表的工作区。 登录 Power BI 并创建工作区。 更多信息：[在 Power BI 中创建新工作区](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- 从 Windows 应用商店中安装 Power BI Desktop：<https://aka.ms/pbidesktop>

   > [!NOTE] 
   > 如果你过去通过直接从“下载中心”页下载可执行文件来安装 Power BI Desktop，请删除它，并使用从 Microsoft Store 获取的 Power BI Desktop。 Microsoft Store 版本会随着新版本的发布而自动更新。
   >
   > 如果无法从 Microsoft Store 安装，请从[“下载中心”页](https://www.microsoft.com/download/details.aspx?id=58494)安装最新的非 Microsoft Store 版本。

- 从应用商店安装 Power BI Desktop 后，请运行它，使用有权在组织中发布 Power BI 应用的帐户登录。

#### <a name="publish-the-dashboard-using-the-pbit-file"></a>使用 .pbit 文件发布仪表板

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

### <a name="after-publishing-the-dashboard"></a>发布仪表板后

若要查看发布的 Power BI 仪表板，请参阅[查看 Power BI 仪表板](configure-data-reporting.md#view-power-bi-dashboard)

## <a name="issues-and-feedback"></a>问题和反馈

- 若要报告“医院应急响应”示例应用存在的问题，请访问 <https://aka.ms/emergency-response-issues>。

- 若要提供关于“医院应急响应”示例应用的反馈，请访问 <https://aka.ms/emergency-response-feedback>。

## <a name="next-step"></a>下一步

[使用“医院应急响应”应用](use.md)
