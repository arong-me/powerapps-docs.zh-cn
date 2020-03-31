---
title: 部署和配置紧急响应应用 | Microsoft Docs
description: 详细介绍医院 IT 管理员如何为组织部署和配置示例应用。
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/26/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- GetStarted
- PowerApps
ms.openlocfilehash: e58b23503e1730c8606a833cb05f7253b5b96f49
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2020
ms.locfileid: "80328352"
---
# <a name="deploy-and-configure-the-emergency-response-app"></a>部署和配置紧急响应应用

为适应你的需求，需要对紧急响应应用进行少量设置。 本文为医院 IT 管理员提供为其组织部署和配置应用程序的分步说明。

上述步骤预计完成时间：35-40 分钟。

## <a name="demo-deploy-and-configure-the-emergency-response-app"></a>演示：部署和配置紧急响应应用

观看如何部署和配置紧急响应应用。

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="deploy-the-emergency-response-app"></a>部署紧急响应应用

执行以下步骤，为你的组织部署紧急响应示例应用。

- [步骤 1：注册 Power Apps 并创建环境](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [步骤 2：下载部署包](#step-2-download-the-deployment-package)
- [步骤 3：将解决方案文件导入到环境中](#step-3-import-the-solution-file-into-your-environment)
- [步骤 4：为组织加载配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)
    - [步骤 4.1：如何从数据文件加载数据？](#step-41-how-to-load-data-from-data-files)
    - [步骤 4.2：导入必需的配置数据](#step-42-import-mandatory-configuration-data)
- [步骤 5：更新移动应用品牌](#step-5-update-the-mobile-app-branding)
- [步骤 6：为移动应用设置绕过同意](#step-6-bypass-consent-for-mobile-apps)
- [步骤 7：将 Azure Application Insights 密钥添加到移动应用以进行遥测](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry)
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

3.  在环境中创建相应的用户。 更多信息：[创建用户并分配安全角色](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

### <a name="step-2-download-the-deployment-package"></a>步骤 2：下载部署包

从 <https://aka.ms/emergency-response-solution> 获取最新的部署包 (.zip)，其中包含解决方案文件、映像和数据文件，用于设置紧急响应应用的应用和业务逻辑。

要开始部署过程，请将部署文件 (.zip) 提取到计算机上的某个位置。 提取的文件夹将包含下列文件夹：

| **文件夹/文件**       | **说明**  |
|-----------------------|------------------|
| **应用图标**         | 包含移动应用（画布应用）的默认应用图标|
| **数据文件**        | 包含使解决方案/应用正常运行的主数据文件和示例数据文件 (.xlsx)。 可以从这些文件导入数据，以便开始使用应用。 有关详细信息，请参阅[步骤 4：为组织加载配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Power BI 模板** | 包含将用于为组织配置报表的 Power BI 报表模板文件 (.pbit)。 详细信息：[使用 Power BI 仪表板获取见解](#get-insights-using-power-bi-dashboards)|
| **PowerShell**        | 包含将用于配置移动应用（画布应用）的脚本。 |
| **解决方案文件**     | 包含用于创建紧急响应应用所需的应用和元数据的 Common Data Service 解决方案文件。  |

### <a name="step-3-import-the-solution-file-into-your-environment"></a>步骤 3：将解决方案文件导入到环境中

1.  导航到你提取部署文件 (.zip) 的位置；你会找到“解决方案文件”文件夹。 我们会将“解决方案文件”文件夹下的托管解决方案 (.zip) 文件导入到我们的环境中。

2.  登录到 [Power Apps](https://make.powerapps.com)。

3.  从右上角选择环境。

4.  在左侧窗格中选择“解决方案”，然后选择“导入”。

    > [!div class="mx-imgBorder"] 
    > ![导入解决方案](media/conf-import-solution.png "导入解决方案")

5.  在“导入解决方案”对话框中，选择步骤 1 中提到的解决方案文件，然后按照向导中的步骤导入解决方案。

6.  成功导入解决方案后，在导入对话框中选择“关闭”，然后选择“公开所有自定义项”。 这可能需要一些时间才能完成。

现在，你将在“应用”**下看到新应用**：

> [!div class="mx-imgBorder"] 
> ![新应用](media/conf-apps-new-apps.png "新应用")

选择“管理应用”以打开模型驱动应用，通过该应用可以配置部署设置的其余部分。 更多信息：[什么是模型驱动应用？](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

> [!div class="mx-imgBorder"] 
> ![打开管理应用](media/conf-admin-app-open.png "打开管理应用")

管理应用具有许多实体，你可以在其中添加和管理医院系统的数据。 可以使用左侧导航窗格下半部分中的区域选取器来选择其他区域。

### <a name="step-4-load-configuration-and-master-data-for-your-organization"></a>步骤 4：为组织加载配置和主数据

提取的部署文件夹下的“数据文件”文件夹下提供了紧急响应应用所需的所有数据。

“数据文件”文件夹包含以下文件和文件夹：

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
<br/>将数据导入这些实体后，将为这些实体创建紧急响应应用所需的记录。
<br/>
<br/>注意
<strong></strong>：请确保你没有更新这些实体中的配置值，但稍后将说明的“应用”<strong></strong>和“应用配置”<strong></strong>实体除外。</td>
</tr>
<tr>
<td>“示例数据”文件夹</td>
<td><p>此文件夹包含示例数据文件 (.xlsx)，可以将其导入以在应用程序中填充示例数据。 这些文件的命名表示应将数据导入到应用中的顺序。 </p>
<p>必须为包含紧急响应应用的主示例数据的以下实体导入数据：
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

#### <a name="step-41-how-to-load-data-from-data-files"></a>步骤 4.1：如何从数据文件加载数据？

要将示例数据从其中一个数据文件加载到实体，请执行以下步骤：

1.  在管理应用的左侧导航窗格中，选择要为其加载数据的实体。 例如，从区域选取器中选择“位置”，然后选择“系统”。

2.  选择“从 Excel 导入”，然后从“示例数据”文件夹中选择“01 - Load Systems.xlsx”文件。

    > [!div class="mx-imgBorder"] 
    > ![从 Excel 导入](media/conf-import-from-excel.png "从 Excel 导入")

3.  继续执行导入向导步骤以导入数据。

4.  导入示例数据后，你将在实体中看到导入的记录：

    > [!div class="mx-imgBorder"] 
    > ![实体记录](media/conf-entity-record.png "导入后的实体中的记录")

对其他实体重复执行上述步骤。

或者，如果要手动输入主数据，请参阅[为组织手动配置和管理主数据](#manually-configure-and-manage-master-data-for-your-organization)。

#### <a name="step-42-import-mandatory-configuration-data"></a>步骤 4.2：导入必需的配置数据

在进入下一步之前，必须在管理应用中的以下实体下导入配置数据：

| 区域名称 | 实体名称| 文件名
|-|-|-
| 位置 | 视敏度 | 00 - Acuities Import.xlsx
| 管理 | 应用配置 | 00 - App Config Import.xlsx
| 管理 | 应用 | 00 - App Import.xlsx
| 人员配备 | 请求角色 | 00 - Request Roles Import.xlsx
| 位置 | 供应 | 00 - Supplies Import.xlsx

以后可以[手动](#manually-configure-and-manage-master-data-for-your-organization)添加其他实体的数据，也可以使用前面介绍的示例数据文件来添加。

### <a name="step-5-update-the-mobile-app-branding"></a>步骤 5：更新移动应用品牌

可以更改移动应用的图标或配色方案，使其与组织的品牌保持一致。

为此，可以使用“管理”区域中的“应用”和“应用配置”实体，在部署包下的“数据文件”文件夹中提供的 Excel 文件中导入应用和应用配置数据，这在前面的步骤中有所介绍。

> [!div class="mx-imgBorder"] 
> ![“应用”和“应用配置”实体](media/conf-app-app-config-entities.png "“应用”和“应用配置”实体")

1.  确保已分别从提取的部署包中的“App Import.xlsx”和“App Config Import.xlsx”文件导入“应用”和“应用配置”实体的配置数据。

1.  下面将复制画布应用的应用 ID，以便可以在导入的“应用”记录中填充它。 登录到 [Power Apps](https://make.powerapps.com)。

1.  从右上角选择环境。

1.  在左窗格中，选择“应用”，为画布应用选择省略号 (…)，然后选择“详细信息”。

    > [!div class="mx-imgBorder"] 
    > ![应用详细信息](media/conf-environments-apps-details.png "应用详细信息")

1.  此应用 ID 将显示在该应用的“详细信息”窗格的底部。 ****  将应用 ID 及其名称复制到记事本文件中。

    > [!div class="mx-imgBorder"] 
    > ![“详细信息”中的“应用 ID”](media/conf-details-app-id.png "“详细信息”中的“应用 ID”")

1.  对每个画布应用重复执行步骤 3 和 4。

1.  打开“管理应用”，在管理应用的左侧导航窗格中，从区域选取器中选择“管理”，然后选择“应用”。 随即显示从“App Import.xlsx”文件导入的所有画布应用记录。

    > [!div class="mx-imgBorder"] 
    > ![管理应用](media/conf-admin-app-records.png "管理应用")

1.  选择其中一个应用记录将其打开。 请注意，“Power App ID”字段内容为空白。

    > [!div class="mx-imgBorder"] 
    > ![Power App ID 字段 ](media/conf-powerapp-id-field.png "Power App ID 字段")

1.  将你之前在步骤 2-6 中复制到记事本的应用 ID 复制到“Power App ID”字段。 还可以通过双击应用图标并指定其他图像来更新应用图标。 保存该记录。

1.  对“应用”**下的每个画布应用记录重复执行步骤 9，添加“Power App ID”** 值。

1.  在左窗格中，选择“应用配置”。

1.  选择“紧急响应应用”记录，将其打开以进行编辑。

    1.  双击图标，指定一个新图像作为应用图标。

    2.  更新应用的应用名称和颜色。

    3.  在“已启用设备共享”字段中选择“是”或“否”，以指定“注销”选项在移动应用中是否可用。 如果选择“是”，将可以使用“注销”选项。

    > [!div class="mx-imgBorder"] 
    > ![“已启用设备共享”字段](media/conf-device-sharing-enabled-field.png "“已启用设备共享”字段")

1.  选择右下角的“保存”以保存更改。

### <a name="step-6-bypass-consent-for-mobile-apps"></a>步骤 6：为移动应用设置绕过同意

只有租户管理员才能完成此步骤。 另外，在执行此步骤之前，需要每个移动应用（画布应用）的应用 ID。

若要获取应用的应用 ID，在管理应用的左侧导航窗格中，从区域选取器中选择“管理”，然后选择“应用”。 随即显示所有移动应用（画布应用）。 选择一个移动应用以查看其应用 ID。 将每个应用的应用 ID 复制到记事本文件中。

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

2.  将每行中的 `APPGUIDHERE` 值替换为画布应用的实际应用 ID。

3.  将文件另存为 .ps 文件。

4.  以管理员身份运行 PowerShell 并执行刚刚创建的 .ps 文件。

5.  对每个画布应用重复执行步骤 2-4。

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry"></a>步骤 7：将 Azure Application Insights 密钥添加到移动应用以进行遥测

可以使用 Azure Application Insights 来收集移动应用（画布应用）的详细遥测，以获取有关应用使用情况的见解。 有关此内容的详细信息，请参阅[使用 Azure Application Insights 记录应用的遥测](https://powerapps.microsoft.com/blog/log-telemetry-for-your-apps-using-azure-application-insights/)

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>步骤 8：与组织中的用户共享画布应用

为了使前端用户能够借助其移动设备中的画布应用使用数据，必须与他们共享这些应用。 使用 Azure AD 组可以更轻松地与用户组共享应用。

1.  登录到 [Power Apps](https://make.powerapps.com)

2.  在左侧导航窗格中，选择“应用”以查看所有应用的列表。

3.  选择移动应用（画布应用），并在横幅中选择“共享”。

    > [!div class="mx-imgBorder"] 
    > ![共享画布应用](media/conf-share-canvas-apps.png "共享画布应用")

4.  指定要与哪些 Azure AD 组或用户共享此应用。 当应用连接到 Common Data Service 数据时，你还需要提供对实体的权限。 共享面板会提示你管理实体的安全性。 将“COVID 19 最终用户”和“Common Data Service 用户”安全角色分配给此应用使用的实体，然后选择“共享”。

    > [!div class="mx-imgBorder"] 
    > ![与 Azure AD 组或用户共享应用](media/conf-share-app-groups-users.png "与 Azure AD 组或用户共享应用")

5.  对每个移动应用重复执行步骤 3 和 4。

要详细了解如何共享应用，请参阅：[共享画布应用](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app)

### <a name="step-9-set-your-mobile-app-as-hero-and-featured-app"></a>步骤 9：将移动应用设置为首推应用和特色应用

通过此步骤，可以将移动应用设置为 Power Apps 移动应用中的首推应用和特色应用。 只有租户管理员才能完成此步骤。

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

2.  将每行中的 `APPGUIDHERE` 值替换为需要分别设置为首推应用和特色应用的实际应用 ID。

3.  将文件另存为 .ps 文件。

4.  以管理员身份运行 PowerShell 并执行刚刚创建的 .ps 文件。

### <a name="step-10-share-model-driven-app-with-admins-in-your-organization"></a>步骤 10：与组织中的管理员共享模型驱动应用

为了让管理员用户能够使用管理员应用（模型驱动应用），必须与他们共享这些应用。 使用 Azure AD 组可以更轻松地与管理员用户组共享应用。

1. 登录到 [Power Apps](https://make.powerapps.com)。

2. 在左侧导航窗格中，选择“应用”以查看所有应用的列表。

3. 选择模型驱动应用（“管理应用”-“紧急响应应用”），然后在横幅中选择“共享”。

4. 指定要与哪些 Azure AD 组或管理员用户共享此应用，分配“紧急响应管理员”安全角色，然后选择“共享”。


## <a name="manually-configure-and-manage-master-data-for-your-organization"></a>为组织手动配置和管理主数据

管理员可以在 [Power Apps](https://make.powerapps.com) 中使用模型驱动应用来创建和管理其组织的主数据。 要使紧急响应应用正常工作，此数据是必需的。

> [!NOTE]
> 还可以将组织数据导入部署包中可用的数据文件，然后将其导入下面的实体。 更多信息：[步骤 4：为组织加载配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)

必须按以下顺序将主数据添加到下面的实体中：

1. [系统](#systems-data)

1. [区域](#regions-data)

1. [机构](#facilities-data)

1. [位置](#locations-data)

1. [科室](#departments-data)

从管理应用左侧导航的“位置”区域中管理主数据：

> [!div class="mx-imgBorder"]
> ![locations-area](media/locations-area.png)

“层次结构”区域下的各实体按应填充数据的顺序列出。

### <a name="systems-data"></a>系统数据

使用“系统”实体可以创建和管理医院系统的条目。 这样就可以管理同一组织内的多个医院系统。

创建记录的步骤如下：

1. 在左窗格中选择“系统”，然后选择“新建”：  
    > [!div class="mx-imgBorder"]
    > ![select-systems-new](media/select-systems-new.png)

2. 在“新建系统”页中，指定适当的值：  
   > [!div class="mx-imgBorder"]
   > ![enter-details-new-system](media/enter-details-new-system.png)

   | **字段**            | **说明**                                    |
   |----------------------|----------------------------------------------------|
   | 系统名称          | 键入医院的名称。                     |
   | 说明          | 键入可选说明。                      |
   | 生效开始日期 | 键入此医院系统的开始日期和时间。 |
   | 生效结束日期   | 键入此医院系统的结束日期和时间。   |

3. 选择“保存并关闭”。 新创建的记录将显示在“系统”列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”。

### <a name="regions-data"></a>区域数据

使用“区域”实体可以管理医院系统的地理区域。

创建记录的步骤如下：

1. 在左窗格中选择“区域”，然后选择“新建”：

2. 在“新建区域”页中，指定适当的值：  

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-region](media/enter-details-new-region.png)

    | **字段**            | **说明**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | 系统               | 选择一个医院系统。 此列表是根据之前创建的“系统”数据填充的。 |
    | 区域名称          | 键入区域名称。 例如，“西雅图”。                                                              |
    | 说明          | 键入可选说明。                                                                            |
    | 生效开始日期 | 键入此医院系统的开始日期和时间。                                                       |
    | 生效结束日期   | 键入此医院系统的结束日期和时间。                                                         |

3. 选择“保存并关闭”。 新创建的记录将显示在“区域”列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”。

### <a name="facilities-data"></a>机构数据

使用“机构”实体可以管理每个区域中的医院位置。 例如，“西雅图”区域内的“雷德蒙德”和“贝尔维尤”的机构。

创建记录的步骤如下：

1. 在左窗格中选择“机构”，然后选择“新建”。

2. 在“新建机构”页中，指定适当的值： 

    > [!div class="mx-imgBorder"] 
    > ![enter-details-new-facility](media/enter-details-new-facility.png)

    | **字段**            | **说明**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | 区域               | 选择区域。 此列表是根据之前创建的“区域”数据填充的。 |
    | 机构名称        | 键入机构名称。 例如，“贝尔维尤”。                                                  |
    | 说明          | 键入可选说明。                                                                   |
    | 呼吸机总数          | 键入机构可用的呼吸机总数                                  |
    | 生效开始日期 | 键入此机构的开始日期和时间。                                                     |
    | 生效结束日期   | 键入此机构的结束日期和时间。                                                       |

    如果需要，请输入机构地址。

3. 选择“保存并关闭”。 新创建的记录将显示在“机构”列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”。

### <a name="locations-data"></a>位置数据

使用“位置”实体可以管理每个医院机构的特定位置。

> [!NOTE]
> 在创建“位置”记录之前，请确保已使用“00 - Acuities Import.xlsx”文件导入视敏度数据（前面的[步骤 4：为组织加载配置和主数据](#step-4-load-configuration-and-master-data-for-your-organization)中说明的步骤）。 这是因为创建“位置”记录需要视敏度信息。

创建记录的步骤如下：

1. 在左窗格中选择“位置”，然后选择“新建”。

2. 在“新建位置”页中，指定适当的值：  
 
    > [!div class="mx-imgBorder"]
    > ![enter-details-new-location](media/enter-details-new-location.png)

    | **字段**            | **说明**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | 位置名称        | 键入位置的名称。                                                                       |
    | 设施             | 选择机构。 此列表是根据之前创建的“机构”数据填充的。 |
    | 层                | 键入机构的楼层信息。                                                         |
    | 单位                 | 键入机构的单位信息                                                           |
    | 位置视敏度      | 选择与此位置关联的视敏度记录。                                                                                                     |
    | 总床位数           | 键入机构中的床位总数。                                                       |
    | 阻止的床位数         | 键入机构中已阻止的床位数。                                                     |
    | 上次统计数量          | 根据创建的上次统计记录进行填充。                                             |
    | 占用率 | 基于上次统计数量和床位总数自动计算                                         |
    | 生效开始日期 | 键入此医院系统的开始日期和时间。                                                   |
    | 生效结束日期   | 键入此医院系统的结束日期和时间。                                                     |
    | 位置顺序       | 键入一个数字，用于对位置下拉列表中的位置进行排序。                               |
    | 备用场地标志  | 供内部使用                                                                                     |

3. 选择“保存并关闭”。 新创建的记录将显示在“位置”列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”。

### <a name="departments-data"></a>科室数据

使用“科室”实体可以管理医院的科室信息。

创建记录的步骤如下：

1. 在左窗格中选择“科室”，然后选择“新建”。

2. 在“新建科室”页中，指定适当的值：    

    > [!div class="mx-imgBorder"]
    > ![enter-details-new-department](media/enter-details-new-department.png)

    | **字段**            | **说明**                                    |
    |----------------------|----------------------------------------------------|
    | Department Name      | 键入科室名称。                            |
    | 说明          | 键入可选说明。                      |
    | 生效开始日期 | 键入此医院系统的开始日期和时间。 |
    | 生效结束日期   | 键入此医院系统的结束日期和时间。   |

3. 选择“保存并关闭”。 新创建的记录将显示在“科室”列表中。

若要编辑记录，请选择记录，根据需要更新值，然后选择“保存并关闭”。

## <a name="get-insights-using-common-data-service-dashboards"></a>使用 Common Data Service 仪表板获取见解

默认情况下，紧急响应管理员（模型驱动）应用中提供以下仪表板：

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

2. 在左侧导航窗格中，从区域选取器中选择“仪表板”：

    > [!div class="mx-imgBorder"]
    > ![select-dashboards](media/select-dashboards.png)

3. 选择左侧导航栏中的仪表板名称以查看图表：

    > [!div class="mx-imgBorder"]
    > ![view-charts](media/view-charts.png)

    > [!NOTE]
    > 可以在屏幕底部筛选数据，并使用筛选后的值自动更新顶部的图表。

4. 选择“展开”选项，以全屏模式查看图表：

    > [!div class="mx-imgBorder"]
    > ![select-expand](media/select-expand.png)

### <a name="additional-analysis"></a>其他分析

- **向下钻取**：可以选择图表区域以进一步细化实体的其他属性（字段）：

    > [!div class="mx-imgBorder"]
    > ![select-chart-area-drill-down](media/select-chart-area-drill-down.png)

- **刷新**：可以刷新仪表板来反映更新后的数据。 可以单击“全部刷新”刷新特定仪表板上的所有图表，，也可以单击“刷新”来刷新选定的图表：

    > [!div class="mx-imgBorder"]
    > ![refresh-dashboards](media/refresh-dashboards.png)

- **查看记录**：选择“更多命令(…)”，然后选择“查看记录”查看与给定图表相关联的所有记录：

    > [!div class="mx-imgBorder"]
    > ![select-more-commands](media/select-more-commands.png)

    > [!NOTE] 
    > 选择“查看记录”时，你将看到图表和记录之间的实体拆分视图。 在右侧对记录的筛选器所做的任何更改都会通过自动更新反映到屏幕左侧的图表中。

若要详细了解如何编辑现有仪表板和更新图表的属性，请阅读[编辑现有仪表板](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard)。

### <a name="create-new-dashboards"></a>创建新仪表板

还可以创建自己的仪表板，并对其进行自定义以适应你的需求。 要创建新仪表板，请选择“新建”，然后选择“Dynamics 365 仪表板”：

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
   > 如果你过去直接从 Power BI 网站下载可执行文件并安装了 Power BI，请将其删除，并从应用商店中使用 Power BI。 随着新版本的发布，应用商店版本将自动更新。

- 从应用商店安装 Power BI Desktop 后，请运行它，使用有权在组织中发布 Power BI 应用的帐户登录。

### <a name="publish-the-power-bi-dashboard"></a>发布 Power BI 仪表板

1. 导航到你提取部署包的位置。 在“Power BI 模板”文件夹下将能够找到 Emergency Response App.pbit 文件。

2. 在 Power BI Desktop 中打开“Emergency Response App.pbit”文件。 在 Power BI Desktop 中打开此文件时，随即显示一个“刷新”对话框，显示数据刷新失败。 这是因为我们尚未指定与 Common Data Service 环境的连接详细信息。

3. 选择“转换数据”指定与 Common Data Service 环境的连接。  
    
    > [!div class="mx-imgBorder"]
    > ![select-transform-data](media/select-transform-data.png)

4. 在查询编辑器中，使用 Common Data Service 环境的 URL 更新 CDSBaseURL 参数。 右键单击“CDSBaseURL”，选择“高级编辑器”，然后指定相应的值。  

    > [!div class="mx-imgBorder"]
    > ![select-advanced-editor](media/select-advanced-editor.png)

5. 保存所做更改。 这时，系统显示一条消息，要求你将挂起的更改应用到查询。 选择**应用**。

6. 系统将提示你输入凭据以连接到 Common Data Service 环境。 选择“组织帐户” > **“登录”**，指定你的 Common Data Service 凭据。  

    > [!div class="mx-imgBorder"]
    > ![select-organizational-account](media/select-organizational-account.png)

7. 选择“连接”以建立连接。

8. 成功连接后，系统将提示你将文件与 Common Data Service 环境信息一起另存为 .pbix 文件。 提供一个名称并将其保存在计算机上。

9. 在“主页”选项卡中，选择“关闭并应用”。

10. 选择“刷新”以刷新 Common Data Service 环境中的数据。 选择“发布”将数据发布到 Power BI 工作区。  
    
    > [!div class="mx-imgBorder"]
    > ![select-refresh-publish](media/select-refresh-publish.png)

11. 在“发布到 Power BI”页上，选择要发布到哪个工作区。

12. 在你的工作区中可以使用此报表了。 下面为数据集配置数据刷新。 选择工作区中的数据集，并选择“计划刷新”图标。  
    
    > [!div class="mx-imgBorder"]
    > ![schedule-refresh](media/schedule-refresh.png)

13. 在数据集的“设置”页上，展开“数据源凭据”，然后选择“编辑凭据”以确保连接到数据源的连接详细信息正确无误  

    > [!div class="mx-imgBorder"]
    > ![select-edit-credentials](media/select-edit-credentials.png)

14. 展开“计划刷新”并指定根据计划刷新数据所需的详细信息。

    > [!NOTE] 
    > 对数据刷新次数存在限制。 Power BI 将共享容量上的数据集限制为每天最多刷新 8 次。 如果数据集驻留在 Premium 容量上，则每天最多可在数据集设置中计划 48 次刷新。 更多信息：[刷新数据](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

15. 在左侧窗格中选择工作区名称，然后选择右上角的“创建应用”。  

    > [!div class="mx-imgBorder"]
    > ![select-create-app](media/select-create-app.png)

16. 在应用发布页上，执行以下操作：

    1. 在“设置”选项卡上，指定应用的名称和描述。

    2. 在“导航”选项卡上，指定要将应用发布到哪个仪表板。

    3. 在“权限”选项卡上，指定将能够查看此应用的用户或组。 请务必选中“自动安装此应用”复选框，以便自动为最终用户安装此应用。 更多信息：[自动为最终用户安装应用](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![select-install-apps-automatically](media/select-install-apps-automatically.png)

17. 选择“发布应用”。 有关在 Power BI 中发布应用的详细信息，请参阅[发布应用](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app)。

### <a name="view-the-power-bi-dashboard"></a>查看 Power BI 仪表板

登录 [Power BI](https://apps.powerbi.com) 即可访问和查看 Power BI 仪表板。

> [!div class="mx-imgBorder"]
> ![view-power-dashboard](media/view-power-dashboard.png)

## <a name="view-and-manage-app-feedback"></a>查看和管理应用反馈

一线员工在其移动设备上使用画布应用提供的所有反馈都存储在“应用反馈”实体中，管理员可以使用管理应用左侧导航窗格中的“管理”区域来查看和管理反馈。

要查看和管理应用反馈，请执行以下操作：

1. 登录到 [Power Apps](https://make.powerapps.com) 并浏览到管理应用。

2. 在左侧导航窗格中，从区域选取器中选择“管理”。

3. 选择“应用反馈”以查看用户提交的应用反馈的列表。 可以单击一条记录以查看详细信息，并可以选择是否将其标记为“已查看”。  

    > [!div class="mx-imgBorder"]
    > ![select-app-feedback](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>问题和反馈

- 若要报告紧急响应示例应用的相关问题，请访问 <https://aka.ms/emergency-response-issues>。

- 有关紧急响应示例应用的反馈，请访问 <https://aka.ms/emergency-response-feedback>。

## <a name="next-step"></a>下一步

[使用紧急响应应用](use.md)
