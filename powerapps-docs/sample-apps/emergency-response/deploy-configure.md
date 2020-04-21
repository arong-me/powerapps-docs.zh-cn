---
title: 部署医院应急响应应用 | Microsoft Docs
description: 提供有关医院 IT 管理员为其组织部署和配置示例应用的详细说明。
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
ms.openlocfilehash: 132276b88fe23e9ea4a69caeff330c10f7d32daf
ms.sourcegitcommit: 371fb08328f88f8bae7335db413d52b5c961c3e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2020
ms.locfileid: "3266796"
---
# <a name="deploy-the-hospital-emergency-response-app"></a>部署医院应急响应应用

医院应急响应应用需要进行少量的设置以适应您的需要。 本文提供有关医院 IT 管理员为其组织部署和配置应用程序的分步说明。

完成这些步骤的估计时间：**35–40 分钟**。

## <a name="demo-deploy-the-hospital-emergency-response-app"></a>演示：部署医院应急响应应用

观看如何部署和配置医院应急响应应用。

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="service-urls-for-us-government-customers"></a>面向美国政府客户的服务 URL

医院应急响应解决方案也适用于美国政府客户。 与商业版本相比，用于访问 Power Apps 美国政府环境和 Power BI 的 URL 集不同。

本文通篇使用服务 URL 的商业版本。 如果您是美国政府客户，请按照以下说明使用相应的美国政府 URL 进行部署：


| **商业版 URL**                | **US Government 版 URL**  |
|-------------------------------------------|--------------------------------|
| https://make.powerapps.com                | https://make.gov.powerapps.us (GCC)<br/><br/>https://make.high.powerapps.us (GCC High)                |
| https://admin.powerplatform.microsoft.com | https://gcc.admin.powerplatform.microsoft.us (GCC)<br/><br/>https://high.admin.powerplatform.microsoft.us (GCC High) |
| https://app.powerbi.com/                  | <https://app.powerbigov.us> (GCC)<br/><br/>https://app.high.powerbigov.us (GCC High)                  |

有关 Power Apps 和 Power BI 的美国政府计划的详细信息，请参阅：
- [适用于美国政府的 Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [适用于美国政府的 Power BI](https://docs.microsoft.com/power-bi/service-govus-overview)


## <a name="deploy-the-hospital-emergency-response-app"></a>部署医院应急响应应用

请执行以下步骤来为您的组织部署医院应急响应示例应用。

- [步骤 1：注册 Power Apps 并创建环境](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [步骤 2：下载部署包](#step-2-download-the-deployment-package)
- [步骤 3：将解决方案文件导入到您的环境中](#step-3-import-the-solution-file-into-your-environment)
- [步骤 4：加载您的组织的配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)
    - [步骤 4.1：加载必需的配置数据](#step-41-load-mandatory-configuration-data)
    - [步骤 4.2：加载主数据](#step-42-load-master-data)
- [步骤 5：更新移动应用品牌](#step-5-update-the-mobile-app-branding)
- [步骤 6：绕过移动应用的同意确认](#step-6-bypass-consent-for-mobile-apps)
- [步骤 7：将 Azure Application Insights 密钥添加到移动应用以进行遥测（可选）](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional)
- [步骤 8：与组织中的用户共享画布应用](#step-8-share-canvas-apps-with-users-in-your-organization)
- [步骤 9：将移动应用设置为首推应用和特色应用](#step-9-set-your-mobile-app-as-hero-and-featured-app)
- [步骤 10：与组织的管理员共享模型驱动应用](#step-10-share-model-driven-app-with-admins-in-your-organization)

### <a name="step-1-sign-up-for-power-apps-and-create-an-environment"></a>步骤 1：注册 Power Apps 并创建环境

如果您还没有 Power Apps，请注册 Power Apps 并购买相应的许可证。

详细信息：

-   [Power Apps定价](https://powerapps.microsoft.com/pricing/)
-   [购买 Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

购买 Power Apps 后，使用 Common Data Service 数据库创建一个环境。

1.  登录 [Power Platform 管理中心](https://aka.ms/ppac)。

2.  使用数据库创建 Common Data Service 环境。 详细信息：[创建和管理环境](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT]
    > 在创建数据库时，如果为数据库选择安全组，则*只能*与属于安全组成员的用户共享这些应用。

3.  在您的环境中创建适当的用户。 详细信息：[创建用户并分配安全角色](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

### <a name="step-2-download-the-deployment-package"></a>步骤 2：下载部署包

从包含解决方案文件、映像和数据文件的 <https://aka.ms/emergency-response-solution> 中获取最新部署包 (.zip)，来为医院应急响应应用设置应用和业务逻辑。

> [!IMPORTANT]
> 在提取部署包（.zip 文件）之前，请确保取消阻止该文件。 取消阻止：
> 1. 右键单击 .zip 文件，然后选择**属性**。
> 2. 在属性对话框中，选择**取消阻止**，然后选择**应用**，再选择**确定**。

<br/>

取消阻止部署文件（.zip 文件）后，将该文件提取到计算机上的某个位置。 提取的文件夹中将包含以下文件夹：

| **文件夹/文件**       | **说明**  |
|-----------------------|------------------|
| **App Icons**         | 包含移动应用（画布应用）的默认应用图标|
| **Data Files**        | 包含让解决方案/应用运行的主数据和示例数据文件 (.xlsx)。 您可以从这些文件导入数据来开始使用应用。 有关详细信息，请参阅[步骤 4：加载您的组织的配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Power BI Template** | 包含 Power BI 报表模板文件 (.pbit)，您将使用该文件来为组织配置报告。 详细信息：[发布 Power BI 仪表板](#publish-the-power-bi-dashboard)|
| **PowerShell**        | 包含您用于配置移动应用（画布应用）的脚本。 |
| **解决方案文件**     | 包含创建医院应急响应应用所需的应用和元数据的 Common Data Service 解决方案文件。  |

### <a name="step-3-import-the-solution-file-into-your-environment"></a>步骤 3：将解决方案文件导入到您的环境中

1.  导航到您提取部署文件 (.zip) 的位置；您将找到一个 **Solution File** 文件夹。 我们会将 **Solution File** 文件夹下的托管解决方案 (.zip) 文件导入到我们的环境中。

2.  登录到 [Power Apps](https://make.powerapps.com)。

3.  从右上角选择您的环境。

4.  在左窗格中，选择**解决方案**，然后选择**导入**。

    > [!div class="mx-imgBorder"] 
    > ![导入解决方案](media/conf-import-solution.png "导入解决方案")

5.  在**导入解决方案**对话框中，选择步骤 1 中提到的解决方案文件，然后按照向导中的步骤导入解决方案。

6.  在成功导入解决方案后，在导入对话框中选择**关闭**。

现在，您将在**应用**下看到新应用：

> [!div class="mx-imgBorder"] 
> ![新应用](media/conf-apps-new-apps.png "新应用")

选择**管理应用**打开模型驱动应用，使用它，您可以配置其余部署设置。 更多信息请参阅：[什么是模型驱动型应用？](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

> [!div class="mx-imgBorder"] 
> ![打开管理应用](media/conf-admin-app-open.png "打开管理应用")

管理应用有许多实体，您可以在其中添加和管理您的医院系统的数据。 您可以使用左侧导航窗格下部的区域选取器来选择不同的区域。

### <a name="step-4-load-configuration-and-master-data-for-your-organization"></a>步骤 4：加载您的组织的配置和主数据

您所提取的部署文件夹下的 **Data Files** 文件夹下提供了医院应急响应应用所需的所有数据。

**Data Files** 文件夹包含以下文件和文件夹：

<table style="width:100%">
<tr>
<th>名称</th>
<th>说明</th>
</tr>
<tr>
<td>在根目录；提供以下文件：
<ul>
<li>00 - Acuities Import.xlsx</li>
<li>00 - App Config Import.xlsx</li>
<li>00 - App Import.xlsx</li>
<li>00 - Request Roles Import.xlsx</li>
<li>00 - Supplies Import.xlsx</li>
</ul>
</td>
<td>这些是必须使用管理应用导入到以下实体的配置数据文件：
<ul>
<li>Acuities</li>
<li>App Config</li>
<li>应用</li>
<li>Request Roles</li>
<li>Supplies Import</li>
</ul>
<br/>将数据导入到这些实体将会创建这些实体的记录，这些实体是医院应急响应应用运行所必需的。
<br/>
<br/>
<strong>警告</strong>：确保除了<strong>应用</strong>和<strong>应用配置</strong>实体之外，不要更新这些实体中的配置值，如文章后面所说明的。</td>
</tr>
<tr>
<td><strong>Sample Data</strong> 文件夹</td>
<td><p>此文件夹包含示例数据文件 (.xlsx)，您可以导入该文件来填充应用程序中的示例数据。 这些文件的名称指示在您的应用中导入数据应该采用的顺序。 </p>
<p>导入以下实体的数据，这些实体包含医院应急响应应用的主示例数据：
<ul>
<li>系统</li>
<li>区域</li>
<li>Facilities</li>
<li>位置</li>
<li>部门</li>
</ul>
<p>如果您要导入组织数据，而不是示例数据，您可以将这些 Excel 文件中的示例数据替换为您的组织数据，然后在应用中导入数据。</p>
<p>您还可以手动输入这些实体的数据。 有关这些实体中的每个实体和这些实体中的字段的信息，请参阅<a href="configure-data-reporting.md#configure-and-manage-master-data-for-your-organization">为您的组织配置和管理主数据</a></p></td>
</tr>
<tr>
<td><strong>Data Template File for Master Data</strong> 文件夹</td>
<td><p>此文件夹包含主实体的“empty”数据文件 (.xlsx)，您可以使用它们来填充组织数据，然后将其导入到应用中。</p>
<p>这些文件的名称指示在您的应用中导入数据应该采用的顺序。 它是前面提到的 <strong>Sample Data</strong> 文件夹的同一个实体列表。</p>
<p>您还可以手动输入这些实体的数据。 有关这些实体中的每个实体和这些实体中的字段的信息，请参阅<a href="configure-data-reporting.md#configure-and-manage-master-data-for-your-organization">为您的组织配置和管理主数据</a></p>
</td>
</tr>
</table>

#### <a name="step-41-load-mandatory-configuration-data"></a>步骤 4.1：加载必需的配置数据

在继续进行下一步之前，**必须**在管理应用中的以下实体下导入配置数据：

| 区域名称 | 实体名称| 文件名
|-|-|-
| 位置 | 锐器 | 00 - Acuities Import.xlsx
| 管理 | 应用配置 | 00 - App Config Import.xlsx
| 管理 | 应用 | 00 - App Import.xlsx
| 人员配备 | Request Roles | 00 - Request Roles Import.xlsx
| 位置 | 用品 | 00 - Supplies Import.xlsx

##### <a name="how-to-load-data-from-data-files"></a>如何从数据文件加载数据？

将数据从其中一个数据文件导入到实体：

1.  在管理应用的左侧导航窗格中，选择要为其加载数据的实体。 例如，从区域选取器中选择**管理**，然后选择**锐器**。

2.  选择**从 Excel 导入**，然后从 **Data Files** 文件夹中选择 **00 - Acuities Import.xlsx** 文件。

    > [!div class="mx-imgBorder"]
    > ![从 Excel 导入](media/conf-import-from-excel.png "从 Excel 导入")

3.  继续执行导入向导步骤导入数据。

4.  在导入数据后，您将在实体中看到导入的记录：

    > [!div class="mx-imgBorder"] 
    > ![实体记录](media/conf-entity-record.png "导入后实体中的记录")

对其他配置数据实体重复上述步骤。

或者，如果要手动输入主数据，请参阅[为您的组织配置和管理主数据](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization)。

#### <a name="step-42-load-master-data"></a>步骤 4.2：加载主数据

如前文所述：
- 您可以使用 **Data Files/Sample Data** 文件夹下的主数据实体的示例数据文件，将示例数据导入所需的实体中。 

- 您可以使用 **Data Files/Data Template File for Master Data** 文件夹下的主实体的“empty”数据文件（可用于填充组织数据），然后将数据导入所需的实体中。

您还可以以后手动添加主数据。 详细信息：[为您的组织配置和管理主数据](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization)

### <a name="step-5-update-the-mobile-app-branding"></a>步骤 5：更新移动应用品牌

您可以更改移动应用的应用图标、颜色方案或显示名称，来匹配您的组织的商标。

您可以通过在**管理**区域中使用**应用**和**应用配置**实体来执行此操作，方法是从部署包下 **Data Files** 文件夹中提供的 Excel 文件，以及 **App Icons** 文件夹下的图标文件导入应用和应用配置数据，如[步骤 2：下载部署包](#step-2-download-the-deployment-package)中所述。

> [!div class="mx-imgBorder"] 
> ![应用和应用配置实体](media/conf-app-app-config-entities.png "应用和应用配置实体")

1.  请确保分别使用 **App Import.xlsx** 和 **App Config Import.xlsx** 文件导入了**应用**和**应用配置**实体的配置数据。

1.  现在，我们将复制画布应用的应用 ID，以便我们可以在导入的**应用**记录中填充它。 登录到 [Power Apps](https://make.powerapps.com)。

1.  从右上角选择您的环境。

1.  在左侧窗格中，选择**应用**，然后选择画布应用的省略号 (...)，再选择**详细信息**。

    > [!div class="mx-imgBorder"] 
    > ![应用详细信息](media/conf-environments-apps-details.png "应用详细信息")

1.  应用 ID 显示在应用的 **详细信息** 窗格的底部。 在“记事本”文件中复制应用 ID 及其名称。

    > [!div class="mx-imgBorder"] 
    > ![详细信息应用 ID](media/conf-details-app-id.png "详细信息应用 ID")

1.  对每个画布应用重复步骤 4 和步骤 5。

1.  打开管理应用，然后在管理应用的左侧导航窗格中，从区域选取器中选择**管理**，然后选择**应用**。 这将显示从 **App Import.xlsx** 文件导入的所有画布应用记录。

    > [!div class="mx-imgBorder"] 
    > ![管理应用](media/conf-admin-app-records.png "管理应用")

1.  通过选择其中一个应用记录来将其打开。 请注意，**Power App ID** 字段是空的。

    > [!div class="mx-imgBorder"] 
    > ![Power App ID 字段](media/conf-powerapp-id-field.png "更新应用信息")

1.  在应用详细信息页面：

    1. 将应用 ID 从“记事本”（先前复制到的位置）复制到 **Power App ID** 字段。

    2. 双击应用图标，然后从 **App Icons** 文件夹中选择应用的图标文件。 图像文件的名称很直观，您可以轻松地选出正确的图标。 例如，为**紧急响应应用**选择“Emergency Response App.png”文件。 您还可以根据您的组织品牌选择自定义图像。

    3. 如果需要，更新应用的**说明**或**显示名称**。

    4. 如果需要，更新**在菜单中隐藏应用**值来设置是否应该在应用列表中显示该应用。 当**应急响应应用**是容器应用时，此值默认设置为**否**。

    5. 如有必要，更新**应用显示排名**值来设置应用在应用列表中的显示位置。

    6. 如果需要，请在**跟踪级别**字段中选择一个值来指定您是否希望在**位置**或**设施**级别跟踪此移动应用中的数据。 详细信息：[管理移动应用的跟踪级别](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

    7. 选择**保存**。

1.  对**应用**下的每个画布应用记录重复步骤 8 和 9。

1.  在左侧窗格中选择**应用配置**。

1.  选择**应急响应应用**记录以将其打开进行编辑。

    1.  如果需要，更新应用的颜色。

    2.  在**设备共享已启用**字段中选择**是**或**否**，指定**注销**选项在移动应用中是否可用。 选择**是**将**注销**选项设置为可用。 详细信息：用户指南中的[结束班次 - 注销](use.md#end-shift---sign-out)。

    > [!div class="mx-imgBorder"] 
    > ![“设备共享已启用”字段](media/conf-device-sharing-enabled-field.png "“设备共享已启用”字段")

1.  选择右下角的**保存**以保存您的更改。

### <a name="step-6-bypass-consent-for-mobile-apps"></a>步骤 6：绕过移动应用的同意确认

您必须是租户管理员才能完成此步骤。 此外，在执行此步骤之前，您将需要每个移动应用（画布应用）的应用 ID。

要获取您的应用的应用 ID，在管理应用的左侧导航窗格中，从区域选取器中选择**管理**，然后选择**应用**。 这将显示所有移动应用（画布应用）。 选择一个移动应用来查看其应用 ID。 将每个应用的应用 ID 复制到一个记事本文件中。

> [!div class="mx-imgBorder"] 
> ![获取应用 ID](media/conf-admin-get-app-id.png "获取应用 ID")

接下来，执行以下操作：

1.  打开“记事本”，复制此 PowerShell 脚本：

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

4.  作为管理员运行 PowerShell 并执行您刚才创建的 .ps 文件。

5.  对每个画布应用重复步骤 2 - 4。

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional"></a>步骤 7：将 Azure Application Insights 密钥添加到移动应用以进行遥测（可选）

或者，您可以使用 Azure Application Insights 收集您的移动应用（画布应用）的详细遥测，以获取有关应用使用的见解。 有关详细信息，请参阅[使用 Application Insights 分析应用遥测](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights)

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>步骤 8：与组织中的用户共享画布应用

为了让您的前线用户在其移动设备中使用画布应用来使用数据，必须将这些应用与其共享。 使用 Azure AD 组轻松地与用户组共享应用会更加简单。

> [!IMPORTANT]
> 确保计划与其共享应用的用户或组*已经*具有您的环境的访问权限。 通常，在[设置您的环境](#step-1-sign-up-for-power-apps-and-create-an-environment)时，您已经添加了用户或组。 或者，您可以按照此处的步骤向您的环境中添加用户，并在与他们共享应用之前提供相应的访问权限：[创建用户和分配安全角色](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)。

1.  登录到“[Power Apps](https://make.powerapps.com)”

2.  在左侧导航窗格中，选择**应用**查看您的所有应用的列表。

3.  选择一个移动应用（画布应用），然后在横幅中选择**共享**。

    > [!div class="mx-imgBorder"] 
    > ![共享画布应用](media/conf-share-canvas-apps.png "共享画布应用")

4.  指定您要与之共享此应用的 Azure AD 组或用户。 在应用连接到 Common Data Service 数据时，您还需要提供实体权限。 共享面板会提示您管理实体的安全性。 将**应急响应用户**和 **Common Data Service 用户**安全角色分配给此应用使用的实体，然后选择**共享**。

    > [!div class="mx-imgBorder"] 
    > ![与 Azure AD 组或用户共享应用](media/conf-share-app-groups-users.png "与 Azure AD 组或用户共享应用")

5.  对每个移动应用重复步骤 3 和步骤 4。

有关共享应用的详细信息：[共享画布应用](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app)

### <a name="step-9-set-your-mobile-app-as-hero-and-featured-app"></a>步骤 9：将移动应用设置为首推应用和特色应用

此步骤可让您将移动应用设置为 **Power Apps** 移动应用中的首推应用和特色应用。 您必须是租户管理员才能完成此步骤。

执行此步骤之前，您需要要将其设置为首推应用和特色应用的每个移动应用（画布应用）的应用 ID。 有关获取画布应用的应用 ID 的信息，请参阅[步骤 6：绕过移动应用的同意确认](#step-6-bypass-consent-for-mobile-apps)

接下来执行以下操作：

1.  打开“记事本”，复制此 PowerShell 脚本：


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

2.  将脚本中的 `APPGUIDHERE` 值分别替换为您要设置为特色和首推的应用的实际应用 ID。

3.  将文件另存为 .ps 文件。

4.  作为管理员运行 PowerShell 并执行您刚才创建的 .ps 文件。
 

### <a name="step-10-share-model-driven-app-with-admins-in-your-organization"></a>步骤 10：与组织的管理员共享模型驱动应用

为了使管理员用户可以使用管理应用（模型驱动应用），必须将应用与他们共享。 使用 Azure AD 组轻松地与管理员用户组共享应用会更加简单。

> [!IMPORTANT]
> 确保计划与其共享应用的用户或组*已经*具有您的环境的访问权限。 通常，在[设置您的环境](#step-1-sign-up-for-power-apps-and-create-an-environment)时，您已经添加了用户或组。 或者，您可以按照此处的步骤向您的环境中添加用户，并在与他们共享应用之前提供相应的访问权限：[创建用户和分配安全角色](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)。

1. 登录到 [Power Apps](https://make.powerapps.com)。

2. 在左侧导航窗格中，选择应用查看您的所有应用的列表。

3. 选择模型驱动应用（**管理应用 – 应急响应应用**），然后在横幅中选择**共享**。

4. 指定要与其共享此应用的 Azure AD 组或管理员用户，分配**应急响应管理员**安全角色，然后选择**共享**。

## <a name="publish-the-power-bi-dashboard"></a>发布 Power BI 仪表板

发布 Power BI 仪表板并将其与组织中的用户共享，让他们可以使用仪表板获取见解、制定决策。

您可以使用以下任一选项发布 Power BI 仪表板：使用来自 AppSource 的模板应用，*或*使用部署包中提供的 **.pbit** 文件。

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>选项 A：使用来自 AppSource 的模板应用发布（首选选项）

这里提供了有关使用来自 AppSource 的模板应用的详细信息：[连接到医院应急响应决策支持仪表板](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-health-emergency-response)

> [!IMPORTANT]
> 与使用 .pbit 文件选项进行发布相比，这是一种发布 Power BI 仪表板的更简便的方法。 我们建议客户使用此选项，而不是使用 .pbit 选项发布。 

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>选项 B：使用部署包中的 .pbit 文件发布

本节提供有关如何使用部署包中提供的 **Emergency Response App.pbit** 发布仪表板的信息。

#### <a name="prerequisites"></a>先决条件

- 分配给访问报表的用户的 Power BI 高级容量或 Power BI Pro 许可证。 

- 在您发布报表的 Power BI 中创建工作区。 登录 Power BI 并创建工作区。 详细信息：[在 Power BI 中创建新工作区](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- 从 Windows 应用商店安装 Power BI Desktop：<https://aka.ms/pbidesktop>

   > [!NOTE] 
   > 如果过去是通过直接从“下载中心”页面作为可执行文件下载安装的 Power BI Desktop，请将其删除然后使用 Microsoft Store 中提供的文件。 Microsoft Store 版本将在新版本可用时自动更新。
   >
   > 如果无法从 Microsoft Store 安装，请从[“下载中心”页面](https://www.microsoft.com/download/details.aspx?id=58494)安装最新的非 Microsoft Store 版本。

- 从应用商店安装 Power BI Desktop 后，运行它，然后使用有权在组织中发布 Power BI 应用的帐户登录。

#### <a name="publish-the-dashboard-using-the-pbit-file"></a>使用 .pbit 文件发布仪表板

1. 导航到您提取部署包的位置。 您将在 **Power BI Template** 文件夹下找到 **Emergency Response App.pbit** 文件。

2. 在 Power BI Desktop 中打开 **Emergency Response App.pbit** 文件。 系统将提示您键入以下值：

    - **Organization_name**：键入将在每个报表页的左上角填充的组织名称。
    - **CDS_base_solution_URL**：键入您的 Common Data Service 环境实例的 URL。 例如：https://*[myenv]*.crm.dynamics.com

    > [!div class="mx-imgBorder"]
    > ![指定组织名称和基础 URL](media/pbi-pub-rep1.png)

    选择**加载**。

3. 系统将提示您输入凭据以连接到您的 Common Data Service 环境。 选择**组织帐户** > **登录**指定您的 Common Data Service 凭据。  

    > [!div class="mx-imgBorder"]
    > ![选择-组织帐户](media/select-organizational-account.png)

4. 登录后，选择**连接**以连接到 Common Data Service 中的数据。

5. 连接成功后，您的数据将显示在 Power BI 报表中。 系统将提示您将挂起的更改应用于您的查询；选择**应用更改**。

6. 选择**发布**将数据发布到您的 Power BI 工作区。 系统将提示您保存所做的更改；选择**保存**。

    > [!div class="mx-imgBorder"]
    > ![选择-刷新-发布](media/select-refresh-publish.png)

7. 系统将提示您将文件另存为 .pbix 文件并保存 Common Data Service 环境信息。 提供一个名称并将其保存在您的计算机上。

8. 保存 .pbix 文件后，系统将提示您发布报表。 在**发布到 Power BI** 页面上，选择要发布的工作区，然后单击**选择**。

12. 报表将在您的工作区中提供。 现在，我们将为数据集配置数据刷新设置。 在工作区中选择数据集，然后选择**计划刷新**图标。  
    
    > [!div class="mx-imgBorder"]
    > ![计划-刷新](media/schedule-refresh.png)

13. 第一次尝试设置数据刷新设置时，您将看到**设置**页，并显示一条消息，指示您的凭据无效。 在**数据源凭据**下，选择**编辑凭据**指定您的凭据。  

    > [!div class="mx-imgBorder"]
    > ![选择-编辑凭据](media/select-edit-credentials.png)

14. 在下一个屏幕中：
    - 为**身份验证方法**选择 **OAuth2**。
    - 为**此数据源的隐私级别设置**选择**组织**。
    - 选择**登录**。

    系统将提示您指定凭据并登录。 成功登录后，您将返回到**设置**页面。

15. 在**设置**页上，展开**计划刷新**，根据计划指定刷新数据所需的详细信息。 选择**应用**。

    > [!div class="mx-imgBorder"]
    > ![计划刷新](media/refresh-schedule.png)

    > [!NOTE] 
    > 可以刷新数据的次数存在限制。 Power BI 将共享容量上的数据集限制为每天刷新八次。 如果数据集位于高级容量上，您可以在数据集设置中最多计划每天刷新 48 次。 详细信息：[刷新数据](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

16. 在左侧窗格中选择您的工作区名称，然后选择右上角的**创建应用**。  

    > [!div class="mx-imgBorder"]
    > ![选择-创建应用](media/select-create-app.png)

17. 在应用发布页面：

    1. 在**设置**选项卡上，指定您的应用的名称和说明。

    2. 在**导航**选项卡上，指定要将其发布到的仪表板所在的位置。

    3. 在**权限**选项卡上，指定能够查看此应用的用户或组。 请确保选中**自动安装此应用**复选框，以为最终用户自动安装此应用。 详细信息：[为最终用户自动安装应用](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![选择-自动安装应用](media/select-install-apps-automatically.png)

18. 选择**发布应用**。 有关在 Power BI 中发布应用的详细信息，请参阅[发布应用](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app)。

### <a name="after-publishing-the-dashboard"></a>发布仪表板后

若要查看已发布的 Power BI 仪表板，请参阅[查看 Power BI 仪表板](configure-data-reporting.md#view-power-bi-dashboard)

## <a name="issues-and-feedback"></a>问题和反馈

- 若要报告有关医院应急响应示例应用的问题，请访问 <https://aka.ms/emergency-response-issues>。

- 有关医院应急响应示例应用的反馈，请访问 <https://aka.ms/emergency-response-feedback>。

## <a name="next-step"></a>下一步

[使用医院应急响应应用](use.md)
