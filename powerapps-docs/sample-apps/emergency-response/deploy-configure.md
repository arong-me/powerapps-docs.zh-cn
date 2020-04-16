---
title: 部署和配置医院应急响应应用 | Microsoft Docs
description: 提供有关医院 IT 管理员为其组织部署和配置示例应用的详细说明。
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/05/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- GetStarted
- PowerApps
ms.openlocfilehash: 624c465ea812e4fe650dda3750259acf91476bb0
ms.sourcegitcommit: 83b35be5df4864e15be9122647b17465e050284c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2020
ms.locfileid: "3229053"
---
# <a name="deploy-and-configure-the-hospital-emergency-response-app"></a>部署和配置医院应急响应应用

医院应急响应应用需要进行少量的设置以适应您的需要。 本文提供有关医院 IT 管理员为其组织部署和配置应用程序的分步说明。

完成这些步骤的估计时间：**35–40 分钟**。

## <a name="demo-deploy-and-configure-the-hospital-emergency-response-app"></a>演示：部署和配置医院应急响应应用

观看如何部署和配置医院应急响应应用。

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


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
- [步骤 7：将 Azure Application Insights 密钥添加到移动应用以进行遥测](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry)
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

若要开始部署过程，请将部署文件 (.zip) 提取到计算机上的某个位置。 提取的文件夹中将包含以下文件夹：

| **文件夹/文件**       | **说明**  |
|-----------------------|------------------|
| **App Icons**         | 包含移动应用（画布应用）的默认应用图标|
| **Data Files**        | 包含让解决方案/应用运行的主数据和示例数据文件 (.xlsx)。 您可以从这些文件导入数据来开始使用应用。 有关详细信息，请参阅[步骤 4：加载您的组织的配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Power BI Template** | 包含 Power BI 报表模板文件 (.pbit)，您将使用该文件来为组织配置报告。 详细信息：[使用 Power BI 仪表板获得见解](#get-insights-using-power-bi-dashboards)|
| **PowerShell**        | 包含将用于配置移动应用（画布应用）的脚本。 |
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
<p>您必须为包含医院应急响应应用的主示例数据的以下实体导入数据：
<ul>
<li>系统</li>
<li>区域</li>
<li>Facilities</li>
<li>位置</li>
<li>部门</li>
</ul>
<p>如果您要导入组织数据，而不是示例数据，您可以将这些 Excel 文件中的示例数据替换为您的组织数据，然后在应用中导入数据。</p>
<p>您还可以手动输入这些实体的数据。 有关这些实体中每个实体和字段的详细信息，请参阅<a href="#manually-configure-and-manage-master-data-for-your-organization">手动配置和管理组织的主数据</a></p></td>
</tr>
<tr>
<td><strong>Data Template File for Master Data</strong> 文件夹</td>
<td><p>此文件夹包含主实体的“empty”数据文件 (.xlsx)，您可以使用它们来填充组织数据，然后将其导入到应用中。</p>
<p>这些文件的名称指示在您的应用中导入数据应该采用的顺序。 它是前面提到的 <strong>Sample Data</strong> 文件夹的同一个实体列表。</p>
<p>您还可以手动输入这些实体的数据。 有关这些实体中每个实体和字段的详细信息，请参阅<a href="#manually-configure-and-manage-master-data-for-your-organization">手动配置和管理组织的主数据</a></p>
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
| 人员配备 | 请求角色 | 00 - Request Roles Import.xlsx
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

或者，如果要手动输入主数据，请参阅[手动配置和管理组织的主数据](#manually-configure-and-manage-master-data-for-your-organization)。

#### <a name="step-42-load-master-data"></a>步骤 4.2：加载主数据

如前文所述：
- 您可以使用 **Data Files/Sample Data** 文件夹下的主数据实体的示例数据文件，将示例数据导入所需的实体中。 

- 您可以使用 **Data Files/Data Template File for Master Data** 文件夹下的主实体的“empty”数据文件（可用于填充组织数据），然后将数据导入所需的实体中。

您还可以以后手动添加主数据。 详细信息：[手动配置和管理组织的主数据](#manually-configure-and-manage-master-data-for-your-organization)

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
    > ![Power App ID 字段](media/conf-powerapp-id-field.png "Power App ID 字段")

1.  在应用详细信息页面：

    1. 将应用 ID 从“记事本”（先前复制到的位置）复制到 **Power App ID** 字段。

    2. 双击应用图标，然后从 **App Icons** 文件夹中选择应用的图标文件。 图像文件的名称很直观，您可以轻松地选出正确的图标。 例如，为**紧急响应应用**选择“Emergency Response App.png”文件。 您还可以根据您的组织品牌选择自定义图像。

    3. 如果需要，更新应用的**说明**或**显示名称**。

    4. 如果需要，更新**在菜单中隐藏应用**值来设置是否应该在应用列表中显示该应用。 当**应急响应应用**是容器应用时，此值默认设置为**否**。

    5. 如有必要，更新**应用显示排名**值来设置应用在应用列表中的显示位置。

    6. 选择**保存**。

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

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry"></a>步骤 7：将 Azure Application Insights 密钥添加到移动应用以进行遥测

您可以使用 Azure Application Insights 收集您的移动应用（画布应用）的详细遥测，以获取有关应用使用的见解。 有关详细信息，请参阅[使用 Application Insights 分析应用遥测](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights)

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


## <a name="manually-configure-and-manage-master-data-for-your-organization"></a>手动配置和管理组织的主数据

管理员可以使用 [Power Apps](https://make.powerapps.com) 中的模型驱动应用来创建和管理其组织的主数据。 此数据是让医院应急响应应用运行所必需的。

> [!NOTE]
> 您还可以将组织数据导入部署包中提供的数据文件中，然后将其导入到这些实体中。 详细信息：[步骤 4：加载您的组织的配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)

您必须按以下顺序在这些实体中添加主数据：

1. [系统](#systems-data)

1. [区域](#regions-data)

1. [Facilities](#facilities-data)

1. [位置](#locations-data)

1. [部门](#departments-data)

从管理应用中左侧导航的**位置**区域管理主数据：

> [!div class="mx-imgBorder"]
> ![位置区域](media/locations-area.png)

**层次结构**区域下的实体按照您填充数据应该采取的顺序列出。

### <a name="systems-data"></a>系统数据

通过**系统**实体，您可以创建和管理医院系统的条目。 这使您可以在同一组织中管理多个医院系统。

要创建记录：

1. 在左侧窗格中选择**系统**，然后选择**新建**：  
    > [!div class="mx-imgBorder"]
    > ![选择-系统-新建](media/select-systems-new.png)

2. 在**新建系统**页上，指定适当的值：  
   > [!div class="mx-imgBorder"]
   > ![输入-详细信息-新建-系统](media/enter-details-new-system.png)

   | **字段**            | **说明**                                    |
   |----------------------|----------------------------------------------------|
   | 系统名称          | 键入医院的名称。                     |
   | 说明          | 键入可选说明。                      |
   | 生效日期 | 键入此医院系统的开始日期和时间。 |
   | 失效日期   | 键入此医院系统的结束日期和时间。   |

3. 选择**保存并关闭**。 新创建的记录将显示在**系统**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

### <a name="regions-data"></a>区域数据

通过**区域**实体，您可以管理医院系统的地理区域。

要创建记录：

1. 在左侧窗格中选择**区域**，然后选择**新建**。

2. 在**新建区域**页上，指定适当的值：  

    > [!div class="mx-imgBorder"]
    > ![输入-详细信息-新建-区域](media/enter-details-new-region.png)

    | **字段**            | **说明**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | 系统               | 选择医院系统。 此列表基于您先前创建的**系统**数据填充。 |
    | 区域名称          | 键入区域名称。 例如，西雅图。                                                              |
    | 说明          | 键入可选说明。                                                                            |
    | 生效日期 | 键入此区域的开始日期和时间。                                                       |
    | 失效日期   | 键入此区域的结束日期和时间。                                                         |

3. 选择**保存并关闭**。 新创建的记录将显示在**区域**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

### <a name="facilities-data"></a>设施数据

通过**设施**实体，您可以管理每个区域中的医院位置。 例如，**西雅图**区域的**雷蒙德**和**贝尔维尤**设施。

要创建记录：

1. 在左侧窗格中选择**设施**，然后选择**新建**。

2. 在**新建设施**页上，指定适当的值： 

    > [!div class="mx-imgBorder"] 
    > ![输入-详细信息-新建-设施](media/enter-details-new-facility.png)

    | **字段**            | **说明**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | 地区               | 选择一个区域。 此列表基于您先前创建的**区域**数据填充。 |
    | 设施名称        | 键入设施名称。 例如，贝尔维尤。                                                  |
    | 说明          | 键入可选说明。                                                                   |
    | 呼吸机总数          | 键入设施中提供的呼吸机总数                                  |
    | 生效日期 | 键入此设施的开始日期和时间。                                                     |
    | 失效日期   | 键入此设施的结束日期和时间。                                                       |

    如果需要，输入设施地址。

3. 选择**保存并关闭**。 新创建的记录将显示在**设施**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

### <a name="locations-data"></a>位置数据

通过**位置**实体，您可以管理每个医院设施内的特定位置。

> [!NOTE]
> 在创建**位置**记录之前，请确保您已按照前面在[步骤 4：加载您的组织的配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)中说明的步骤，使用 **00 - Acuities Import.xlsx** 文件导入了锐器数据。 这是因为创建**位置**记录需要用到锐器信息。

要创建记录：

1. 在左侧窗格中选择**位置**，然后选择**新建**。

2. 在**新建位置**页上，指定适当的值：  
 
    > [!div class="mx-imgBorder"]
    > ![输入-详细信息-新建-位置](media/enter-details-new-location.png)

    | **字段**            | **说明**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | 位置名称        | 键入位置的名称。                                                                       |
    | 设施             | 选择一个设施。 此列表基于您先前创建的**设施**数据填充。 |
    | 楼层                | 键入设施的楼层信息。                                                         |
    | 单位                 | 键入设施的单元信息                                                           |
    | 锐器      | 选择与此位置关联的锐器记录。                                                                                                     |
    | 冠状病毒位置      | 选择此位置是否用于处置冠状病毒患者（**是**或**否**）。                                                                                                      |
    | 床位总数           | 键入设施中的床位总数。                                                       |
    | 加床数           | 键入设施中的加床数量。 加床数是指如果患者需要收治，可以配备的超过许可床位的床位数。                                                      |
    | 冻结床位数         | 键入设施中冻结的床位数量。                                                     |
    | 上次人数统计          | 根据创建的上一次人数统计记录填充。                                             |
    | 占用率 | 基于上次人数统计和床位总数自动计算                                         |
    | 生效日期 | 键入此位置的开始日期和时间。                                                   |
    | 失效日期   | 键入此位置的结束日期和时间。                                                     |
    | 位置顺序       | 键入位置在位置下拉列表中所排顺序的数字。                               |
    | 替换站点标志  | 供内部使用。                                                                                     |

3. 选择**保存并关闭**。 新创建的记录将显示在**位置**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

### <a name="departments-data"></a>部门数据

通过**部门**实体，您可以管理医院的部门信息。

要创建记录：

1. 在左侧窗格中选择**部门**，然后选择**新建**。

2. 在**新建部门**页上，指定适当的值：

    > [!div class="mx-imgBorder"]
    > ![输入-详细信息-新建-部门](media/enter-details-new-department.png)

    | **字段**            | **说明**                                    |
    |----------------------|----------------------------------------------------|
    | 部门名称      | 键入部门名称。                            |
    | 说明          | 键入可选说明。                      |
    | 生效日期 | 键入此部门的开始日期和时间。 |
    | 失效日期   | 键入此部门的结束日期和时间。   |

3. 选择**保存并关闭**。 新创建的记录将显示在**部门**列表中。

若要编辑记录，选择该记录，根据需要更新值，然后选择**保存并关闭**。

## <a name="get-insights-using-common-data-service-dashboards"></a>使用 Common Data Service 仪表板获取见解

在医院应急响应管理（模型驱动）应用中，默认提供以下仪表板：

- **床位管理**

   跨不同设施显示床位可用情况、占有率和床位总数。

- **设备和用品**

  跨不同设施显示正在使用的关键设备和可用的用品。

- **人员管理**

  跨不同设施显示申请、分配和可用的人员数量。

- **冠状病毒患者**

  显示不同设施正在接受调查以及已发现 2019 冠状病毒病呈阳性的患者数量。

- **出院**

  显示预期出院和实际出院的患者人数。

除了默认提供的仪表板之外，您还可以创建自己的仪表板。

### <a name="manage-dashboards"></a>管理仪表板

要管理仪表板：

1. 登录 [Power Apps](https://make.powerapps.com)，浏览到您的管理应用。

2. 在左侧导航窗格中，从区域选取器中选择**仪表板**：

    > [!div class="mx-imgBorder"]
    > ![选择-仪表板](media/select-dashboards.png)

3. 在左侧导航窗格中选择仪表板名称查看图表：

    > [!div class="mx-imgBorder"]
    > ![查看-图表](media/view-charts.png)

    > [!NOTE]
    > 您可以在屏幕底部筛选数据，顶部的图表会自动更新为筛选出的值。

4. 选择**展开**选项可在全屏模式下查看图表：

    > [!div class="mx-imgBorder"]
    > ![选择-展开](media/select-expand.png)

### <a name="additional-analysis"></a>其他分析

- **向下钻取**：您可以选择图表区域来通过实体的其他属性（字段）进一步向下钻取：

    > [!div class="mx-imgBorder"]
    > ![选择-图表区域-向下钻取](media/select-chart-area-drill-down.png)

- **刷新**：您可以刷新仪表板来反映更新的数据。 您可以使用**全部刷新**刷新特定仪表板上的所有图表，也可以使用**刷新**刷新所选图表：

    > [!div class="mx-imgBorder"]
    > ![刷新-仪表板](media/refresh-dashboards.png)

- **查看记录**：选择**更多命令** (**…**)，然后选择**查看记录**查看与给定图表相关联的所有记录：

    > [!div class="mx-imgBorder"]
    > ![选择-更多-命令](media/select-more-commands.png)

    > [!NOTE] 
    > 当您选择**查看记录**时，您将看到在图表和记录之间进行拆分的实体视图。 对右侧记录的筛选器所做的任何更改都会经过自动更新反映到屏幕左侧的图表中。

有关编辑现有仪表板和更新图表属性的详细信息，请阅读[编辑现有仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard)。

### <a name="create-new-dashboards"></a>创建新仪表板

您还可以创建自己的仪表板，并进行自定义来满足您的需求。 若要创建新仪表板，请选择**新建**，然后选择 **Dynamics 365 仪表板**：

> [!div class="mx-imgBorder"]
> ![选择-新建-dynamics-仪表板](media/select-new-dynamics-dashboard.png)

有关创建新仪表板的详细信息，请阅读[创建新仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard)。

## <a name="get-insights-using-power-bi-dashboards"></a>使用 Power BI 仪表板获取见解

发布 Power BI 仪表板并将其与组织中的用户共享，让他们可以使用仪表板获取见解、制定决策。

### <a name="prerequisites"></a>先决条件

- 分配给访问报表的用户的 Power BI 高级容量或 Power BI Pro 许可证。 

- 在您发布报表的 Power BI 中创建工作区。 登录 Power BI 并创建工作区。 详细信息：[在 Power BI 中创建新工作区](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- 从 Windows 应用商店安装 Power BI Desktop：<https://aka.ms/pbidesktop>

   > [!NOTE] 
   > 如果您过去是通过直接从 Power BI 站点下载为可执行文件安装的 Power BI，请将其删除，然后使用从应用商店获取的版本。 应用商店版本将在新版本可用时自动更新。

- 从应用商店安装 Power BI Desktop 后，运行它，然后使用有权在组织中发布 Power BI 应用的帐户登录。

### <a name="publish-the-power-bi-dashboard"></a>发布 Power BI 仪表板

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

### <a name="view-the-power-bi-dashboard"></a>查看 Power BI 仪表板

登录到 [Power BI](https://apps.powerbi.com) 访问和查看 Power BI 仪表板。

> [!div class="mx-imgBorder"]
> ![查看 Power BI 仪表板](media/view-power-dashboard.png)

您可以使用报表顶部的筛选器来筛选医院系统、区域和设施的数据。 您还可以筛选冠状病毒位置。

> [!div class="mx-imgBorder"]
> ![报表筛选器](media/report-filters.png)

#### <a name="system-at-a-glance-page"></a>系统概览页 

**系统概览页**是提供整体视图的默认页面或顶层页面。  

此页面显示以下信息的摘要视图： 

- **冠状病毒患者**：显示冠状病毒患者总数、2019 冠状毒病发现呈阳性的患者人数以及正在接受调查的患者人数。 

- **床位管理**：显示床位可用情况、占有率、加床数量和床位总数。 您也可以使用下面的网格以锐音符的单位查看数字。 

- **护士配备管理**：显示 ICU 患者人数、分配的护士和护士与患者的比例。  

- **出院**：显示长期住院患者总数、预计出院的患者人数和实际出院人数。 

- **设备**：显示呼吸机总数、正在使用的呼吸机数量以及可用呼吸机数量。 

- **用品**：按日显示现有用品数量。

> [!NOTE]
> - 在任何汇总区域中选择信息图标 (i) 将转到区域的相应详细信息页面。 
> - 您还可以对报表执行其他操作，如筛选和排序数据、将报表导出到 PDF 和 PowerPoint、添加聚焦等。 有关 Power BI 中的报表功能的详细信息，请参阅 [Power BI 中的报表](https://docs.microsoft.com/power-bi/consumer/end-user-reports)
> - 其中的某些报表的最新或上次更新列显示上次刷新数据的日期和时间。 通过查看以下列中的日期和时间值的颜色，可以轻松识别数据的新旧：
>    - 黑色：数据刷新不超过 20 小时
>    - 灰色：数据在 20 - 24 小时以前刷新
>    - 红色：数据刷新超过 24 小时 
 
#### <a name="system-view-page"></a>系统视图页面

**系统视图**页显示包含以下医院系统信息的图表：
- 正在使用的呼吸机和可用呼吸机
- 床位和急症护理床位可用情况和占用率
- 申请的人员总数、患者人数（人数统计）、护士与患者的比例。
- 按日显示的现有用品

> [!div class="mx-imgBorder"]
> ![系统视图](media/report-system-view.png)

#### <a name="location-details-page"></a>位置详细信息页 

若要通过位置向下钻取报表，请单击右上角的**位置详细信息**。 **位置详细信息**页面按位置显示数据，如床位总数、可用床位数、加床数量、冠状病毒患者等。 

> [!div class="mx-imgBorder"]
> ![位置详细信息](media/report-location-details.png) 

#### <a name="covid-patient-details-page"></a>冠状病毒患者详细信息页 

**冠状病毒患者详细信息**页面提供有关冠状病毒患者的向下钻取信息，如每个位置的患者，一段时间内的患者趋势（显示正在接受调查的患者 (PUI) 和发现呈阳性的患者人数的峰值和谷值），了解患者在医院内的位置。

> [!div class="mx-imgBorder"]
> ![冠状病毒患者详细信息](media/report-covid-details.png)

#### <a name="bed-management-page"></a>床位管理页 

**床位管理**页按位置提供向下钻取信息，如可用床位总数和占用率。

> [!div class="mx-imgBorder"]
> ![床位管理](media/report-bed-details.png)

#### <a name="staff-details-page"></a>人员详细信息页  

**人员详细信息**页面按位置提供有关人员的详细信息、已分配的护士数量、患者总数和冠状病毒患者人数。 另外还会显示一段时间内护士与患者的比例和 ICU 护士与患者的比例。

> [!div class="mx-imgBorder"]
> ![人员详细信息](media/report-staff-details.png)

#### <a name="equipment-details-page"></a>设备详细信息页 

**设备详细信息**页面按位置提供有关设备的详细信息、正在使用的呼吸机总数、被冠状病毒患者人数覆盖的设备和其他设备（如正在使用的呼吸器带、充电器和面罩）。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-equipment-details.png)

#### <a name="discharge-details-page"></a>出院详细信息页 

**出院详细信息**页面提供有关长期患者的详细信息，一段时间内的出院障碍，以及实际出院和预计出院的人数差。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-discharge-details.png)

#### <a name="supplies-on-hand-details-page"></a>现有用品详细信息页 

**现有用品详细信息**页面按位置和用品提供有关用品的详细信息；另外还提供一段时间内现有可用用品的相关数据。

> [!div class="mx-imgBorder"]
> ![设备详细信息](media/report-discharge-details.png)

## <a name="view-and-manage-app-feedback"></a>查看和管理应用反馈

在移动设备上使用画布应用的前线人员提供的所有反馈都存储在**应用反馈**实体中，管理员可以使用管理应用中左侧导航窗格的**管理**区域查看和管理这些反馈。

若要查看和管理应用反馈：

1. 登录 [Power Apps](https://make.powerapps.com)，浏览到您的管理应用。

2. 在左侧导航窗格中，从区域选取器中选择**管理**。

3. 选择**应用反馈**查看用户提交的应用反馈列表。 您可以单击一条记录来查看详细信息，并标记是否审阅。  

    > [!div class="mx-imgBorder"]
    > ![选择-应用反馈](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>问题和反馈

- 若要报告有关医院应急响应示例应用的问题，请访问 <https://aka.ms/emergency-response-issues>。

- 有关医院应急响应示例应用的反馈，请访问 <https://aka.ms/emergency-response-feedback>。

## <a name="next-step"></a>下一步

[使用医院应急响应应用](use.md)
