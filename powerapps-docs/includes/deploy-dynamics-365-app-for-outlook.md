---
title: 部署 Dynamics 365 App for Outlook | MicrosoftDocs
ms.custom: ''
ms.date: '2017-04-20'
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 09736e14-e744-48ca-a755-1b05bb55340e
caps.latest.revision: 39
author: jimholtz
ms.author: jimholtz
manager: brycho
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>部署 Dynamics 365 App for Outlook
用户在桌面、Web 或平板电脑中使用 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 时，可以通过 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] 体验 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 的强大功能。 例如，查看有关电子邮件或约会收件人的信息，或者将 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 电子邮件或约会链接到 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 记录，例如商机、客户或案例。 若要了解 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] 的功能，请参阅 [Dynamics 365 App for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=613099)。  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 与 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] 不一样。 从 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] 开始，[!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] 搭配 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] 是首选的 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 与 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 集成方法。 **请注意，当 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 和 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] 由同一用户同时使用时不支持跟踪活动。** 有关 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] 加载项的信息，请参阅 [Dynamics 365 for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=524751)。  
>   
>  [委派用户](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540)无法使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 跟踪电子邮件。 建议为委派用户使用[文件夹级别的跟踪或自动跟踪](https://www.microsoft.com/en-us/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx)。  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>比较 Dynamics 365 App for Outlook 与 Dynamics 365 for Outlook  
 下表比较 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 功能与 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] 的 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]（也称为 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 客户端或加载项）。  
  
||||  
|-|-|-|  
|**功能**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|跟踪并设置电子邮件的相关项|是|是|  
|跟踪并设置约会的相关项|是|是|  
|跟踪并设置联系人的相关项|是|是|  
|跟踪并设置任务的相关项|否|是|  
|一键式设置相关项|是|否|  
|显示收件人摘要|是|否|  
|显示电子邮件/约会中的相关记录摘要|是|否|  
|与 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] 一起使用|是|否|  
|使用 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 桌面|是|是|  
|与适用于 Mac 的 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 一起使用|是|否|  
|与手机一起使用|是|否|  
|直接打开并创建 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 记录|是|是|  
|应用自定义窗体和业务逻辑|是|是|  
|脱机工作|否|是|  
|应用电子邮件模板|是|是|  
|应用销售宣传资料|是|是|  
|应用知识文章|是|是|  
|可以在发送后监视电子邮件|是|否|  
|排序、筛选、格式化、分组和分类视图|否|是|  
|创建 Word 邮件合并文档|否|是|  
|控制字段同步|否|是|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>要求  
 以下是使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 时必须具备的条件：  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] 或 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   通过服务器端同步以同步传入电子邮件。 [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][设置电子邮件、约会、联系人和任务的服务器端同步](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   如下所述的必需权限  
  
> [!NOTE]
>  我们的文档中列出了 [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] 功能的支持配置和要求。 应将未记录的特定配置视为不受支持。  
  
### <a name="required-privileges"></a>所需权限  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] 通过**使用 Dynamics 365 App for Outlook**权限提供对 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 的访问。 如果用户没有该权限，则他们会收到以下错误消息：  
  
> “您未被授权使用此应用程序。 请与您的系统管理员核查以更新您的设置。”  
  
 用户还必须具有对下列实体的读写权限。  
  
 “业务管理”选项卡：  
  
-   **邮箱**  
  
 “自定义”选项卡：  
  
-   **实体**  
  
-   **字段**  
  
-   **关系**  
  
-   **系统应用程序元数据**  
  
-   **系统窗体**  
  
-   **用户应用程序元数据**  
  
-   **视图**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>为安全角色设置权限  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  单击**安全角色**。  
  
3.  选择安全角色，然后单击**业务管理**选项卡。  
  
4.  在**实体**部分，检查**邮箱**权限设置。 安全角色应具有“用户”或更高的设置。  
  
5.  在**与隐私相关的特权**部分，验证**使用 Dynamics 365 App for Outlook** 是否已设置为**组织**。 如果未设置，请单击**使用 Dynamics 365 App for Outlook**。  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Microsoft Exchange 支持的配置  
 自 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] 起，您可以将该应用程序与任何 [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] 或 [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] 和 [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] 或 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]（本地）的组合结合使用，包括混合配置。 这意味着您可以在以下任何配置中使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]：  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]（内部部署）|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]（内部部署）|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  如果您使用 [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]，则您需要使用 IFD 身份验证进行验证（如下所述）。  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>Web 上 Outlook 支持的浏览器  
 您可以在以下浏览器中使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 和 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]：  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)]、[!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)] 或 [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     以下配置受支持：  
  
    -   为 **Internet** 安全区域启用保护模式。 若要启用保护模式：在 IE 10 或 11 中，转至**工具** > **Internet 选项** > **安全选项卡** > **Internet**。  
  
    -   将为**本地内联网**安全区域启用保护模式。 若要启用保护模式：在 IE 10 或 11 中，转至**工具** > **Internet 选项** > **安全选项卡** > **本地 Internet**。  
  
    -   您的 [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] URL 在可信网站的**本地内联网**安全区域列表中。 在 IE 10 或 11 中，转至**工具** > **Internet 选项** > **安全选项卡** > **本地内联网** > **站点** > **高级**。  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)] 上的 [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)]（最新版本）  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)] 上的 [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)]（最新版本）  
  
-   [!INCLUDE[tn_apple](../includes/tn-apple.md)] Mac 或 OSX 上的 [!INCLUDE[tn_Safari](../includes/tn-safari.md)]（版本 9 或 10）  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>台式机上 Outlook 支持的操作系统  
 您可以在台式机的这些版本的 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 上使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]：  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 和 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016。  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] for Mac*。  
  
     需要 *[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 版本 15.0.847.32 或更高版本。  
  
### <a name="supported-mobile-devices"></a>支持的移动设备  
 可以在以下任何手机和操作系统上的移动浏览器中将 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 与 [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] 配合使用：  
  
-   运行 iOS 版本 8、9 或 10 的 [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_iphone](../includes/tn-iphone.md)] 设备。  
  
-   运行 [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4 (KitKat)、5.0 (Lollipop)、6 (Marshmallow) 或 7 (Nougat) 的 [!INCLUDE[tn_android](../includes/tn-android.md)] 手机。  
  
-   运行 [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] 或 [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)] 的 [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] 设备。  
  
### <a name="supported-clients-per-feature"></a>每项功能支持的客户端  
 支持的 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 功能取决于您运行的客户端。 下表汇总了 [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 和 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 的每个客户端/配置支持的功能。  
  
 ![各 Dynamics 365 App for Outlook 功能支持的客户端](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "各 Dynamics 365 App for Outlook 功能支持的客户端")  
  
 (1)  [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] 支持 [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)]、[!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)]、[!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]、[!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9、[!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10、[!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] 和 [!INCLUDE[tn_chrome](../includes/tn-chrome.md)]。  
  
 (2)  Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] 支持 [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)]、[!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)]、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 8、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 9、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 10、[!INCLUDE[tn_android](../includes/tn-android.md)] KitKat (4.4)、[!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop、[!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow 和 [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat。  
  
 (3)  撰写模式中的跟踪电子邮件和跟踪约会需要 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 CU14 或 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016。  
  
 (4)  跟踪联系人仅在 [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]2016 CU3 和 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 及更高版本上受支持。  
  
 (5)  Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] 不支持添加电子邮件模板、知识管理文章和销售宣传资料。  
  
 (6)  仅在 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 和更高版本上受支持。  
  
 (7)  仅在 16.0.6741.1000 和更高版本上受支持。  
  
> [!NOTE]
>  目前不支持平板电脑（2017 日历年度即将推出）。  
  
 [阅读此博客中有关支持的客户端的更多详细信息：Dynamics 365 App for Outlook 支持矩阵](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>支持的服务器  
 [使用 Office 加载项的服务器要求](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins)为 [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)]、[!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)] 或 [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]。  
  
### <a name="supported-languages"></a>支持的语言  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 支持以下语言：  
  
||||  
|-|-|-|  
|保加利亚语（保加利亚）- 1026|印地语（印度）- 1081|葡萄牙语（葡萄牙）- 2070|  
|中文（中华人民共和国）- 2052|匈牙利语 - 1038|罗马尼亚语 - 1048|  
|中文（中国台湾）- 1028|印度尼西亚语 - 1057|俄语 - 1049|  
|克罗地亚语（克罗地亚）- 1050|意大利语 - 1040|塞尔维亚语 - 2074|  
|捷克语（捷克共和国）- 1029|日语 - 1041|斯洛伐克语 - 1051|  
|丹麦语 - 1030|哈萨克语 - 1087|斯洛文尼亚语 - 1060|  
|荷兰语 - 1043|朝鲜语 - 1042|西班牙语 - 3082|  
|英语 - 1033|拉脱维亚语 - 1062|瑞典语 - 1053|  
|爱沙尼亚语 - 1061|立陶宛语 - 1063|泰语 - 1054|  
|芬兰语 - 1035|马来西亚语 - 1086|土耳其语 - 1055|  
|法语 - 1036|挪威语 - 1044|乌克兰语 - 1058|  
|德语 - 1031|波兰语 - 1045|越南语 - 1066|  
|希腊语 - 1032|葡萄牙语（巴西）- 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>部署 Dynamics 365 App for Outlook  
 设置 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] 及所需权限后，您可以将 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 推送到部分或所有用户，也可以允许用户根据需要自行安装它。  
  
> [!NOTE]
>  如果您在 [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)] 上，请参阅以下部分：[部署到 Dynamics 365 本地用户](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>将应用程序推送给用户  
  
1.  转到**设置** >  **Dynamics 365 App for Outlook**。  
  
2.  在 **Dynamics 365 App for Outlook 入门**屏幕中，在**为符合资格的用户添加**下面，（如果第二次或后续时间打开此屏幕，可能需要单击**设置**），选中**将应用程序自动添加到 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]** 复选框（如果您想让用户自动获取应用程序）。 如果用户具有必要的权限，而且电子邮件通过 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] 同步，您不必再执行任何操作即可将应用程序推送到他们。 例如，如果您向销售员角色添加必需的权限，然后将该角色分配给新用户，则他们将自动获取应用程序。  
  
3.  执行下列操作之一：  
  
    -   若要将应用程序推送给所有符合资格的用户，请单击**为所有符合资格的用户添加应用程序**。  
  
    -   若要将应用程序推送给某些用户，请在列表中选择这些用户，然后单击**将应用程序添加到 Outlook**。  
  
    > [!TIP]
    >  如果列表显示某个用户已挂起或还未添加，您可以单击该用户旁边的**了解更多**链接查找有关状态的详细信息。  
  
4.  完成后，请单击**保存**。  
  
#### <a name="to-have-users-install-the-app-themselves"></a>让用户自行安装应用程序  
  
1.  用户单击**设置**按钮 ![设置按钮](media/mp-ua-r16-settings.png "设置按钮")，然后单击 **Dynamics 365 应用**。  
  
2.  在 **Dynamics 365 应用程序**屏幕中，在 **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]** 下面，用户单击**将应用程序添加到 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]**。  
  
> [!NOTE]
>  如果需要，用户还可以自行禁用或删除加载项。 有关更多信息，请参阅 [Dynamics 365 App for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=613099)。  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>部署到 Dynamics 365 本地用户  
 如果使用的是 Dynamics 365 本地部署，请执行以下步骤。  
  
-   将您的 Dynamics 365 Server 配置为面向 Internet 的部署。 请参阅[为 Microsoft Dynamics 365 配置 IFD](https://technet.microsoft.com/library/dn609803.aspx)。  
  
-   如果您要连接到 Exchange 本地部署，请配置 OAuth 提供程序和注册客户端应用程序。 参阅[配置使用 OAuth 的 Windows Server 2012 R2 for Dynamics 365 应用程序](https://technet.microsoft.com/library/hh699726.aspx)。  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>解决安装问题  
 如果您或您的用户安装 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 时遇到困难，可能是因为他们的 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 邮箱当前链接到其他 [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 组织。 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 邮箱（电子邮件地址）只能同步一个组织的约会、联系人和任务，并且属于该组织的用户只能用 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 邮箱同步约会、联系人和任务。  如果要更改主要同步组织，可以覆盖 [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] 中存储的设置。 有关更多信息，请参阅[此知识库文章。](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook)  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>浏览用户指南和培训用户  
 若要了解如何使用 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]，[请参阅 Dynamics 365 App for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=613099)。  
  
 ![Dynamics 365 App for Outlook 用户指南页](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Dynamics 365 App for Outlook 用户指南页")  
  
## <a name="see-also"></a>另请参阅  
 [Dynamics 365 App for Outlook 用户指南](http://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [阅读此博客中有关支持的客户端的更多详细信息：Dynamics 365 App for Outlook 支持矩阵](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [设置电子邮件、约会、联系人和任务的服务器端同步](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [添加用户、许可证和安全角色](http://msdn.microsoft.com/en-us/23612155-f92d-4871-a109-186419d5c19d)   
 [向 Microsoft Dynamics 365（联机）添加互操作功能](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)