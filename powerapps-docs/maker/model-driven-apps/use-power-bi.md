---
title: Power BI 与 Dynamics 365 应用结合使用 | MicrosoftDocs
ms.custom: null
ms.date: 12/07/2018
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement  (online)
  - Dynamics 365 for Customer Engagement  Version 9.x
ms.assetid: 48997010-a47c-4e16-b7d2-f55d7a52ba19
caps.latest.revision: 36
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - admin
search.app:
  - D365CE
  - Powerplatform
---
# <a name="use-power-bi"></a>使用 Power BI

Power BI 云服务与 Common Data Service 应用结合使用可提供自助服务分析解决方案。 Power BI 自动刷新显示的应用数据。 借助 Power BI Desktop 或 Microsoft Excel（用于报表创作的 Power Query 和用于共享仪表板的和刷新来自模型驱动应用的数据的 Power BI），您的用户拥有了一个使用应用数据的强大的新方法。  
  
<a name="PowerBIGetstarted"></a>   
## <a name="get-started-using-power-bi-with-dynamics-365-for-customer-engagement-apps-online"></a>将 Power BI 与 Dynamics 365 for Customer Engagement (online) 应用结合使用入门  
 您可以通过适用于 Power BI 的 Dynamics 365 应用内容包轻松访问和分析销售、服务或营销数据。  
  
 要使用内容包创建 Power BI 仪表板，请按照以下说明操作。  
  
1. 如果尚未注册 Power BI，[请注册 Power BI](http://powerbi.com/)。  
  
2. 登录 Power BI 后，请选择**数据集**区域中的**获取数据**，再选择**服务**下的**获取**，然后再从下列内容包中进行选择。  
  
   - **Dynamics 365 的销售分析**  
  
   - **Dynamics 365 的客户服务分析**  
  
   - **Microsoft Dynamics 365 - Social Engagement**  
  
3. 若要获取销售分析和服务分析内容包，请输入实例的 URL，例如 *<https://OrganizationName.crm.dynamics.com>*，其中 *OrganizationName* 是您的实例的组织名称，然后选择**下一步**。  
  
   > [!NOTE]
   >  如果您的数据中心位于北美地区以外，crm.dynamics.com 域名可能有所不同，例如 crm2.dynamics.com、crm3.dynamics.com、crm4.dynamics.com 等。要查找域名，在应用 Web 应用中，转到**设置** > **自定义** > **开发人员资源**。 列出的 URL 将指示正确域名。  
  
    若要获取营销内容包，请输入 URL，例如 *<https://OrganizationName.marketing.dynamics.com/analytics>*，其中 *OrganizationName* 是您的 Dynamics 365 实例的组织名称，然后选择**下一步**  
  
4. 在**身份验证方法**下，选择**oAuth2**。  
  
5. 您的实例数据已导入，并且多个可视化效果变为可用状态。  
  
> [!TIP]
>  如果选择的内容包在您的浏览器打不开，请单击 Power BI 工作区左侧窗格的**仪表板**下的内容包。  
  
### <a name="content-packs-available-for-download"></a>可下载的内容包。  
 Dynamics 365 内容包支持应用的默认现成实体。 但是，您可以通过下载 .PBIX 文件，再使用 Power BI Desktop 自定义内容包，再将其上传到 Power BI 服务的方式自定义以下内容包。  
  
- [下载 Dynamics CRM Online Sales Manager .PBIX](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
- [下载 Dynamics 365 for Customer Engagement (online) 应用服务管理器 .PBIX](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  适用于 Connected Field Service 的 Power BI 报表模板让用户可以发布显示已连接设备实时检测信号的 Power BI 报表。  
  
- [下载 Power BI Report Template for Connected Field Service for Dynamics 365 for Customer Engagement](http://download.microsoft.com/download/E/B/5/EB5ED97A-A36A-4CAE-8C04-333A1E463B4F/PowerBI%20Report%20Template%20for%20Connected%20Field%20Service%20for%20Microsoft%20Dynamics%20365.pbix)  
  
 关于如何自定义内容包的信息，请参阅[自定义 Dynamics 365 for Customer Engagement 应用 Power BI 内容包](customize-power-bi-content-packs.md)。 
  
<a name="BPI_embed"></a>   
## <a name="embed-power-bi-visualizations-on-personal-dashboards"></a>在个人仪表板中嵌入 Power BI 可视化  
 必须先启用组织范围内的设置，用户才能在个人仪表板中嵌入 Power BI 可视化。  
  
> [!NOTE]
>  默认情况下，Power BI 可视化嵌入已禁用，用户必须将其嵌入个人仪表板中，才能启用。  
  
### <a name="enable-power-bi-visualizations-in-the-organization"></a>在组织中嵌入 Power BI 可视化  
  
1. 以拥有系统管理员安全角色的用户的身份登录 Dynamics 365。  
  
2. 转到**设置** > **管理** > **系统设置**。  
  
3. 在**报告**选项卡上的**允许 Power BI 可视化嵌入**选项中，选择**是**即启用，选择**否**则禁用。  
  
4. 选择**确定**。  
  
若要了解有关如何向个人仪表板添加 Power BI 磁贴的详细信息，请参阅[在个人仪表板中嵌入 Power BI 磁贴](/dynamics365/customer-engagement/on-premises/basics/add-edit-power-bi-visualizations-dashboard.md#embed--power-bi-tiles-on-your-personal-dashboard)。  
  
若要了解有关如何向个人仪表板添加 Power BI 仪表板的详细信息，请参阅[在个人仪表板中添加 Power BI 仪表板](/dynamics365/customer-engagement/on-premises/basics/add-edit-power-bi-visualizations-dashboard.md)。  
  
<a name="CRMOnline_PBIDesktop"></a>   
## <a name="use-power-bi-desktop-to-connect-directly-to-your-instance"></a>使用 Power BI Desktop 直接连接到实例。  
 您可以使用 Power BI Desktop 连接到实例，以便 创建要与 Power BI 服务结合使用的自定义报表和仪表板。  
  
### <a name="requirements"></a>要求  
  
- Power BI 服务注册  
  
- Power BI Desktop  
  
- Dynamics 365 实例  
  
### <a name="connect"></a>连接  
  
1. 启动 Power BI Desktop。  
  
2. 从“主页”选项卡上，选择**获取数据**，然后选择**更多**。  
  
3. 在“获取数据”列表中，选择 **Dynamics 365 Online**。  
  
4. 输入 Dynamics 365 OData 终结点 URL。 它应看起来类似此 URL，其中 *OrganizationName* 是您的组织的名称，**v8.1** 是版本。 选择**确定**。  
  
    https://<em>OrganizationName</em>.api.crm.dynamics.com/api/data/*v8.1*  
  
> [!IMPORTANT]
> 有关不同终结点版本的详细信息，请参阅 [Web API URL 和版本]( https://msdn.microsoft.com/library/gg334391.aspx#bkmk_url_and_versions)。
 
> [!TIP]
>  您可以找到您的 OData 终结点 URL。 转到**设置** > **自定义** > **开发人员资源**，然后在**实例 Web API** 下找到该 URL。  
  
5. 在访问 OData 源对话中，选择**组织账户**，然后选择**连接**。  
  
   > [!NOTE]
   >  如果您无法登录到您的实例，请在“访问 OData 源”对话框中单击**登录**，再选择“连接”。  
  
6. 组织数据库实体表显示在 Power BI Desktop 导航器窗口中。 可以选择默认和自定义实体。 有关使用 Power BI Desktop 创建报表的详细信息，请参阅 [Power BI 支持：Power BI Desktop 中的报表视图](https://powerbi.microsoft.com/documentation/powerbi-desktop-report-view/)。  
  
   ![选择实体表](media/pbi-select-entity-table.PNG "选择实体表")  
  
   > [!TIP]
   >  使用类似步骤连接到 Dynamics 365，方法是选择 Excel 中 **Power Query** 选项卡上的**来自其他源**。  
  

